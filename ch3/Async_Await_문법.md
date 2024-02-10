#### 📚 1. Async 키워드
> 💡 Async 키워드
* ES8부터 제공
* 함수 앞에다가만 붙일 수 있는 키워드
* Promise 오브젝트를 리턴해줌
* 단 오직 성공만 판정가능
```js
// promise를 활용한 콜백함수 작성법
function 더하기() {
  	return new Promise((resolve, reject) => {
      	resolve(1 + 1)
    })
}
>
더하기().then(function() => {
	console.log('성공했어요')           
})
>
// async 활용법
async function 더하기() { // async를 function앞에 붙이면 함수 실행 후에 Promise 오브젝트를 리턴해줌
  	1 + 1
}
>
더하기().then(function() => {
	console.log('성공했어요')           
})
>
// 연산 결과를 파라메터로 담아서 보내는 방법
async function 더하기() {
  	return 1 + 1 // return 키워드를 작성해주면 됨
}  
>  
더하기().then(function(결과) => {
	console.log(결과)           
})  
```
####

#### 📚 2. Await 키워드
> 💡 Await 키워드
* async 함수 안에서 쓰는 await은 then 키워드 대신 사용이 가능함.
* await 키워드가 발동되면 그 해당 코드들은 프로미스가 해결될 때까지 대기함.
* 단 await은 프로미스 판정이 실패하면 동작을 멈추기 때문에 예외처리를 해줘야 함.
```js
// async 함수 안에서 쓰는 await
>
// async 함수 안에서 Promsie 작성	
async function 더하기() {
  	var 프로미스 = new Promise(function(resolve, reject) {
		var 힘든연산 = 1 + 1;
      	성공() // 성공판정 내림
    });
>  	
  	// 성공 판정시 실행될 코드 작성법 1. then 키워드 사용
	프로미스.then(function() {
  		console.log('성공했어요')
	})
>
	// 성공 판정시 실행될 코드 작성법 2. await 키워드 사용
  	var 결과 = await 프로미스;
  	console.log(결과);
>
  	// 실패 판정시 실행될 코드 작성법 (await은 판정 실패시 동작을 멈추기에 예외처리 해주어야 함)
  	try {
		var 결과 = await 프로미스;
      	console.log(결과)
    } catch {
      	console.log('프로미스 연산에 문제 발견!')
    }
>  	
}
```
####

#### 📚 예제) Async / Await 키워드를 이용한 예제
> 💡 Q1 < button >을 누르면 성공하는 Promise 만들기
*  HTML 페이지 내에 버튼 아무거나 하나 만들고, 그걸 클릭하면 성공하는 Promise를 만들고 싶습니다. 
* 성공하면 콘솔창에 '성공했어요'를 출력하고요.
> 🗣️ 답안
```js
<button id="btn1">버튼1</button>
<script>
  const btn1 = document.getElementById("btn1");
>
  const clickDetector = async () => {
>    
    const promise = new Promise((resolve, reject) => {
      btn1.addEventListener("click", () => {
        resolve();
      });
    });
>
    try {
      var result = await promise;
      console.log("클릭완료");
>      
    } catch {
      console.log("에러발생");
    }
  };
>
  clickDetector();
</script>
```