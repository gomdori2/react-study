# CSS 최적화 - > 일단 나중에

# js Syntax 1장

### **인터프리터**(interpreter, [문화어]: 해석기/ 번역기)[WIKI백과]

- 프로그래밍 언어의 소스 코드를 바로 실행하는 컴퓨터 프로그램 또는 환경을 말한다.
- 그때 그때 기계어로 번역해주는거.
- 번역기 ex) 갤럭시 AI/웹브라우저
  - 웹브라우저가 번역해서 실행

### 컴파일러는 되있는것을 번역

의미는 코드의 실질적인 기능/작업

### 프로그래밍

- 0과 1밖에 알지 못하는 기계가 실행할 수 있는 정도로 정확하고 상세하게 요구사항을 설명하는 작업이며 그 결과물이 바로 코드이다.
- 요구사항을 분석하고, (개인별로 작성 : 의사코드)
  Syntax 를 이용해서
  적절한 자료구조 + 적절한 함수를 활용하고,
  흐름을 제어하여 요구사항을 만족 시킨다.

### 자연어

- 사람이 쓰는 언어

### 기계어

- 컴퓨터가 쓰는 언어

### Syntax(구문)

- 약속된 문법

### **Semantics(의미)**

# js Syntax 코드 위치

1. inline 방식

```html
    <div onclick="alert("안녕");"></div>
```

2. 태그 방식

```html
<head>
  <script>
    alert("반가워");
  </script>
</head>
```

3. 외부파일 방식

- 태그 방식으로 잡았을 경우 내부에 있는 script를 덮어쓴다.

```html
<script src="./js/script.js">
    // 실행안됨.
  alert("반가워");
</script>
```

# Swiper Slide 적용해 보기

- Slide 를 직접 코딩하지 마세요.
- 사용법을 배운다.

- Swiper, Slick, BxSlider 가 있다.

## 1. Swiper 슬라이드 적용 시 주의 사항

- html 로드 완료 및 이미지 로드 완료 후 실행 권장

```js
window.addEventListener("load", function () {
  // 실제 슬라이드 코드 배치하자.
});
```

## swiper

1. ??
2. 호환되는게 많음(react, vue...)
3. 반응형 지원된다.

# Swiper Slide 적용해 보기2

- 데모사이트의 core 메뉴를 통해서 참조한다.
- 기본 css 와 js 파일은 CDN 으로 참조한다.

```html
<!-- Swiper -->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css"
/>
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
```

- 기본형 코드를 작성해서 원하는 영역에 배치한다.

- 슬라이드 개수 만큼 swiper-slide div 를 만든다.

```html
<div class="swiper 이름">
  <div class="swiper-wrapper">
    <div class="swiper-slid"></div>
    <div class="swiper-slid"></div>
    <div class="swiper-slid"></div>
    <div class="swiper-slid"></div>
  </div>
</div>
```

- css 로 `원하는 이름` 을 찾아서 width, height 를 100% 주자.
- css 로 `원하는 이름` 에 절대로 display 등을 넣으면 안되요.
  - **너비 높이 외에는 주면 안됨.**

# 3. Swiper Slide 적용해 보기

- 외부 데이터 연동(json)

- 데이터 구조를 설계

- 목업데이터/더미데이터 : 테스트용 가짜데이터

- json이란 javaScript Object Notation 입니다.

```json
[
  { "키": 값, "키": 값, "키": 값, },
  { "id": 2, "pic": "b2.png", "url": "#" },
  { "id": 3, "pic": "b3.png", "url": "#" },
  { "id": 4, "pic": "b4.png", "url": "#" }
]

```

# 4. Swiper Slide 적용해 보기

- 비동기 호출하기((vanila/pure) js -> 추후 j-Query)
  : BE 와 협업 시 활용합니다.
- fetch 를 활용 가능
- async await 활용 가능
- 인터넷에서 주고 받고 하는 것은 문자열(string)입니다.
  - 작은 문자열 단위 토큰(token)이라 한다.

