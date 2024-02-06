#### 📚 함수를 만들어 객체내에 데이터를 다루는 이유
> 💡 함수를 만들어 객체내에 데이터를 다루는 이유
* 1. 객체 자료가 복잡할 때 데이터를 다루기 쉽다.
* 2. 내부에 있는 변수에 자료형을 직접 수정하지 않아서 실수를 방지할 수 있다.
```js
var 사람 = {
  	name : 'Park';
  	age : 30;
>
  	nextAge() {
    	return this.age + 1
  	},
 	setAge(age) {
    	this.age = parseInt(age); // parseInt : 문자형 변수를 정수형 변수로 수정해줌. 
  	},
>
사람.nextAge();
사람.setAge('20');
}
```
####

#### 📚 get, set 함수
> 💡 get이란?
* 내가 수정하고 싶은 데이터 변수에 할당되어 있는 **값을 가져**올 때 사용.
* get함수를 사용하면 반드시 **return**값이 있어야 한다.
>
> 💡 set이란?
* 내가 수정하고 싶은 데이터 변수를 지정하고 **값을 수정**할 때 사용.
* set함수는 반드시 하나 이상에 **파라미터**가 존재해야 한다.
####
```js
var 사람 = {
  	name : 'Park';
  	age : 30;
>
  	get nextAge() {
    	return this.age + 1
  	},
>
  	setAge1(age) {
    	this.age = parseInt(age);
  	},
  	set setAge2(age){
    	this.age = parseInt(age);
    },
}
>
사람.nextAge;
>
사람.setAge1('20');
사람.setAge2 = 20;
```
####

#### 📚 class에서 getter, setter 함수
> 💡 class에서 getter, setter 함수
```js
class 사람 {
  	constructor() {
      	this.name = 'Park';
      	this.age = 20;
    }
  	get getAge(){
      	return this.age + 1
    }
  	set setAge(나이){
      	this.age = 나이;
    }
}
>
var 사람1 = new 사람()
``` 
> 💡 정리
Q) 데이터 출력 / 수정 함수를 만들어 쓰는 이유는?
A) 🗣️ 데이터의 무결성 유지하기 위해서.
#####