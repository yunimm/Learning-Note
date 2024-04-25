[code](https://codesandbox.io/s/css-wen-ti-ji-zhi-zhong-de-fang-fa-z7kw55?file=/q2/styles.css)
1. 快速置中的方式：
```css
使用flex
main {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
}
使用定位
main {
	height: 100vh;
	position: relative;
}
.box {
	width: 100px;
	height: 100px;
	background-color: red;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translateY(-50%);
}
使用grid 
main {
	height: 100vh;
	display: grid;
	align-items: center;
	justify-content:center;
}
```
2.  padding和margin的差異：
   - padding是調整border內的間距，margin是調整border外的距離，會影響到其他元素。
3. vw和%差別：
   - vw是目前視窗的寬度，數值會隨著視窗大小變動。%是相對父元素寬度的數值，假設父元素寬度為 100px，子元素寬設為50%則子元素寬度＝100px * 50%=50px
5.  inline 和 block差別：
   - block可以包住inline但inline不能包住bloclk。inline不能設定高度和寬度由元素決定高寬，可以設定padding，但設定margin時只會影響左右，不會影響上下。block可以設定且默認情況下繼承父層的寬度即寬度100%
6. 如何讓瀏覽器使用比預設字級更小的字體：
```css
transoform:scale(0.X)
```
