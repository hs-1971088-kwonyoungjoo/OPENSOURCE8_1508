* 설계서 12/4 최종 마감

<hr>

</br>

# 시스템 설계서

## 1.서비스

### 1-1. 개요

한성대 학생을 위한 통합 챗봇 서비스

### 1-2. 서비스 소개

학교 생활에 도움이 되는 여러 기능을 제공받을 수 있는 챗봇 서비스이다.

학교식당 메뉴, 교통정보, 날씨정보를 제공하고, 모든 기능에는 오픈소스가 활용되었다.

추가로 음성입력, 번역 기능을 제공함으로 이용 대상과 편의성을 확장시켰다.


## </br>2. 유사 서비스

https://medium.com/naver-cloud-platform/%EA%B0%84%EB%8B%A8-%EC%B1%97%EB%B4%87-%EB%A7%8C%EB%93%A4%EA%B8%B0-%EC%B1%97%EB%B4%87-%EC%84%9C%EB%B9%84%EC%8A%A4%EB%A5%BC-%EA%B8%B0%ED%9A%8D%ED%95%A0-%EB%95%8C-%EB%B0%98%EB%93%9C%EC%8B%9C-%EA%B3%A0%EB%A0%A4%ED%95%B4%EC%95%BC-%ED%95%98%EB%8A%94-4%EA%B0%80%EC%A7%80-70d66108e434



## </br>3. 오픈소스 소프트웨어

### </br>3-1. Kochat

한국어 목적지향 챗봇 프레임워크

### 조사자: 박수훈

Kochat: 한국어 목적지향 챗봇 프레임워크
-------------------------------------

## Kochat이란?
Kochat은 한국어 전용 오픈소스 목적지향 챗봇 프레임워크이다. <br>
목적지향 챗봇은 일정 관리, 호텔/식당/항공권 등의 예약, 음악 듣기 등 명령 전달, 콜센터 상담 등과 같은 특정된 목적을 달성하기 위해 사용되는 챗봇을 말한다.

## Kochat을 선정한 이유
초보자가 연구자들의 소스코드를 활용하여 챗봇을 만들 때, 각각의 모듈을 구현하는 것은 어려우며, 이러한 모듈을 연결하여 파이프라인을 형성하는 것도 많은 전문성을 요한다. 따라서 이들이 목적지향 챗봇을 구현할 때는 직접 모든 모듈을 구현하기보다는 챗봇 빌더나 오픈소스 프레임워크를 활용하는 것이 일반적이다. <br>
이 중 챗봇 빌더의 경우, 대부분 과금 정책을 적용하고 있기 때문에 무료로 목적지향 챗봇을 개발하려면 오픈소스 프레임워크를 이용해야 한다. 현재까지 몇몇 오픈소스가 출시되었지만 주로 영어를 위주로 개발되어 왔고, 한국어를 처리하기 위해서는 복잡한 과정을 거쳐야만 한다. <br>
Kochat은 오픈소스 챗봇 개발 프레임워크이기 때문에 머신러닝 개발자라면 누구나 무료로 한국어 챗봇을 개발할 수 있다. <br> 또한 Kochat은 일반인을 타깃으로한 챗봇빌더보다는 개발자를 타깃으로한 프레임워크로 프레임워크에 본인만의 모델을 추가할 수 있고, Loss 함수를 바꾸거나 새로운 기능을 첨가할 수 있다. <br>
이에 따라, 한국어 전용 목적지향 챗봇 프레임워크인 Kochat을 사용하게 되었다.
## Kochat 프레임워크에 대해
Kochat 은 데이터세트, 임베딩, 인텐트, 폴백, 엔티티, 슬롯필링+API, 시각화 등의 모듈로 구성된다.

+ 데이터 세트 모듈 <br>
  사용자의 입력 데이터를 전처리하기 위한 모듈이다. 사용자로부터 문장이 입력되면 네이버 맞춤 검사기를 이용하여 오탈자를 교정한 뒤, 품사를 기반으로 토큰화를 진행한다.
+ 임베딩 모듈 <br>
  데이터 전처리 이후에 임베딩 모듈을 통해 워드 임베딩을 수행한다.
+ 인텐트 모듈 <br>
  사용자 발화의 의도를 파악하기 위해 사용된다.
