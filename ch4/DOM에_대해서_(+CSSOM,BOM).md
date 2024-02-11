#### 📚 1. DOM에 대해서
> 💡 DOM(Document Object Model) 이란?
* HTML이나 XML 문서를 실체로 나타내는 API입니다. 여기서 'Document'는 HTML 문서를 의미합니다.
* HTML 문서는 크롬과 같은 브라우저들에게 보내는 일종의 주문서로 볼 수 있습니다. HTML 문서에는 웹페이지 요소들과 그 구조가 설계도처럼 표현되어 있습니다.
* 브라우저는 이 HTML 문서를 바탕으로 Body, div, li, span 등과 같은 HTML 요소들을 바탕으로 레이아웃을 그립니다. (이 과정이 파싱)
* 예를 들어, HTML 문서에서 input 태그는 클래스 등의 속성들이 가진 문자열이지만 브라우저에서는 지정된 타입에 따라 빈칸에 문자열이나 숫자를 입력받고 그 값을 value로 내보내도록 만들어진 input 객체로 실체화됩니다.
* DOM은 HTML 문서에 작성된 전체 구조에 맞춰서 이 제품들이 배치되고 이들에게 추가적으로 명령을 보내 속성이나 디자인, 배치 등을 조작할 수 있도록 된 상태입니다. 즉, HTML이란 코드로 설계된 웹페이지가 브라우저 안에서 기능들을 수행할 객체들로 실체화된 형태입니다.
* DOM은 자체 API를 갖고 있으며, DOM을 사용해서 원하는 대로 웹 화면을 그리고 필요에 따라 자바스크립트를 사용해서 조작할 수 있습니다.
```js
<html lang="ko">
<head>
	<title>DOM 예제</title>
</head>
>
<body>
	<h1 id="title">장 봐올 것</h1>
	<ul>
		<li>당근</Li>
		<Ll>오이</Li>
		<Ll>양파</Li>
	</ul>
>
	<button>알~겠나요?</button>
</body>
</html>
>
```
![](https://velog.velcdn.com/images/codudals98/post/58813af1-8997-4a56-a256-e1209107ad55/image.png) 
* 위 html을 바탕으로 제작한 DOM 트리       
####

#### 📚 2. DOM에서의 노드(Node)
> 💡 DOM에서의 Node
* 노드는 DOM의 핵심 기본 단위로, DOM 트리 구조의 각 요소를 나타냅니다. HTML 태그, 텍스트 내용, 주석 등 모든 것들이 각각 하나의 노드가 됩니다.
* HTML 문서를 보면 HTML 태그 안에 head, body 태그가 있고, body 태그에는 div 등 여러 다른 태그들이 또 포함되어 있습니다. 이 각각의 요소들이 노드로 표현되며, 이들이 서로 포함 관계를 가지면서 트리 모양의 구조를 이룹니다.
* 노드는 추상 클래스로서, DOM의 모든 요소들 (예: HTML, div, radio, table 등)은 모두 노드로부터 상속받습니다. 즉, 거의 모든 HTML 태그들은 기본적으로 노드입니다.
* 노드는 다음과 같은 공통적인 속성과 메소드를 갖습니다: textContent (노드의 텍스트 내용), childNodes (자식 노드들), firstChild (첫 번째 자식 노드), lastChild (마지막 자식 노드), parentNode (부모 노드), cloneNode (노드 복제), appendChild (자식 노드 추가), insertBefore (특정 자식 노드 앞에 새 노드 추가) 등.
* 노드는 EventTarget 인터페이스를 상속받아, 클릭 등의 이벤트가 가해지는 대상이 됩니다. 이 때문에 모든 노드는 addEventListener 등의 이벤트 관련 메소드를 갖고 있습니다.
* 노드에는 고유의 속성이나 기능들이 있습니다. 예를 들어, a 태그는 'href' 속성을, img 태그는 'src' 속성을 갖습니다. 이런 속성들을 통해 각 노드는 자바스크립트나 다른 언어를 통해 조작될 수 있습니다.![](https://velog.velcdn.com/images/codudals98/post/094ae1a5-a97e-4ba9-b722-fb5142450d5c/image.png)
* 다음과 같이 하나하나의 모든 HTML요소들이 노드임
####

#### 📚 3. 자바스크립트로 DOM 동작시키기
> 💡 자바스크립트로 DOM을 조작하는 방법
```js
<html lang="ko">
<head>
	<title>DOM 예제</title>
</head>
>
<body>
	<h1 id="title">장 봐올 것</h1>
	<ul>
		<li>당근</Li>
		<Ll>오이</Li>
		<Ll>양파</Li>
	</ul>
>
	<button>알~겠나요?</button>
</body>
</html>
>
// 해당 코드들은 자바스크립트로 작성되어 HTML을 수정하기 위한 것이 맞음.
// 그러나, document.getElementById, .textContent은 자바스크립트가 아님.      
>      
const title = document.getElementById('title');
title.textContent = '주문할 것';
```
* document객체는 nodeJS런타임에서는 작동하지 않음, 즉 이 객체는 브라우저 환경에서 제공하는 한 요소임.
![](https://velog.velcdn.com/images/codudals98/post/afed1a59-5877-45b2-ad74-294eab93bcb4/image.png)![](https://velog.velcdn.com/images/codudals98/post/dd2a37df-b3b5-4092-a391-6cf8656037b6/image.png)
* 위에 DOM 트리 요소들이 각각 가지고 있는 상속구조
* document.getElementById('title'); 이 자바스크립트 코드에서, getElementById는 Document의 고유기능으로 Document에서만 사용 가능
* title.textContent에 textContent는 노드의 기능으로써, 모든 하위 요소들이 사용가능함
* eventTarget는 클릭, 드래그, 키보드입력 과 같은 요소들의 이벤트들을 의미
```js
const button = document.querySelector("button");
button.addEventListener("click", () => {
// 여기서 addEventListener는 eventTarget는의 기능이기에 이로부터 상속받는 HTMLButtonElement뿐 아니라 모든 요소에서 사용 가능함.  
	window.alert("알~겠어요!"); // window는 Browser Object Model에 일부
});
>  
button.disabled = true;  // disabled는 HTMLButtonElement에 요소이기에, HTMLButtonElement에서만 사용 가능
```
####

#### 📚 4. CSSOM(CSS Object Model) 과 BOM(Browser Object Model)
> 💡 CSSOM(CSS Object Model) 이란?
* CSSOM은 CSS를 조작하기 위한 API로, DOM과 같이 트리 형식으로 출력됩니다.
####
> 💡 BOM(Browser Object Model)이란?
* BOM은 브라우저 자체를 다루기 위한 API입니다. window 객체 안에 location, navigation, screen 등이 포함되어 있습니다.
* 브라우저가 실행 주체인 기능(alert, setTimeout, replace 등)들은 BOM에 속합니다.
####
> 💡 Web Api란? 
* 🗣️ Web APi : Document Object Model과 Browser Object Model뿐만 아니라 브라우저에서 제공하는 모든 기능들
* 🗣️ Web APi는 자바스크립트의 기능은 아니지만 자바스크립트등 언어에 의해 제어되도록 브라우저에 의해 제공되고 있음.![](https://velog.velcdn.com/images/codudals98/post/2fd9138f-6521-467f-a31a-43871c68d9cf/image.png)
####
