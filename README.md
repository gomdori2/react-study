# CSS 기초

- html 은 화면에 보여줄 데이터(글자) 입니다.
- css 는 화면에 보여줄 데이터를 보기 좋게 꾸며주는 역할을 합니다.

## 1. css 작성법 (4가지)

### 1.1. 인라인 방식(html에 직접 적용)

- tag 내부에 직접 적용
- <태그 style="이름 : 값">

- 가독성이 떨어진다.
- class로 관리 x 할 시 재사용 불가능
- 리액트에선 의외로 많이 쓴다.

- 퍼블리셔 기준으로는 중요 x

```html
<body style="background:green"></body>

리액트에선 > 삼항연산자를 사용한다.
<body style={ 결과 ? {"background:green"} : {"background:red"} }></body>

```

### 1.2. `<style>` 태그 활용 하기

- 가독성은 좋다.
- css 코드 재활용은 힘들다.
- 선택자 { css 적용 }
  \_ css Selector { css 적용 }

```html
<style>
  body {
    background: hotpink;
  }
</style>
리액트 const bodyCss ={ background : "hotpink" }

<body style="{bodyCss}"></body>
```

### 1.3. 외부 파일로 css 분리하기

- 가독성 좋아요.
- 재활용 좋아요.
- 일반적으로 활용해요.(무조건 추천)
- ex) css/common.css(확장자는 무조건 파일명.css)

```html
<link rel="stylesheet" href="./css/common.css" />

body{ background : "green" }
```

### 1.4. css에 css 파일 불러들여서 관리하기

- 대표적으로 글꼴을 @import 해서 사용

- import는 글꼴 불러올 때 쓴다.(다른것도 있다고 하심.)

```html
리액트에선 이렇게 함. import "./css/common.css" @import
url("https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100..900&display=swap");
body{ background: green; }
```

- 참고사항
  : 프로그래밍 언어는 문장의 끝을 표현한다. `;` 으로

## 2. css 초기화 하기

### 2.1. 선택을 하자. (코딩 컨벤션)

- Normalize.css (https://necolas.github.io/normalize.css/8.0.1/normalize.css)
  _ 자유도가 떨어진다.
  _ 추가할게 적어진다.
- reset css (https://meyerweb.com/eric/tools/css/reset/reset.css)
  _ 자유도가 보장된다.
  _ 대신 조금 추가해야한다.

- 우리가 만든 common.css 도 링크하자.
  : 꼭 기억하자. `box-sizing: border-box;`
  : 필요 시 `outline-style: none;`
- 정말 중요한 것은 css 코드 배치 순서
- 웹브라우저에선(개발자 도구 확인) > 아래에서 위로 읽어 들인다.
- 정말 중요한 것은 css 코드 배치 순서(stylesheet 링크 순서도 중요{무조건 적용해야 된다면 밑으로 내려야함})
  : html 태그 > .class > #id의 순서로 적용됨
  : 만약 같은 종류라면 작성 순서 기준
  : 가장 우선시 한다면 `!important`

```css
<link rel="stylesheet" href="./css/reset.css" />
<link rel="stylesheet" href="./css/common.css" />
```

- 공기관 사이트는 tap키 건드리지마라
- border box까지 합해서 width / height 잡아줌

## 3. css 로 전체 레이아웃에 적용해 보기

### 3.1. 멘토 및 실무자는 반드시 반응형을 봅니다.

- 큰화면에서 점차 작은 화면의 레이아웃을 작업한다.

- 화면(디바이스) 너비 관례상 기준
  : 기본 화면(1280px 이상)을 먼저 작업한다.

  ```css 반응형 기본형은 아래것만 들어가면됨.
  .wrap {
    width: 95%;
    max-width: 1280px;
   - 중앙정렬
    margin: 0 auto;
  }
  ```

  - 역피라미드 형식으로 작업해야한다.

  : 랜탑 화면 (1024px) 화면의 레이아웃을 작업한다

  ```css
  @media screen and (max-width: 1024px) {
  }
  ```

  : 타블렛 화면 (960px) 화면의 레이아웃을 작업한다

  ```css
  @media screen and (max-width: 960px) {
  }
  ```

  : 고해상도 모바일 화면 (764px) 화면의 레이아웃을 작업한다

  ```css
  @media screen and (max-width: 764px) {
  }
  ```

  : 중해상도 모바일 화면(480px)

  ```css
  @media screen and (max-width: 480px) {
  }
  ```

  : 저해상도 모바일 화면(320px)

  ```css
  @media screen and (max-width: 320px) {
  }
  ```

완성된 예
: 랜탑 화면 (1024px) 화면의 레이아웃을 작업한다

```css
.wrap {
  width: 95%;
  max-width: 1280px;
  margin: 0 auto;
}
@media screen and (max-width: 1024px) {
}
@media screen and (max-width: 960px) {
}
@media screen and (max-width: 764px) {
}
@media screen and (max-width: 480px) {
}
@media screen and (max-width: 320px) {
}
```
