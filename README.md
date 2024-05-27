# Axios

## 1. axios 를 연습할때

- [josn-server](https://www.npmjs.com/package/json-server)
- [참조자료](https://poiemaweb.com/json-server)

## 2. 서버 구축 과정

- D:드라이브에 server 폴더를 만든다.
- VSCode 에서 프로젝트 등록을 한다.
- Node.js 프로젝트로 등록을 한다. (리액트 상관없음)

## 3. Node.js 프로젝트 생성하기

- `npm init` 엔터

## 4. json-server npm 설치

- `npm install -g json-server`
- db.json 파일 생성

```json
{
  "posts": [
    { "id": "1", "title": "a title", "views": 100 },
    { "id": "2", "title": "another title", "views": 200 }
  ],
  "comments": [
    { "id": "1", "text": "a comment about post 1", "postId": "1" },
    { "id": "2", "text": "another comment about post 1", "postId": "1" }
  ],
  "profile": {
    "name": "typicode"
  },
  "todos": [
    {
      "id": 1,
      "content": "HTML",
      "completed": true
    },
    {
      "id": 2,
      "content": "CSS",
      "completed": false
    },
    {
      "id": 3,
      "content": "Javascript",
      "completed": true
    }
  ],
  "users": [
    {
      "id": 1,
      "name": "Lee",
      "role": "developer"
    },
    {
      "id": 2,
      "name": "Kim",
      "role": "designer"
    }
  ]
}
```

## 5. json-server 실행

- `json-server --watch db.json`
- 리액트가 3000 포트를 사용하고 있음.
- json-server 도 3000 포트를 사용하므로 충돌 발생함.
- `json-server --watch db.json --port 5000`
- json-server 포트를 5000 번으로 변경

## 6. package.json 에 script 명령어 추가하기

```json
{
  "name": "server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "json-server --watch db.json --port 5000"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "json-server": "^1.0.0-beta.0"
  }
}
```

## 7. API 테스트하기

- CRUD 테스트 (크러드)
  : Create (POST)
  : Read (GET)
  : Update (PUT / Fetch )
  : Delete (DELETE)
- Postman (웹 API 테스트시 일반적 사용)
- Swagger (웹 API 테스트시 별도로 BE에서 셋팅)
- Web Browser (웹 프로젝트 CORS 에러 발생 함)
  : package.json 에 "proxy":"주소" 를 작성해야 한다.

## 8. Axios 활용

- [axios](https://axios-http.com/kr/docs/intro)
- `npm install axios`

## 8.1. axios 폴더 추천

- /src/apis 폴더 생성
- /src/apis/config.js

```js
// 서버 주소
export const SERVER_URL = "http://localhost:5000";
```

- /src/apis/todos.js

# 리액트 이벤트 핸들러

## 1. 기본

- click, change

### 1.1. JS 태그버전 이벤트 핸들러

- 태그에 직접 이벤트 연결하기
- 함수 호출 시 `()` / 반드시 `on에 소문자이벤트명` 이거만 기억하자.
- <태그 on이벤트명="함수명()">내용</태그>
- 소문자 onclick="함수명()"
- 소문자 onChange="함수명()"
  - 주의사항
    - 반드시 소문자로 on + 이벤트 로 작성한다.
    - 예) onclick
- 저는 안좋아합니다. 이유는 태그가 복잡해짐.
  - inline방식으로 접근을 하기 시작하면 너무 복잡해진다.
  - 여러가지 기능을 넣을 수 가 없다.

```html
<button onclick="alert('safd')">클릭</button>;
```

- 태그에 JS 를 실행하는 경우 호출(call)을 꼭 해주자.

```html
<script>
  function 함수명() {}
</>
<button onclick="함수명">클릭</button>;
```

```html
<script>
  function 함수() {
    alert(안녕);
  }
</script>

<!-- 실행 안됨_호출이 없음. -->
<button onclick="함수">클릭</button>

<!-- 실행 됨_호출이 있음. -->
<button onclick="함수()">클릭/ 실행 됨.</button>
```

### 1.2 JS 태그 메서드 버전

- 먼저 내용을 정리하고 참조하자.
  - 태그를 먼저 찾고 이벤트를 연결한다.
  - 태그.소문자 on이벤트명 연결한다.
  - on이벤트명 함수 연결시 실행(Call)하면 안되는 주의사항
  - 여러개의 함수를 등록할 수 없다. (사용안하게 된 계기)

```html
<button id="bt" class="bt">클릭</button>
  <script>
    // 아이디 고정으로 찾음.
    document.getElementId("bt");
    // 아이디
    document.querySelector("#bt");
    // 클래스
    document.querySelector(".bt");
    // 태그명
    document.querySelector("button");
    // 호출 X () 화면 로드 시 바로 실행 됨
    bt.onclick = 함수명;
  </script>
</button>
```

- 객체.메소드
- 아래의 코드는 html 태그를 못찾아서 에러 발생
- script를 아래로 내리던가 빼던가 해야될듯.
- 관례 > 파일을 외부로 X 현재 파일 안에 js코드를 작성할 경우
  `최`하단부에 배치해야함

```html
<button
  id="btn"
  style="
    width: 100px;
    height: 100px;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 9999999999999999;
"
>
  클릭
</button>
<script>
  function 함수() {
    alert("안녕");
  }
  const btElementId = document.getElementById("btn");
  const btQueryId = document.querySelector("#btn");

  // 아래 코드는 함수를 실행하고 그 결과를 저장하라는 코드
  // 바로 그냥 실행해라 임
  btQueryId.onClick = 함수();
</script>
```

```html
<!-- 코드 순서상 찾을 수 있음 -->
<button
  id="btn"
  style="
    width: 100px;
    height: 100px;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 9999999999999999;
"
>
  클릭
</button>
<script>
  const btElementId = document.getElementById("btn");
  const btQueryId = document.querySelector("#btn");
  function 함수() {
    alert("안녕");
  }

  function 함수2() {
    alert("반가워");
  }

  // 아래 코드는 함수를 실행하고 그 결과를 저장하라는 코드
  // 바로 그냥 실행해라 임
  // call back 함수
  // 이런식으로 아이디에 onclick 주면 이벤트 줄 수 있음.
  // 아래처럼 진행한다. () 를 제거해야 한다.
  btQueryId.onclick = 함수();

  // 이 경우 아래꺼만 실행된다.
  // 기능은 1개 밖에 연결이 안되는 단점이 있다.
  // 덮어써서 그런다.
  btQueryId.onclick = 함수;
  btQueryId.onclick = 함수2;

  // 이건 2개다 되긴한다
  btQueryId.onclick = function () {
    함수();
    함수2();
  };
</script>
```

## 3. JS 태그 이벤트 핸들러 등록 버전

- 아래의 내용을 참조하고 코드 보자.
  - 여러개의 함수를 등록할 수 있다.
  - 주의사항은 on 이라는 글자가 제거되어야 함.

```html
<button
  id="btn"
  style="
    width: 100px;
    height: 100px;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 9999999999999999;
"
>
  클릭
</button>
<script>
    const btQueryId = document.querySelector("#btn");

    function 함수() {
      alert("안녕");
    }

    function 함수2() {
      alert("반가워");
    }
    // 이건 실행이 안된다.
    // onclick X / click O
    btQueryId.addEventListener("onclick", () => {
      // 실행 기능
      함수();
    });
    // 객체 이벤트 핸들러 등록 방식
    // 이벤트 명만 적어야 함. 그래서 오류
    // 이벤트를 여러개 걸 수 있다.
    btQueryId.addEventListener("click", () => 함수());
    btQueryId.addEventListener("click", () => 함수2());
  // 이벤트 3가지
  // 매개변수 event 객체는 나중에 하자.
  <body onload="함수명()">
  document.onload = function(){}
  document.addEventListener("load", () => 함수2());
</script>
```

2. html 객체에 이벤트 연결하기
   2.1. 메소드 방식
   2.2. 이벤트 핸들러 방식

## 4. 리액트 버전

- 아래의 내용을 먼저 정리합니다.
  - **중요**
  - `리액트는 JSX(리액트 태그) 버전이 기본입니다.`(인라인방식만 있다.)
  - **중요**
  - 원하는 이벤트를 쓰고 싶을 때 dipatch 사용
  - js : load > react : useEffect
  - 이벤트는 on소문자 대문자시작하는 카멜케이스임.
  - 이벤트에 연결될 함수는 2가지 방식으로 작성이 가능하다.
  - 절대로 해서는 안될 방식
    - 렌더링 될 때 마다 바로 실행 되기때문에 하면 안된다.
    - 함수명() 로 ()를 붙이면 함수 Call 즉, 실행입니다.
      - <JSX onClick={handleClickEv()}></JSX>
    - 이렇게 사용하자.\_바로실행은 오류입니다.
      - <JSX onClick={handleClickEv}></JSX>
  - 매개변수 전달되는 함수라면 화살표 함수로 감싸주세요.
  - 태그내부 이벤트핸들러에 그냥 전부 화살표 함수로 함수를 감싸자.

```jsx
// 여기에 함수
const handleClickEv = ()=>{}
const handleChangeEv = ()=>{}
return(
// 이건 바로 실행되므로 오류입니다.
<JSX onClick={handleClickEv()}></JSX>;

// 매개변수 보낼 때 이렇게 해야한다.
// 함수를 익명함수로 묶어서 이벤트 막아놓고 누를 때 실행되게
// 매개변수 보낼 때 arrow 함수 내부에 > 함수 넣으면 자동실행이 안된다.
<JSX onClick={()=>{handleClickEv("매개변수")}}></JSX>;

<JSX onClick={handleClickEv}></JSX>;
<JSX onChange={handleChangeEv}></JSX>;
)
```

## JS 25장 클래스

- 단어에 대한 정의가 있다면 이해가 좀 편하다.

- 인스턴스, 객체, 프로퍼티, 메소드 를 단어에 대한 이해..
- 문법에 제시되는 클래스라는 것을 현업에서 많이 쓰는가요?
- 외부 소스 활용시 참조가 필요해요.
- 다른 프로그래밍을 배우신 분들이 js 에 적응하라고 나온 문법

1. 객체 생성 함수 와 클래스를 같이 비교하면 이해가 편하다.
   1.1 객체 생성자 함수
   객체 : 인스턴스 > new!
   생성자 : constructor() {} // 고정된 이름
   함수 : class

```js
function Person(){}
const a = new Person();
- class Person{}
- const a = new Person();
```

3.  1.2. 클래스와 생성자 함수의 차이점

1.  클래스는 new 연산자 없이 호출하면 에러 발생. 생성자 함수는 new 연산자 없이 호출하면 일반 함수로서 호출된다.

```js
function Go() {}
new Go();
Go();

class Go {}
Go();
에러;
```

2. 클래스는 extends와 super 키워드로 상속 가능. 생성자 함수는 extends와 super 키워드를 지원하지 않는다.

```js
// 에러
  function Go() extends(확장) {
    super()
  }
  new Go();
  Go();

  class 강아지 extends 동물 {
    constructor(){
      super();
    }
  } Go(); 에러
```

3. 클래스는 호이스팅이 발생하지 않는 것처럼 동작하고,

```js
// 오류 아래에 해놓으면 오류 X
class 강아지 {}
const a = new 강아지();
```

함수 선언문으로 정의된 생성자 함수는 함수 호이스팅이,

```js
const go = new 강아지();
function 강아지() {}
```

함수 표현식으로 정의한 생성자 함수는 변수 호이스팅이 발생한다.

```js
const 강아지 = function () {};
const go = new 강아지();
```

class Person {
// new Person() 하면 자동 실행 되는 메서드 : 인스턴스 생성자 함수
constructor(){
// 따로 안적어줘도 this를 리턴함.
// new 해서 만들어진 인스턴스를 리턴한다.
return this
}
// 일반 메소드 nonconstructor
// 화살표 함수 nonconstructor
sayHi(){}
sayBye(){}
// 클래스 메소드로서 Person.go() : 반드시 클래스명을 적고 실행
static go(){}
}

4. 클래스 내부에는 자동으로 strict mode가 지정되며 해제할 수 없다. 생성자 함수는 직접 지정해 줘야한다.
5. 클래스의 constructor, 프로토타입 메서드, 정적 메서드는 모두 열거되지 않는다.(`[[Enumerable]]` ⇒ `false`)

- class : 접근 제한자.

  - private : 외부에서 읽기, 쓰기, 변경 안되요
  - public : 외부에서 읽기, 쓰기 , 변경 다~~되요
  - protected : 허락된 환경만 읽기, 쓰기, 변경 다~~되요

- 접근자 프로퍼티

```js
// 클래스 필드 : 클래스에 정의한 속성
class Person = {
  # firstName: "Ungmo",
  lastName  : "Lee",
  get fullName(){
    return `${this.firstName} ${this.lastName}`;
  }
  set fullName(){
    [this.firstName, this.lastName] = name.split('  ')
  }
}

const go = new Person();
go.fullName;
go.fullName = "홍길동";
```

6. 상속에 의한 클래스 확장 (extends)

- 오로지 class 에만 작성 가능

-

- 각각을 적다 보면 공통되는 사항이 나옴
- 그때 class로 그 부분을 묶어서 내려준다.

```js
class 동물 {
  constructor() {
    (this.eye = 2), (this.nouse = 1), (this.mouse = 1);
  }
}

class dog extends 동물 {
  constructor() {
    super();
  }
}

class cat extends 동물 {
  constructor() {
    super();
  }
}

const dog = new dog();

const cat = new cat();

dog;
cat;
```

```js
class 동물 {
  #eye = "";
  constructor() {
    (this.#eye = 2), (this.nouse = 1), (this.mouse = 1);
  }
}

class dog extends 동물 {}

class cat extends 동물 {}

const dogEx = new dog();

const catEx = new cat();

//dogEx.eye = 11
console.log(dogEx);
console.log(catEx);
```

- 각각의 new를 붙여서 생성자 함수를 쓰면
  - constructor(){}가 내장 되어있음
  - constructor 가 자동으로 super를 실행시킨다.
- 속성과 메소드 상속
- 자기만의 속성과 메소드 정의로 확장

BE ===> DB
CRUD

- C : axios.Post
- R : axios.Get
- U : axios.Patch / axios.Put
- D : axios.Delete

## REST API

- 브라우저 창에 주소 및 패스(path)를 의미있는 단어로 제공한다.
- REST API 를 실행할 때 GET, POST, PUT, PATCH, DELETE 를 활용 한다.
  - URL 만 봐도 뭐하는앤지 알게해주자.
  - http://127.0.1.234/todos/1
    - 단어만 봐도 \_ 추측이 가능하도록 해주자
      - todos 할일 목록 /1 1번글
      - 1번 상세페이지
      - 1번 글을 지워라
  - ## http://127.0.1.234/todos/delete/1
  - REST FULL
    - path만 봐도 뭔지 알 수 있다.
    - 어설프면 RestFul 하지 않다

export : export 한 하나의 내용만 보내는거
export default : 정의해놓은 블록 내부에 모든걸 보내는거

status ===> 200 ~ 299 번까지 정상 처리된 것입니다.

## 26 장

1. 우리반 만 정의한 호칭

- 이제부터 함수 와 메소드를 명칭을 컨벤션하겠습니다
- 일반 함수

  - function 함수명(){}

  - 객체 함수
    {
    함수명 : function(){}
    }
  - 메서드
    - 메서드 축약형
      {
      함수명(){}
      }

2. 화살표 함수

- 매개 변수 가 있을 때 모양을 신경쓰자.

  - 2.1. return 도 신경 써요.
    : return 작성을 안해도 자동으로 return 붙여준다.
    : 아래는 기본형입니다.
    : 실행해야 하는 함수 블록이 1 줄이라면

```js
2.2.1 한줄이라면
(x, y) => {
  return x + y;
};
// 한줄이라서 {} 이 생략가능
(x, y) => return x + y;
// 바로 리턴되는 경우는 return 생략 됨.
(x, y) => x + y;

//
2.2.2 두줄이라면
// {} 생략 불가능
(x,y) => const a = x+y; // syntax error
  // const a = x+y; 만 해석
  return a;

(x,y) => {
  const a = x+y;
  return a;
}

2.2.3. 실행해야 하는 함수가 객체 리터럴을 리턴하는 경우
- 객체 만들기 위해서 작성 > 한줄이라 이렇게 작성

- (x,y) => {a:x,b:y}; // 문법오류


- (x,y) =>{
  // 정상 객체를 바로 return 하려면 () 해줘라
  return ({a:x,b:y});
}

```

this 객체

3. Rest 파라미터

- 함수 ( 매개 변수 )
  3.1 파라미터(parameter) 함수 (매개 변수)

  : ...매개 변수 는 [] 입니다.

  : ...매개 변수 는 arguments 를 대체합니다.

  3.2 Rest 파라미터 위치를 살펴보면

  : 나머지를 받아서 배열로 만든다.

  - 나머지 매개변수를 끝자리에 보내자
    : 함수(a, ...rest, c) // 오류
    : 함수(a, b, ...rest) // 정상

4. 함수의 매개변수의 기본값 셋팅 가능
   : 함수(a=1, b={age:5}, c=3){}

27 장 배열

- 저는 배열을 책장으로 비유하겠습니다.
  - 저장할 수 있는 공간.

1. 명칭에 대한 이해가 필수

- 요소 :
- 인덱스 :
- length : 3

- [인덱스 0 "요소: 책", 인덱스 1 "요소: 인형", 인덱스 2 "요소: 화분"]
- 요소 ?

  - 책장에 있는 내용(칸 X / 내용물 : element O)
    - 책장 ["책", "인형", "화분"...]
    - 특정한 칸에 보관하는 값(책, 화분, 인형)[내용물]이다

- 인덱스 ?

  - 특정한 칸에 번호를 말함.
  - 인덱싱 - 시작부분부터 ~ 도착전까지 - 0~7 : 0 < 8 임 -
    - 인덱싱 프로그래밍

- 길이 ? length(칸의 개수)

2. 왜 필요하니?
   배열
   const good_arr = ["사과", "딸기"]

- 쇼핑몰 운영자

```js
const 사과 = { 이름: "사과", 가격: 1000, 판매: true, 할인: 0.5 };
const 딸기 = { 이름: "사과", 가격: 1000, 판매: true, 할인: 0.5 };
// 점점 확장 되어감.
const fruit = function GoodRegister(
  이름,
  가격,
  판매,
  할인,
  전시장소 = "추천상품"
) {
  // 이름이 같음

  return {
    이름,
    가격,
    판매,
    할인,
    전시장소: 전시장소,
    인사말: function () {
      alert(this.이름 + "구매해주셔서 감사합니다.");
    },
  };
};
const good_arr = new fruitObj(1, 2, 3, 4);

// 객체 를 넣음.
const price_1 = [사과, 딸기];
const state_1 = [true, false];
const ratio_1 = [0.5, 1];
//  ... 이게 상품의 갯수 만큼 계속 늘어나야함.
```

3. 기능들?

- 기준은 원본 배열을 훼손 함수 - 불변성(immutable)
  - 원본의 배열은 고치면 안된다
  - 스프레드 연산자로 복사해서 그걸 수정하는 형식으로 해라.
  - 임시저장\_
    // rest 파라미터
  - function go(...arr)
    // 배열을 복사하는 스프레드 연산자
  - [...arr, 원본배열]
- 기준은 원본 배열을 유지하고 복사해서 결과를 돌려주는 함수

- useState > 원본이랑 비교해서 다르면 > 리렌더링

4. 원본을 훼손하는 것과 원본을 복사하여서 원본을 유지하고 복사본을 사용하는 이유?

- React 의 Re-Rendering 을 위해서

5. 배열에서 고차함수들의 기본형을 꼭!!! 알자

- 고차함수는 원본 배열을 복사해서 사용한다.
  - 데이터 불변성을 위해서 고차함수를 사용
    배열.함수명( 고차함수 > (요소,인덱스,복사배열) = > {...})

redux ====> reduce 를 보고 이름 정함

//
[1,2,3,4].reduce((acc, cur, index, arr)=>{
return acc + cur, 0 (초기값)
})

배열

- 데이터 구조 잡는게 중요

- 고차함수 사용 - 불변성 유지

- XHR, fetch, axios , ajax (jQuery)로 api 연동
- 서버 : 인터넷에 주소와 포트를 공개한 컴퓨터
- 클라이언트 : 서버를 이용하는 컴퓨터

  - 서버의 종류(3가지)
    1.1. 웹(web)서버(풀)

        - 클라이언트가 요청(Request)을 보내면 받아서
        - 데이터 베이스 에 CRUD 를 요청하고
        - 다시 클라이언트에게 응답(Response) 하는 용도의 컴퓨터
        - cont > db > cont > view
        - 일반적으로 html, css, js 도 함께 만들어서 제공하는 경우를 말합니다.

          1.2. API 서버(자료만 주는 서버)

        - 서버 만 관리하는 직업이 있음 데브업스
        - 클라이언트가 요청(Request)을 보내면 받아서
        - 데이터 베이스 에 CRUD 를 요청하고
        - 다시 클라이언트에게 응답(Response) 하는 용도의 컴퓨터
        - 일반적으로 형태가 JSON 형태

          1.3. 데이터베이스 서버

        - table 모양의 데이터 베이스 프로그램(엑셀)
          - mySql, oracle, msSql, maria DB
        - 문서 형태의 데이터 베이스 프로그램(메모장)\_
          - 파일 하나에다가 json 형태로 저장
          - 하나의 폴더에 각각을 저장함.
            - mongo DB, FireBase

    ==============================================================================================

3. api 연동
   3.1. XHR 를 이용한 연동
   : Xml Http Request
   예제)

```js
const xhr = new XMLHttpRequest();
const method = "GET";
const url = "https://7942yongdae.tistory.com/";

// 요청을 초기화 합니다.
xhr.open(method, url);

// onreadystatechange 이벤트를 이용해 요청에 대한 응답 결과를 처리합니다.
xhr.onreadystatechange = function (event) {
  const { target } = event;

  if (target.readyState === XMLHttpRequest.DONE) {
    const { status } = target;

    if (status === 0 || (status >= 200 && status < 400)) {
      // 요청이 정상적으로 처리 된 경우
    } else {
      // 에러가 발생한 경우
    }
  }
};

// 서버에 요청을 보냅니다.
xhr.send();
```

3.2. fetch 를 이용한 연동

예)

