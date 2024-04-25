
```html
<script>
	//a
	console.log(this);
	//b
	function a() {
		console.log(this)
	}

	let obj = {
		userName: 'Ning',
		fn: function() {
			console.log(this)
		}
	
	}
	//c
	obj.fn()

	var obj2 = {
		userName:'Amy',
		fn1: function() {
			console.log(this.userName);
		}
	}

	//d
	window.obj2.fn1()

	var obj3 = {
		a:10,
		b:{
			a:12,
			fn: function() {
				console.log(this)
			}
		}
	}

	//e
	obj3.b.fn()

	var id = 66;
	function fn5(){
		setTimeout(()=>{
			let that = this
			console.log(that.id)
		},500)
	}

	//f
	fn5({id:22})

	延伸題，如果要讓fn5印出帶入的值呢？要怎麼修改？
</script>
```
請問各印出什麼？
a: window
b: window
c:```
```
{userName: 'Ning', fn: ƒ}

1.  fn: ƒ ()
2.  userName: "Ning"
3.  [[Prototype]]: Object
```
d: 'Amy'
e:{a:12,fn:f}
f:66
g:給this一個作用域，使用call
如何使用let that = this ??
https://pjchender.dev/javascript/js-arrow-function/