총 개수를 아는 경우라면 ?
배열은 배열명.length 를 통해 총 요소(element)수를 알 수 있다.

총 개수를 모르는 경우라면 ?

# 5. Swiper Slide 적용해 보기

- 외부 js 파일을 이용한다

```html
<head>
  <script src="./js/topslide.js"></script>
</head>
```

```js
window.addEventListener("load", function () {
}
```

- swiper 에 보여줄 데이터를 외부 .json 파일로 연동한다.
  : 자료(데이터)를 만들어주는 동료가 BackEnd 입니다
  : BE 와 협의가 필요하다. (협업의 기본)
  : 초기에는 가짜데이터(Dummy, Mockup) 을 가지고 작업

`json 파일 내용 형식`

```json
[
  { "키명": "키값" },
  { "키명": "문자열값" },
  { "키명": 55 },
  { "키명": true },
  { "키명": [] },
  { "키명": {} }
]
```

```json
[
  {
    "id": 1,
    "pic": "b1.png",
    "url": "#",
    "title": "AI 헬스케어의 <br/> 마일스톤을 찍다"
  },
  {
    "id": 2,
    "pic": "b2.png",
    "url": "#",
    "title": "카카오브레인의 <br/> 연구문화"
  },
  {
    "id": 3,
    "pic": "b3.png",
    "url": "#",
    "title": "PathFinder 2기의 <br/> 언어모델 활용기"
  },
  {
    "id": 4,
    "pic": "b4.png",
    "url": "#",
    "title": "칼로리의 꿈 <br/> 시리즈 ③"
  }
]
```

- json 데이터를 이용해서 자료를 추출한다.
  : 외부 주소를 통해서 자료를 불러들이기 위해 fetch 를 알고 적용한다.
  : 더불어서 크롬 개발자 도구 (F12) 의 NetWork 탭을 알아야 한다.
  : 옵션으로 fetch/XHR을 선택할 수 있어야 한다.
  : request 와 response 를 구별하여 파악할 수 있어야 한다.

### fetch 기본구조

```js
fetch(주소).then().then().catch();
```

1.

```js
fetch(주소).then(결과 =>{
  접속결과;
}).then((result) => {
  받아온 값
}).catch();
```

2.

```js
fetch(주소)
  .then((결과) => {
    // 위에 매개변수
    const 접속결과 = 결과.json();
    return 접속결과;
  })
  .then((최종자료) => {
    // 하고 싶은 일 마음대로...
  })
  .catch();
```

3.

```js
fetch(주소)
  .then((결과) => {
    // 위에 매개변수
    const 접속결과 = 결과.json();
    return 접속결과;
  })
  .then((최종자료) => {
    // 하고 싶은 일 마음대로...
    // 우리가 할 일을 진행한다.
  })
  .catch((오류) => {
    오류처리;
  });
```

- 추출된 데이터로 html 을 생성한다.
  : 백틱(``)을 적극적으로 사용한다.
- swiper 를 작동시킨다.

```js
window.addEventListener("load", function () {
  // 1. 외부에서 자료를 불러온다.
  const dataUrl = "./apis/topslide.json";

  fetch(dataUrl)
    .then((response) => {
      // Step 1. 자료 받아서 json 변경하기

      // 이 문장은 변경 X

      // json은 내려온 데이터를 문자열(토큰) 배열로 바꿈.
      // 자바스크립트의 문법(syntax)로 바꿔서 해준다.
      const data = response.json();
      //   console.log(response);
      // 변환된 결과를 돌려주기
      return data;
    })
    .then((result) => {
      // Step 2. json 변경된 데이터 활용하기.
      // 전체 글자 모음
      let slideTags = "";

      for (let i = 0; i < result.length; i++) {
        const data = result[i];
        console.log(data);

        // 템플릿 문법(``) 필요
        const aaa = `<div class="swiper-slide">
                            <a href="${data.url}" style="background : url('./images/${data.pic}') no-repeat center; background-size : cover;">
                                <p class="slide-title">
                                    ${data.title}
                                </p>
                            </a>
                        </div>`;
        slideTags += aaa;
      }
      // 원하는 장소에 출력해 보자.
      // 2. 자료를 이용해서 슬라이드에 배치할 html 을 만든다.
      const whereTag = document.querySelector(".topslide .swiper-wrapper");
      whereTag.innerHTML = slideTags;

      // 3. html 완성 후 swiper 를 생성한다.
      // 기본코드를 넣어보자

      var topSlide = new Swiper(".topslide", {});
    })
    .catch((error) => {
      console.log(error);
    });
});
```

