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

### 2.2. flex 기초(외우자 중요)

: container (상자) > 부모

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
}
```

: item (요소들) > 자식
:

- 블록 / 인라인
