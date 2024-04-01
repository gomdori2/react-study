# 프로젝트 생성

## 1. 기본 사항
- 깃허브에 먼저 소문자로 프로젝트명을 생성

- 깃허브에 설명(describtion)은 반드시 작성한다.

- PC에 동일한 소문자로 폴더를 만든다.

### 1.1. 리액트 및 퍼블리싱 프로젝트 생성
- VSCode 를 실행한다.
- pc에 만든 폴더를 드래그 해서 등록한다.
- 명령어를 통하여 기본 파일럿 프로젝트를 생성한다.
: `npm create-react-app ./`를 실행한다.
: Node.js 권장 설치버전(https://nodejs.org/en/download)
: Node.js 는 LTS 버전을 선택하자.
: 설치는 기본폴더 그대로 설치하자. 손대면 오류발생 가능
: 2024-04-01 시점(v.20.12.0)
: react 설치 오류 처리(-4058 에러)
: `npm uninstall -g create-react-app`
: `npm install -g create-react-app`
: 위처럼 오류 발생시 위의 사항을 실행하고 난 후 
: `npm create-react-app ./`를 실행한다.
git에 저장소 생성 / d드라이브에 연결/ 프로젝트 확인 / `npm create-react-app ./`
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
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>카카오 브레인 블로그</title>
</head>
<body>

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