# 6. Swiper Slide 적용해 보기

- 옵션(https://swiperjs.com/demos#autoplay)
  : loop
  : autoplay
  : effect
  : speed
  : pagenation(https://swiperjs.com/demos#pagination)
  : 페이지네이션 디자인 참조.

# js 4장

- var 변수명 = 변수값;
- let 변수명 = 변수값;
- const 변수명 = 변수값;

```txt
 호이스팅(hoisting) 은 변수, 함수를 선언하지 않았는데도 사용할 수 있음. (hoisting 이 일어나지 않도록 주의 : var 쓰지 말자)
```

# css 의 opacity 와 position 의 이해.

- opacity 는 DOM의 내용까지도 투명도가 적용된다.

```css
대상 {
  position: relative;
}
대상 {
  position: absolute;
}
대상 {
  position: fixed;
}
```

```html
<div class="box-wrap">
  <div class="box"></div>
</div>
```

```css
.box-wrap {
  position: relative;
  margin: 0 auto;
  width: 600px;
  height: 300px;
  background: orange;
}
.box {
  position: absolute;
  right: 80px;
  bottom: 20px;

  width: 200px;
  height: 200px;
  background: red;
}
```

position
: position 중에 absolute 로 픽셀 위치 설정의 경우 주의
: 반드시 position 코드가 바깥 영역에도 있어야 합니다.
: position 중에 fixed 는 웹브라우저를 기준으로 배치
: fixed 는 반드시 left, top, right, bottom 을 주자
: fixed 는 보통 z-index 를 준다.
: fixed 는 높이에 반영이 안되므로 주의하자.(레이아웃 배치 문제)

# js 윈도우 스크롤의 위치를 알아내기

```js
window.addEventListener("load", () => {
  // 브라우저의 스크롤바의 위치를 파악해야함
  // 현재 스크롤바의 위치값 알아내기
  let scY = this.window.scrollY;
  // scY 즉, 스크롤바의 위치가 0 보다 크면 스크롤 된거다.
  // header 에 라인의 css 를 적용한다.
  const header = document.querySelector(".header");
  if (scY > 0) {
    // header 객체, 즉, DOM 에 css 목록에 추가 하자 (class명)
    header.classList.add("line-active");
  } else {
    // header 객체, 즉, DOM 에 css 목록에 제거 하자 (class명)
    header.classList.remove("line-active");
    // header.classList.toggle("line-active");
    // header.classList.contains("line-active");
  }

  window.addEventListener("scroll", () => {
    // 스크롤 했을 경우에 스크롤바의 위치값 알아내기
    scY = window.scrollY;
    if (scY > 0) {
      header.classList.add("line-active");
    } else {
      header.classList.remove("line-active");
    }
  });
});
```

# js 로 css의 클래스 동적으로 활용하기

```js
// dom 찾아서 변수로 레퍼런스 하기

if (scY > 0) {
  // header 객체, 즉, DOM 에 css 목록에 추가 하자 (class명)
  header.classList.add("line-active");
} else {
  // header 객체, 즉, DOM 에 css 목록에 제거 하자 (class명)
  header.classList.remove("line-active");
  // header.classList.toggle("line-active");
  // header.classList.contains("line-active");
}
// dom 을 이용해서 선택한 곳에 적용된 css 클래스 목록

const tags = document.querySelector(".클래스명");
// header 객체, 즉, DOM 에 css 목록에 제거 하자 (class명)
// 추가
tags.classList.add("line-active");
// 삭제
tags.classList.remove("line-active");
// 있으면 x 없으면 넣기
tags.classList.toggle("line-active");
// 포함여부
tags.classList.contains("line-active");
```

# js의 함수란? 1번

- function은 웬만하면 동사로 짓자

```js
// 함수만들기(함수 선언)
function 적절한동사(매개변수){
  하고싶은일 작성
}

// 함수사용하기(함수호출)
적절한동사();
// 예(함수 체이닝)
// 연결고리
fetch().then().then().catch();
```

- 함수는 무조건 1개의 값을 리턴하도록 규정되어 있습니다.
  - 리턴이라는 것은 함수 실행() 후 값을 돌려주는 것을 말합니다.

```js
function 함수명() {
  // 아무것도 작성안하면 return undefined;
  // return undefined;
}
함수명();
```

- 동일한 코드가 2번 이상 반복되면 함수를 만들려고 노력하자.
- 반복은 되지 않더라도 하나의 기능이 너무 복잡하면 함수를 만들려고 노력하자.
- 복잡하지는 않는데 코드가 너무 길어지면 함수로 묶어주려고 노력하자.
- 실행의 결과가 그때, 그때 다른 경우에도 함수를 만들자.
- 함수 정의 문

```js
function 함수이름() {
  // 할일
}
```

- 함수 실행/호출(call) 문

```js
함수이름();
```

# 리스트 영역에 json 활용해 보기.

# js 5장

# js 1번 리팩토링 ? 2번

```js
window.addEventListener("load", () => {
  // 브라우저의 스크롤바의 위치를 파악해야함
  // 현재 스크롤바의 위치값 알아내기
  let scY = 0;

  // function은 웬만하면 동사로 짓자
  // scY 즉, 스크롤바의 위치가 0 보다 크면 스크롤 된거다.
  const header = document.querySelector(".header");

  // 변경되는 css 클래스명
  const headerActiveClass = "line-active";

  // 클래스가 적용되는 최소 높이값
  const headerActiveValue = 0;

  // 매개변수로 받기에는 문제가 하나있다.
  const showLine = () => {
    // header 에 라인의 css 를 적용한다.

    scY = this.window.scrollY;

    if (scY > headerActiveValue) {
      // header 객체, 즉, DOM 에 css 목록에 추가 하자 (class명)
      header.classList.add(headerActiveClass);
    } else {
      // header 객체, 즉, DOM 에 css 목록에 제거 하자 (class명)
      header.classList.remove(headerActiveClass);
      // header.classList.toggle("line-active");
      // header.classList.contains("line-active");
    }
  };
  showLine();
  document.addEventListener("scroll", () => {
    showLine();
  });
});
```

# js 의 함수의 매개변수란 ? 3번

- 초기 기능 즉, 함수를 정의하기 전에 기능 상 자주 변하는 데이터를 고민한다.
- 기능은 스크롤 시 특정 위치 보다 커지면 css 추가하기
- 이전 코드는 좋지 않은 코드라고 생각이 든다.
- 함수는 스스로 지역 즉, Local 영역(scope) 에서 처리되는 것이 좋다고 봐요.
- 처리라는 말은 변수를 찾는다 던가
- 처리라는 잘못된 값이 전달되어서 오류가 나는 것을 방지하는 것을 말합니다.

```js
// 홍길동에게 줄 함수
const a = 5;
const b = 6;
function 나누기(_num1, _num2) {
  if (_num2 === 0) {
    alert("나눗셈에서 0은 안됩니다.");
  }
  return _num1 / _num2;
}

나누기(a, b);
```

1. 완성을 목표로
2. 고민 (함수)
3. 고민 (함수 매개변수)

- utils 폴더에다가 정리

# js 6장

데이터 타입(Data Type) : 자료의 종류(자료형)
타입 이라는 말이 자료의 형태
타입스크립트

- 자료의 형을 설명하는 문법

1. 데이터 타입 : js의 리터럴로 처리될 수 있는 자료의 종류
2. js 에서는 값 리터럴에 따라 변수의 종류를 `타입추론` 한다.(암묵적 타입변경)
3. ex) let a = 1; > js 는 1이 숫자 리터럴이라고 타입을 `추론` 한다
   a = "안녕" 이라 하면 문자로 변경한다.
   뭘 집어넣어도 애(js)가 알아서 타입을 지정해서 오류나 원했던 결과가 아닐수도 있다.
   이러한 문제점을 해결하기 위해 나온게 `타입스크립트`
   let a:number = 1;
   a = "안녕";

// 코딩 할 때 스스로 고민해 보자.

1. 꼭 필요한 경우인지를 파악하고 변수를 만들자.
2. 변수 유효범위는 좁게(block을 가능하면 쓰자)
3. 전역 변수는 가능하면 만들지 말자.
   ex) let a = 1; 전역변수 (bad)
   {a = 2} 지역변수 (good)
