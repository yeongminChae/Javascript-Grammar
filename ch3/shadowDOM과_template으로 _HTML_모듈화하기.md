#### 📚 shadow DOM과 template으로 HTML 모듈화하기
> 💡 shadow DOM이란?
* web component에 style 태그를 작성하면 다른 html태그들에도 그 작성값이 적용됨.
* 이를 해결하기 위해 적용하고 싶은 사항들을 shadow dom안에 저장하는 것
```html
<body>
>  
  	<div id='mordor'></div>
  	<script>
      	// 기본적인 작성법
      	document.querySelector('#mordor').attachShadow({mode: 'open'})
      	document.querySelector('#mordor').shadowRoot.innerHTML = `<p>심연에서 왔도다.</p>` 
	</script>
  	<script>
      	// shadow dom을 적용해 커스텀 엘리먼트 만드는 방법.
      	class 클래스 extends HTMLElement {
          	conneectedCallback(){
              	this.attachShadow({mode: 'open'})
				this..shadowRoot.innerHTML = `<label>이메일 입력.</label><input><style><style>label {color: red}</style>`;
            }	
>      
      	customElements.define("custom-input",클래스)
	</script>
```
####
> 💡 template이란?
* HTML 임시보관함
```html
<body>
>  
  	<template id='template1'>
      	<label>이메일 입력.</label><input>
      	<style><style>label {color: red}</style>
  	</template>      
>      
  	<script>
      	class 클래스 extends HTMLElement {
          	conneectedCallback(){
              	this.attachShadow({mode: 'open'})
				this.shadowRoot.append(template1.content.cloneNode(true))
>      
      			let el = this.shadowRoot.querySelector('label');
      			el.addEventListener('click', function() {console.log('click')})
            }	
>      
      	customElements.define("custom-input",클래스)
	</script>
```