# Network Intrusion Detection

## Ⅰ.프로젝트 목표<br>
• 제공된 데이터셋을 바탕으로 네트워크 트래픽 분석<br>
• 네트워크 침입 탐지 AI 모델 구축<br>
• 구축한 모델을 이용해 악성 패킷 탐지<br>
<br>

## Ⅱ. 데이터 전처리 과정<br>
### <데이터 분석 내용><br>
• Malicious 데이터셋에 TCP, FTP 패킷만 존재<br>
• 비어있는 feature 다수 존재<br>
• Training Set으로 병합 시 Malicious와 Benign 구별 어려움<br>
<img width="776" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/de2b6d9c-9e4b-4c0b-9fe5-a013e2257c1a"><br>
<br>

### <데이터 전처리><br>
• TCP, FTP 프로토콜에 해당하는 패킷 추출<br>
• NaN 값을 0으로 초기화<br>
• Label을 표시할 Column 추가<br>
<br>

## Ⅲ. 모델 선정 및 결과<br>
### <Logistic Regression 모델><br>
• 특징 : Sigmoid 함수를 통해 확률을 0에서 1 사이의 값으로 예측하고, 그 확률에 따라 가능성이 더 높은 범주에 속하는 것으로 이진 분류<br>
• 문제점 : Malicious 패킷과 Benign 패킷의 데이터 수가 매우 불균형해 정확도가 매우 높음에도 실제로는 모델이 기능하지 못했음<br>
<img width="284" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/5911d748-94f4-4a64-978a-11bd1f241b7d"><br>
• 해결방안 : Benign 패킷을 랜덤으로 Under Sampling 및 데이터 Weight Balancing<br>
<img width="626" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/3bddfb26-4ed0-4a4c-9440-706c04a02269"><br>
• 정확도 : 94.4%<br>
<br>

### <Random Forest 모델><br>
• 특징 : 특정 Feature 에 대한 질문을 기반으로 데이터를 분리하는 방법으로 분류 및 회귀 문제에 모두 사용 가능<br>
• 문제점 : 달리 파라미터 튜닝을 거치지 않아도 매우 높은 성능 보였음<br>
<img width="296" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/f98e9115-45b2-45f1-ab63-2f027e85947c"><br>
• 정확도 : 99.9%<br>
<br>

### <CNN 모델><br>
• 특징 : Convolution과정을 거쳐 가중치의 개수를 줄이고, 국부 영역에 대한 특징에 집중 할 수 있음<br>
• 문제점 : Feture의 수가 매우 적어 단순한 데이터이고, 서로간의 연관성이 적어 제대로 된 성능 발휘 힘듦<br>
<img width="120" alt="image" src="https://github.com/7zllco/NetworkIntrusionDetection/assets/90850532/204a67db-eabc-46f3-bbb8-83599cd8a4d9"><br>
• 정확도 : 89.0%<br>
<br>