```js
const method = "GET";
const url = "https://7942yongdae.tistory.com/";

fetch(url, {
  method: method,
})
  .then((response) => {
    if (response.ok) {
      return response.text(); // 응답이 성공적인 경우
    } else {
      throw new Error("Network response was not ok."); // 에러가 발생한 경우
    }
  })
  .then((data) => {
    // 여기서 응답 데이터를 처리합니다.
    console.log(data);
  })
  .catch((error) => {
    // 여기서 에러를 처리합니다.
    console.error("There has been a problem with your fetch operation:", error);
  });
```

3.3. axios 를 이용한 연동

```js
const method = "GET";
const url = "https://7942yongdae.tistory.com/";

axios({
  method: method,
  url: url,
})
  .then((response) => {
    // 요청이 정상적으로 처리된 경우
    console.log(response.data); // 응답 데이터를 처리합니다.
  })
  .catch((error) => {
    // 에러가 발생한 경우
    if (error.response) {
      // 서버가 응답했지만 상태 코드는 2xx 범위 밖에 있는 경우
      console.error("Error:", error.response.status, error.response.statusText);
    } else if (error.request) {
      // 요청이 만들어졌지만 응답을 받지 못한 경우
      console.error("No response received:", error.request);
    } else {
      // 요청을 설정하는 중에 문제가 발생한 경우
      console.error("Error setting up request:", error.message);
    }
  });
```

