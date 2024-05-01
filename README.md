// git 협업

1. 카카오가치같이 팀 협업

- 프로젝트 명 > 폴더 생성
  : TypeScript 로 프로젝트 생성 > 권장사항
  : npx create-react-app ./ --template typescript

- 팀장이 협의하에 기본형을 생성한다.
- 기본형 생성 후 GitHub 에 저장소 생성한다.
- 팀원은 GitHub 주소를 공유 받는다
- 팀원은 공유받은 주소에 가서 fork 를 받는다.
- 팀원은 본인의 주소로 가서 fork 주소를 확인한다.
- 팀원은 PC 에 fork 한 주소를 클론한다.
- 팀원은 PC 에서 브랜치를 생성한다.
- 팀원은 PC 에서 브랜치로 이동한다.
- 팀원은 PC 에서
- 팀원은
- 팀원은
- 팀원은
- 팀원은

# JS 12 장

원시데이터 ===> 값
복합데이터 : 복잡한 속성, 메서드를 가진 객체 ===> function, [], {}.

"함수(값)는 객체의 문법을 따르는 값이다." >

function 함수이름(매개 변수){
return 문장을 작성 (값을 `반드시` 출력 : 표현식!!)
}

함수이름(인자) : 함수 호출, 함수 실행, 함수 콜...

리터럴은 JS 가 알아먹을 수 있는 데이터 형태로 작성한 것
const a = 1; 숫자 리터럴
const add = function (){} > 함수는 객체 > 함수 리터럴

JS 의 일급객체에 대해서 말해 보시오.
함수가 일급 객체일까 ?

1. 값처럼 변수에 할당할 수 있는가?
   const add = function() {}
2. 객체의 프로퍼티의 값으로 담을 수 있는가?
   const obj = {add : function (){}} > 메서드

3. 배열의 값으로 담을 수 있는가?
   const arr = [1,2,3,function(){}, {}, []]
4. 함수의 매개변수 값으로 전달할 수 있는가?
   function 말해봐(기능){
   // 함수는 객체의 값으로 쓰임.
   // 그렇기 때문에 넘길 수 있다.
   기능();
   }
   const 안녕 = function(){}

   안녕(function (){console.log("안녕하세요")}) // 한번 사용하고 사용 X 시 함수 정의하고 쓰지말고 그냥 익명 써라

함수 가 객체를 생성하는 함수를 객체 생성자 함수 라고 한다.

// 자바스크립트 엔진이 만든것.
JS 의 함수에 전달되는 매개변수 목록을 arguments 라는 객체 라고 한다.

1. {} > 객체 리터럴 변수에 할당

2. object 함수 문법

3. 생성자 함수 문법

4. Object.create 함수 문법

5. class 함수 문법

- 함수의 매개변수로

1. 원시 값을 인자로 전달하는 경우
   const age = 15;
   function grow(\_value){
   return \_value + 5;
   }
   grow(age);

age 는 얼마인가?

age 는 변화가 없다.

2. 객체를 인자로 전달하는 경우
   const person = { age = 10, }

function grow(\_who){
\_who.age = 150;
}

// 객체의 참조(주소) 값 전달
grow(person); > 메모리 주소가 전달 되기 때문에 값이 변동됨.

// 객체의 상태가 변경이 일어난다.
// 예측하기가 곤란하다.

즉시 실행 함수
(function(){
실행할거.
})();

중첩 함수
이런 구조
function outer(){
function inner() =>{}
inner()
}

리액트에서는 클로저가 대부분이다.
function outer(){ > rafce 구조
const handelClick = () =>{}
inner()
return (jsx 구문)
}

- 콜백 함수가
  // window에 메서드를 콜 후 2번째 매개변수에 메서드를 콜백시킴.
  window.addEventListener("이벤트", function(){

});

// 함수

순수 함수 - 권장

- 외부에 영향을 끼치지 않는 함수

```js
ex)
function add(a,b){
	return a+b;
}
```

비순수 함수 - 권장 하지않음

- 외부에 영향을 받는 함수.

```js
const age = 10;
function add(a, b) {
  return age + b;
}
```

# js 13 장

스코프(scope) : 대상을 사용할 때 어디를 찾을 범위

- 대상 : 함수, 변수, 클래스 등...

- var 변수

- let 변수, 또는 const 변수가 차이가 큽니다.

- 함수를 실행 할 때 내부에 그 변수가 있는지를 먼저 찾고
  이후 전역으로 올라가서 찾는다

