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

활용 빈도가 높은 css
:before
:after

```html

```

```css
/* css로 해당되는 태그의 앞쪽과 뒤쪽을 찾는 것.
            before, after*/
.wrap {
  position: relative;
  width: 100%;
  height: 400px;
  background-color: goldenrod;
  margin: 100px auto;
  padding: 50px;
}
.box {
  position: relative;
  width: 100px;
  height: 100px;
  margin: 100px auto;
  background-color: hotpink;
  text-align: center;
}
.box span::before {
  display: inline-block;
  content: "";
  width: 4px;
  height: 4px;
  background-color: red;
  border-radius: 10px;
  position: absolute;
  left: 24px;
  top: 1px;
}
.box span::after {
  display: inline-block;
  content: "";
  width: 10px;
  height: 10px;
  background-color: blue;
}
```

```html
<div class="wrap">
  <div class="box">
    <span>안녕</span>
  </div>
</div>
```

## js 16장. Property Attribute (get, set, 불변객체(freeze))

[[단어]]

const Obj = {}
Obj.[[Prototype]] 이렇게 정의는 되어도
우리는 사용할 수 없어요.
Obj.**proto** 이렇게 접근이 가능하도록 개방됨.

const Person = {
age: 10
}
Pesong.nickName = "홍길동";

console.log(Person.age); // 개발자가 활용
console.log(Person.nickName); // 개발자가 활용

Person.age // [[value]] ===> true,

Person.job = "학생";
Person.age // [[writable]] ===> true,

// 반복을 통해서 요소들을 출력할 수있다.
Person.age // [[enumarable]] ===> true,

Person.age = 10000
Person.age // [[configurable]] ===> true,

const [age, setAge] = useState(0)

const who = {} // const 적용시 불안정하다.
who = "안녕" // 변경 불가

who.age = 100; // 막을 방법이 없다.

객체 변경 금지... (완벽하게 막을 수 없어서)
: 객체를 복사해서 사용
: lodash 라이브러리 활용 (https://lodash.com/docs/#cloneDeep)

객체 만드는 법
: 객체 리터럴 {}
: 함수로 객체만드는 법 (4가지)

모든 hook 들은 컴포넌트 js 의 첫번째 영역에 배치를 하자.

- 일반 변수는 값이 바뀌어도 재렌더링 없음.

- 의존성 배열은 나중에 알려주신다함.
- 리액트 변수는 값이 바뀌면 재 렌더링 되므로 화면 반영

모든 hook 들은 컴포넌트 js 의 첫번째 영역에 배치를 하자!

hook ?

일반 변수는 값이 바뀌어도 재렌더링 없음
리액트 변수는 값이 바뀌면 재 렌더링 되므로 화면 반영

1.  리액트용 변수 즉, useState 는 재 렌더링시 표현된다.

2.  리액트용 변수 즉, useState 는 컴포넌트에서만 작성할 수 있습니다.

3.  useState 는 비동기이므로 즉시 참조할 수 가 없다.

4.  useState 에 직접 값을 변경할 수 없다.
    const [age, setAge] = useState(0);
    age = 100; (X)

5.  useState 에서 현재값을 참조하고
    즉시 갱신을 하려면 함수를 활용하여 업데이트 한다.

    const [age, setAge] = useState(0);
    setAge(age++); // 1 이 되지 않는다. 즉, 즉시 갱신 되지 않는다.
    console.log(age);
    // 우리는 1증가한 값을 기대하였다. 하지만 값은 옛날거 유지
    // 함수가 종료되면 그때 업데이트 된다.

    const [isOpen, setIsOpen] = useState(false);

    const clickMbbt = () => {

        const now = !isOpen;
        setIsOpen(now);

        //     즉시 갱신을 하려면 함수를 활용하여 업데이트 한다.

        // setIsOpen((prev) => {
        //   return !prev;
        // });

    };

6.  useState 에서 기존 값 참조 후
    직접 값 갱신 리턴 받아서 바로 사용하고 싶다.

    const [age, setAge] = useState(0);
    setAge(age++) ; // 기존 방식 (새로운 값 안나옴)

    setAge( 이전값 => { return 새로운값 } ) // 함수 방식(새로운 값 나옴)
    setAge( prev => { return prev+1 } ) // 함수 방식(새로운 값 나옴)

useState 정리

## js 17장

1.  객체 가 뭘까?

: 객체를 만든다는 말은 데이터를 설계하는 것.
: 예) 유아제품을 판매하는 서비스에서 제품을 표현한다면?

