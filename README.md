# Relay 21  
![_2020-07-31__2 53 51](https://user-images.githubusercontent.com/21030956/89019291-0b656a80-d358-11ea-82f2-f60358dc763c.png)  

[서비스조사](Documents/ProjectResearch.md)  
[기능 설계](Documents/ProjectDesign.md)

---
## 참여자
1주차 : 정재명, 정택현, 조경환, 조기현, 조송주, 조수정, 조인택, 조정래, 김병인, 김석호, 김승언, 김신우  
2주차 : 이은정, 권지웅, 박재현, 허경영, 현기엽, 김근수, 심영민, 이지원, 조경환, 정택현, 양어진  
3주차 : 신병기, 조인택, 문성주, 서명렬, 유시형, 정재명, 김석호, 김영렬, 백종근, 임수현, 강민석, 이태경  
4주차 : 송민관, 양어진, 조수정, 조기현, 김병인, 박태희, 백종근, 이진호, 홍동현, 류연수, 임리나

## 2주차

### FrontEnd

- cocoaPods
- `MessageKit`
- Program Flow
- MessageKit으로 UI 구성
- 메세지 작성 후 보내기 할 때, Server에 해당 message에 대한 유해성 검사
- 검사 후 넘어온 data를 message로 전송

### BackEnd

1. 서버 Flask, Django, Spring중  Flask로 서버 선택
2. Flask 개발 환경 설정을 했다.
3. 메세지를 받을 때 NLP라이브러리로 욕설부분만 " * "로 변환한다.
4. 변환한 메세지를 Front로 json형식으로 보낸다.

```sudo
pip3 install -r requirements.txt
flask run -h 0.0.0.0 -p 80
```

### 실행결과

![1](https://user-images.githubusercontent.com/35067611/90239190-1cd36a00-de62-11ea-865e-eee0983784a4.png)
![2](https://user-images.githubusercontent.com/35067611/90239191-1e049700-de62-11ea-9fb0-89a4f4383d1a.png)
![3](https://user-images.githubusercontent.com/35067611/90239193-1e9d2d80-de62-11ea-8f02-e8f2f0425c1e.gif)  


## 3주차

### [데모영상링크👀](https://youtu.be/ub9kPr_HmlQ)



### 기능B 소개 및 요구사항

목적 : 음란성 이미지를 검열하여 건전한 채팅문화 조성

기능: 사용자가 채팅창에 사진을 보냈을 때 유해성 검사 후 유해할 시 blur 처리하여 업로드, 유해하지 않다면 바로 업로드  

### 체크포인트

✅ 고양이 사진(음란성 사진 대신 고양이사진)을 채팅창에 보냈을 때 blur 처리

✅ 고양이 사진이 아닌 채팅창에 보냈을 때는 원본사진 보여주기  

### 실행하기

1. ~~~shell
   git clone https://github.com/boostcamp-2020/relay_21.git
   ~~~

2. ~~~shell
   cd relay_21/BE
   ~~~

3. ~~~shell
   pip3 install -r requirements.txt
   ~~~

   - 이 때, 오류가 나는 line 모두 지우기 (지워도 실행 됩니다!)

4. ~~~shell
   vim relay_21/FE/Sources/Extensions/Networkhelper.swift
   ~~~

   - private let baseUrl = ```http://49.50.166.93/hello``` ➡  ```http://0.0.0.0/hello```로 바꿔주기

5. ~~~shell
   cd relay_21/BE
   ~~~

6. ~~~shell
   flask run -h 0.0.0.0 -p 80
   ~~~

7. Xcode Run



### API

1. ```UIBlurEffect``` (iOS에서 블러처리하는 API) : https://developer.apple.com/documentation/uikit/uiblureffect
2. Core ML & Vision on iOS (iOS 머신러닝) ```SqueezeNet```
   - 설명 블로그 : http://throughkim.kr/2017/09/06/ios-coreml/
   - Core ML Models Download : https://developer.apple.com/machine-learning/models/



### FrontEnd

1. 사용자가 업로드할 사진을 선택

2. 선택한 사진에 대한 유해성 판단 (고양이인지 판단)
   - 고양이라고 판단되면 블러처리 (A기능의 경우 욕설 판단을 서버에서 했으나 B기능은 iOS 머신러닝 모델을 통해 프론트에서 함)
3. 사진을 채팅창에 보여줌



### Backend

2주차와 동일



### 실행결과

![notcatpart](https://user-images.githubusercontent.com/35067611/90238891-a171b880-de61-11ea-837d-7051c3821127.gif)

![catpart](https://user-images.githubusercontent.com/35067611/90238744-6079a400-de61-11ea-85a0-68f36cfcac8f.gif)



### 참여자

신병기 조인택 문성주 서명렬 유시형 정재명 김석호 김영렬 백종근 임수현 강민석 이태경


# [릴프] 버디버디

# 👋🏻 4주차 - 예측 모델

---

## 🙈 참여자 및 역할 분담

## [CoreML] 구성원 🙊

S020 박태희 | S021 백종근 | S042 이진호 | S065 홍동현 | S015 류연수 | S044 임리나 

## [User Interface] 구성원 🙊

S026 송민관 | S030 양어진 | S055 조수정 |  S053 조기현 | S008 김병인

---

## 📌 기능 C - 추천 서비스

- 사용자의 관심사를 기준으로, 유사한 관심사를 선정 해준다.
- 유사한 관심사를 가진 사람과 랜덤으로 채팅이 가능하다.

## [User Interface]

- User id data에 관심사 항목 추가
- 추천 목록 서비스 페이지 작성

<img src = "https://user-images.githubusercontent.com/21030956/90867222-fcf6f580-e3cf-11ea-879d-545094970bf9.png" width = "400">

<img src = "https://user-images.githubusercontent.com/21030956/90867227-fff1e600-e3cf-11ea-966a-2d6ea4837295.png" width = "400">

## [CoreML]

- Hobby CSV 파일에 간단한 데이터 값을 만들어 학습

    5개의 관심사를 가진 8명의 데이터 값으로 학습을 진행함

    <img width="1512" alt="_2020-08-21__4 13 52" src="https://user-images.githubusercontent.com/21030956/90867444-57905180-e3d0-11ea-8b5a-f565c0a411ea.png">
<img width="1512" alt="_2020-08-21__4 14 12" src="https://user-images.githubusercontent.com/21030956/90867460-5d863280-e3d0-11ea-9f93-a95dc93c36eb.png">
    
Recommendations training
    
    <img width="300" alt="_2020-08-21__4 14 12" src="https://user-images.githubusercontent.com/21030956/90867511-742c8980-e3d0-11ea-8906-54ff92a9e26b.png">
    
    <img width="300" alt="_2020-08-21__4 14 12" src="https://user-images.githubusercontent.com/21030956/90867516-768ee380-e3d0-11ea-8467-82eabb6f7d95.png">
    
    <img width="300" alt="_2020-08-21__4 14 12" src="https://user-images.githubusercontent.com/21030956/90867518-77277a00-e3d0-11ea-848a-9c6064f514f1.png">
    
    <img width="300" alt="_2020-08-21__4 14 12" src="https://user-images.githubusercontent.com/21030956/90867520-77c01080-e3d0-11ea-852c-f2b9d0fbd9ad.png">




- 학습을 시킨 HobbyRecommendation ML 모델로 사용자의 관심사 값을 분석하여 추천

![Untitled 5](https://user-images.githubusercontent.com/21030956/90867525-7858a700-e3d0-11ea-8ae2-ac8b2798e7f3.png)

참고 자료 

[https://heartbeat.fritz.ai/build-a-core-ml-recommender-engine-for-ios-using-create-ml-e8a748d01ba3](https://heartbeat.fritz.ai/build-a-core-ml-recommender-engine-for-ios-using-create-ml-e8a748d01ba3)

## [Database]

- Flask를 활용해 signup, favorites를 구현
- Database는 h2 사용

```python
@app.route('/signup', methods=['POST'])
def signup():
    data = request.get_json()
    user_id = data.get("userId")
    favorites = data.get("favorites")
    userdata[user_id] = favorites

    return jsonify(data)

@app.route('/favorites', methods = ['GET'])
def favorites():
    user_id = request.args.get('userId',"test")
    # print(userdata[user_id])
    return userdata[user_id]
```
