# 프로젝트 생성

## 1. 기본 사항
- 깃허브에 먼저 소문자로 프로젝트명을 생성

- 깃허브에 설명(describtion)은 반드시 작성한다.

- PC에 동일한 소문자로 폴더를 만든다.

- npm / npx 차이
- npx > - 프로젝트생성
- npm > - 내 피시에 저장하고 싶을 때


### 1.1. 리액트 및 퍼블리싱 프로젝트 생성
- VSCode 를 실행한다.
- pc에 만든 폴더를 드래그 해서 등록한다.
- 명령어를 통하여 기본 파일럿 프로젝트를 생성한다.
: `npx create-react-app ./`를 실행한다.
: Node.js 권장 설치버전(https://nodejs.org/en/download)
: Node.js 는 LTS 버전을 선택하자.
: 설치는 기본폴더 그대로 설치하자. 손대면 오류발생 가능
: 2024-04-01 시점(v.20.12.0)
/******************* react 설치 오류 처리(-4058 에러) **********************/

: `npm uninstall -g create-react-app`
: `npm install -g create-react-app`
: `npm i`
: 위처럼 오류 발생시 위의 사항을 실행하고 난 후 
: `npx create-react-app ./`를 실행한다.
git에 저장소 생성 / d드라이브에 연결/ 프로젝트 확인 / `npm create-react-app ./`

/******************* react 설치 오류 처리(-4058 에러) **********************/


### 1.2 테스트 해보기
- `npm run start`
- 터미널에서 `ctrl + C` 로 미리보기 종료한다.

## 2. 작업 순서 기준
### 2.1. 웹서비스 개발 순서(프론트)

- 퍼블리싱부터 진행(필수, 기본)
- 리액트 진행(필요시)
- 타입스크립트 진행(필요시)
- Next.js 진행(필요시)

### 2.2. 퍼블리싱 해보기
- 생성된 폴더 최상위를 `Root` 라고 부른다.
- 코드상으로는 `/` 로 표현
- 퍼블리싱은 `/public` 폴더에 `www` 로 폴더 생성 후 진행
- 퍼블리싱 기본 폴더 생성 진행
: images 폴더 생성(.png, .jpg, .gif, .svg)
: css 폴더 생성(.css 파일들을 보관)
: js 폴더 생성(.js 파일들을 보관)
: assets 폴더 생성(문서, 동영상, 디자인원본(.psd[포토샵])..)
: index.html 파일 생성

#### 프로젝트 내부  기본구성(Root / public / www / images, css, js, assets, index.html)

### 2.3. index.html 기본구성
- `! 누르면서 탭 키를 선택`하면 html 기본형 제공(html[스냅샷,snapshot])

- lang = "ko"로 수정

- 최소 타이틀은 변경한다.

- 미리보기(html 파일에서 마우스 오른쪽 open with live server 선택)

```html 이렇게 틸트 내부에 html로 하면 아래와 같이 표시된다.```
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>카카오 브레인 블로그</title>
</head>
<body>
  <div class="wrap">

  </div>
</body>
</html>
```
- git remote add origin https://github.com/gomdori2/react-study.git
  깃  명령어 온라인 추가하라 별명(호칭) 주소... 
- git remote -v 주소 제대로 됬는지 확인할때
- git add .
- git commit 



- git push -u origin main
- -u를 붙여서 올리면 > git push만 해도 올라감.
- git push origin main
  깃 origin > main 

### 2.4. html 문서 작업 순서(컴포넌트 구분 디자인을 받았을 때 html 섹션 나누는법 배우기)
- 배치(레이아웃)를 위한 태그 (div 태그)
  _ html은 무조건 소문자
- 태그 호환성 알려주는 사이트
  _ https://caniuse.com/


- 디자인 레이아웃 보기
- https://chromewebstore.google.com/detail/gofullpage-full-page-scre/fdpohaocaechififmbbbbbknoalclacl
  : 디자인 파일은 /public/www/assets 폴더에 보관
- 디자인을 살펴보고 영역을 구분하는 작업 진행
    : 레이아웃을 위한 영역
  

- html 의 태그의 활용 이전에 꼭 체크 해 보자.

: 내용별 배치 영역
      _
      : 시멘틱 하다
      : 태그가 내용을 설명하는 역할을 시멘틱
      ``` html
      <!DOCTYPE html>
      <html lang="ko">
      <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>카카오브레인 Blog</title>
      </head>
      <body>
          <!-- 전체 레이아웃 -->
          <div class="wrap">
              <!-- 상단 레이아웃 -->
              <header class="header"></header>
              
              <!-- 메인 레이아웃 -->
              <main class="main"></main>

              <!-- 하단 레이아웃 -->
              <footer class="footer"></footer>
          </div>

      </body>
      </html>
      ```

      ``` html
      <!DOCTYPE html>
      <html lang="ko">
      <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>카카오브레인 Blog</title>
      </head>
      <body>
          <!-- 전체 레이아웃 -->
          <div class="wrap">
              <!-- 상단 레이아웃 -->
              <div class="header"></div>
              
              <!-- 메인 레이아웃 -->
              <div class="main"></div>

              <!-- 하단 레이아웃 -->
              <div class="footer"></div>
          </div>

      </body>
      </html>
      ```
- 메인 > 큰거를 위주로 잡고 > 단계별로 작아진다.
- 매트료시카 처럼 해라.

- 참고사항
  : camelCase(카멜케이스)
  : PscalCase(파스칼케이스)
  : snake_case(스네이크케이스)

- html -> main-top/main_top 식으로 함
<태그 class="" id=""></태그>
<div class="slide" id="card"></div>
- div 는 레이아웃 용도
- class 는 꾸미기(색상, 너비, 높이, 위치, 액션 ...)
- id    는 js 로 제어

- div 구조를 이용해서 뼈대를 잘만드는 것이 실력
: <div class="wrap">내용</div> 무조건 기본
``` html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>카카오브레인 Blog</title>
</head>
<body>
     <!-- 전체 레이아웃 -->
     <div class="wrap">
        <!-- 상단 레이아웃 -->
        <header class="header">
            <!-- 상단 로고 -->
            <div class="header-logo"></div>
            <!-- 상단 메뉴 -->
            <div class="header-navi"></div>
        </header>
        
        <!-- 메인 레이아웃 -->
        <main class="main">
            <!-- 메인상단 영역 -->
            <div class="main-top">
                <!-- 슬라이드 -->
                <div class="main-top-slide"></div>
                <!-- 타이틀 배너 -->
                <div class="main-top-banner"></div>
            </div>
            <!-- 메인하단영역 -->
            <div class="main-bottom">
                <!-- 메인 리스트 영역 -->
                <div class="main-bottom-list">
                    <!-- 새글리스트 -->
                    <div class="main-bottom-list-new"></div>
                    <!-- 배너 -->
                    <div class="main-bottom-list-banner"></div>
                    <!-- 추천글 리스트 -->
                    <div class="main-bottom-list-picks"></div>
                </div>
                <!-- 메인 카드 영역 -->
                <div class="main-bottom-cards">
                    <!-- 카드 슬라이드 -->
                    <div class="main-bottom-cards-slide"></div>
                </div>
            </div>
        </main>
        <!-- 하단 레이아웃 -->
        <footer class="footer">
            <!-- 하단 사이트정보 및 사이트 맵  -->
            <div class="footer-top">
                <!-- 회사 소개 -->
                <div class="footer-top-info"></div>
                <!-- 사이트맵 -->
                <div class="footer-top-sitemap"></div>
            </div>
            <!-- 하단 카피라이터 및 SNS 링크 -->
            <div class="footer-bottom">
                <!-- 카피라이터 -->
                <div class="footer-bottom-copyright"></div>
                <!-- sns 목록 -->
                <div class="footer-bottom-sns"></div>
            </div>
        </footer>
    </div>
</body>
</html>
```


## 3. Git 기초 명령어

### 3.1. 깃으로 관리할거에요.(초기화 : 한번만 )
- `git init` > 내 피시에 git으로 관리

### 3.2. 깃으로 관리하는 파일을 추가해주기.(매일 퇴근전, 필요시)
- `git add .`     > 모든 파일을 다 관리할거다.
- `git add 명칭`  > 해당되는 파일 하나만.

### 3.3. 깃으로 작업 내역을 기록해 둔다.(메모 퇴근전, 필요시 마다)
- `git commit`
- 첫줄      제목
- 두번째줄  내용
### 3.4. 깃을 깃허브로  업로드 한다.
- `origin은 따로 명명하는 alias`
- `git remote add origin http주소`
- `git remote add origin https://github.com/gomdori2/kakao-brain-gomdori2.git`
- `git remote -v` > add 됬는지 확인할 때_ 처음할때만 

### 3.5. 깃을 깃허브로 push 후 퇴근 한다. (매일 퇴근전, 필요시) 
- `git push -u origin main` 
- `git push origin main`
- `git push`