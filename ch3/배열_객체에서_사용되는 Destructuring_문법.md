#### 📚 Destructuring 문법
> 💡 Destructuring 이란?
> 🤔 배열, 객체안에 있는 원소 전부를 변수로 설정하려면 ?
```js
// 배열에서
>
var [a,b,c] = [2,3,4]; // 출력 : a = 2, b = 3, c = 4
var [a,b,c = 10] = [2,3]; // default로 변수 설정 가능.
var [a,b,c] = [2,3]; // 출력 c : undefined
>
// 객체에서
>
var obj = { name : 'Kim', age : 30 }
var { name, age } = { name : 'Kim', age : 30 } // 객체에서는 변수명이 key값과 똑같아야함.
var { name: 이름 , age } = { name : 'Kim', age : 30 } // 생성되는 변수명을 name 에서 이름으로 변경.
```
####

> 💡 Destructuring 응용?
> 🤔 변수들을 배열, 객체안에 저장하려면?
```js
var name = 'Kim';
var age = 30;
>
var obj1 = { name : name, age : age };
var obj2 = { name, age }; // ES6부터는 key와 value가 같을경우 다음과 같이 작성 가능.
```
> 🤔 함수 파라미터 만들 때 사용하려면?
```js
var obj = { name : 'Kim', age : 30 };
>
function 함수( { name, age } ) {
	console.log(name);
  	console.log(age);
}
>
함수(obj);
```
####