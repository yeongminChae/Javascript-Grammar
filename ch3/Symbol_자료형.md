#### 📚 Symbol 자료형
* Symbol 자료형은 enumerate하지 않음.
* Symbol('설명'), '설명'이 같게 작성되더라도 해당 '설명'을 사용하는 심볼들은 같은 데이터들이 아님.
* 전역 심볼 작성법 => var a = Symbol.for('설명')
* Array, Object 자료형을 만들 때 몰래 붙어있는 기본 Symbol들도 있음. (array 자료형은 [Symbol.iterator]라는 이름을 가진 심볼이 안에 있음.)
> 💡 Symbol 자료형 만드는법
```js
var 심볼 = Symbol('설명')
>
var person = { name: 'Kim' };
>
// 해당 객체에 비밀스런 데이터를 저장하고 싶을 때
var weight = Symbol('secret weight')
person[weight] = 100 // 이렇게 작성되면 반복문등에서 공개되지 않음
>
// 두 번째 symbol 작성법
var height = Symbol('my height')  
var person2 = { name: 'park', [height]: 160 };
>
// 전역 심볼
var a = Symbol.for('설명')  // 전역 심볼
```