+ 폴백 모듈 <br>
  정해진 도메인 이외의 문장이 입력된 경우, “잘 모르겠어요.”와 같은 문장을 반환하여 대화가 지정된 도메인 안에서 진행되게 유도한다.
+ 엔티티 모듈 <br>
  문장 내에 존재하는 개체명을 인식하기 위해 사용된다. 예를 들어 “수요일 부산 날씨 어때?”라는 문장이 주어지면, ‘수요일’을 날짜(DATE)로, ‘부산’을 장소(LOCATION)로 인식한다.
+ 슬롯필링 + API 모듈 <br>
  슬롯필링은 목적지향 챗봇 구현시 주로 이용되는 기법이다. 먼저 인텐트 모듈을 통해 슬롯을 고르고, 엔티티 모듈을 통해 해당 슬롯을 채운다. 마지막으로 API 를 호출하여 사용자에게 정보를 제공할 수 있다. 예를 들어, 사용자가 “수요일 부산 날씨 어때?”라는 문장을 입력하면 인텐트 모듈은 이 문장을 날씨에 관련된 문장으로 분류하여 여러 슬롯 중, 날씨 API 를 호출하기 위한 슬롯을 선택한다.
+ 시각화 모듈 <br>
  사용자는 별도의 설정 없이 여러가지 시각화 자료를 제공받을 수 있다.
+ 사용자 인터페이스
  사용자는 아래와 같이 사용하기 쉬운 인터페이스를 통해 자신만의 챗봇을 구축할 수 있다.


    출처: 고현웅 외 2명. (2021). Kochat: 한국어 목적지향 챗봇 프레임워크. ACK 2021 학술발표회 논문집, 28(2), pp. 596-599.

> 오픈소스 소스코드와 문서: https://github.com/hyunwoongko/kochat


    Copyright 2020 Hyunwoong Ko.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.



### </br>3-2. Kospeech(STT)

음성 언어를 문자데이터로 전환(Speech-to-Text)

...


### <br>이찬우<br>
***
### </br>3-3. OpenWeather

### <br>:sunny: __찾은 Open-source Link__ : https://openweathermap.org/api

### <br>:ledger: __오픈소스 이름__ : OpenWeather (전 세계 날씨 정보를 알려주는 통합 API)

### <br>:question: __오픈소스 선정이유__ : 해당 API는 전 세계의 개발자들이 활용하여 정확도가 높다고 판단해 선정했습니다.

### <br>:open_mouth: __해당 오픈소스 특징__ : <br>
* JSON 형태로 다양한 언어를 활용해 서비스를 제작할 수 있다.

* 국가, 도시명으로 분류하는 것이 아닌 위도와 경도의 수치로 해당 위치에 대한 정보를 주어 특정 위치의 데이터를 얻기가 수월하다.
  
* 다양한 개발자의 커스텀된 자료와 융합을 할 수 있다.
  
* 온도뿐만이 아닌 미세먼지 정보도 호출할 수 있다.

### <br>🔧 __해당 오픈소스 기능__ : Free Plan 기준으로 작성<br>
* 현재 날씨 데이터
* 날씨 예보 (5일 동안)
* 기본 날씨 지도
* 날씨 대시보드
* 대기오염 API
* 지오코딩 API (지리적 위치와 좌표로 검색)
* 날씨 위젯
   
### <br>:bulb: __오픈소스 활용 방안__ : 
1. 현 거주지의 날씨 정보 및 학교 주변의 날씨, 대기오염을 알려주어 <br>
   등하교 시의 날씨로 인한 불편함을 없게 한다.
   
2. 날씨 위젯을 활용하여서 한 눈에 날씨 정보를 알 수 있도록 한다.
<br><br>

### 📝 __라이선스__ : __ODbL__ (Open Database License)
Free와 Startup plan에 한 함.<br><br>

### __API를 이용한 Demo Web Page__
...

***



### </br>3-4. Scrapy

#### 1. 오픈소스 링크 

https://github.com/scrapy/scrapy

#### 2. Scrapy란?

웹 데이터 수집 가능한 오픈소스 웹 크롤링 프레임워크

#### 3. Scrapy 사용목적

학교 홈페이지에 제시되어 있는 학생식당, 교직원식당의 식단내용을 스캔&저장후 제공한다.

