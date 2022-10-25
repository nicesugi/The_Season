# The season of N.11 &nbsp;&nbsp;|&nbsp;&nbsp; 2022년 6월 28일 - 2022년 7월 6일 (1주)

### 서비스 소개 </br>

<details>
<summary>
유화 제작 인공지능 기술로 이미지를 변환시켜주는 SNS 입니다.
</summary>
</br>

사용자가 이미지를 선택하여 게시글을 등록하면 유화제작 인공지능 기술(NST)을 사용하여 해당 이미지의 스타일을 변환해주어 게시글을 생성합니다.

유화 스타일은 총 11가지로 구성하였습니다. 게시글 등록시 스타일의 원작 이미지를 확인할 수 있습니다. 

결과물은 메인페이지와 마이페이지에서 확인이 가능합니다.

이 프로젝트는 이미지 생성 기술(Generative models)을 이용해서 사용자가 흥미를 느낄 수 있는 서비스를 만들고자 하였으며

본인이 작성한 글 이외에도 다른 사용자의 글을 열람하여 댓글을 작성해 사용자 간의 소통이 가능합니다.

모든 게시글에는 좋아요와 북마크 기능이 있으며 내가 작성한 글과 북마크한 글들을 모아볼 수 있습니다. 

내가 작성한 게시글의 이미지를 제외한 내용은 수정,삭제가 가능하며 북마크 또한 해제가 가능합니다.

서비스 특성상 모바일 접속자가 많을 걸로 예상하여 반응형을 적용하였습니다.