3.4. ajax 를 이용한 연동

```js
const method = "GET";
const url = "https://7942yongdae.tistory.com/";

$.ajax({
  method: method,
  url: url,
  success: function (data) {
    // 요청이 정상적으로 처리된 경우
    console.log(data);
  },
  error: function (jqXHR, textStatus, errorThrown) {
    // 에러가 발생한 경우
    console.error("Error:", textStatus, errorThrown);
  },
});
```

================================ 4. fetch 상세 문법 살펴보기

4.1. 기본문법

```js
// https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch
// POST 메서드 구현 예제
async function postData(url = "", data = {}) {
  // 옵션 기본 값은 *로 강조
  const response = await fetch(url, {
    method: "POST", // *GET, POST, PUT, DELETE 등
    mode: "cors", // no-cors, *cors, same-origin
    cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, *same-origin, omit
    headers: {
      "Content-Type": "application/json",
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: "follow", // manual, *follow, error
    referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify(data), // body의 데이터 유형은 반드시 "Content-Type" 헤더와 일치해야 함
  });
  return response.json(); // JSON 응답을 네이티브 JavaScript 객체로 파싱
}

postData("https://example.com/answer", { answer: 42 }).then((data) => {
  console.log(data); // JSON 데이터가 `data.json()` 호출에 의해 파싱됨
});
```

