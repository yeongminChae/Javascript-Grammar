#### 📚 1. API에 대해서
> 💡 API란?
* Application Programming Interface : 한 프로그램에서 다른 프로그램으로 데이터를 주고받기 위한 방법
* Interface : 기계와 인간, 기계와 기계, 소프트웨어와 소프트웨어 사이에서 일어나는 수많은 요청과 정보교환을 위한 일종의 소통창구
```js
app.get('/detail/:id', function(req, res)) // 이 url로 get 요청할 시.
	db.collection('웹툰').findOne({ _id: parseInt(req.params.1d) },function(에러, 결과){
		console.log(결과);
		res. render ('detail.ejs', { data: 결과); 
	})
})
// 여기서 get요청하는 것이 api예시
```
####
> 💡 API가 담고있어야할 내용
* 요청방식이 들어있어야 함(get, post, patch, delete...)
* endpoint를 담고있어야 함 (url)
* 자료요청에 필요한 추가정보, (파라메터등을 담고 있어야 함 : '?titleId=2312321')
* ex) get: comic.naver.com/webtoon/detail?titleId=2312321
* API는 항상 공개적으로 사용될 필요는 없으며, 필요에 따라 private하게 설정할 수도 있음.~~텍스트~~
####

#### 📚 2. REST API에 대해서
> 💡 REST API란?
* REST API는 개발자들 간에 정보를 주고 받기 위한 일종의 형식
* 무슨 언어를 사용하든, 어떤 라이브러리, 프레임워크로 소프트웨어를 만들 든 REST API폼에 맞춰서 개발하면 됨. 
* REST API의 가장 중요한 특징은 각 요청이 어떤 동작이나 정보를 위한 것인지 그 요청의 모습만으로 추측이 가능해짐.
* url : 자원을 구조와 함께 나타내는 이러한 형태의 구분자
* 서버에 REST API로 요청을 보낼 때는 http 프로토콜에 맞춰서 보내야함.
####
> 💡 대표적인 REST API 메소드
* CRUD (Create, Read, Updata, Delete)를 구현하기에 가장 적합한 메소드들
* get메소드 : read
* post메소드 : create
* patch/put메소드 : update (put은 정보를 통째로 수정할 때, patch는 정보중 일부를 수정할 때)
* delete메소드 : delete
####
> 💡 REST API생성 규칙
* 유저 그리고 동료 개발자들과 더 쉽게 소통하기 위한 표준 코드 작성법
    * 1. 동사를 url에서 사용하지 않는다. (명사들을 위주로 작성)
    * 2. 컬렉션들에는 복수를 사용한다. (/movies)
    * 3. DB에서 고유 식별자용를 사용한다. (/movies/Inception)
    * 4. 필요에 맞게 REST API메소드를 사용해서 url를 작성한다.
    * 5. 검색을 하고 싶은 요소가 있다라면, 쿼리 파라메터를 적극적으로 이용한다. (/movies?releast_date=2023)
	
