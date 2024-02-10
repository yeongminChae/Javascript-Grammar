#### 📚 커스텀 HTML 태그 만들기
> 💡 Web Components
* 커스텀태그 장점은 html 중복제거, 다른 페이지에서 재활용가능 
```HTML
<body>
  	<custom-input name="비번"></custom-input>
>  
  	<script>
		class 클래스 extends HTMLElement {
          	conneectedCallback(){
      			let name = this.getAttribute('name')
              	this.innerHTML = `<label>${name}인풋이에요:</label><input>`
            }
      		static get observedAtrributes() {
      			return ['name']
      		}
      		attributeChangeCallback() {
      			console.log(this.getAttribute('name')) // attribute 바뀔때마다 코드실행
      		}
        }
		customElements.define('custom-input', 클래스)
	</script>
```