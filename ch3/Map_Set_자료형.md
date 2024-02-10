#### 📚 1. Map 자료형
> 💡 Map 자료형
* key, value를 저장하는 자료형.
* 자료의 연관성을 표현하기 위해 사용.
* key값에 문자열만 입력할 수 있는 객체와는 달리 map은 모든 자료형을 입력할 수 있음.
```js
var person1 = new Map()
>    
person.set('name','Kim') // map에 자료형 저장하는 방법
person.get(age)
person.size
>
var person2 = new Map([ // map에 여러 자료형을 한번에 저장하는 방법
  	['name', 'Kim'],
  	['age', 20],
])  
>  
for (var key of person.keys()){
  	console.log(key)
} 
```
####

#### 📚 2. Set 자료형
> 💡 Set 자료형
* 중복 자료를 허용하지 않는 자료형
```js
var 출석부 = ['john', 'tom', 'andy', 'tom']
var 출석부2 = new Set(['john', 'tom', 'andy', 'tom'])
>
출석부2.add('sally')
출석부2.delete('john')
출석부2.size
>
// array를 set로 바꾸기
var 출석부2 = new Set(출석부);
// set을 array로 바꾸기
출석부 = [...출석부2]  
```					    	