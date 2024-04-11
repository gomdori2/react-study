# css header 영역

## 1. html 태그 작업

### 1.1. anchor 태그

- `<a href="보여줄 페이지 주소">글자</a>`
- `<a href="보여줄 페이지 주소>그림</a>`
- `<a href="http://www.naver.com" target="_blank">네이버</a>`
  : 새 탭으로 보여주기(`target="_blank`)

### 1.2. img 태그

- src(source)

: 파일명.jpg, 파일명.png(뒷 배경이 불투명한), 파일명.gif, 파일명.svg
: 팁 1. \*\*\* 1순위 png 고화질에 이미지 및 뒷 배경이 투명한 이미지
: 팁 2. FE 는 .WebP(Next.js)
: 상식. .gif 는 여러장의 이미지를 일정한 시간으로 교체하면서 보여주는 파일(여러사진을 합쳐서 시간을 줘서 움직이는것 처럼 만든거.) \_ 용량/css변경 불가.

- `<img src="경로/파일명.확장자" alt="이미지설명" />`
- alt="이미지설명" 인터넷 끊겼을 때 대신해주는거

### 1.3. 목록 태그 (ul,li(순서가 없다.)/ol,li(순서가 있다.))

- 필수입니다.
- 사용 판단 : 레이아웃이면 div, 내용이 동일한 형태일 경우 ul, li

## 2. css 선택자 태그

### 2.1. 범위 안쪽에 있는 태그 찾기

```css
/* 앞에 class에 children 중 img태그를 찾아라 css에선 공백은 범위 */
.header-logo-slide img {
  ....;
}

.header-logo-slide img a {
  ....;
}
```

### 2.2. display 간단 이해

- 신규 프로젝트는 적극적으로 `display : flex`를 사용해라 .