```js
// 설명으로 바깥쪽 (함수의 바깥쪽)
// 통상 전역(global)스코프라고 합니다.
var age = 15;

function say() {
  // 통상 `지역(local) 스코프` 라고 합니다.
  console.log(age); // 지역 찾고 위에 전역에 있으니 전역변수를 가져옴

  console.log(name); // undefined > 없으니
}
say(); // ?
```

```js
// 설명으로 바깥쪽 (함수의 바깥쪽)
// 통상 전역(global)스코프라고 합니다.
var age = 15;

function say() {
  // 지역 스코프에 해당 변수가 있으면
  // 따로 전역을 뒤져서 그걸 가져오지 않음.
  var age = 100;
  console.log(age);
}
say(); // ?
```

```js
var var_1 = 1;
if (true) {
  var var_2 = 2;
  if (true) {
    var var_3 = 3;
  }
}
function say() {
  var var_4 = 4;
}
console.log(var_1); // var_1 찾고
console.log(var_2); // var_1 찾고 > var_2 찾고
console.log(var_3); // var_1 찾고 > var_2 찾고 > var_3 찾고
console.log(var_4); // undefined 함수 내부에 있고 실행 x
```

렉시컬 환경(실행과 작성위치)

JS는 레시컬 스코프를 기본으로 합니다.

- js 는 대상이 코딩 즉, 작성할 때 스코프가 정해진다.
- 즉, 그때 그때(실행 시) 스코프가 달라지지 않는다.

코드 작성 시 > global

```js
   // 작성하는 순간에 지경을 잡음.
age += 1; > global
function say(){
   // 내부에 적기 시작하면 내부로 스코프가 정해짐.
   var id = "hong" // 지역
}
// global에서 실행
say();
```

- 앞으로 살펴볼 내용 예습

```js
let age = 1; // 호이스팅 X
if (true) {
  let age = 2;
  if (true) {
    let age = 3;
  }
}
console.log(age);
```

```js
// 다 덮어쓰고 넘어감.
// var 는 펑션을 기준으로 체크함
var age = 1; // 호이스팅 X
if (true) {
  var age = 2;
  if (true) {
    var age = 3;
  }
}
console.log(age); // 3이 나옴

// -------------------------------------------------------------

// {} 블록이 있으면 한문장으로 생각함.
// let 은 {}(블록)을 기준으로 체크함
// 건너뜀
let age = 1; // 호이스팅 X
if (true) {
  let age = 2;
  if (true) {
    let age = 3;
  }
}
console.log(age); // 1이 나옴
```

# 리액트 프로젝트 준비

## 0. 사전준비

- node.js 설치 (nvm 을 통해서 버전 교체 가능) - node.js 설치는 회사규칙
- npm 은 자동으로 설치됨.
- yarn 은 직접 설치하여야 함.
- gitHub 에 repository 생성.

## 1. 프로젝트 생성법

: 폴더명은 규칙 (소문자로)
: 리액트 프로젝트

- npx create-react-app ./ --template typescript

## 2. 진행순서

: public > www 폴더 생성 > images, js, assets, css 폴더 생성
: React js 버전으로 진행. (CSR) > 바로 타입스크립트로 들어가는걸 (권장) - 현재는 안배웠음.
: React ts 버전으로 진행.
: Next ts 버전으로 진행. (SSR)

## 3. 프로젝트 내용 기본 파악하기

### 3.1. node_modules

: npm 또는 yarn 으로 다운로드 받은 파일 보관 폴더
: npm install 라이브러리명 을 이용하여 다운로드 받고 활용
: 만약 프로젝트가 라이브러리 등의 오류가 발생했다면(파일 깨졌을 때)

- node_modules 폴더 삭제
- package-lock.json 파일 삭제 - node_modules 에서 다운받은 목록이 들어가 있음.
- 이후 `npm i` 를 작성 후 실행(터미널)
  : 깃허브에 push 대상에서 제외하기 위해 .gitignore 에 자동 입력 되어있음.

### 3.2. public 폴더

- **꼭 기억하세요. 압축 안됩니다.**
  - 용량 최적화를 하지않음.
  - Webpack에서 제외됨.
  - Webpack > 용량최적화 시켜주는 거
  - 파일들이 있다면 src에 넣어두자.
    - src는 Webpack 해준다.

### index.html