: 여러 개의 데이터와 여러 개의 기능을 묶어서
마치 데이터종류처럼 사용할 수 있다는 장점

하나의 이름으로 {
데이터... 가지고 있고,
데이터... 가지고 있고,
데이터... 가지고 있고,
기능... 가지고 있고,
기능... 가지고 있고,
}

    const Person = {
       age: 10,
       nickName: "홍길동"
    }

    Person 의 데이터 타입(종류)
    -  객체:Person ====> { age:number, nickName:string}

2. 객체 는 정말 좋은데 (다양한 자료를 묶어서 이름 한개로 표현 가능)
   만드는 방법이 2가지 형태(리터럴, 함수)를 띈다.

2.1. 객체 리터럴

- 장점 : 가독성, 관리 손이 고생한다.
- 단점 : CRUD가 힘들다.
  const obj = { name : "귀마개", count:10} > JSON

  > 객체 내부에 데이터를 다룰 때.. 문제가 많음.
  > const obj_1 = { name : "귀마개", count:10}
  > const obj_2 = { name : "귀마개", count:10}

- 이것을 개개로 만들지 말고 함수로 만들자 해서 나온게
  ↓
  2.2. 객체 생성자 함수 사용 - object 생성자 함수
  Object() : ? 함수 call 하는 구나.

  > new / return 없이 하면 undefined
  > new Object()
  > : ? new 함수 call 하는 구나.
  > new는 문법 Object() 객체 생성
  > this라는 것을 돌려줌.

- 2.2.1. 관례

  > : 개발자가 함수의 모양만 봐도 객체생성함수 / 일반함수 인지 구별이 가능하다.
  > : 앞글자가 대문자일 경우 > 객체 생성함수임.
  > Swiper()
  > Axios()
  > : 일반적으로 call 하는게 아니다를 표현한다면

  - new Swiper()
  - new Axios()

- 2.2.2. 함수 안쪽에 this 는 죄송하게도 call 방식에 따라서 this 의 값은 다르다.
  function Foo(){

  }
  Foo(); // this 는 window
  new Foo(); // this 는 만들어질 객체 (인스턴스 : 앞으로 보관될 것)
  2.2.3. 제발 용도를 구분하셔서 함수 call 과 new 객체생성자함수 를 구분하셔서
  리턴을 하셔야 해요.
  : 일반 함수는 자유롭게 return 값;
  : 객체생성용 함수는 제발 return 적지 마세요.

  2.2.4. constructor 함수 / none-constructor 함수
  : 모든 함수는 new 사용가능(constructor)
  : 근데, ES6 도입 후 new 사용못하는 함수
  (화살표함수, 축약메소드 함수 none-constructor)

  ```js
  축약형 메서드
  function a(){
    x () {}
  }
  ```

  2.2.5. new로 생성된 객체(인스턴스)의 원본확인 연산자 instanceof
  : 객체 확인용

  2.3. 클래스 함수 사용 (25장에서 등장)

1. 매개변수이름 은 관례상 props 라고 작성합니다.

```js
<Header clickMbbt={clickMbbt} age={10} />
1번 방법
const MbHeader = (props) => {
  props.clickMbbt();
  props.age;
  return (....)
}

2번 방법
const MbHeader = (props) => {
  const clickMbbt = props.clickMbbt;
  const age = props.age;
  clickMbbt();
  console.log(age);
  return (....)
}

3번 방법 - 3, 3.5 : 타입스크립트에서 도움을 받을 수 있다.
const MbHeader = ({clickMbbt}) => {
  clickMbbt();
  return (....)
}

3.5번 방법 - 매개변수가 여러개일 때.
const MbHeader = ({clickMbbt, age}) => {
  clickMbbt();
  console.log(age);
  return (....)
}
```

2. 리액트 용 변수 즉, useState 이해
   : 컴포넌트에 새로고침을 진행하도록 한다. (useEffect 를 강제 실행)

- 대신 자기자신의 컴포넌트만 렌더링 되게 한다.

: useEffect 용도?

```js
- 컴포넌트가 생성될 때 실행하고 싶은 것
  - 이건 선언 시

    useEffect(()=>{
    // 죽어도 한번만 실행하라!
    },[]); // [] 에 아무것도 작성하지 않는다면.
- 컴포넌트가 제거될 때 실행하고 싶은 것

  - cleanUp 함수
    useEffect(()=>{
      return ()=>{
      // cleanUp 함수
      // 죽을 때 한번만 실행한다.
      }
    },[]);

- 컴포넌트가 업데이트될 때 실행하고 싶은 것
  - 의존성 배열
    useEffect(()=>{
      return ()=>{
      }
    },[
      // 업데이트 될 때 마다 실행한다.
      // 리액트 변수 useState변수.
    ]);
```

