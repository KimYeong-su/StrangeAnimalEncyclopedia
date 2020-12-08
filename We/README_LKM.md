# README



## 아이디어 회의

1. 오답노트

   - 문제를 사진 찍으면 해당 과목의 개념을 분류
   - 음성 녹음으로 해설
   - 다른 문제 추천
   - 시험 기능

   :speech_balloon: _기술적으로 가능하다면 괜찮음_

   

2. 진단

   - 피부병 같은 것들

   - CNN을 이용해 이미지를 분류하고, 그에 대한 정보 제공

   :speech_balloon: _데이터 수집 해결해야 함 - 이미지 크롤링_

   :speech_balloon: _심사위원들에게 어필할 만한 아이디어 (비즈니스적 관점)_

   

3. 의류 사이즈 추천

   - 상하의, 신발 등의 사이즈를 측정하여 추천

   :speech_balloon: _기준 잡는 것이 중요_

   

4. 반려동물 SNS

   - 반려동물 종 분류
   - 피드
   - 유기동물 관련 서비스
   - 건강 관련 서비스 (다이어리 등)
   - 정보 전달
   - 부가적인 기능 : 채팅(DM), 알림, 자동 완성

   :speech_balloon: _CNN 활용하기_

   :speech_balloon: _괜찮은 서비스_

---

### 고양이 종 분류 :heavy_check_mark:

- 고양이 이미지를 인식해 종을 분류
- 사람 사진은 가장 닮은 고양이 종 알려줌
- 나만의 도감
- 정보 제공



## ERD

- 회원 - id, username, email, password
- 고양이 - id, species
- 도감 - id, user_id(FK), cat_id(FK), image, created_at



---

- 각 고양이의 특징을 테이블에 각각 필드로 넣음
  - 몸의 빛깔
  - 분포 지역
  - 성격?

- 고양이 성격 특징을 별도의 테이블로 만듦

- 분석 결과
- 히스토리



## 0916 Django project 연습 & 정리

- 1학기 Django, vue 강의 다시 보면서 정리하고, 따로 프로젝트 생성하여 연습



### Serializers

- request.POST로는 **json**으로 넘어온 데이터를 못잡고 request.data로는 해당 데이터를 파싱해서 딕셔너리 형태로 변환할 수 있음

  ```
  request.POST = <QueryDict: {}>
  request.data = {'title': 'TITLE', 'content': 'CONTENT'}
  ```

- 어떤 데이터가 넘어올지 모르니까 `request.data` 사용
  (**form-data**로 넘어온 데이터는 request.POST도 가능)

- is_valid를 통과하지 못했을 때 return값이 없는 경우

  - `raise_exception=True`를 인자로 추가해 에러메시지를 보여줌



### Authentication

```bash
$ pip install django-rest-auth django-allauth
$ pip freeze > requirements.txt
```

- django-rest-auth를 쓰면 login, logout 기능을 쓸 수 있음
- django-allauth까지 쓰면 signup 기능도 가능

- header에 토큰값을 넣어서 보내면 request.user가 알아서 잡힘


#### Login & Logout

- Login은 POST 요청 (username, password 데이터 필요)

- Logout은 POST 요청으로 header에 토큰 값을 넣어서 보내면 해당 user가 로그아웃됨

#### Registration

- 요청 보낼 때

  - header에 Authorization : Token 토큰값
  - body에 title, content 값 json 형태로 넣음
- 토큰이 없을 경우(비로그인 상태의 경우) 함수 실행이 되지 않도록 함



:bulb: header에 token을 넣어서 요청 보내면 DRF가 알아서 request.user를 찾아옴

:bulb: vue에서 axios post 요청을 보낼 때 header에 토큰 값을 넣어서 보내야 인증할 수 있음



## 0921

1. API url 문서 만들기
   - 요청하는 url, 필요한 데이터, response 등
2. erd에 테이블 추가
   - 분석했을 때 결과가 예측이랑 다를 때 그 데이터를 저장할 수 있어야 함



## 0922

https://www.kaggle.com/ma7555/cat-breeds-dataset

- 고양이 정보를 JSON 파일로 만들거나 DB에 직접 저장

  1. 종류별로 검색해서 정보 저장 (신뢰도 있는 사이트)

  2. 나눠서 모은다면 어떤 식으로 저장할지 생각해보기

     ```json
     [
         {
             "pk": 1,
             "model": "cats.cat",
             "품종": "아비시니안",
         },
         {
             "pk": 2,
             "model": "cats.cat",
             "품종": "먼치킨",
         }
     ]
     ```

- 리스트로 반환 (종에 대한 확률들) - max를 써서 최고 갖는 걸 index로 반환(cat_id)

- 테이블에 영어, 한글 이름 전부 저장

- 일단 14개 (A부터)



:exclamation: 고양이 품종 분류 엎음

- 비슷한 외형을 가진 품종들이 존재함

:exclamation: 기능은 그대로 유지하되, 대상을 **모든 동물 + 상상의 동물**로 확장시킴



## 0923 데이터 크롤링 & 정제

- 바뀐 주제에 맞게 ERD 수정

- 크롤링 할 때 사진 부족하면 영어로도 검색, 제대로 된 사진 아니면 삭제

- 각 동물 당 100개씩

