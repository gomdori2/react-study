# 리액트 컴포넌트

- 퍼블리싱 > 리액트 순으로 하는 이유
  - 아직 리액트 구조를 못잡아서 그렇다.
    - 컴포넌트 잡는거.

HTML : 2가지 분리

1. 퍼블리싱 HTML

2. JSX Element라고 호칭(리액트용)
   - 배치

### 컴포넌트 폴더 구조

- 간략하게 설명해주심.
- layout 폴더(큰거) > header, footer, main
- index 폴더(자잘한 컴포넌트) > mainTop, mainBottom ...

## 1.0. 컴포넌트를 왜 생성하는가?

- 프로젝트 규모에 따라 협업이 필요로 함.
- 기능별로 html, css, js 가 별도로 관리 필요.
  - 협업 과정에서 이게 한번에 되어 있으면 협업이 힘들다.
  - 그렇기에 파일을 뜯어서 관리한다.
- css에서 쓰니까
  - 다른것은 괜찮은데 image만은 src에 넣어줘야한다.
- 리액트 구조
  - pages 폴더 내부 : 화면을 위한 페이지 들어옴.
  - 컴포넌트는 하나가 아님

## 1.1. 컴포넌트 배치되는 내용(JSX, CSS, JS)

- JSX 가 배치된다. (리액트용 HTML 태그 class => className) > index.js 안에 태그가 들어간다.
  1. JSX 내부에 DOM내부 주석이 들어간다면 오류 남.
  2. html은 나온다. > render 내부에 태그 막 넣어서 관리 x
  3. .js로 쪼개기를 해야함 - components폴더에 component 쪼개서 넣는다.
  4. class > className으로 수정해야한다.

```js
const 컴포넌트명 = () => {
  return (
    // JSX Element 리턴
    // 여러개를 리턴 불가. 프라그 먼트로 묶어줘야한다.
    <>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </>
  );
};
```

- css 가 배치된다. (background : url(경로문제))

  1. css, module, scss, emotion 등등
  2. import로 배치하자.

- js 를 배치된다.

## 1.2. 이미지를 배치하는 2가지 경우(주의사항)

- html 태그에 이미지를 배치한 경우
- inline 스타일로 할때 얘는 public/images 폴더를 참조합니다.
  - index.html 이 public에 있음

```html
public 안에 이미지를 참조
<img
  src="../images/etc/logo-kakao.png"
  alt="카카오브레인 블로그"
  className="header-logo-img"
/>
```

- css 배경으로 이미지를 배치한 경우
- src/images 폴더를 참조합니다.

- 이유
  - css 파일을 js 컴포넌트에서 사용하면 webpack 이 압축한다.
  - src에 있는 css는 src기 때문에 src images 폴더를 찾아간다.

```css
dumy {
  background: url("../images/icon/icon-search.png") no-repeat center;
  /* 해당 url 처럼 인코딩 되서 넘어감. */
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAABYlAAAWJQFJUiTwAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAK1SURBVHgB7ZnrURsxFIUPaQDcQCJXAOlAHSQdYNJASAVsB0kFxGkgpAI7aSCPBsBOATwaMOiMdoflSvuwVpJhZr+Z80OeWa3P3nv1BEZGRtrYQzy00aHRkdFBKXJrtDa6Mvpl9BfPEG30xejG6L6naOirkcIzQBst0f/PN2lnhpgunzHcQF0bozMMZJsaUUYXsDXgg7XwA7YG1mWbHJTPsH40HmtHwr4/1J5LgoLNbd8XXZZ/sC+zlr4ukTDVVMOL+ZtGOLOGfn+jOWqD8L1sHullU6M/nv6/IzK+wi4QlwlcMxwAThEJBdfEBdLgM3ONSCm2hFsTSXK3hGkmJ9YCA9Fwo/Ee6fmEyFGZwx1ic8B5rR6VwbUiQ6yRj0K8e4FANNzayMkE7gjWmV6vPL/JJcg/5IVLFLnUP+p6yGdEifZP5Ed+vCAjh6KdO7WYTqtamwNAUGpJ7pCftWi/7nqgj5FdICPQ+TF9RuR+QCE/+6IdZESGNeWyxAdrol6nrJnOzZbPyEq0NfIjR6mgkxd2Up+QOMvnjMoU7oQYjFyivEMemFZzRFqikAK7WTQyGld4Go1jDEDBXcbPkJ4C7mHEYBZwa2WKdMjaiLatVrAbm3rH3I5OEB+ZUlU0og0yp3C/UmwzPhODa8OHTLFqjxIjzd7Cf9yU5JCD4b30vIw1wz12yNUE+yzgP21MFhGi4DdTRWcGG6E9tBtjP2fodw2xlZltvmZ1En/c8hyXEivYjRHXbPvlc29glzoKzfAAXJ7U0NCJ0TckgANAU3RCxL502fcJMqYZUbCXNJtSIQaYXgXcITa7GaJg62OBR1Objj+/NPqI9jliazMxL0PrFzqcZ6rt6X/YuqFYQ30vcmjmXPyWtGZS0hSZHMe30fGZSXUrkBxp5hwvGKYTBwrOZbnPEUZGXjwPpHWHxr3CqWQAAAAASUVORK5CYII=)
    no-repeat center;
}
```