: 리액트 변수 만들기

```js
// 각각의 컴포넌트에서만 사용가능.
// [겟이름(getter함수) : 없어도 오류는 안남, set이름(setter함수)  : 없어도 오류는 안남 _ 대신 값을
// 갱신 못한다.]
const [겟이름(getter함수), set이름(setter함수)] = useState(초기값);

: 리액트 변수 값 고치기
- 이러시면 안되요.
  - get이름 = 값을 직접 입력은 반영 안된다.
    - js 형식으로 하지마라.
- 함수가 종료되어야 업데이트 된 결과를 참조할 수가 있다.
- 방식은 2가지
  1. 즉시 변경이 안됨. : 함수가 끝날 때까지 기다림.
  set이름(새로운 값);
  const [mbMenuOpen, setMbMenuOpen] = useState(false);

  2. 즉시 변경 : set안에 함수를 넣어서 내부 함수의 block이 끝나는 시점에 종료시켜서 값을 뱉어냄.
  set이름((기존값)=>{return 새로운값;})

- 활용 예)
const clickMbbt = () => {
  setMbMenuOpen((prev) => {
    return !prev;
  });
};
```

useEffect

- addEventListner같은건 따로 관리하는게 좋다.

1. Magic Number를 상수로 만들어서 export 하기

if (조건식) {
// 조건식 이 참일때
}else{
// 그렇지 않을 때 즉 거짓일때라고 보면 됨.
}

== 값
1 == "1" true

=== 값 그리고, 종류까지 비교
1 == "1" false

Swiper 는 js 로 하면됩니다.

근데...

Swiper 는 리액트용 npm 제공.

vw 계산하기

## js 18장

- 일급 객체
  : 익명 리터럴로 생성이 가능해야 인정
  : 저장가능하니? 데이터 자료로
  const go = function(){}
  const obj = {}
  : 함수(매개변수) 및 리턴 가능?
  function say( \_val){}
  say(go)
  say(obj)
  useEffect(()=>{
  cleanUp 함수
  return ()=>{}
  },[])

1. 유사 배열 객체 / 이터러블
   : Rest 파라미터 function(...args){}

- 배열처럼 생긴 객체 > 배열은 아님.

- 순회 즉 반복이 가능하다.

- 스프레드 연산자는 배열로 만들어준다.
  const arr = [5,8,77,9,7];

arr.reduce(함수, 시작값)
[5,8,77,9,7].reduce(함수, 시작값)
arr.reduce( function(){},0)

arr.reduce(function(이전요소, 다음요소, 원본){},0)

// 배열 안쪽에 있는 값을 반복문 없이 알아서 더 해줌
arr.reduce(function(이전요소, 다음요소, 원본){
return 변경값
},0)

4. ** proto ** 는 객체의 prototype 요소에 접근할 때 작성

5. Prototype 은

- 상속(extension) 구현하기 위해 활용
- 객체 생성자 함수(new Obj)로 호출할 수 있는 함수객체 만이
  가지고 있는 속성이다.
- 객체 생성자 함수를 호출하면 인스턴스 변수를 만들어요.
  const slide = new Swiper();
  slide 에는 prototype 이라는 객체를 만들어 준다.
- new Obj 하면 인스턴스가 나온다 이 인스턴스는 참조한 객체의 내용을 가지고 온다

- flex : 속성값 이해

```txt
// flex-grow   : 1 다른 flex 아이템들과 동일한 비율로 나누어 가짐
// 배치후 남는 여백 설정
// flex-shrink : 1 아이템이 공간이 부족할 때 줄어 들 수 있는 정도
// 1을 주면 container 박스 안에 비슷한 비율로 줄어든다.
// flex-basis  : 0 아이템의 시작 크기 설정
// 0은 원래크기 무시 grow, shrink에 따라 결정된다.
flex: 1;
// 배치 후 남는 공간(여백) 을 나누어서 너비가 늘어나는 비율
// 1 내부 태그들이 똑같이 늘어나라.
flex-grow: 1;
// 배치 후 공간이 부족한 경우 너비가 줄어드는 비율
// 0 절대로 줄어들면 안된다.
flex-shrink: 1;
// 기본 너비 값
// 버그 있다함.
flex-basis: 0%
  flex: 1;
```

1. 프로젝트 생성은 typeScript 버전
2. ESLint 설정 (vscode 설치)
3. Prettier 설정 (vscode 설치)
4. EsLint 와 Prettier 통합
5. 기본 npm 설치
   : axios
   : react router dom
   : emotion 등등등

