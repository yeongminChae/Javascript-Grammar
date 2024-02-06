#### 📚 JS에서의 모듈화
> 💡 모듈화란?
* 자바스크립트에서 모듈화란 코드를 여러 개의 독립적인 파일로 분리하여 관리하는 것을 의미.
* 필요한 부분만 불러와 사용할 수 있으므로 코드의 재사용성과 유지 관리성을 높일 수 있음.

#### 📚 import, Export 문법
> * ES6이전 html파일에서 js파일을 첨부하는 방식
```js
<script src="첨부하고싶은.js"> 
	// ...
</script>
```

> 💡 import 문법이란? 
> * ES6부터는 직관적인 js파일 첨부방식을 지원함.
```js
// index.html
<script type="module"> 
// ES6에 import js는 모든 자바스크립트 내용을 가져오지 않음.
	import a from '/첨부하고싶은.js' // import 'js에서 가지고 오고 싶은 것' from '경로'
// js에서 a라는 변수만 가지고 오고 싶을 때. 
// 여기서 변수명 키워드는 꼭 export되는 변수명과 같을 필요는 없음.
>
	 ...
</script>
>
// 첨부하고싶은.js
var a = 10;
export default a; // a라는 변수를 기본으로 내보내고 싶다.
```
* 💡 Export 문법 사용법
1. 여러 변수를 한번에 export 하고 싶을 때.
```js
// 첨부하고싶은.js
var a = 10;
var b = 5;
export var c = 6;
>
export {a, b};
// index.html
<script type="module"> 
	import {a} from '/첨부하고싶은.js' 
// 반드시 export 되는 모든 변수를 다 받아줄 필요는 없음.
// 단, 여기서 변수명 키워드는 export되는 변수명과 반드시 같아야 함.
>
	 ...
</script>
```
2. export default와 export를 동시에 사용 하고 싶을 때.
```js
// 첨부하고싶은.js
var a = 10;
var b = 5;
var c = 6;
>
export {a, b};
export default c;
>
// index.html
<script type="module"> 
	import 아무값 from '/첨부하고싶은.js' // export default 변수 받을 시, 키워드 내가 작문 가능
	import {a} from '/첨부하고싶은.js' // export 변수 받을 시, 키워드 정확해야 함
	import c,{a,b} from '/첨부하고싶은.js' // export default, export 모든 변수를 받아오는 방법
	// export default의 변수는 반드시 왼쪽에 와야한다.
>
	 ...
</script>
```
####

#### 📚 as 문법
> 💡 as 문법이란? 
import하는 변수의 변수명을 작명할 수 있음.
```js
// 첨부하고싶은.js
var a = 10;
>
export {a};
>
// index.html
<script type="module"> 
	import {a as 별명} from '/첨부하고싶은.js' 
>
	 ...
</script>
```

#### 📚 * 문법
> 💡 * 문법이란? 
import할때 해당 js파일을 모두 받아오고 싶을 때.
```js
// 첨부하고싶은.js
var a = 10;
var b = 20;
>
export {a};
export default b;
>
// index.html
<script type="module"> 
	import * from '/첨부하고싶은.js' 
	import * as 별명 from '/첨부하고싶은.js' 
	import b as from '/첨부하고싶은.js' // export default 변수는 반드시 이처럼 import해야함.
>
	 ...
</script>
```