- 내 담당

  - 완료 : 거미, 불가사리, 지네, 치타, 
  - 정제 중 : 금붕어, 게, 늑대, 백호, 코뿔소, 
    - 문제 있음 : 가물치/망둥어/메기(낚시, 손질/회/매운탕/양념돼있거나 말려지는 사진 多), 유니콘(그림 같은 게 많음), 주작(주작글 캡쳐가 많음), 재규어(자동차가 8-9할, 영어로 쳐도!)
  - 크롤링 해야 함 : 붕어, 올빼미, 표범, 퓨마(영어로 해보기)
  - 추가할지 고민 : 가오리, 문어, 오징어, 나무늘보, 악어

  - 크롤링 해야 함 : 붕어, 올빼미, 표범, 퓨마(영어로 해보기), 문어, 오징어, 가오리

- 다시 크롤링한 결과
  - 가오리/나무늘보/악어/올빼미/표범 : 데이터 양 충분한 듯!
  - 문어/붕어/오징어 : 다른 생선들과 비슷한 결과...
  - 유니콘/재규어/퓨마 : 영어로 해도 답이 없음



## 0924

### 데이터 정제

- 유니콘 : 사진 양이 충분하지 않아서 그림도 가능
- 사진 잘 안 뜨는 품종은 앞에 '동물' 붙여서 검색하기
- 다시 크롤링한 결과
  - 유니콘 : 100장 맞출 순 있겠지만, 데이터의 퀄리티가 좋지는 않은 듯..
  - 돌고래/재규어/퓨마/해파리 : 데이터 양 충분
  - 문어 : 요리는 거의 안 나오지만 그림이 많음
  - 비버 : 저스틴 비버...
- 내 담당
  - 완료 : 거미, 늑대, 돌고래, 불가사리, 지네, 치타, 해파리
  - 정제 중 : 가오리, 금붕어, 게, 나무늘보, 백호, 붕어, 악어, 올빼미, 재규어, 코뿔소, 표범, 퓨마
    - 문제 있음 : 유니콘(그림 같은 게 많음)



### To do list

- 소셜로그인 했을 때 넘어오는 response 알아보기
  1. vue에서 request 보냄
  2. views.py에서 구글/카카오 api로 request 보냄
  3. 로그인 되고 reponse가 넘어옴
  4. 그 정보(nickname, ...)를 기반으로 회원가입 시킴
  5. vue에 성공적으로 끝났다고 reponse 보냄

- 위의 방식으로 할 수 있는지 찾기
  - 구글 : views.py에서 처리할 수 있는지 확인
  - 카카오 로그인 구현과 병행



## 0925

- env 파일 파싱

  ```bash
  $ pip install python-decouple
  ```



### 카카오 로그인

> 참고 : https://github.com/snoop2head/fitcuration-django/blob/master/users/views.py

1. 인증 코드 받기 :heavy_check_mark:
2. 사용자 토큰 받기 :heavy_check_mark:
3. 사용자 정보 가져오기 - 이메일, 닉네임 :heavy_check_mark:
4. 로그인
   - 해당 메일을 가진 사용자가 카카오로 회원 등록이 되어있으면 로그인, 아닌 경우 예외처리
   - 그런 사용자가 없는 경우, 카카오 API를 이용해 얻은 사용자 정보를 바탕으로 회원 등록, 로그인함
5. 성공 시 홈으로 리다이렉트, 예외 발생 시 로그인 페이지로 리다이렉트



- 일요일까지 데이터 정제 완료하기
  - 완료 : 게, 금붕어, 악어, 올빼미
  - 정제 중 : 가오리, 나무늘보, 백호, 붕어, 유니콘, 재규어, 코뿔소, 표범, 퓨마

- 참고한 프로젝트에서는, User 모델에 회원 등록 방식(REGISTER_LOGIN_METHOD)를 필드로 넣어놓고, 로그인 기능 구현에서 활용함
  - 우리 User 모델과 다르므로 어떻게 구현할지 생각해보기

- 구글 로그인 views.py에서 구현 완료했었으나
  - 갑자기 안 됨 (아직 이유 못 찾음)
  - 그 정보를 바탕으로 우리 서비스 User DB에 등록하는 걸 아직 구현하지 못함



## 0926

- 카카오 로그인 구현 완료
  - 카카오 사용자 정보를 이용해 우리 서비스의 User로 등록

- 데이터 정제
  - 완료 : 가오리, 나무늘보, 달팽이(추가), 백호, 유니콘, 재규어, 코뿔소, 퓨마
  - 정제 중 : 표범
  - 문제 있음 : 붕어



## 0927

- 데이터 정제
  - 완료 : 표범



### 구글 로그인

> 참고
>
> https://velog.io/@maintain0404/Google-OpenIDOauth-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-with-django

0. 라이브러리 설치

   ```bash
   $ pip install --upgrade google-auth
   $ pip install google-auth-oauthlib
   $ pip install google-auth-httplib2
   ```

1. flow 객체 생성 :heavy_check_mark:
2. 인증 코드 받기 :heavy_check_mark:
3. 토큰 받기 :heavy_check_mark:
4. 구글에 사용자 정보를 요청 :heavy_check_mark:
5. 받아온 데이터를 서버 데이터와 조회해 로그인 처리 :heavy_check_mark:



## 0928

- 소셜로그인 - Response로 리턴하도록 바꾸기
- 동물 데이터 수집

