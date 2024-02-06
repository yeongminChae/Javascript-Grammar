#### 📚 ES5 방식으로 쉽게 구현하는 상속기능
> 💡 Object.create(prototype 객체)란?
```js
var 부모 = { name: 'Kim', age: 50 };
var 자식 = Object.create(부모);
자식.age = 20;
>
console.log(자식); // 출력 : {}
console.log(자식.name); // 출력 : Kim
console.log(자식.age); // 출력 : 20
>
var 손자 = Object.create(자식);
console.log(손자.name); // 출력 : Kim
console.log(손자.age); // 출력 : 20
```