#### Rest 파라미터
```js
// arguments => 오래된 문법
function 함수(a, b, c){ 
	for(let i = 0; i < arguments.length; i++){
      	console.log(arguments[i]) 
    }
}

function 함수2(...rest){ 
 	console.log(파라미터들)
}

함수2(1,2,3,4,5,6,7) // 출력결과 [1,2,3,4,5,6,7]
// Rest 파라미터 : 모든 파라미터들을 배열에 보관해주는 메소드.

// arguments VS Rest 파라미터 
// arguments : 순서, 위치 상관없이 모든 파라미터들을 []비슷한 자료형에 담아준다.
// Rest 파라미터 : function 함수2(a, b, ...rest) 다음과 같이 파라미터를 작성해준다면 '...rest' 자리에 오는 파라미터들만 배열에 담아준다.

// if, Rest 파라미터를 사용하여 모든 파라메터들을 하나씩 출력해주는 함수.
function 함수2(...rest){
  	for (let i = 0; i < rest.length; i ++){
	  	console.log(rest[i])
    }
}

// Rest 파라미터를 주의점
// 1. 파라미터에서 가장 뒤에 써야한다.
// 2. 한번만 사용 가능
```
