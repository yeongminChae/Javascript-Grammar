#### ES6 Spread Operator란? '...'으로 작성되는 문법으로, 쉽게말해 '괄호'들을 제거해 주는 연산자이다.

#### 배열에서
```js
var array = ['hello', 'world'];
console.log(array); // 출력 : (2) ['hello', 'world']
console.log(...array); // 출력 : hello world

var 문자 = 'hello';
console.log(문자); // 출력 : hello
console.log(문자[0]); // 출력 : h
console.log(문자[1]); // 출력 : e

// 활용 예시(1) 배열 합치기
var a = [1,2,3];
var b = [4,5];
var c = [...a, ...b];

console.log(c) // 출력 : (5) [1, 2, 3, 4, 5]

// 활용 예시(2) 배열 복사
var a = [1,2,3];
var b = a;

console.log(a); // 출력 : (3) [1, 2, 3]
console.log(b); // 출력 : (3) [1, 2, 3]
// 그런데 이렇게 값을 복사하면 문제가 되는게, 만약 내가 a의 값을 수정하면 b또한 값이 바뀝니다.
// 이는 a의 값들을 복사하는게 아니라 메모리상에서 a가 가르키고 있는 위치를 공유하는 것이기 때문입니다.
// 따라서 다음과 같은 경우는 각각 고유의 값을 갖고 있는것이 아니고 a의 값을 공유하고 있는 것 입니다.

var a = [1,2,3];
var b = [...a]; // spread를 사용해서 복사 해주면 값 공유가 일어나지 않습니다.

console.log(a); // 출력 : (3) [1, 2, 3]
console.log(b); // 출력 : (3) [1, 2, 3]

a.push(4)

console.log(a); // 출력 : (4) [1, 2, 3, 4]
console.log(b); // 출력 : (3) [1, 2, 3]

```

#### 객체에서
```js
var o1 = { a:1, b:2 };
var o2 = { c:3, ...o1 }
console.log(o2); // 출력 : {c: 3, a: 1, b: 2}

// 참고(1) : 오브젝트의 key값 중복이 발생하면?
var o1 = { a : 1, b : 2};
var o2 = { a : 3, ...o1 };
console.log(o2); // 출력 : {a: 1, b: 2}, 다음과 같이 중복이 발생할 경우, 뒤에 오는 키값으로 기존 값이 대체 됩니다.

// 참고(2) : spread는 함수소괄호, 오브젝트 중괄호내, 어레이 대괄호내에서 보통 사용해야 한다.
```

#### 함수에서
```js
// 배열과 같은 요소를 함수의 파라미터로 사용하고 싶을 때 
function 더하기(a, b, c) {
	console.log(a + b + c)
}
var array= [10, 20, 30]
더하기(...array) // 출력 : 60
```

#### apply, call 메소드
```js
// apply는 이 메소드를 다른 메소드에도 적용시켜주는 역할을 함.
var person = {
  	greeting: function() {
      	console.log(this.name + 'hello')
	}
}

var person2 = {
  	name: '손흥민'
}

// 여기에서 person에서 만들어둔 greeting을 person2에서 사용하고 싶을 때?
person.greeting.apply(person2); // 출력 : '손흥민hello'

// call 이라는 메소드도 있는데 이는 apply와 비슷하게 작동함.
var person = {
  	greeting: function() {
      	console.log(this.name + 'hello')
	}
}

var person2 = {
  	name: '손흥민'
}

person.greeting.apply(person2) // 출력 : '손흥민hello'
person.greeting.call(person2) // 출력 : '손흥민hello'

// apply VS call 
// apply는 파라미터를 [array]로 값을 할당할 수 있고, call은 그냥 1,2,3 이런식으로 일반 함수처럼 만 할당할 수 있다. 
// ex)

person.인사.apply(person2, [1,2,3]);
person.인사.call(person2, 1,2,3);

// 아까 함수 복사에 사용한 함수
function 더하기(a, b, c) {
	console.log(a + b + c)
}
var array= [10, 20, 30]
더하기(...array) // 출력 : 60
더하기.apply(undefined, array) // 출력 : 60 (이렇게 작성하는 것도 가능)
// undefiend는 값이 아무곳에도 적용되어 실행되지 않게 하기 위해 적은 내용.
``` 