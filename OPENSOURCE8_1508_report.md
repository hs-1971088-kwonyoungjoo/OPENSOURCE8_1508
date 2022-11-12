### 박태범

### STT(Speech To Text)

## STT 오픈소스 링크

https://github.com/sooftware/kospeech

## STT란?

음성인식(Speech Recognition)이란 사람이 말하는 음성 언어를 컴퓨터가 해석해 그 내용을 문자데이터로 전환하는 처리를 말하며 STT(Speech-to-Text)라고도 한다.

## 활용분야

어학원 및 어학 컨텐츠: 외국어 교육 학원 및 컨텐츠 업체에 음성인식을 적용하여 발음 정확도 향상

네비게이션: 네비게이션의 목적지 검색 및 설정 시 음성으로 입력하는 기능

홈쇼핑: 자동 주문 시 물품 수령 주소에 대한 음성인식

채팅 서비스: 사용자의 음성을 인식하여 자동으로 채팅창에 입력하는 기능

## STT 오픈소스 중 Kospeech 모델 선정 이유

Kospeech는 2020년 김수환이라는 개발자가 공개한 한국어 음성인식 모델을 제공하는 오픈소스 툴킷이다. Kospeech의 모델들은 End-to-End 방식을 따르는데, 여기서 End-to-End는 음성 데이터가 포함하는 문법, 발음 등의 특징까지 모두 모델이 학습하도록 하는 방식을 말한다. 따라서 Raw audio를 통째로 input으로 넣어주는 것이 특징이다.
Pytorch 기반의 딥러닝 모델로 한국어만 지원하고 DeepSpeech2, Las, SpeechTransformer 등 다양한 모델과 프레임워크를 제공한다.
