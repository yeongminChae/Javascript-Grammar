#### 📚 ?. / ?? 연산자 (optional chaining)
> 💡 optional chaining('.?')이란
* '?.'왼쪽에 존재하는 자료형이 null혹은 undefined인 경우 마침표 찍지 말고 undefined로 남겨줌
* 객체 자료형들이 중첩되어 있는 자료에서 데이터를 뽑을 때 reference에러 없이 안전하게 데이터를 뽑을 수 있게 해줌
* ?. 이건 에러를 해결해주는 문법이 아니라 에러나지 않게 감추는 문법
```js
// 중첩된 객체 자료형
var user = {
    name : 'kim',
    age : { value : 20 }
}
>
console.log(user.age.value);    
// 이 경우 object안에 있는 자료형을 찾기 위해서 . 을 이용해야 하는데, 여기서 잘못 입력하면 에러 발생
console.log(user.age1.value1) // 에러 발생
console.log(user.age1?.value1) // 에러를 리턴하는 대신 undefined를 리턴해줌
// 간단한 object에서 데이터뽑을 때 해당하는 자료가 없으면 자동으로 undefined가 남아서 중첩된 객체가 아니고선 사용할 필요가 없음   
```
####
> 💡 ?? nullish coalescing operator
```js
var user;
console.log(user ?? '로딩중') // ?? 왼쪽이 null, undefined 일 경우 로딩중을 리턴해달라는 뜻
```