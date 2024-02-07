#### 📚 웹 브라우저란?
> * 서버에서 받아온 **HTML, CSS, JS**를 해석해서 실행시켜주는 프로그램.
> * 브라우저는 C++ 라는 프로그램으로 작성되어있고, 브라우저는 실행해야할 JS 코드를 발견하면 C++ 언어로 만들어둔 **stack에 넣어서 작동**시킴.
> * **Stack**은 JS 요소들을 다 집어놓고 맨 윗줄부터 **하나씩** 실행시켜주는 공간임.

#### 📚 웹 브라우저 내부 동작 원리
>![](https://velog.velcdn.com/images/codudals98/post/f550faf6-1cb4-4268-8ae8-32fc2c32453c/image.png)
* Heap : **메모리 할당**이 이루어지는 곳으로써 **객체, 배열, 변수등이 할당**되는 공간. 메모리 관리는 가비지 컬렉션에 의해 자동으로 이루어짐. **힙**은 **구조화 되지 않은 메모리 영역**을 의미함.
* Call Stack : 동기적인 코드를 실행시켜 주는 공간. **자바스크립트**에서는 **한번에 한개**씩만 코드를 실행시켜줌.
    * 자바스크립트는 **Single Thread** 언어이다.
* Task Queue : 자바스크립트에서 setTimeout와 같은 비동기 작업들을 대기시키는 큐, 이벤트 루프는 Call Stack이 비어있을 때 이 큐의 작업을 가져와 실행.
* Micro Task Queue (Event Queue) : Promise와 같은 비동기적인 코드를 보관하고 있는 공간. 현재 실행 중인 Event Queue가 종료되자마자 작업을 가져와 Event Loop에 의해 Call Stack 에 추가함.이때 Event Queue의 작업들이 Task Queue에 작업보다 우선적으로 옮겨짐.
* Event Loop : 자바스크립트가 동시성을 다루는 방식의 핵심으로 이벤트 루프는 자바스크립트의 단일 스레드 언어의  한계를 극복하기 위해 사용됨. Call Stack이 비어있는 경우 Task Queue의 작업을 Call Stack으로 이동 시켜줌.

#### 📚 웹브라우저 동작 예시
> 💡 만약 반복문을 100억번 돌려야 할 경우?
* 이정도에 반복문을 실행시키면 CPU 가 아무리 좋을지라도, 상당한 시간이 소요될 것.
1. setTimeout을 사용해서 0초마다 0 ~ 1억 반복과 같이 코드를 실행시킨다.
2. Web Worker를 이용. 이는 다른 JS파일을 이용해서 그 파일에서 힘든 연산을 시키고 후에 값을 가져오도록 코드를 작성함.
```js
// main.js
var myWorker = new Worker('worker.js');
>
w.onmessage = function(e){
  	console.log(e.data) 
}  
>
// worker.js
var i = 0;
postMessage(i + 1)
```
* 이렇게 작성하면 postMessage함수로 인해 worker.js 작업이 완료될 시 main.js로 완료된 결과를 전달할 수 있고 이러면 Stack이 바빠지지 않음.