## js 19장

6. 프로토 타입 \_ _ proto _ \_
   : 문법의 알아야 하는 이유는 저명한 사람의 소스를 읽어야 할 때가 옵니다.

: JS 에서 객체의 기본 속성을 알고 싶다.
: \_ _ proto _ \_ 로 접근한다.
: (하지만 사용하지 마세요.)

2. prototype

   JS 에서 직접 기본 속성을 만들고 싶다. ?
   만든다는 의미는 함수를 말합니다.
   여기서 함수는 객체를 생성하는 객체 생성자 함수를 말합니다.
   이때 나는 객체의 기본 속성을 만들고 싶다. 라면

   - prototype.속성명 = 값;

3. class - ES6에서 추가됨.
   : 객체를 생성하는 문법 중 하나

4. 객체 지향 프로그래밍
   : OOP : Oriented Object Programming
   : 실세계에 존재하는 대상에 대해서 특징과 성질, 행동을 코드로 표현하겠다.
   : 프로그래밍에서 활용할 특징, 행동만 별도로 뽑아서 설계를 추상화한다.
   : 특징 또는 성질을 Properties, Attribute
   : 행동을 Behavior, Method
   : 객체는 Property, Methode를 가진 데이터

const Circle = {
radius : 3, // 속성명 : 속성값
getArea : function() {} // method : method 기능

// method : method 기능
// 축약형 new라고 못쓴다.
getArea() => {}
}

5. 상속
   : 하나의 객체의 속성, 메소드를 다른 객체가 사용할 수 있도록 허용한다.
   : 그래서 똑 같은 기능을 다시 만들지 않아도 된다.
   : 그래서 똑 같은 속성을 다시 만들지 않아도 된다.

: 아래 예제는 new 실행시 불필요하게 say 메서드가 만들어진다.

```js
function 말해봐(단어) {
  // 얘는 계속 바뀜.
  this.word = 단어;

  // 기능을 중복으로 생성할 필요가 없다.
  // 요게 계속 생성된다.
  [
  this.say = function say() {
    console.log(this.word);
  };
  ]
}

function 말해봐(단어) {
  // 얘는 계속 바뀜.
  this.word = 단어;

  // 기능을 중복으로 생성할 필요가 없다.
  // 요게 계속 생성된다.

}
// 위의 중복생성 문제를 해결하기 위해서
// prototype으로 해결한다.
// 정보만 기록이 된다.
 말해봐.prototype.say = function say() {
    console.log(this.word);
  };

// 해당 new로 객체 생성 시 ...
//
const 홍길동 = new 말해봐("밥먹고 다니니?");

const 둘리 = new 말해봐("뾰로롱");
홍길동.say();
둘리.say();
```

6. \_ _ proto _ \_
   : JS 의 모든 객체가 가진 기본값

7. prototype
   : 오로지 함수 객체에서만 존재하는 것.
   : 그래서 우리는 new 를 통해서 생성하므로
   : 적극적으로 활용을 해서 진행한다.

8. 오버라이딩
   : prototype 기능 덮어쓰기
   : 똑같은 이름으로 정의한다.

function 말해봐(단어){
this.word = 단어;
}

말해봐.prototype.say = function(){
console.log(this.word);
}

const 홍길동 = new 말해봐("밥은 먹고 다니니?");
// 홍길동. say = function(){
console.log("ㅎㅎㅎㅎㅎㅎㅎ")
}

홍길동.say();

9. instanceof
   : 여기서 instance 란?

- new 로 만들어진 변수
  : instance of 어떤객체의 instance
- new로 만들어진 변수 > 생성자 함수로 만들어진 객체

10. 정적인 property / method
    : 정적이라는 말은 객체생성자 함수에 고정시킨 속성과 메소드
    : 정적(static 이라는 단어)

11. in 연산자
    : 프로퍼티 있니?

```js
const ab = { a: 1, b: 2 };
console.log("a" in ab);
```

12. for ... in 문
    : for (변수명 in 객체) {}
    : 배열인 경우만 조심해서 사용하자.
    - 배열은 forEach임.

```js
for (c in ab) {
  console.log(ab[c]);
}
```

13. for ... of 문
    : 자주 쓰자.
    : 배열 값 뽑을 때 사용

# 리액트 프로젝트 셋팅

- 모든 프로젝트에서 공통 적용

## 1. 단계

### 1.1. 소문자프로젝트 폴더 생성

- `npx create-react-app ./ --template typescript`

### 1.2. GitHub 생성

