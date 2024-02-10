#### 📚 Functional Array Method
> 💡 1. find
* 배열내에서 아이템을 찾고 싶을때 사용.
* find 메소드는 하나의 콜백함수를 필요로 함.
* true를 리턴해주면 우리가 찾고 싶어한 아이템을 찾음을 의미.
```js
function findAvocado(currentFruit) {
  	return currentFruit == '🥑';
}
>
const fruits = ['🍎','🍌','🍉','🥑'];
const avocado = fruits.find(findAvocado)
```
####
> 💡 2. map
* map을 사용하면 배열의 요소를 가져와 반환한 다음 새 배열에 배치할 수 있음.
* map은 'source'배열을 수정하지 않고 대신 변환한 값으로 완전히 새로운 배열을 만듦. 
* map은 메소드는 하나의 콜백함수를 필요로 함. 그리고 이 콜백함수는 반드시 리턴할 값들이 필요함.
```js
function double(currentNumber) {
	return currentNumber * 2; // 여기서 콜백함수에 의해 반환되는 리턴값들이 새 배열에 있는 값이 됨.
}
>
const source = [2,4,6,8,10] 
const transformed = source.map(double)
```
####
> 💡 3. Arrow Function을 사용하여 작성한 find, map 메소드들
* 화살표 함수는 코드 한 줄에 함수를 쓸 수 있게 해줌.
* 화살표 함수는 '암묵적 반환'이라는 기능이 있기에 반환하기 위해 리턴 키워드가 필요하지 않다.
```js
// find method
const fruits = ['🍎','🍌','🍉','🥑'];
const avocado = fruits.find((currentFruits) => currentFruits === '🥑')
>
// map method
const source = [2,4,6,8,10] 
const transformed = souce.map((currentNumber) => currentNunber * 2)
```
####
> 💡 4. filter
* filter는 'source'배열을 수정하지 않고 대신 내가 원하지 않은 아이템을 제거한 상태로 새로운 배열을 만듦. 
* 콜백함수가 true를 리턴하면 항목이 새 배열로 이동하고, false를 리턴하면 해당 항목을 새 배열에서 제거함.
```js
const fruits = ['🍎','🍌','🍉','🥑','👻']; // 우리는 과일만 갖고 싶음 따라서 콜백 함수에서 과일이 아닌 '👻'을 제외하고 새로운 배열을 만들어야 함
const avocado = fruits.fillter((currentFruits) => currentFruits === '👻')
```