- 주의사항 : 이미지의 경우 특히 css 배경이미지는 주의하자.

```js
import React from "react";
import ReactDOM from "react-dom/client";
const root = ReactDOM.createRoot(document.getElementById("root"));

// 상단에 출력할 JSX
// 너무 복잡 > 컴포넌트 사용
// 컴포넌트 변수는 무조건 const > 값이 바뀔리가 없음. > 동일명 오류 잡아내려고
// 컴포넌트 변수는 리액트 컴포넌트 규칙 맨앞글자 대문자임.
// 컴포넌트 변수는 무조건 function
// const Header = function () {
//   return (
//     <header>
//       <h1>상단</h1>
//     </header>
//   );
// };
// const Main = function () {
//   return (
//     <main>
//       <h1>메인</h1>
//     </main>
//   );
// };
// const Footer = function () {
//   return (
//     <footer>
//       <h1>푸터</h1>
//     </footer>
//   );
// };
// html 다 때려 넣어도 나오긴함. > 구조가 너무 복잡해져서 위 방법
// 이것도 나중되면 복잡 > js 파일로 뜯어서 보기 쉽게 해준다
root.render(
  <div>
    {/* <header>안녕</header>
    <main>메인</main>
    <footer>하단</footer> */}
  </div>
);
```

하나의 화면은 여러개의 요소(컴포넌트를) 배치하는게 관례

## 1.3. js를 React 로 마이그레이션 진행

- 리액트스럽게 바꾸는 과정

### 1.3.1. load 가 useEffect 로 변경

```js
window.addEventListener("load", function(){})
↓ 변경
useEffect(()=>{
  return ()=>{}
},[])
```

### 1.3.2. querySelector 가 useRef(null) 로 변경

```js
  const tag = document.querySelector(".bt");
  const bt = useRef(null);
  <button ref={bt}>
  useEffect(()=>{
    bt.current.innerHTML = "와아아"
    return ()=>{}
  },[])
```

## js 14장

- var를 쓰지말자.

- 외부에서 변수 및 함수에 접근할 수 있는 권한 (클래스에서 설명나옴)

public : 외부 어떤 곳에서도 사용할 수 있다.

private : 외부에서 절대로 사용할 수 없다.

protected : 허용한 대상만 사용할 수 있다.

# js 15장

```txt
### const 주의사항(오해의 소지가 있는 경우)

const 객체 = {} 오해의 소지가 발생.

정군은 const 는 절대로 값이 안변한다.

값을 변경하려고 하면 에러난다.

const age; // 무조건 값이 undefined로 고정된다.

const age = 15;

age = 100; // 에러..

const 정군 = {age : 10}      // 이미 주소는 고정이 되어 버렸다.

정군 = 11

- // 주소를 교체 하려고 했다.
- 그래서 const 에 위배된다.  에러

정군.age = 10

- 주소를 교체하는 것이 아니고, 안쪽의 연결된 내용을 수정한다.

// 메모리주소를 바꾸니 오류가 터짐.

정군 = “안녕”

// 메모리 주소 내부의 값을 변경은 된다.

// 내부는 교체 가능 메모리 주소를 바꾸는 것은 안된다.

정군.age = 10

정군[age] = 10

var vs let vs const

- var 키워드는 사용하지 않는다.
- 재할당이 필요한 경우에 한정해 let
    - 변수의 스코프는 최대한 좁게 만듬
- 변경이 발생하지 않고

### 변수 선언

1. const 변수이름 : 값을 고정시키겠다.
    - 소스 열었을 때 대문자 : 상수
2. let 변수이름      : 값이 수시로 바뀌어집니다.
```

# 실 업무에서 알아야 하는 상식

## 1. nvm(Node Vertion Manager) 설치 및 활용

: https://github.com/coreybutler/nvm-windows/releases

: 설치 버전 확인 `nvm -v`
: 설치 가능한 버전 목록 `nvm list available`
: 설치 하기 `nvm install 버전`
: 현재 사용중인 Node 버전 확인하기 `node -v`
: 현재 설치된 Node 목록 확인 `nvm ls`
: 사용할 Node 버전 선택하기 `nvm use 버전`
: Node 설치된 경로 알아보기 `which node`

## 2. yarn 세팅

- npm 보다는 yarn 선호
  - Node Package Manager (node_modules)
  - package.json 의 dependencies 목록을 참조
  - npm 이 가끔 다운로드 중 오류가 발생하고, 소스가 깨짐 현상
  - 예) 네이버 Toast UI 등.
- npm 보다 안정적인 package 관리를 위해서 yarn 을 활용
- `npm install -g yarn`
- `yarn --version` yarn 버전 확인.
- npm i 패키지명
- yarn add 패키지명

## 3. favicon 만들기(디자이너 담당)
