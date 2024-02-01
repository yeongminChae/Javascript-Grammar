#### Primitive 자료형 : 할당된 값이 메모리에 바로 지정되는 값들 ex) 변수
```js
// Primitive 자료형
var 이름1 = 'kim';
var 이름2 = 이름1;
이름1 = 'park';
// 출력결과 : 이름1 = 'park', 이름2 = 'kim'
```

#### Reference 자료형 : 할당된 값이 메모리에 참조되는 자료형들 ex) 배열, 객체

```js
// Reference 자료형
var 이름1 = { name: 'kim' };
var 이름2 = 이름1;
이름1.name = 'park';
// 출력결과 : 이름1 = 'park', 이름2 = 'park'
// 이는 Reference 자료형은 데이터가 참조되어있는 공간을 서로 공유하기 때문에, 참조된 값을 공유하게 된다.

var 이름1 = { name : '김' };
var 이름2 = { name : '김' };
이름1 == 이름2 // false 
// 같은 값을 갖고 있지만, 메모리에 참조되어있는 공간은 서로 다르기 때문에 false가 출력된다. 

```