- 최초 웹서비스 실행 시 실행되는 파일명.(파일명 변경 불가)
- lang="ko" 수정
- favicon 아이콘 수정
- SEO 관련 내용은 별도 추가 (네이버 검색, 구글 검색, GA4 적용 예정)
- apple-touch-icon 수정
- title 내용 수정
- manifest.json 은 추후 내용 수정필요
- id="root" 는 리액트 미리보기 및 결과물이 배치되는 장소

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <!-- SEO 적용 필요 : 네이버 검색 및 구글 검색 등록, GA4(누가 왔는지 분석 하는 것) 예정 -->
    <meta name="description" content="카카오 브레인 블로그 클론 코딩" />
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <title>카카오 브레인블로그</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

: manifest.json

- https://web.dev/articles/add-manifest?hl=ko

```json
{
  "short_name": "카카오 브레인 블로그 클론코딩",
  "name": "카카오 브레인 블로그 클론코딩",
  "icons": [
    {
      "src": "favicon.ico",
      "sizes": "64x64 32x32 24x24 16x16",
      "type": "image/x-icon"
    },
    {
      "src": "logo192.png",
      "type": "image/png",
      "sizes": "192x192"
    },
    {
      "src": "logo512.png",
      "type": "image/png",
      "sizes": "512x512"
    }
  ],
  "start_url": ".",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff"
}
```

: robots.txt

- 검색엔진 로봇이 내용을 접근해서 보관하는 여부 설정
- 상세 경험은 네이버 및 구글 검색엔진 등록 시 실습
  - 크롤링
  - 정보 기재로 필요 정보를 제외시키거나 할 때 사용

# 3.3. src 폴더

- webpack 의 대상폴더
- index.js
- 리액트 실행 시 최초 대상의 파일

```js
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

// 아래 모양이 기본형태임 주석빼고.

// 아래 라이브러리는 구글의 웹 성능 리포트 기능
// import reportWebVitals from "./reportWebVitals";
// react가 만든 html에 아이디 root를 찾아서 태그 가져와라
const root = ReactDOM.createRoot(document.getElementById("root"));
// root 태그에 .render로 해당 jsx(프라그먼트)를 그려줘라
root.render(
  // StrictMode 콘솔을 2번 찍어준다. 디버그 전용 <React.StrictMode>  </React.StrictMode>
  <App />
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
//reportWebVitals();
```

```js
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

// react study에 정리 되있음.
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

## src 내부 삭제 해야될 파일

### TDD 관련 파일 제거 (Test Driven Devlop)

- App.test.js
- setupTests.js
- TDD란?

  - 테스트 주도 개발
  - 프로젝트 다 끝나고 나중에 알려주신다함.
  - 성공 가능성이 있는 프로젝트라면 TDD를 한다함.
  - 시제품이 들어가고 반응이 좋으면 TDD 적용 후 고도화

- 성능 측정 파일 제거

  - reportWebVitals.js

- App.js 는 최초 하면에 보여지는 내용

# 3.4. .gitignore 파일

- 깃허브 파일 예외 사항 기재
- 폴더 및 파일 작성하면 제외됨.
- git에 파일 제외 시키는 명단
- 추후 내용 작성 필요(예. 인증키(.env))

# 3.5. package-lock.json

- node_modules 에서 사용된 라이브러리의 버전 보관

- 빽업 파일이라 보면됨.
- 손도 대지말고 그대로 둬라
- 대신 파일이 깨졌을 땐 node-modules하고
  package-lock.json 삭제하고 npm i 해서 다시 설치해라

# 3.6. package.json

- 라이브러리 뭐 썼는지 알 수 있음.
- node.js 프로젝트 생성 시 기초 정보 관리내용
- `매우 중요` dependencies
  - dependencies 항목이 중요합니다.
    - 프로젝트에 실제 활용한 라이브러리 목록(파악용도)
    - 최종 빌드한 소스에 포함이 되는 라이브러리들 목록
    - 개발 / 최종 빌드한 소스에 포함이 되는 라이브러리들 목록
      - npm start 개발 시 포함
      - npm build 배포 시 포함
- 인터넷에 같이 올라가는 것

- 밑에 @testing 으로 된거 주석으로 된거는 지워라

```json
"dependencies": {
    //"@testing-library/jest-dom": "^5.17.0",
    //"@testing-library/react": "^13.4.0",
    //"@testing-library/user-event": "^13.5.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    //"web-vitals": "^2.1.4"
  },
```

# React 기초 1.
