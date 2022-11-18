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

...



### </br>3-2. Kospeech(STT)

음성 언어를 문자데이터로 전환(Speech-to-Text)

...



### </br>3-3. OpenWeather

날씨 정보 알려주는 통합 API

...



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

...





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

     

     