#### 4. Scrapy 선정 이유 

1. js가 사용되지 않은 홈페이지의 식단표 정보를 수집하기에는, 여러 크롤러중 가장 가벼운 Scrapy가 유리함.
2. 많은 활용 사례로 인해 커뮤니티가 활성화 되어, 개발에 대한 용이성.

#### 5. Scrapy의 특징

* <strong>GitHub의 스타 수 45.1k 개로, 현재까지 활발히 개발</strong>되고 있는 크롤러
* 비동기 네트워킹 라이브러리(asynchronous networking library)인 [Twisted](https://twistedmatrix.com/trac/)를 기반으로 매우 우수한 성능 발휘.
* 페이지 렌더링을 위해 필요한 js, image 파일 등을 조회하지 않고 <strong>지정된 URL만 조회함으로 기타 크롤러 대비 가볍고 빠른 성능</strong> 발휘.
* XPath, CSS 표현식으로 HTML 소스에서 데이터 추출 가능.
* 미들웨어 추가나 파이프라인 연결의 용이성으로 우수한 확장성.
* javascript 지원 불가로 인해 동적 웹페이지 정보 수집 불가.

#### 6. LICENSE

BSD 3-Clause "New" or "Revised" License ([참고](https://github.com/scrapy/scrapy/blob/master/LICENSE))



### </br>3-5. ODsay LAB

대중교통 API

...



### </br>3-6. Kakao Maps API

지도

...



### </br>3-7. koNLpy

한국어 형태소 분석으로  문장 내의 키워드 추출

...



### </br> 3.8 파파고

번역 오픈소스

# 보고서 작성 
### 이선영

<hr>

### :link: 오픈소스 링크 : https://developers.naver.com/docs/papago/papago-nmt-api-reference.md

### :mag: 오픈소스 이름 : 파파고

### :sunny: 오픈소스 선정이유 
* 교내에서 사용되는 챗봇이기에 해외 교환학생과 같은 외국인 학생을 위한 번역기능이 필요하다고 판단했습니다.


### :heavy_check_mark: 오픈 소스 특징
- 파파고는 다국어 언어 처리에 대한 네이버의 기술과 경험을 번역 엔진에 적용해 보다 정확한 번역 결과를 제공하는 서비스입니다. 파파고가 제공하는 RESTful 형태의 API를 사용하면 서비스에 번역 기능을 간단하게 적용할 수 있습니다.

	- **Papago 번역**: 파파고의 인공 신경망 기반 기계 번역 기술(NMT, Neural Machine Translation)로 텍스트를 번역한 결과를 반환하는 RESTful API입니다.
	- **언어 감지**: 입력된 텍스트의 언어를 감지해 주는 RESTful API입니다.
	- **한글 인명-로마자 변환**: 한글로 된 이름을 로마자 표기로 변환한 결과를 반환하는 RESTful API입니다.

### :bulb: 오픈소스 활용 방안
-  STT로 추출 된 텍스트 혹은 입력된 텍스트를 kochat 프레임워크에 번역처리 과정을 거쳐 사용자에게 적합한 언어로 변환 후 최적의 답변을 제공
	- EX) **How to go Hansung university?** 라는 질문이 입력되면 **한성대학교에 어떻게 가나요?** 로 번역되어 챗봇 프레임워크인 **kochat**에 전송하여 답변을 사용자 맞춤 언어로 변환하여 사용자에게 제공





## </br>4. DFD

...





## </br>5. 시나리오

* 사용자는 채팅창에서 챗봇과 대화할 준비를 한다.

* 음성 입력 버튼을 눌러, 채팅 대신 음성으로도 챗봇 이용이 가능한다.

* 요청 문장(음성)을 입력한다.

  1. 음성을 입력했다면 Kospeech을 통해 문자 데이터로 전환한다.
  2. 요청 문장(음성)이 외국어라면 한국어로 번역한다.

* Kochat을 통해 문장(키워드)을 분석한다.

  1. 날씨

     OpenWeather를 이용해 해당 날씨 정보 return

  2. 식당

     Scrapy를 통해 생성한 식단DB에서 요청에 맞는 식단 정보 return

  3. 교통

     대중교통 시간표나 도착시간 return
