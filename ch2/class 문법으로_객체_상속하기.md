#### 📚 객체지향은 왜 쓰는것인가?
> 💡 객체지향은 왜 쓰는것인가?
* 이유1 : 여러 객체를 편하게 생성하고자 사용하는 것.

#### 📚 class 문법으로 구현하는 constructor
> 💡 class란? 
* constructor, prototype를 이용한 상속기능을 구현하도록 도와주는 문법.
```js
class 부모 {
  	constructor(name){
      	this.name = name;      
>
  		this.sayHi1 = function() { console.log('Hello') } 
      	// 함수를 추가하는 방법1 : 자식은 이 메소드를 상속받는다. 
    }
>
  	sayHi2(){
      	console.log('Hello')
	}
  // 함수를 추가하는 방법2 : 자식에게 직접 상속되지 않는다. 위 함수는 부모 prototype에 추가된다.
}
>
부모.protype.sayHi3 = function {console.log('Hello')} 
// 함수를 추가하는 방법3 : 위 함수는 부모 prototype에 추가된다.
>
var 자식 = new 부모('Kim');
```
####

#### 📚 class 를 복사하는 방법 1 : Extends 
> 💡 extends란? 
* **기존**에 생성되어 있는 **class**와 **유사한** **class**를 추가적으로 생성하고 싶을 때 사용함. 
>
```js
class 할아버지 {
  	constructor(name){
      	this.surName = 'Kim';
      	this.firstName = name;
	}
>
  	sayHi(){ // 할아버지 객체 prototype에 저장됨.
      	console.log(`안녕 나는 할아버지`);
	}
}
>
var 할아버지1 = new 할아버지('만덕')
>
class 아버지 extends 할아버지{
  constructor(name){
    super(name);
    this.나이 = 50;
  }
}
```
####

#### 📚 class 를 복사하는 방법2 : Super
> 💡 super란?
* **extends로 상속**중인 **부모 class**의 **constructor()**를 의미한다.
>
```js
class 아버지 extends 할아버지 {
  	constructor(name){
		super(name) // 할아버지 class의 constructor()와 같은 값을 가진다. 
		this.age = 50;
	}
>
  	sayHi(){ // 아버지 객체 prototype에 저장됨.
      	console.log(`안녕 나는 아버지`); // 출력 : 안녕 나는 아버지
		super.sayHi() // 출력 : 안녕 나는 할아버지
		// 두 코드가 모두 출력됨. 
	}
}
>
var 아버지1 = new 아버지('만수')
아버지1.sayHi()
```
####