#### 📚 1. 자바스크립트 반복문
> 💡 자바스크립트 반복문
* 자바스크립트는 코드를 반복할 때도 사용하지만, Array * Object등에서 자료를 꺼내쓸 때도 사용
```js
for (var i = 0; i < 3; i ++){}
>
[1,2,3].forEach() // 배열 전용
>
for (var key in 오브젝트) {} // 오브젝트 전용 
>
for (var key of 자료형 ) {}  // iterable한 자료형 전용 
```
####

#### 📚 2. for ~ in 반복문
> 💡 for ~ in 반복문
* 객체에 있던 값들을 하나씩 꺼내 사용하고 싶을 때.
* enumerable(셀 수 있는지에 대한 여부)한 것만 반복해줌.
* 부모의 prototype도 출력해줌.
```js
var 오브젝트 = { name: 'kim', age: 30 }
>
for (var key in 오브젝트) { // for in 반복문은 객체에 저장된 자료형 개수만큼 반복됨
  	console.log(오브젝트[key])
}
>
class 부모 {
>
}
부모.prototype.name = 'Park';
>
var 오브젝트2 = new 부모();
>
for (var key in 오브젝트2) {
  	console.log(오브젝트2[key]) // 출력 : 'Park' 부모 prototype까지 출력
	오브젝트2.hasOwnProperty(key) // 오브젝트2가 직접 가지고 있는 값인지에 대한 여부 판정해주는 함수
}  
```
####

#### 📚 3. for ~ of 반복문
> 💡 for ~ of 반복문
* Array, 문자열, arguments, NodeList, Map, Set등에서 사용됨
* for ~ of는 iterable한 자료형에만 사용가능
* terable한 자료형? [Symbol.iterator]() 이라는 일종의 메소드를 가지고 있는 자료형들
```js
var array = [2,3,4,5]
>
for (var data of array) { 
  	console.log(data)
}
```
####

#### 📚 예제) for ~ of, for ~ in 활용 예제
> 💡 object자료의 key값에 오타를 제거하는 코드
* 🗣️ 답안
```js
var products = [
  {
    name1 : 'chair',
    price1 : 7000,
  },
  {
    name2 : 'sofa',
    price : 5000,
  },
  {
    name1 : 'desk',
    price3 : 9000,
  },
]; 
>
let newValue;
let newKey;
>
for (let item of products) {
  	for (let key in item) {
>      
      	if (isNan(parseInt(key.slice(-1))) == false ) {
>          
          	newValue = item[key];
          	newKey = key.slice(0, -1);
          	item[newKey] = newValue;
>          
          	delete item[key];
        }
    }
}
>
console.log(products)
```