[🔗 frontend repo](https://github.com/2JYK/The-season-of-N.11_frontend/)<br>
</details>

간단한 시연영상 링크 >> [클릭](https://tv.kakao.com/v/430188053)


### 목차

[1. 개발환경](#개발환경) <br>
[2. 나의 역할](#나의-역할) <br>
[3. 와이어 프레임](#와이어-프레임) <br>
[4. 기능 명세서](#기능-명세서) <br>
[5. 데이터베이스 ERD](#데이터베이스-erd) <br>
[6. API 설계](#api-설계) <br>
[7. 컨벤션](#컨벤션) <br>

## 개발환경
Backend : <img src="https://img.shields.io/badge/Python-3.9.10-3776AB?style=flat-square&logo=Python&logoColor=white"/> <img src="https://img.shields.io/badge/Django-092E20?style=flat-square&logo=Django&logoColor=white"/> <img src="https://img.shields.io/badge/Django REST framework-092E20?style=flat-square&logo=Django REST framework&logoColor=white"/> 

Frontend : <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=HTML5&logoColor=white"/> <img src="https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=CSS&logoColor=white"/> <img src="https://img.shields.io/badge/jQuery-0769AD?style=flat-square&logo=jQuery&logoColor=white"/> <img src="https://img.shields.io/badge/Javascript-F7DF1E?style=flat-square&logo=Javascript&logoColor=white"/> 

DataBase : <img src="https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=SQLite&logoColor=white"/>

Infra : <img src="https://img.shields.io/badge/Gunicorn-499848?style=flat-square&logo=Gunicorn&logoColor=white"/> 
<img src="https://img.shields.io/badge/Amazon AWS-232F3E?style=flat-square&logo=Amazon AWS&logoColor=white"/> <img src="https://img.shields.io/badge/Amazon EC2-FF9900?style=flat-square&logo=Amazon EC2&logoColor=white"/> <img src="https://img.shields.io/badge/Amazon S3-569A31?style=flat-square&logo=Amazon S3&logoColor=white"/> <img src="https://img.shields.io/badge/Netlify-00C7B7?style=flat-square&logo=Netlify&logoColor=white"/>

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)


## 나의 역할

- 회원가입
- simple JWT 을 이용한 로그인
- 마이 페이지 구현
    - 내가 작성한 게시글들 조회
    - 게시글 수정
    - 게시글 삭제 
- 북마크 페이지 구현
    - 북마크한 게시글을 조회
    - 해당 게시글의 북마크 해제
- 유화제작 인공지능 기술(NST)
    - 원하는 이미지를 11가지의 스타일 중 하나로 적용하여 이미지 생성, 조회, 저장(서버/DB/브라우저)
<br>

## 와이어 프레임
<details>
<summary> Click ! </summary>
<img width="1242" alt="mockup" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FM7SBU%2FbtrFZdSFHcO%2FpEnrZBks6tez01kwFxsowK%2Fimg.png">
</details>

<br>

## 기능 명세서
<details>
<summary> 회원가입 / 로그인 </summary>
<div markdown="1">

-   아이디와 비밀번호를 입력해 회원가입 또는 로그인을 할 수 있습니다.
    -   회원가입은 아이디와 패스워드가 6자리 이상 이여야 가능합니다.
    -   아이디가 중복되면 회원가입이 불가합니다.
-   로그인이 된 상태에선 회원가입/로그인 페이지에 접속이 불가합니다.
-   추가 : 소셜 로그인 회원가입/로그인 기능
-   추가 : 비밀번호 찾기

</div>
</details>

<details>
<summary> 메인 페이지 </summary>
<div markdown="1">

-   여러 사용자가 업로드한 게시물을 한 눈에 확인할 수 있습니다. (역순)
-   각 게시물에 좋아요와 북마크를 누를 수 있습니다.
-   업로드 버튼을 누르면 업로드 페이지로 이동합니다.
-   페이지 네이션을 통해 2 x 3 이 넘어가면 페이지가 생깁니다.
-   게시물을 클릭 시 게시글의 상세페이지로 이동합니다.

</div>
</details>

<details>
<summary> 업로드 페이지 </summary>
<div markdown="1">

-   사진을 선택하여 업로드 하면 머신러닝을 통해 사진의 스타일을 변환합니다.
-   사용자는 자신이 원하는 계절감의 사진을 선택합니다.
-   머신러닝의 결과물이 나오면 사진에 맞는 코멘트를 작성한 뒤 사진을 게시합니다.
-   제목은 30자, 설명은 100자 이하로만 작성할수 있습니다.
-   업로드 버튼을 클릭 시 메인페이지로 보내집니다.

</div>
</details>

<details>
<summary> 마이 페이지 </summary>
<div markdown="1">

-   현재 로그인한 사용자가 올린 사진 및 북마크한 사진을 확인할 수 있습니다.
-   기본값으로는 사용자가 올린 사진들이 보여집니다.
-   무한 스크롤을 이용하여 보여집니다.
-   게시물을 클릭 시 게시글의 상세페이지로 이동합니다.
-   사용자가 올린 사진에 대한 수정 및 삭제가 가능합니다.

</div>
</details>

<details>
<summary> 게시글 상세 페이지 </summary>
<div markdown="1">

-   다른 사용자가 댓글을 작성할 수 있습니다.
-   다른 사용자의 글에 북마크를 남겨 마이 페이지의 북마크 탭에서 확인할 수 있습니다.
-   좋아요 카운트 숫자를 보여주고 누릅니다.

</div>
</details>

<details>
<summary> 게시글 수정 페이지 </summary>
<div markdown="1">

-   로그인한 사용자가 작성한 사진 중 수정할 사진을 선택하면 해당 화면으로 들어와
-   사용자가 수정을 진행할 수 있습니다.
-   취소 버튼을 누르면 마이페이지로 다시 돌아갑니다.
-   수정할 수 있는 내용은 아래와 같습니다.
    -   게시글의 제목
    -   게시글의 설명
-   우상단의 삭제 버튼을 눌러 해당 게시글을 삭제할 수 있습니다.

</div>
</details>

</details>
<br>


## 데이터베이스 ERD
<details>
<summary> Click ! </summary>
<img width="1213" alt="season" src="https://user-images.githubusercontent.com/104303285/185300027-4c89cd18-10f6-478c-9044-996720b03c6c.png">
</details>

<br>

## API 설계
<details>
<summary> ARTICLE 앱 </summary>
<img width="1176" alt="스크린샷 2022-08-18 오후 2 50 40" src="https://user-images.githubusercontent.com/104303285/185303999-8ad88f51-c369-4288-910b-624a92ce4e64.png">
</details>

<details>
<summary> USER 앱 </summary>
<img width="1141" alt="스크린샷 2022-08-18 오후 2 50 17" src="https://user-images.githubusercontent.com/104303285/185304009-60d545a6-3dec-4a4e-a468-bf15c03fba25.png">
</details>

<br>

## 컨벤션

### GitHub

<details>
<summary> 브랜치 </summary>
<br>
(app 별로)

-   article
-   nst -> 기능 테스트 후 article 브랜치로 이동
-   user

</details>
<br>

<details>
<summary> 커밋 메세지 </summary>
<br>

```
Commit Type
- Add : 새로운 파일 추가
- Feat : 새로운 기능 추가/수정/삭제
- Fix : 버그 수정
- Update : 기존 기능 추가/수정/삭제
- Comment : 주석 관련
- Docs : 문서 수정
- Design : CSS 등 사용자 UI 디자인 변경
- Style : 코드에 영향을 주지 않는 변경사항 /  코드 포맷 변경, 새미 콜론 누락, 코드 수정이 없는 경우
- Refactor : 코드 리팩토링
- Rename : 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우
- Remove : 파일을 삭제하는 작업만 수행한 경우

Subject
- 50자를 넘기지 않고, 커밋 타입을 준수함.

 Body
- 72자를 넘기지 않고, 모든 커밋에 본문 내용을 작성할 필요는 없음.
```

</details>