5. 나머지 메소드도 그런지?

```js
const instance = axios.create({
  baseURL: "https://some-domain.com/api/",
  timeout: 1000,
  headers: { "X-Custom-Header": "foobar" },
});
```

## 29장 Math

//
getBoardTotal = 13

게시판 페이지당 5개
몇페이지? (페이지네이션)

// 올림
13 / 5 = .ceil(2.6) > 페이지가 3페이지 나오니까 올림...

prev 1 / 2 / 3 / 4 / ... next

- 클래스명 : 대표적인 명사로 하면 된다.
  : 이름만 봐도 알 수 있는 것.
  : 관련있는 데이터를 묶어서 관리하려는 데이터 타입(종류)
  : 사과, 딸기, 상추 > class 야채 {}
  : 곽도억, 김민지 > class Student {}
- 함수 : 동사(카멜케이스? 파스칼 케이스?)
  : 이름만 봐도 알 수 있는 것.
  : 낙타 표기법 : studentSay();
  : 대문자 표기법 : StudentSay(); (생성자함수 객체생성)

- open api는 get만 있다고 보자

- 어디서 봤던거 처럼 만들면 잘 만들었다.

- 교수님이 따로 말이 없더라도 git add, push 해놓을 것

- 코드 변천사(xhr, fetch , axios, ajax)

