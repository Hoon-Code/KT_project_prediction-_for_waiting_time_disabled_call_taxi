# 장애인 콜택시 대기시간 예측 
---
## 프로젝트 개요
- 주제 : 장애인 이동권 개선을 위한 장애인 콜택시 대기시간 예측
- 학습 과목 : 데이터전처리, 데이터분석, 머신러닝
- 데이터 출처 : <https://www.data.go.kr/data/15057705/openapi.do>
- 중점 사항 : 시계열 데이터 전처리, 단변량/이변량 분석, ML 모델링
- 프로젝트 목표 : 장애인 콜택시를 이용하는 고객들의 불편사항을 개선하고 서비스의 품질을 높이기 위해 콜택시 운행이 종료된 시점에 다음 날의 기상 예보를 바탕으로 기상 상황에 따른 장애인 콜택시의 평균 대기 시간을 예측하고 예상 대기시간을 제공할 수 있는 모델 완성
---

## 도메인 이해 
![image](https://github.com/user-attachments/assets/e98b8d49-f9b8-465f-b54a-70cced5fc309)
![image](https://github.com/user-attachments/assets/8b47a077-f8c3-441b-8d7c-6b5eb539cc30)
![image](https://github.com/user-attachments/assets/5b28fa39-52a6-4997-98ab-9653c477368f)
![image](https://github.com/user-attachments/assets/ce59a873-a7b3-4e52-8300-011d52d88683)
![image](https://github.com/user-attachments/assets/df600ce8-f2f1-4544-a668-e1e70d906a99)
![image](https://github.com/user-attachments/assets/450669e2-3a86-4a8d-92e3-8e156b8c3980)
---

## 데이터 소개 

![image](https://github.com/user-attachments/assets/7677a115-687a-446d-bfc5-1fb65c6c9236)

- 장애인 콜택시 운행정보
![image](https://github.com/user-attachments/assets/ef7247f2-b312-4568-a5b6-3b5c850d2f50)


- 날씨 정보
![image](https://github.com/user-attachments/assets/8e8bc27a-7185-4a1c-a433-8bfca16e1602)
---

## 핵심 사항 

![image](https://github.com/user-attachments/assets/e599475a-551a-43d4-8bbd-3b583e66d15f)

---
## 데이터 분석 및 전처리 
- 익일의 대기시간(waiting_time)을 오늘의 데이터를 활용해 예측해야 하는 대상(target)으로 설정

![image](https://github.com/user-attachments/assets/52a3736f-3010-472e-9eab-17dbf8932712)

- target과 다른 변수들간의 상관 관계 확인
![image](https://github.com/user-attachments/assets/a0ce28f3-c0cf-4ca9-bfa7-af58e8204c25)

- target 과 ride_rate간의 산점도
![image](https://github.com/user-attachments/assets/985a6c41-9619-4fb2-8ff3-db93022dd4a2)

- 운임요금과 요일별 target 산점도
![image](https://github.com/user-attachments/assets/79f7451e-c98b-4888-a9eb-ebf916de4bcf)

## 범주형 변수들과 target 간의 관계 
- 휴일 여부

![image](https://github.com/user-attachments/assets/b9dfa94c-bd2f-4aef-9032-9feef65e5ec2)
![image](https://github.com/user-attachments/assets/a6541f64-ebc7-4b24-b7dd-657e8f2d4f75)

- 요일
![image](https://github.com/user-attachments/assets/bfac29d0-d309-4791-83e2-a9b7b2c9d214)
![image](https://github.com/user-attachments/assets/a16833a9-ecf8-46ab-a12e-402c4f484685)

- 계절
![image](https://github.com/user-attachments/assets/04cd0b23-c46c-4c99-ace9-5564a7b0ff7d)
![image](https://github.com/user-attachments/assets/f422d2a8-0479-4942-99d4-6d5a534fb8c8)

## 변수 정리 
- 강한 관계의 변수 : waiting_time, MA_wt7, ride_rate, holiday
- 약한 관계의 변수 : car_cnt, fare, distance, weekday, season
- 관계가 없는 변수 : 나머지 변수들
---

## 모델링
1) 선형회귀 모델
![image](https://github.com/user-attachments/assets/1a111cf2-1b02-46fe-8e15-f9053f343552)
![image](https://github.com/user-attachments/assets/0dcd43de-e191-487a-b37e-78d04c2d58e9)

2) KNN
![image](https://github.com/user-attachments/assets/4988c501-3ce6-4d97-9365-1fb95338dcd9)
![image](https://github.com/user-attachments/assets/e60bb7b3-9417-442f-affa-6700eb5aa176)

3) RandomForestRegressor
![image](https://github.com/user-attachments/assets/b182ddd8-5e64-48bb-b424-d504f3dd781b)
![image](https://github.com/user-attachments/assets/4d84461f-e718-4714-9633-e6a09d7c4440)

4) XGB
![image](https://github.com/user-attachments/assets/c3d5b95b-90bb-4b27-9866-8636ffbab00d)
![image](https://github.com/user-attachments/assets/8eaf8d0a-4fc8-489e-90ec-7cfa1096edfc)

### *모델별 비교*
![image](https://github.com/user-attachments/assets/25a53a01-e73b-4330-ac3b-c0616484bb33)

- XGB, RF, LinearRegression 모델 성능 우수 확인

