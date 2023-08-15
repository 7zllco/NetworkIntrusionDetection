# Network Intrusion Detection

##Ⅰ.프로젝트 목표
• 제공된 데이터셋을 바탕으로 네트워크 트래픽 분석
• 네트워크 침입 탐지 AI 모델 구축
• 구축한 모델을 이용해 악성 패킷 탐지

##Ⅱ. 데이터 전처리 과정
###<데이터 분석 내용>
• Malicious 데이터셋에 TCP, FTP 패킷만 존재
• 비어있는 feature 다수 존재
• Training Set으로 병합 시 Malicious와 Benign 구별 어려움
<img width="776" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/de2b6d9c-9e4b-4c0b-9fe5-a013e2257c1a">


###<데이터 전처리>
• TCP, FTP 프로토콜에 해당하는 패킷 추출
• NaN 값을 0으로 초기화
• Label을 표시할 Column 추가

##Ⅲ. 모델 선정 과정
###<Logistic Regression>
특징 : Sigmoid 함수를 통해 확률을 0에서 1 사이의 값으로 예측하고, 그 확률에 따라 가능성이 더 높은 범주에 속하는 것으로 이진 분류
문제점 : Malicious 패킷과 Benign 패킷의 데이터 수가 매우 불균형해 정확도가 매우 높음에도 실제로는 모델이 기능하지 못했음
<img width="284" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/5911d748-94f4-4a64-978a-11bd1f241b7d">
해결방안 : Benign 패킷을 랜덤으로 Under Sampling 및 데이터 Weight Balancing
<img width="626" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/3bddfb26-4ed0-4a4c-9440-706c04a02269">
정확도 : 94.4%

###<Random Forest>
특징 : 특정 Feature 에 대한 질문을 기반으로 데이터를 분리하는 방법으로 분류 및 회귀 문제에 모두 사용 가능

###<CNN>
특징 : Convolution과정을 거쳐 가중치의 개수를 줄이고, 국부 영역에 대한 특징에 집중 할 수 있음