4. 변수보단 상수를 사용하자.
   let > const
5. 변수 이름을 명확하게 만들자.

# 함수의 이해 7번

1. 함수를 만들어야겠다고 판단하는 케이스

- 동일한 코드가 2번 이상 반복되면 함수를 만들려고 노력하자.
- 반복은 되지 않더라도 하나의 기능이 너무 복잡하면 함수를 만들려고 노력하자.
- 복잡하지는 않는데 코드가 너무 길어지면 함수로 묶어주려고 노력하자.
- 실행의 결과가 그때, 그때 다른 경우에도 함수를 만들자.

2. 왜 화살표 함수를 만들지?

- 기본구조 > const 명칭 = (매개변수) => {//할일}

- 트렌드를 쫓아가자. (있어보이잖아요.)
- 코드가 해석하기 더 어려워집니다.

```js
// 화살표 함수 연습
steb 0.
function say() {
  console.log("안녕", this);
}
steb 1.
say() => {
  console.log("안녕", this);
}
steb 2.
const say = () => {
  console.log("안녕", this);
}
const say = () => {}
```

: 매개 변수가 있는 경우

: steb 1.

```js
function say(_who) {
  console.log("안녕", _who, this);
}
```

: steb 2.

```js
const say = (_who) => {
  console.log("안녕", _who, this);
};
```

- this 를 정확히 지정하기 위해서 활용한다.
  : 화살표 함수를 사용하면 일반적으로 큰 고민없이 사용하면 된다.
  : 하지만, 함수 안에 this를 작성하시면 상황이 달라집니다.
  : 일반 함수는 코딩된 자리, 적은부분에 상위개념을 찾아온다.
  : 화살표 함수에서 this 는 window를 가리킵니다.
  : 결론은 `화살표 함수에서 this 를 사용한다면` console.log(this) `*확인필수!`
  : 화살표함수에서 this 조심하자.
  : 컨텍스트 > 코딩된 자리
  : window를 카리켜야한다면 arrow쓸 것
  : 화살표 함수는 예전 `일반 함수에서 window 를 참조하지 못하는 문제`를 해결함.

```js
const btWrap = document.querySelector(".bt-wrap");
btWrap.addEventListener("click", function () {
  console.log(this);
});
btWrap.addEventListener("click", () => {
  console.log(this);
});
```

# 배열의 이해

- 객체 > 일반객체
- 배열객체
- [요소,요소,요소,요소 ]
  : 요소로 담을 수 있는 자료형은 7가지 입니다.
- 배열의 속성(배열을 위한 특별한 변수)은 1개가 있습니다.
  : length 가 있어요. (요소의 개수)
- 배열의 메소드(배열을 위한 특별한 함수)는 너무 많아요.
- 상당히 많은 메소드(배열을 위한 함수) 가 있습니다.
- 배열.forEach((요소)=>{}), 배열.map((요소)=>{}), 배열.filter((요소)=>{}), 배열.find((요소)=>{})
- 배열의 요소를 하나씩 접근해서 활용하기
- 카멜케이스 사용해라(배열.forEach)

```js
result.forEach((item) => {
        const tag = `<a href="${item.link}" class="list-box">
        <div class="list-box-img br-20" style="background: url('./images/${item.imgpath}') no-repeat center; background-size: cover;"></div>
        <div class="list-box-cate">
          <img src="./images/icon/${item.icon}" alt="${item.category}">
          <span style="color:${item.txtcolor};">${item.category}</span>
        </div>
        <p class="list-box-title">${item.title}</p>
        <span class="lsit-box-day">${item.day}</span>
      </a>`;
```

- 키값 이 일반 변수 인 경우와 (프로퍼티)

  - 일반 변수
    - 변수 (var, let, const)

- 키값 이 함수 인 경우를 구분하고 표현한다.(메소드)

  - function a(){} - 일반함수

- 객체에 정의한 변수를 커뮤니케이션 하기 곤란하니까 이걸 속성(프로퍼티)이라고 호칭합니다.

- 객체에 정의한 함수를 커뮤니케이션 하기 곤란하니까 이걸 메소드라고 호칭합니다.
- 프로퍼티(객체 내부 키값), 속성
  const a = {
  a : 1, 프로퍼티(객체.속성)
  b : function(){} 메소드(객체.기능)
  }
  일반 객체 변수(리터럴 객체)
  const 객체 = {
  property : value,
  method : function(){}
  }

## js 7장

operator (연산자)

이 항 : 2개의 항목 을 처리하는 연산자 값만들기

- a + b = c
  삼 항 : 3개의 항목 을 처리하는 연산자 값만들기
- (조건식) ? 참 실행 : 거짓 실행
  단 항 : 1개의 항목 을 처리하는 연산자 값만들기

- - - / % (모듈러 연산자)

5 % 3 = 2 (나누고 난 후 나머지 값, 게시판 목록..)

    단  항   :   1개의 항목 을 처리하는 연산자 값만들기

    let a = 1;
    a = a + 1;
    a++;    // 원 값에 1을 더하라
    ++a;    // 원 값에 1을 더하라
    --a;    // 원 값에 1을 빼라
    a--;    // 원 값에 1을 빼라
    for(let i = 0; i < 10; i++) {
    }
    장바구니 개수 추가
    let bucket = 0;
    bucket++;

    알고리즘 공부
    let a = 1;
    let b = a++;   // b?  1   a = 2
    let b = ++a;   // b? 2

1 + 2 = 3
'1' + 2 = "12"
글자도 더할 수 있다.

const filePath = "./images/"
const fileName = ".jpg";
for(let i = 0; i < 10; i++) {
const img = filePath + i + fileName;
const img = "./images/" + 0 + ".jpg";
const img = "./images/" + 1 + ".jpg";
const img = "./images/" + 2 + ".jpg";
}

    처음 코딩 배우면 어려워 하는 것

    문법
        []  ....
        for  문....
        할당 문...
        let num = 0;
        num = num + 1;
        num ++;
        num += 1;

==================== 적절한 구조를 어떻게? ====
변수, 함수, 객체 구조?

1 == '1' 같다 (true)
암묵적으로 타입 변환 시켜서 진행 : 나중에 오류의 원인
절대로 사용하지 마세요.

1 === '1' 다르다. 1. 먼저 데이터 종류 (data type) 비교합니다. 2. 데이터 값 (data value) 비교합니다.

     !==



     (조건) ? 참실행 : 거짓실행

     (level > 10) ?  <div>주인님</div>    :   <div>일반회원</div>

     if(isLogin) {

        <div>"반가워"</div>

     }else{

        <div>회원가입</div>
     }

     const 객체 = {
         프로퍼티명 : 프로퍼티값
     }
     객체 in 프로퍼티명
     delete 객체.프로퍼티명;

     const sw = new Swiper(".slide", {} )

     const a = (1 + 10) * 100

함수의 리턴(return 값 default : undefined)의 이해

1. 함수 정의

function 함수이름(매개변수) {
// 직접 return 값; 미작성

}; 2. 함수 호출
const gogo = 이름(100); // gogo 에는 undefined;

3. 리턴이 여러개인 경우
   : return 의 의미는 함수 결과값 돌려주기
   : return 은 함수 종료하기
   function 함수이름(매개변수){
   return 1;
   return 2; // 영원히 실행 안됨.
   }

원래 swiper 의 영역은
overflow : hidden이 되어 있습니다.

- 영역 외는 잘라라

if (화면의 너비가 1024 보다 작으면)
{
swiper 생성

} else {
그렇지 않으면
swiper 해제(깨버리기)
}

현장에서 고객 및 기획자는 다양한 아이디어를 냅니다.
그래서, 슬라이드도 반응형에 맞게 배치가 됩니다.
기본은 css 로 레이아웃 처리
1024 보다 작으면 swiper 생성 및 작동
1024 보다 크면 swiper 제거한다.

window.addEventListner("resize",function(){

})

1. pc 와 mobile 에 가장 보기 좋도록 배치

## js 8장

```txt
제어문은 조건에 따라 코드 진행 방향이 결정된다.

고차함수 란?
함수의 매개변수로 함수를 전달한다.
글자, 숫자, boolean, null, undefined, symbol
객체 : [], function, {} ...
확률이 높은 조건을 먼저 조건으로 쳐라
버스를 기다린다.

300번은 5분마다 온다.

700번은 10분마다
if(조건){

} else if (조건){

} else {

}

- forEach 메서드 : 배열을 순회할 때 사용
- for in 문 : 객체의 프로퍼티를 열거할 때
- for of 문 : 이터러블을 순회 가능
```

# js 9장

명시적 타입 변환

- 개발자가 타입을 강제로 변환하는 것
- 타입캐스팅
  암묵적 타입 변환 (코드에러가 아니고 원하는 결과가 아닌 경우가 발생)
- 개발자가 아닌 자바스크립트가 타입을 몰래 변환
- 타입 강제 변환
- 결과를 예측할 수 있어야 합니다.(대비책)
- \+ 연산자는
  - '글자' + '글자' = '글자'
  - 숫자 + 숫자 = 숫자
  - '글자' + 숫자 = '글자' 원칙(일단 글자로 바꿈)
  - js는 html에 작성한 내용은 일단 글자로 받아드림
    - ex) 회원가입 : 전화번호 이런것들
