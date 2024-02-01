
#### object 자료형 내에서
```js
var 오브젝트1 = {
  data : 'Kim',
  함수 : function(){ console.log(this) } 
}
오브젝트1.함수() // 출력값 : {data: 'Kim', 함수: ƒ} => 다음과 같이 메소드 안에서 this 키워드를 사용하게 되면 해당 메소드를 가지고 있는 객체를 리턴해준다.

var 오브젝트2 = {
  data : {
    함수 : function(){ console.log(this) }
  }
}
오브젝트2.data.함수(); // 출력값 : {간지함수: ƒ} => 함수라는 메소드를 가지고 있는 data객체를 리턴한다.
```

#### constructor 자료형 내에서
```js
// constructor안에서 사용하면 constructor로 생성되는 새로운 객체를 의미합니다.
// constructor 예시;
function 기계(){
  	this.이름 = 'Kim'; // 여기서의 this는 생성자(constructor)로부터 생성될 새로운 객체를 의미합니다.
}

// constructor를 통해서 새로운 객체를 생성하는 법
var 오브젝트 = new 기계() // 다음과 같이 new 키워드를 이용하면 새로운 객체를 생성할 수 있습니다.

```

#### eventlistener 안에서 쓰면
```js
document.getElementById('버튼').addEventListener('click', function(e){
  console.log(this) // 여기서 this는 e.currentTarget과 같은 뜻 즉, 현재 이벤트가 동작하는 곳을 의미
});
```