- 캘린더, 리덕스, JWT 인증, 파일업로드

- 데드라인 > 우선순위대로 하다보니 일정이 안맞았다...

- 로그인

  - 프론트에서 관여 할 필요가 없다함.

- 자만심/교만을 가지지 말자

  -

- 코딩 컨벤션

  - 규약...

- 프로젝트에 대한 공포
  - 어차피 벽돌을 내려쳐야 합니다.
  - 손부러지면 병원가서 누워있으면 되죠.

## 세션, 쿠키의 개념

실습은 2개 (로컬 스토리지/쿠키) : 사용자 로그인 정보

- 웹브라우저 저장되는 공간은 4개
  - 웹 브라우저 프로그램에 기록
  - 웹 브라우저 데이터 베이스
  - 중요한 정보 저장하면 절대 안된다.
  - 누구나 접근가능
  -
- 로컬 스토리지(Local storage)

  - 누구나 볼 수 있음.
  - 영원히 기록됨(지울때까지)
  - 사용하지 않음. 대신 쿠키 사용.

- 세션
  - 누구나 볼 수 있음.
  - 웹브라우저 보고 있는 중만 있고, 닫으면 없어짐
  - 세션은 프론트가 관여하는곳이 아님.
  - 빽엔드에서 내려줌
  - 그러니 신경쓰지말자
- 쿠키

  - 누구나 볼 수 있음.
  - 일정한 기간을 지정해서, 생성과 삭제가 가능함.

- indexdDB

  - 요즘은 아예 안쓴다.
