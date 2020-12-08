# README

## 아이디어 추가 제안(09/07)

### :bulb: 틀린그림찾기/숨은그림찾기

이미지 => 색 추출 => 비슷한 색의 물체를 사진 속 해당 색상 위치에 넣고 찾는 미니게임



### :bulb: RETRO) 다마고치

이미지 => 해당 물체를 픽셀화 => 캐릭터화시켜서 게임 속 캐릭터로



### :bulb: 물건찾기

이미지 => 이미지 속 물체를 분석

- 물체로 구분 가능하면 => 원하는 물건 찾기 가능

- 불가능하면 => 남은 영역에 원하는 물건이 있다



### :bulb: 챗봇



### :bulb: 교육 + 유튜브

- 특정 영상 속에서 키워드 추출 => 키워드 관련 교육 영상/또는 관련 영상 제안



## 아이디어 추가 제안(09/08)

### :bulb: 언제까지

- 물체 이미지 > 해당 제품의 유효기한 제안
  - 샀을 때 이미지 입력 > 유효기한 끝나면 알림



## 아이디어 정리(09/09)

### 반려동물 관련 서비스

- 반려동물 관련 SNS
- 분류(ai)
- 유기견,유기묘 관련 서비스



## 아이디어 수정(09/10)

### 반려동물 관련 서비스

- 반려동물 + 다이어리
- 반려동물 + 건강
- 반려동물 + 의료



### 그 외

- 보류



## 아이디어 결정(09/11)

### 고양이 분석기

- 고양이 이미지 => 종 분석 => 정보 제공 / 유저 도감에 추가 
- 인간 => 어떤 고양이와 비슷한지
- 고양이 도감 등



## 와이어프레임 / ERD (09/14-15)

- 와이어프레임 초안 제작
  - 이번 주 내로 와이어프레임 ver 1.0 만들고, 프로젝트 시작

- 와이어프레임 수정 후 ver 0.1.2 공유



## 라우터 구조화 (09/16)

App.vue

- 네비게이션바, 푸터, 라우터 뷰



라우터(views 폴더)

- home 관련
  - 메인페이지
- analysis 관련
  - 고양이 분석 페이지
  - 유저 얼굴 > 고양이 분석 페이지
- account 관련
  - 로그인 했을 경우
    - 마이페이지
    - 나의 고양이 도감
    - 검색 히스토리
  - 로그인 하지 않았을 경우
    - 로그인 페이지
    - 회원가입 페이지
- cat 관련
  - 고양이 검색 페이지
  - 고양이 상세보기 페이지
- else
  - 에러 관련 페이지



## 라이브러리, UI/UX 활용 (09/17)

이미지 사이즈 조정

- https://vuejsexamples.com/vue-js-image-clipping-components/



슬라이드

- https://swiperjs.com/vue/
- https://github.surmon.me/vue-awesome-swiper/?ref=madewithvuejs.com
- https://madewithvuejs.com/vue-awesome-swiper
- https://vuejsexamples.com/slight-vue-slider-component-for-h5/
- https://vuejsexamples.com/ios-style-swipe-actions-for-vue-js/



기타 사용할만한 라이브러리

- 비율 : https://dumptyd.github.io/vue-css-donut-chart/
- https://vuejsexamples.com/powerfull-carousel-component-for-vue-js/



## 와이어프레임/UXUI 재설계 (09/23)

- 와이어프레임, UXUI 다시 설계

- 이미지 크롤링