### 1.3. 프로젝트 폴더와 깃허브 연결

### 1.4. 개발환경 셋팅

- esLint 설정
  - js 문법을 안내해 줌.
  - 오류에 대해서 설명해 줌.
  - 미리 문제발생할 소지가 있는 부분을 안내해 줌.
  - 즉 도움을 주는 도구
  - 프로젝트에서 전체 셋팅을 하는 것이 관례
    - 팀장이 eslint까지 다 세팅해서 줘야함.
  - 아래의 순서를 준수하자.
  - 충돌나던 파일 을 직접 설치
    - `npm install eslint-plugin-react@latest --save-dev`
    - `npm install eslint@8 --save-dev`
  - `npx eslint --init`
- prettier 설정
  : 문서포맷 정리
  : 들여쓰기, 따옴표, 세미콜론 등등등.
  : `npm install --save-dev --exact prettier`
  : 환경설정 파일을 / 에 만든다
  : 파일명은 약속이 되어 있다.

- esLint & prettier 설정
  : eslint 에서 prettier 의 설정 안내해 주도록 연결
  : `npm install eslint-config-prettier --save-dev`
- .eslintrc.js 수정으로 마무리
- eslint.config.mjs(module javaScript)
  - 신규프로젝트는 써도 된다.
    - 그러나 구버전은 적용시 깨진다.

```js
// 현재 eslintrc.js 가 아니라
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: ["eslint:recommended", "plugin:react/recommended", "prettier"],
  overrides: [
    {
      env: {
        node: true,
      },
      files: [".eslintrc.{js,cjs}"],
      parserOptions: {
        sourceType: "script",
      },
    },
  ],
  parserOptions: {
    ecmaVersion: "latest",
    sourceType: "module",
  },
  plugins: ["react"],
  rules: {},
};
```

### 1.5. 관련 라이브러리 설치

- axios
- react router dom
- emotion

### 1.6. 기본 퍼블리싱

- pulic / www 폴더 안에 작업 진행

### 1.7. 기본 리액트 작업

-

# 리액트의 용도

- 이동성이 좋다.
  - SNS, 실시간으로 왔다갔다하는거.
  - 은행이나 병원 같은 곳의 사이트는 적합하지 않다.

객체 생성하는 방법

1. {} 객체리터럴
2. new 객체명() 객체생성자함수
3. class class

DOM document Object Model 태그

<div 속성="값"></div>

FB 객발자가 JSX 를 만들때 DOM 을 참조해서 만들었다
ReactDom

```js
<header class="header" gogo={1}></header>

Props 는 리액트의 JSX로 만든 컴포넌트 에 매개변수로 전달할 내용

const Header = (gogo) =>{
  gogo > 1
return (<></>)
}
```

### 리액트 구성요소

1. html
2. css
3. js
4. hook

a.js

let age = 1;

b.js

let age = 100;

웹브라우저 새로 고침 - 동기 / 비동기
리액트 컴포넌트 새로 고침 - 비동기로 이루어진다고 보면 된다.
일반 변수를 쓰는 것은 리액트 스럽지 않다.
위의 문제 해결책은 되지만 리액트 서럽지 않다.

웹브라우저를 새로고침하는 것은 웹사이트 전체 초기화
컴포넌트는 useState 의 내용이 set 되면 Re-Rendering
컴포넌트는 useEffect 의 의존성배열 > [state] 내용이 set 되면 바뀌면 Re-Rendering

컴포넌트 초기값 셋팅은 Re-Rendering 되더라도 유지함.
useEffect 의 [] 생성 시 처리
useState() [] 생성 시 처리

## 정리 해야함.

- 빌트인 ( 미리 작성되어 있는 JS )
  JS 라면 가지고 있어야 하는 내용을
  MS, Apple, Google, ... 개발자

- 웹브라우저
- Node.js

  const go = "안녕"; // 기본(원시)

  . 찍고 접근하면 속성에 접근
  ? go 는 객체도 아닌데 어떻게?

  go.length
  go["length"]

  const go = new String("안녕")

  go.length
  go["length"]

  Infinity (무한값) 1/33333
  NaN (숫자아님)

  isFinite()
  parseFloat();

  isNan();
  parseInt();
  값.toString();

  http : html 로 해석하기로 약속한 프로토콜(약속)
  ftp : file 을 주고 받도록 약속한 프로토콜
  smtp : simple male transper protocol

  BE 아저씨가
  패스(경로/주소)는 http://localhost:3000/docs/search 이용  
   cate 라는 변수에는 카테고리를 보내주시고
  lang 라는 변수에는 국가를 보내주시고
  name 라는 변수에는 단어를 보내주세요.
  그러면 결과를 리턴해 드릴께요.

  http://localhost:3000/docs/search?cate=값&lang=값&name=값

  http://localhost:3000/docs/search
  ?cate=singer&lang=ko&name=%EC%95%84%EC%9D%B4%EC%9C%A0