- 유지, 보수 프로젝트는 `display : inline, display : inline-block`을 조심하세요.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>레이아웃</title>
    <style>
      div,
      header,
      footer {
        border: 5px solid red;
        /* 안적어도 block */
        /* display: block; */
      }
      main {
        display: none;
      }
      .community {
        display: flex;
        /* justify-content: space-between; */
      }
      /* 안써주면 default */
      .news {
        width: 25%;
        height: 400px;
      }
      .notice {
        width: 25%;
        height: 400px;
      }
      .banner {
        width: 25%;
        height: 400px;
      }
      .product {
        width: 25%;
        height: 400px;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <!-- 상단 -->
      <header class="header">상단</header>
      <!-- 메인 -->
      <main class="main">
        <div class="slide">슬라이드</div>
        <div class="community">
          <div class="news">뉴스</div>
          <div class="notice">공지사항</div>
          <div class="banner">배너</div>
          <div class="product">제품소개</div>
        </div>
      </main>
      <!-- 하단 -->
      <footer class="footer">하단</footer>
    </div>
  </body>
</html>
```

### 2.3. flex 기초(외우자 중요)

- 관련사이트
  : https://studiomeal.com/archives/197

: https://codepen.io/enxaneta/pen/adLPwv

: https://flexboxfroggy.com/#ko

- container 용 flex (상자) > 부모
- item (요소들) > 자식

```css
.header-logo-link {
  display: flex;
  /* 세로 중앙 */
  align-items: center;
  /* 가로 왼쪽 정렬 */
  justify-content: flex-start;
  /* 가로 가운데 정렬 */
  justify-content: center;
  /* 가로 오른쪽 정렬 */
  justify-content: flex-end;
  /* 가로 양쪽 균등 정렬 */
  justify-content: space-between;
  justify-content: space-around;

  /* 아이템과 아이템 사이의 여백 */
  gap: 30px;
}
```

- itme 용 flex (요소들)
  : 거의 손을 안댄다.

- 블록 / 인라인

1. display 의 이해

```txt
- display : block;

  - 대표적인 태그
    - `<div>`
      -`<img>`
      -`<a>`

    - `<ul>(unlist)`
    - `<li>(list)`
      - 동일한 모양이 반복 된다면 사용해라. (div 너무 쓰지마라)
    - `<p>`
    - `<h1>~<h6>`

  // 사용안함

- display : inline;
  - inline은 넓이 / 높이 / margin / padding 못준다.
    // 아주 가끔 쓰는데 `***엔터키 공백` 들어가요.
- display : inline-block;
// 적극적으로 사용

- display : flex;
  - block > inline > inline-block 중간에 엔터키 다 없애줌

// 자주활용

- display : none;
  - css로 초기 모양을 설정하는 부분에 오류발생 소지가 있다.
  - 해당 태그 없애줌.
  - 일단은 none 반대는 block이라 생각하자.
```

- 퍼블리싱 할 때 css 전에 폰트세팅 해줘야 한다.

- google 폰트 찾아보고 / 없으면 눈누에서 찾아봐라.

```css 폰트 사용법
`- common.css 에 @import 시키고 아래;`

.noto-sans kr-<uniquifier > {
  font-family: "Noto Sans KR", sans-serif;
  font-optical-sizing: auto;
  font-weight: <weight>;
  font-style: normal;
}
```

### 2.4. 글꼴

- 초기 디자인 및 css 작업은 글꼴에 대한 협의가 끝나고 진행한다. (1순위)
- [구글폰트](https://fonts.google.com/?query=inter) 검색 > [눈누](https://noonnu.cc/) 검색
- 존재 하지 않는 경우 직접 폰트 생성진행

# main 영역 html , css

## 1. html

- 레이아웃을 공통적용을 위해서 inner div 작성(header 처럼)
- main-top 과 main-bottom 을 inner 안쪽으로 배치
- main-top 클래스에 왼쪽, 오른쪽 영역 잡기

## 2. css

- 화면의 너비 즉, vw 를 이용해서 높이에 반영
- `보여줄 너비 / 화면의 너비 \* 100 = 결과%`
- `보여줄 높이 / 화면의 너비 * 100 = 결과vw`

- 모서리를 둥글게
  : `border-radius : 20px`
- 내용 일부 가리기
  : `overflow:hidden`

- 배경에 이미지 넣기
  : 그림깔고 내용 위치잡기

```css
.main-top-banner a {
  display: block;
  width: 100%;
  height: 100%;
  /* 이미지 넣기 */
  background-image: url("../images/br.png");
  /* 영역을 꽉채워라 */
  background-size: contain;
  /* 반복 x */
  background-repeat: no-repeat;
  /* 중앙으로 가라. */
  background-position: center;
}
```

```css
background: url("../images/br.png") no-repeat center;
background-size: cover;
```

## 0. 배포하기

## 0. 배포하기

1. https://www.dothome.co.kr/ 가입하기
2. 홈에서 웹호스팅에서 무료 호스팅
3. 상세보기 > 신청하기
4. 정보 작성
5. 파일질라 설치 (백신 좀 설치 X)
6. 파일질라 실행
7. 아이디/비번 등록하기

- [파일질라](https://filezilla-project.org/)
- [무료웹호스팅](https://www.dothome.co.kr/)
- [Beyond compare](https://www.scootersoftware.com/)

- 통신 프로토콜(약속 : 규약)
  http 또는 https 는 웹브라우저 주소(html을 보여줄 때)
  ftp 는 file(file Transfer Protocol) 이 있는 곳(file을 보여줄 때)
  smtp 는 simple mail transfer protocol(이메일 보낼 때)

- 서버 란 24시간 동안 안꺼지는 컴퓨터 에요.

- 기본형(primitive)

  - number, string, boolean, null, undefined, symbol(유일한값 / 절대로 중복되지 않는 값)

    복잡한것(묶은것 : 기본형들을 모아서 활용) : object

- 여러 문장으로 연결된 경우의 글자는 <p>태그를 쓰자
- 단어를 작성하는 경우는 span 태그 쓰자

- 굵은 글자를 쓸때는
  <b> 태그를 쓰자

- 강조하고 싶은 글자는 strong
  <strong> 태그를 쓰자

- 기울임 글꼴을 쓸때는 italic
  <i>

- 한줄 내림 필수태그
  <br/>

웹브라우저는 a (anchor) 태그라면
기본적으로 파랗게, underline 으로
클릭이 가능해요. css 없이 표현 가능

display : inline 은 가로로 글자처럼 배치된다.

- 너비 / 높이 못준다.
- 마진, 패딩 일부만 들어감.
- 대표 태그

  - a, img, span, b, strong, i

- word-break : 단어를 기준으로 잘라라.

  - 규칙 없는 게 규칙, 카카오브레인 미니컨을 소개합니다 🙌

- flex 를 활용 시 참고사항
  : 기본적으로 flex 를 적용하면 줄내림은 없다.

```css
.box {
  display: flex;

  flex-wrap: nowrap;
}
```

: 필요 시 100% 넘는 item 들이 있으면 줄내림 하려면

```css
.box {
  display: flex;
  flex-wrap: nowrap;
}
```

- 효과 CSS3
  : [css box-shadow generator 검색](https://cssgenerator.org/box-shadow-css-generator.html)
  : [css filter](https://developer.mozilla.org/en-US/docs/Web/CSS)
  : transition 기본형

  - `transition : 속성명 시간초 시간효과 지연시간`

  ```css
  transition: width 0.5s, ease-in(가속도), background 0.5s;

  .list-box:hover .list-box-img {
    filter: drop-shadow(0px 25px 25px rgb(0 0 0 / 0.2));
    transform: translateY(-10px);
  }

  .list-box-img {
    width: 100%;
    overflow: hidden;
    height: 17.09vw;
    max-height: 200px;
    margin-bottom: 24px;

    transition: all 0.2s ease-in;
  }
  ```