- \- 연산자는

  - '글자' - '글자' = NaN
  - 숫자 - 숫자 = 숫자
  - '글자' - 숫자 = 숫자 원칙(일단 숫자로 바꿈)
  - console.log(typeof 결과)

- Boolean true / false
- Falsy(결과값이 false로 나오는 애들) 한 것들을 반드시 알아야해요
  - if(!false)
  - if(!undefined)
  - if(!null)
  - if(!0)
  - if(!NaN)
  - if(!'')

문자열 데이터 지정 만들기
변수 + '' 글자로 만들어짐

숫자 데이터 지정 만들기
parseInt(변수) : 정수 만들기
parseFloat(변수) : 실수(소수) 만들기

단축 평가
: 리액트에서 엄청 사용한다.
: 반드시 정말 알아야 합니다.

- 논리곱(&&)

  - true && true 결과는 true 입니다. > 이거 아니다
  - "비욘세" && "디카프리오" 결과는 죄송하지만 true 가 아닙니다.
    결과는 죄송하지만 "디카프리오" 이다.
  - const isLogin = false;
  - isLogin && "<div>안녕</div>"
    - return (X)
    - isLogin 이 true 일 때 return "<div>안녕</div>"
  - 참 && 참2 > 일 경우 뒤에 참2를 리턴한다.

