---
date : 2022-06-0116:39
aliases : []
---
# Metadata
Status :: #ð± <br>
Note Type :: #ð¨/ð¿ <br>
Source URL :: <br />
[Closures in JS ð¥ | Namaste JavaScript Episode 10](https://www.youtube.com/watch?v=qikxEIxsXco&t=275s) <br />
[ExplaninThis](https://www.explainthis.io/zh-hant/interview-guides/javascript/what-is-closure)<br>

Author :: [[@Akshay Saini]]  [[@ExplanThis]]<br>
Topics :: [[-Javascript moc]] <br>
# Evergreen Note

Question :: éé¨æå­¸ä¸»è¦å¨èªªä»éº¼ ?

Answer :: æ·±å¥æ·ºåºéåçæ¦å¿µãåçãç¨æ³
- [x] [çè§£éååºæ¬æ¦å¿µ ](https://youtu.be/qikxEIxsXco?t=675)
- [x] [çè§£éåæç¨ ](https://pjchender.blogspot.com/2017/05/javascript-closure.html)
- [ ] çè§£éåé²éç¨æ³
---

# Summary 
éåæ¯ä»éº¼ï¼å®£åfunctionæï¼functionå°å¶è©æ³ç°å¢ç¶å®(è¨ä½äºå®£åæçä½ç¨åç°å¢)ï¼ä½¿å¾å§å±¤functionå¯ä»¥å¼ç¨å¤é¨è®æ¸ï¼ä¸¦ä¸è¨ä½éåè®æ¸ãå çºè½å¤ è¨ä½éåå¤é¨è®æ¸ï¼éåå¾å¸¸è¢«ç¨ä¾åçæä¿å­ã
éåçæç¨ï¼
- çæä¿å­ï¼ä¾å¦Reactä¸­ç`useState` æ¨¡æ¬ä¸åç°¡åççÂ `useState` :
```javascript
function useState(initState) {
	let state = initState;
	
	function getState(){
		return state;
	}
	function setState(updateState) {
		state = updateState;
	}

	return [getState, setState];
}
const [count, setCount] = useState(3);

count();//3
setState(5);//5

```
- è®æ¸ç§æå : ææåæåå¨éç¼æï¼æäºè®æ¸ä¸¦ä¸æ³è®å¤é¨ä¾å­åï¼æä»¥éè¦è®æ¸ç§æåçæ¹æ³ä½JSä¸¦ä¸æ¯æ´è®æ¸ç§æåï¼æåå¯ä»¥éééåçæ¹å¼ååºé¡ä¼¼çåè½ï¼
```javascript
// privateCounter æ²è¢«æ³è¢«å¤é¨ä¿®æ¹
// å çºéåçéä¿ increment è decrement å¯ä»¥å­åå° privateCounter
// å æ­¤ privateCounter åªè½å¤ éé increment è decrement ä¾æ¹ï¼éè½ææé¿åè¢«èª¤è§¸å°
const counter = (function() {
  let privateCounter = 0;

  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    },
  }
})();

console.log(counter.value()); // logs 0
counter.increment();
counter.increment();
console.log(counter.value()); // logs 2
counter.decrement();
console.log(counter.value()); // logs 1
```
- ç·©å­æ©å¶ï¼ä¸è¬å½æ¸çè©æ³ç°å¢å¨å½æ¸è¿åå¾å°±è¢«é·æ¯ï¼ä½æ¯éåæä¿å­å°åµå»ºææå¨è©æ³ç°å¢çå¼ç¨ï¼å³ä¾¿åµå»ºææå¨çå·è¡ä¸ä¸æè¢«é·æ¯ï¼ä½åµå»ºææå¨è©æ³ç°å¢ä¾ç¶å­å¨ï¼ä»¥éå°å»¶é·è®éççå½é±æçç®çã
  [ç¯ä¾1](https://hackmd.io/@wheat0120/javascript-memoization)
```javascript
function getTool(todoTask) {
  const doneCache = {};
  return function (){
    const taskContent = JSON.stringify(arguments);

    if(doneCache[taskContent]) {
      return doneCache[taskContent];
    } else {
      const taskResult = todoTask.apply(this,arguments);
      doneCache[taskContent] = taskResult;
      return taskResult;
    }
  }
};

const work = getTool((task) => {
    console.log('åå¾ååº«æ¿å·¥å·')
    return task + ': å·²å®æå·¥ä½'
})


console.log('Day1', work('ä¿®çé¦¬æ¡¶'));
console.log('Day2', work('ä¿®çé¦¬æ¡¶'));
console.log('Day3', work('ä¿®çå±é '));

```
[ç¯ä¾2](https://www.explainthis.io/zh-hant/interview-guides/javascript-whiteboard/cache-function)
ä¸ç¢ºå®æå¸¶å¥å¹¾ååæ¸ï¼å¯ä»¥ä½¿ç¨å±ééç®å­çå¯«æ³ï¼æå°æ¸çµè½ææåæ¸
``` javascript
let args = [1, 2, 3];

function add(a, b, c) {
  return a + b + c;
}

console.log(add(...args)); // Output: 6

```

``` javascript
function cached(fn) {
  // è²æä¸å cache ç©ä»¶ï¼éé cache ä¾æ¾ç·©å­çæ±è¥¿
  // å çºéåçç·£æï¼ä¸é¢åå³çå½å¼å¯ä»¥å­åå°éå cache è®æ¸
  const cache = {};

  // ééæ´å±éç®ç¬¦ï¼æ¿å°å¼æ¸
  return (...args) => {
    // å°å¼è¿°ç¶ä½ç·©å­ç key
    const key = JSON.stringify(args);
    // æ¥çç¾å¨çç·©å­ææ²æéå keyï¼æçè©±å°±ä¸ç¨åç®ï¼ç´æ¥åå³
    if (key in cache) {
      return cache[key];
    } else {
      // æ²æçè©±ï¼å°±ææ¶å°å¼æ¸å¸¶å¥ï¼éç®åºçµæ
      const val = fn(...args);
      // æçµææ¾å¥ç·©å­ï¼ä¸æ¬¡æåæ¨£ç key å°±ä¸ç¨éæ°éç®
      cache[key] = val;
      return val;
    }
  };
}
```
éåçç¼ºé»ï¼
- å§å­æ³é²

---

# Note

ç¯ä¾ä¸ï¼
```js
function outer() {
	const x = 10
	function inner() {
		console.log(x)
	}
	return inner
}
const z = outer()
console.log(z)
z()
```

ç¯ä¾äºï¼
1. å¨å¨åå»ºç«åçºdogHouseçfunction
2. å°æ¸å­0å­å¨è®æ¸count
3. return ä¸åå¿åfunctionï¼å¸¶å¥åæ¸nameï¼ç¶functionè¢«å·è¡count+1ä¸¦å°åºcount nameå­ä¸²
4. å¨å¨åå»ºç«dogCountçå¸¸æ¸ï¼å°dogHouse functionè³¦å¼çµ¦å®
5. å·è¡dogCountä¸¦å¸¶å¥åæ¸dogå­ä¸²

```js

function dogHouse () {
	let count = 0;
	return (name) => {
	count += 1;
	console.log(`${count}${name}`);
	};
};

const dogCount = dogHouse()

dogCount('dog'); //1dog
dogCount('dog');//2dog
dogCount('dog');//3dog

const catCount = dogHouse()

catCount('cat'); //1cat
catCount('cat');//2cat
catCount('cat');//3cat
```
æ­¥é©äºå¸¶å¥çå­ä¸²å°æreturnçå¿åfunctionçåæ¸ï¼å¦æä»å¤©æ¯å¨dogHouse function å¸¶å¥åæ¸å...

```js
function dogHouse (name) {
	let count = 0;
	return () => {
	count += 1
	console.log(`${count}${name}`)
	};
};

const dogCount = dogHouse('dog')

dogCount()
dogCount()
dogCount()
```



