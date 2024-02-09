#### 📚 1. Promise에 대해서
> 💡 Promise 정의
* 프로미스는 성공과 실패를 판단해주는 디자인 패턴 (성공시 then, 실패시 catch)
####
> 💡 Promise 작성하는 방법
```js
var 프로미스 = new Promise(function(성공, 실패) {
  성공() // 성공 판정 => then() 안에 코드 실행
});
>
프로미스.then(function(){
 	// ...
}).catch(function(){ // catch : 에러와 버그를 잡기 위한 메소드
  	// ...
});
>
```
####
> 💡 Promise 예시 1) 프로미스를 활용한 간단한 연산 코드 작성
```js
var 프로미스1 = new Promise(function(성공, 실패){
	var 연산 = 1 + 1;
  	성공() // 출력 : 성공했어요.
});  
>
프로미스1.then(function(){
  console.log('성공했어요');
}).catch(function(){
  console.log('실패했어요');
});
>
>
var 프로미스2 = new Promise(function(성공, 실패){
	var 연산 = 1 + 1;
  	실패() // 출력 : 실패했어요.
});  
>
프로미스2.then(function(){
  console.log('성공했어요');
}).catch(function(){
  console.log('실패했어요');
});
>
>
var 프로미스3 = new Promise(function(성공, 실패){
	var 연산 = 1 + 1;
  	성공(연산) // 이 처럼 변수를 파라메터로 보내면 then안에서 활용이 가능.
});  
>
프로미스3.then(function(결과){
  console.log('성공했어요' + 결과);
}).catch(function(){
  console.log('실패했어요');
});
```
####
> 💡 Promise 예시 2) 1초 대기 성공 후에 뭔가 실행하고 싶은 경우
```js
var 프로미스 = new Promise(function(성공, 실패){
	setTimeout(function() {
		성공() // 출력 : 성공했어요.
	}, 1000)
});  
>
프로미스.then(function(){
  console.log('성공했어요');
}).catch(function(){
  console.log('실패했어요');
});
>
```  
####
> 💡 Promise 특징
* 프로미스의 상태
    * 1. 성공시 : Promise {< resolved >}
    * 2. 실패시 : Promise {< pending >}
    * 3. 판정 대기중 : Promise {< rejected >}
* 프로미스에 대한 오해
    * 프로미스는 동기적으로 실행되는 코드를 비동기적으로 바꿔주는 문법이 아님, 프로미스는 콜백의 단점을 해소하기 위해 고안된 일종의 디자인 패턴임.
####
> 💡 Promise 가 사용된 문법
* fetch()
```js
fetch() // fetch는 프로미스가 내장되어 있으므로, 판정값을 사용할 수 있음
fetch().then().catch() // 이런식으로 코드 작성 가능
```
####

#### 📚 2. Promise 관련 예제
> 💡 Q1. < img > 이미지 로딩 성공시 특정 코드를 실행하고 싶습니다.
* HTML 안에 있는 이미지 로딩이 끝나면 무언가 코드를 실행하고 싶습니다. 
* < img id="test" src="https://codingapple1.github.io/kona.jpg" >
* 이 이미지가 로드가 되면 콘솔창에 성공, 로드가 실패하면 콘솔창에 실패를 출력하고 싶습니다.
####
> 🗣️ 답안
```js
<img id="test" src="https://codingapple1.github.io/kona.jpg" />
>
<script>
  const promise = new Promise((resolve, reject) => {
    const test = document.getElementById("test");
>    
    test.addEventListener("load", () => {
      resolve();
    });
>    
    test.addEventListener("error", () => {
      reject();
    });
  });
>
  promise
    .then(() => {
      console.log("이미지 로드 완료");
    })
>
    .catch(() => {
      console.log("이미지 로드 실패");
    });
</script>
```
####
> 💡 Q2. Ajax 요청이 성공하면 무언가 코드를 실행하고 싶습니다. 
* https://codingapple1.github.io/hello.txt 라는 경로로 GET 요청을 하면 인삿말이 하나 딸려옵니다.
* 여기로 GET 요청을 해서 성공하면 Promise의 then 함수를 이용해서 Ajax로 받아온 인삿말을 콘솔창에 출력해주고 싶습니다.
####
> 🤔 Ajax로 get요청 보내는 법
```js
// 방법1
$.ajax({
    type: 'GET',
    url: 'https://codingapple1.github.io/hello.txt',
}).done(function(결과){
    console.log(결과);
})
>
// 방법2
$.get('https://codingapple1.github.io/hello.txt').done(function(결과){
  console.log(결과)
});
```
####
> 🗣️ 답안
```js
var 프로미스 = new Promise(function(성공, 실패) {
    $.get('https://codingapple1.github.io/hello.txt').done(function(결과){
      성공(결과)
    });
});
>
프로미스.then(function(결과) {
  console.log(결과);
})
```
####
> 💡 Q3. Promise chaining 
* 2번 문제에서 https://codingapple1.github.io/hello.txt 라는 경로로 GET 요청을 한 뒤에 .then을 이용해 인삿말을 콘솔창에 출력해보았습니다. 
* 이번엔 그 직후 https://codingapple1.github.io/hello2.txt 라는 경로로 GET 요청을 또 하고.then을 이용해 인삿말을 또 출력해보고 싶습니다. 
> 🤔 Promise chaining
```js
프로미스.then(function(결과) {
    console.log(결과);
  	return new Promise() // .then()에서 new Promise()를 리턴하면, 뒤에 then을 연속해서 사용 가능.
}).then(function(결과) {
    console.log(결과);  
}) 
```
> 🗣️ 답안
```js
var 프로미스 = new Promise(function(성공, 실패) {
    $.get('https://codingapple1.github.io/hello.txt').done(function(결과){
      성공(결과)
    });
});
>
프로미스.then(function(결과) {
  console.log(결과);
>
  var 프로미스2 = new Promise(function(성공, 실패) {
    $.get('https://codingapple1.github.io/hello2.txt').done(function(결과){
      성공(결과)
    })
  });
>
  return 프로미스2;
>
}).then(function(결과) {
    console.log(결과);
})
>
> // 위에 코드를 함수를 사용해서 재사용 부분을 덜어낸 코드
var 프로미스 = ajax만들어주는함수('https://codingapple1.github.io/hello.txt')
>
프로미스.then((결과) => {
  	console.log(결과)
  	return ajax만들어주는함수('https://codingapple1.github.io/hello2.txt')
}).then((결과) => {
  	console.log(결과)
})  
>  
function ajax만들어주는함수 (URL) {
  	return new Promise((성공, 실패) => {
    $.get(URL).done((결과) => {
      성공(결과)
    })
  });
}  
```
> 💡 위 문제 3 코드에서 볼 수 있듯이 promise를 사용해도, 코드가 길어지면, 직관성이 떨어지는 단점이 있음