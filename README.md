# Kaggle_Aerial_Cactus_Identification
https://www.kaggle.com/competitions/aerial-cactus-identification/overview

참고: https://www.kaggle.com/code/werooring 

## 1 경진대회 이해
목표: 항공사진에서 선인장 식별하기

Data:

![image](https://github.com/user-attachments/assets/5084b8f1-9553-4576-a0e0-9d08789ed0bd)

- train.zip: 훈련 이미지 데이터 (jpg)
- test.zip: 테스트 이미지 데이터 (jpg)
- train.csv: 훈련 이미지 데이터 파일명 및 타깃값 (0 or 1)

  ![image](https://github.com/user-attachments/assets/197afe7e-5ddf-4e30-9a57-2a8e01c94ff9)

- samole_submission.csv: 샘플 제출 파일

  ![image](https://github.com/user-attachments/assets/fbd2ab23-7057-4c74-839c-f2aa5b2ea73d)


## 모델링 전략
- 베이스라인 모델: 얕은 CNN
- - 신경망 구조: 합성곱x2, 풀링, 평탄화, 전결합
  - 옵티마이저: SGD
- 성능 개선: 살짝 깊은 CNN
- - 데이터 증강: 다양한 변환기 사용
  - 신경망 구조: 합성곱x5, 배치 정규화, 풀링, 평탄화, 전결합x2
  - 옵티마이저: Adamax
  - 기타: 훈련 에포크 수 증가