- 논리합(||)
  - true || true 결과는 ture 입니다.
    - '10억' || '1원' // 10억
    - '' || '1원' // 1원
    - true1 || true2 true 일 경우 결과값이 앞에게 나옴.

옵셔널체이닝 나오게 된 이유 (?.)

```js
var elem = null;
var result = elem.gogo; // 문법 에러
//------------ 위는 Syntax에러로 전체 js가 멈춤 ------------//
//------------ 아래는 괜찮음. ------------//
var elem = null;
var result = elem && elem.gogo; // 문법적으로 에러 안남.
//------------ 업그레이드 ?버전 ------------//
var elem = null;
var result = elem?.gogo; // 문법적으로 에러 안남.
```

: Syntax 에러로 js가 멈추지 않기를 바란다.

- 병합연산자(??)
  - const result = null ?? "없군요" 결과값은 "없군요"

# js 10 장 객체 리터럴

- 너무 중요해요.
  : 활용빈도 말도 안되게 높고,
  : 본인 및 타소스를 이해하려면 알아야 해요.
  : 핵심은 JS 의 모든 자료타입은 객체입니다.

  - 타입(js가 리터럴로 인정하는 자료의 종류)

  : 원시 타입
  ( string, number, null, undefined, bool, symbol )

  : 객체타입
  ( [ 원시타입들... ] , { 속성명:원시타입 }, function .... )

  - 객체 구성 ( 객체가 가진 데이터를 객체 내에서 제어하겠다.)

  : 객체에 포함된 변수를 `프로퍼티/속성` 이라고 호칭
  : 객체에 포함된 함수를 `메소드/기능` 이라고 호칭
  const obj = {

        "프로퍼티명" : 원시값 또는 다른 객체,
        "프로퍼티명" : string,
        "프로퍼티명" : [],
        "프로퍼티명" : {},
        "메소드명" : function () {},
      }

  - 객체 만드는 법
    인스턴스 란 ?
    : 남에게 말해주기가 어려운 개념
    : `객체를 생성하는 방법을 활용` 해 생성한 변수를 인스턴스라고 한다.

  1.  객체 리터럴 문법 : 활용빈도 높다. const 인스턴스 = {}

  const 인스턴스 = {
  "myName" : 5,
  myJob : 5,
  "my-age" : 5,
  say : function () { this["my-age"] },
  sayHi : () => { this["my-age"] },
  }
  인스턴스.myName
  인스턴스["myJob"]
  인스턴스.say()
  인스턴스["say"]()
  인스턴스.gogo = "안녕"

      : 객체 리터럴 문법 보완 및 축약 (ES6)

        // 기본형
        const 인스턴스변수 = {
          프로퍼티명: 프로퍼티값 ,
          프로퍼티명: 프로퍼티값 ,
          메소드명 : function() { },
          메소드명 : function() { }
        };

        const age = 10;
        const nickName = "홍길동";

        // 외부 변수 전달 받는데    이름이 똑~~ 같다?
        const person = {
           age      : age,
           nickName : nickName
        };

        //  축약형
        const person = {age, nickName};

        // 메소드 기본형
        const person = {
           say      : function() { }
        };

        // 메소드 축약형
        const person = {
           say() { }
        };

  2.  Object 함수 문법

  3.  생성자 함수 문법 : 활용빈도 높다.

  4.  Object.create 함수 문법

  5.  class 함수 문법 : 활용빈도 높다.

1. 팀장 및 팀원은 먼저 레이아웃 을 토의하고, 작업 및 담당자 영역을 나누고
   css파일, js 파일을 각자 작업 후 git에 push 합니다.

# 카카오 브레인 블로그 사이트

- 반드시 저작권을 밝혀야 한다.
- 어떤 화면이든 첫 화면만 연습 하면 됩니다. (첫 화면이 가장 어렵다)
aaa