# js 22장

## this 키워드

1. 객체 는 상태(property, methode)를 가지고 있다.

2. 객체는 독특한 데이터 종류이다.

- 메소드는 자기가 코딩된 객체의 property 를 변경 할 수 있다.
  - 코딩된 객체 : 실행이 되는 순간 인스턴스
- 속성을 변경하려면 메소드는 자기가 속한 객체를 알수가 있어야 한다.
  - 속성을 변경하려면 메소드는 자기가 속한 객체(this)

3. this 는 함수 호출 방식에 따라서 그때 그때 결정이 된다.

3.1 일반 함수 호출

```jsx
function Go() {
  // this => window
}
```

Go(); // window

3.2 메서드 호출 방식

```jsx
const obj = {gogo: function(){
	this?
	}
}
```

obj.gogo(); // obj

3.3 생성자 함수 호출 방식

```jsx
function Go() {
  // this
}
```

const who = new Go(); // who

3.4 간접 적으로 간접해서 호출 (X)

Function.prototype.call()

Function.prototype.apply()

Function.prototype.bind()

4. 주의 하자.(setTimeOut / setInterval)

- setTimeOut : 시간이 지나면 함수 호출
- setInterval : 일정한 시간마다 지나면 함수 호출
  - 몇초 마다 뭐해라

```js
var value = 1;

const obj = {
  value: 100,

  foo() {
    // obj를 가리킨다.
    console.log(this);
    // setTimeout
    // 일반함수 호출 > window
    setTimeout(function () {
      console.log(this.value);
    }, 1000);
    setTimeout(() => {
      console.log(this.value);

      console.log(gogo.value);
    }, 1000);
  },
};

obj.foo();

// 메서드로 호출했다.

// 지금까지의 얘기로는 this 는 obj 를 가르킨다고 알고 있었다.

// 그런데

obj.foo(); // 객체생성자 함수 :obj, setTimeOut : window
```

- 코딩된 위치(렉시컬)를 기준으로 바인딩(연결) 한다.

5. 결론

- 일반함수 호출은 this가 window 를 대상으로 한다.
- 객체를 가리키고 싶다면(참조한다면) 화살표 함수 쓰세요.

- SlideTopMain.js

  : 반복 되는 화면 단위의 요소를 컴포넌트로 뽑아보기.

react 에서
JSX 에 style 사용하고 싶다.

  <div style={{이름:값, 이름:값}} >

style = {객체 리터럴로 넣자}

# 23장 실행 컨텍스트

1. 실행 컨텍스트 알면 좋은점.
   1.1. 외운다기 보다는 여러분이 JS 를 실행하는 플레이어로 생각하면 좋겠습니다.
   예) mp4 영상이 있다면 플레이어 소프트웨어가 어떤 실행 과정을 가질까?

   - js가 어떻게 실행이 되는지 알아보자 컴퓨터가 되지말자.
   - 곰 플레이어가 어떻게 영상을 실행하는지가 실행 컨텍스트이다.

1.2. JS 가 변수(식별자 : 구분자)와 변수(식별자: 구분자) 를 구분하고 어떻게 찾아서
사용하는가에 대한 이해를 돕는다.

1.3. 호이스팅의 과정을 알 수 있다. (var 또는 function a(){} 사용 시 발생)

```js
1번줄 console.log(age); // 에러가 아님
100번줄 var age = 15;
130번줄 function go(){

}
go()
```

1.4. Closer 에 대한 과정을 알 수 있다.
함수가 종료되었는데 어떻게 지역변수(즉, 함수 안에 만든 변수가 살아있지?)
ex) useEffect, useState ... Closer

1.5. 실행컨텍스트를 알면 구조가 어떻게 돌아가는지 이해하기 쉽다.

- Task 큐 (해야할 일 쌓는 것을 큐라한다함.) + 이벤트 핸들러 의 작동 방식의 이해(addEventListner, fetch, axios)

2. JS play 를 할 수 있는 환경에 2개가 있습니다.

