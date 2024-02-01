#### Function
```
// 함수를 사용하는 이유

// 1. 동일하거나 유사한 기능을 구현하는 함수들을 정리하여, 재사용할 수 있도록 하기 위해.
// 2. 입출력 기능을 구현할 때 => 파라미터들에 값을 집어넣었을 때 무언가를 'return'하도록 하고 싶을 때.
```

#### Function in JavaScript

```js
// js에서 함수를 생성하는 방법

//(1)
function func1() { 
  	console.log('Hello World')
} 
//(2)
var func2() = function() {
  console.log('Hello World')
}
//(3)
var func3 = () => {
  console.log('Hello World')
}
```

#### Arrow Function
```js
// Arrow Function 장점 : 
// 1. 함수 본연의 기능을 직관적으로 나타내 준다. (함수를 보고 기능을 이해하기가 쉬어진다.)
// 2. 소괄호와 중괄호를 생략할 수 있다. => 더 단순하고 직관적으로 함수를 표현할 수 있다.
// ex)
var 표현법1 = (x) => { return x * 2 }
var 표현법2 = x => { return x * 2 } // 파라미터가 하나일 때
var 표현법1 = x => x * 2 // 중괄호 안 리턴문이 한 줄뿐일때

// Arrow Function 단점 : 
// Arrow Function과 일반 function은 용도가 항상 같지많은 않다.
// ex) Arrow Function을 사용하여 내부에서 this값을 쓸 때 단순히 function을 쓸때와는 값이 달라집니다.
var obj1 = {
  	함수: function() { console.log(this) }
}
obj1.함수() // 출력 값 : {함수: ƒ}

var obj2 = {
	함수: () => { console.log(this) }
}
obj2.함수() // 출력 값 : window

// 분석 : Arrow Function은 함수가 생성된 시점의 this를 가리킨다. 이를 Arrow Function 내부에 가져와서 사용하기 때문에 window가 출력된다. 
// 반면에, obj1에서 this는 obj1 객체 내에서 익명 함수인 function()이 호출되는 컨텍스트를 참조한다. 따라서 this는 function()을 포함하고 있는 obj1 객체를 가리키게 되며, 이 때문에 {함수: ƒ}가 출력됩니다. 
```