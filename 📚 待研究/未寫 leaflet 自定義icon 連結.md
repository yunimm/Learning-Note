
iconUrl這段載入時會找不到圖片,原本的程式碼
```
iconUrl:

'../src/assets/user-position.png',

iconSize: [50, 50],

})
```
改成這個寫法就可以
```
function userMark() {

const myIcon = L.icon({

iconUrl:

'https://raw.githubusercontent.com/yunimm/bicycle-app/main/src/assets/user-position.png',

iconSize: [50, 50],

})

map.eachLayer(function (layer) {

if (layer instanceof L.Marker) {

map.removeLayer(layer)

}

})

L.marker([lat.value, lng.value], { icon: myIcon })

.bindPopup(

'<h2 class="text-base text-primary-500 font-bold">目前位置</h2>',

{ closeButton: false }

)

.addTo(map)

}
```