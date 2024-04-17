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