- Web Browser
- Node.js

  2.1. 소스코드가 실행시 player 는 준비합니다.
  2.2. 분류(평가 작업) - 스스로 구분해서 장소를 마련
  2.2.1. 전역코드
  2.2.2. 함수코드
  2.2.3. eval : 글자를 자바스크립트로 인정해서 실행한다. 절대로 신경쓰지 마세요.
  2.2.4. 모듈 코드 : export, import 등등 .js 파일내의 작성 되었구나.

  2.3 실행준비(player)

- 1단계로 코드를 보고 평가를 한다.
- 2단계로 실행한다.

3. 렉시컬 환경은 어떻게 쌓여있는 스택들 간에 변수, 함수를 찾아서 쓰는가 ?

- Scope 가 결정되어 지면 체인(찾아가는 연결(바인딩))이 관리한다
- 전역(Global) : window
- 지역(Local) : { //block }
- 상위로 가는것을 체인이라한다.

4. 비동기의 이해 (addEventListner, fetch, axios)

- bt.addEventListener("click", function(){...})
- fetch(url).then(function(){}).catch(function(){})
- fetch 실행 중 비동기[ 위임(promise) ] >
  - 비동기 : 잠깐 다른곳에 모아뒀다가
  - fetch 가 끝났을 때 then을 실행컨텍스트에 올린다.
    10 번줄 fetch(url).then(function(){console.log(res)})
    ....
    20 번줄 say()

일반변수와
리액트 변수의 차이는 화면
리렌더링 에 표현이 되는지 안되는지로 구분하세요.

결론
변수라면 고민하지 마시고 보여지든,
아니든 리액트에게 맡기자.
리액트는 최적화를 스스로 해 준다.

# Axios

## 1. axios 를 연습할때

서버가 없어서 테스트하기 곤란하다.
임시로 서버를 구축 >

- [josn-server](https://www.npmjs.com/package/json-server)
- [참조자료](https://poiemaweb.com/json-server)

## 2. 서버 구축 과정

- D: 드라이브에 server 폴더를 만든다.
- VSCode 에서 프로젝트 등록을 한다.
- Node.js 프로젝트로 등록을 한다. (리액트 상관없음)

## 3. Node.js 프로젝트 생성하기

- `npm init` 엔터

## 4. json-server npm 설치

- `npm install json-server`
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

- `npx json-server db.json`
- `npx json-server db.json --port 5000`
  <!-- 위에 꺼와 아래꺼의 port 번호가 겹침 -->
  <!-- 충돌발생 위험이 있음. -->
- `json-server --watch db.json`
- `json-server --watch db.json --port 5000`
- `http://localhost:3000/profile`

## 6. package.json 에 script 명령어 추가하기.

/package.json

```json
 "scripts": {
    "start": "json-server --watch db.json --port 5000"
  }
```

## 7. API 테스트하기

- CRUD 테스트(크러드)

  - C : Create(POST)
  - R : Read(GET)
  - U : Update(PUT : 그냥 PUT을 쓰자. / Fetch)
    - PUT : 다 업데이트 하는거
    - Fetch : 일부분만 수정한다.
  - D : Delete(DELETE)

- Postman(웹 API 테스트 시 일반적 사용)
- Swagger(웹 API 테스트 시 별도로 BE에서 셋팅)
- Web Browser(웹 프로젝트 CORS 에러 발생 함.)
  - 접근권한에 대한 오류가 나온다.
    - 직접 해당 IP주소의 컴퓨터에 접근 하기 때문에 오류가 나온다.
    - proxy서버 : 컴퓨터를 속이는 것.
      - 그 컴퓨터에서 작업하는 것 처럼 속이는 것.
    - package.json 에 proxy를 셋팅해야 한다.
  - package.json 에 "proxy" : "주소" 를 작성해야 한다.
  - 내컴퓨터에 자기가 쓰는것은 문제가 없다.
  - 하면 db.json에 바로바로 반영된다.
  - 지우면 json에 객체가 날아가고 생성하면 추가되고 그런다.

## 8. Axios 활용

- [axios](https://axios-http.com/kr/docs/intro)
- npm install axios

```js
// 서버 주소
export const SERVER_URL = "http://localhost:5000";
```

## 24장 클로저

1. 실행 컨텍스트

- 코딩을 했다

  - JS 플레이어(Web Browser) 에서는 2단계 진행

    - 1단계

      - 소스 코드 분석 단계 (전역(변수 목록)/함수(함수 목록)/모듈)
      - 변수 목록/함수 목록 을 관리

    - 2단계
      - 코드 실행 단계(렉시컬은 변수 찾기 범위 설정)
      - 변수 / 함수들의 대한 참조를 결정지어 버린다.
      - 참조한 내용들의 정보를 절대로 바꾸지 않는다.

2. 클로저

- `함수에서 함수 return 하는것을 클로저`
  2.1. 함수와 그 함수가 선언된(코딩된) 렉시컬 환경과의 조합.

- JS 는 함수를 호출 즉 Call 이 아니고, 작성을 하는 순간 모든 참조가 결정된다.(렉시컬 환경 셋팅 완료)

```js
const ab = 10;
function a() {
  const ab = 1;
  function abc() {
    // 외부 참조
    console.log(ab); // 1로 나옴.
  }
}
```

- 궁금하면 this 찍어보자.

```js
const ab = 10;
function a() {
  const ab = 1;
  abc();
}
function abc() {
  // 안에 ab가 없기 때문에 전역으로 나가버림.
  console.log(ab); // 1로 나옴.
}
```

2.2. 외부 렉시컬 환경에 대한 참조도 저장해 둔다. 3. 함수 객체
3.1. 함수 도 객체라서 속성이 있다.

- [[Environment]]
- 환경 슬롯을 이미 코딩된다.
- 여기에는 렉시컬 환경 참조, 즉 상위 스코프를 기억한다.
-

4. 클로저의 조건?
   4.1. 함수 안에 함수를 만들고 함수를 리턴한다.

```js
// 1번 조건 함수 안에 함수 만들기
function Outer() {
  function gogo() {}
}
// 2번 조건 함수 안에 함수를 리턴한다.
function Outer() {
  function gogo() {}
  return gogo;
}
```

4.3. React 예

```js
  const Header = function(){
    // this 찍으면 Header로 나올거임
    const handleClick = function (){console.log(this)};

    return (<>
      <div></div>
    </div>);
  }
```

4.4. 외부 함수 보다 중첩 함수가 더 오래 유지되는 경우

- 외부함수 보다 중첩함수가 더 오래 유지되는 경우(중첩함수를 외부 함수에서 return 했을 때)
  중첩 함수는 이미 종료되어 버린 외부 함수의 변수를 참조할 수 있다.
- 변수를 막 가져다 쓰는거 X 해줄 수 있음.

```js
const age = 111;
function Out() {
  const age = 10;
  function In() {
    console.log(age);
    return age;
  }
  return In;
}
const gogo = Out();
gogo(); // gogo에 return 한 In 함수를 담아둠.
age; // 오류남 함수의 생명주기가 끝났기 때문임.
```

5. 클로저 활용

5.1. 함부로 접근해서 변수의 상태를 바꾸지 못하게 할 수 없을까?

```js
let num = 0;
const add = function () {
  return ++num;
};

console.log(add());
console.log(add());
console.log(add());
```

```js
const take = function () {
  let money = 100;
  return money--;
};
// 함수 안에 있어서 -는 되는데
// 이게 100으로 고정되있음.
// 함수의 지역변수로 만들기 (은닉)
console.log(take());
console.log(money); // 오류 전역에 없음
```

5.2. 외부에서 함수에 만든 지역 변수를 접근할 수 없을까?

```js
const take = function () {
  let money = 100;
  const changeMoney = () => {
    return --money;
  };
  return changeMoney;
};

const takeMoney = take();
takeMoney();
takeMoney();
takeMoney();
takeMoney();
takeMoney();
```

```js
const numberChange = function () {
  let num = 0;
  const add = () => {
    return ++num;
  };
  return add;
};

const a = numberChange();
a();
```

6. 클로저란?
   6.1. 함수에서 내부 함수를 리턴한다.
   6.2. 내부 함수는 외부의 변수를 사용한다.
   6.3. 이렇게 하면 데이터를 외부에서 접근할 수 없으므로 데이터를 은닉할 수 있다.
   6.4 데이터에 접근하는 내부 함수를 통해서만 접근할 수 있으므로 안전하다.

- 우리가 허락 된 기능만 사용 할 수 있게 제한한다.

```js
// undefined 나옴
function 회원정보() {
  let 사용자레벨 = 1; // 회원

  return function () {
    사용자레벨++;
  };
}

const 회원업데이트 = 회원정보();
회원업데이트();
회원업데이트();
회원업데이트();
회원업데이트();
회원업데이트();
```

7. 고차함수

7.1. 면접볼때 자주 나오는 내용
7.2. 함수에 함수를 매개변수로 전달한다.

배열.map(함수); // 고차함수
배열.map(function(item, index, arr){}); // 고차함수

8. 클로저

8.1.목적은 데이터를 안전하게 보관한다. 즉, 외부에서 함부로 접근못하게 한다.
8.2. 데이터를 변경해야 할 경우 내부 함수로 변경한다.