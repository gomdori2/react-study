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
