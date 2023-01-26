---
date : 2022-05-1304:55
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💣<br>
Author ::  <br>
Topics :: [[-Pinia moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
在進行bicycle app開發時，原本是將資料整合的寫法寫在getters裏再從組件呼叫執行，但後來發現重新運行瀏覽器時pinia無法正常運作，原本以為是pinia的bug，後來透過devtool發現store->getters裡的mixData()為undefined，所以判斷應該是這段程式碼出問題。

**測試**

我先將getters的方法註解，此時瀏覽器能夠順利載入actions拉取的api資料。

**解決流程**

先回過頭去研究什麼是getters，從官方範例中可以得知getter功能等同於computed，是進行計算的，原本以為資料整合應該是屬於computed，所以就將商業邏輯放在getters。
我將mixData()的語法搬到actions底下，沒有使用非同步寫法，我一樣在元件先呼叫getData()再呼叫mixData()，但是實際執行會發現執行順序不是預期的getData()->mixData()，這部分應該是非同步的關係。
爬文參考網路範例
```
 export const useUserStore = defineStore({
  id: 'user',
  actions() {
    async login(account, pwd) {
      const { data } = await api.login(account, pwd)
      this.setData(data) // 呼叫另一個 action 的方法
      return data
    },
    setData(data) {
      console.log(data)
    }
  }
})
```
上述範例中可以看到，我可以在actions裡呼叫另一個function，所以我將程式碼改成:
```
actions: {

async getData() {

try {

this.staticData = (await instance.get(

`api/basic/v2/Bike/Station/${this.city}?%24top=30&%24format=JSON`

)).data

this.dynamicData = (await instance.get(

`api/basic/v2/Bike/Availability/${this.city}?%24top=30&%24format=JSON`

)).data

console.log('getData執行了')

this.mixingData()

} catch(e) {

console.log(e)

}

},

mixingData(){

this.staticData.forEach((station) => {

this.dynamicData.forEach((item) => {

if (station.StationUID == item.StationUID) {

let obj = {

uId: station.StationUID,

id: station.StationID,

name: station.StationName,

status: item.ServiceStatus,

rent: item.AvailableRentBikes,

return: item.AvailableReturnBikes,

}

await this.newData.push(obj)

}

})

})

console.log('mixingData執行了')

}

}
```

使用async await先拉取資料再呼叫 mixdata()