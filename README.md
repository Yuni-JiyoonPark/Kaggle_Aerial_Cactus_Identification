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



---------------------------------------------------------------------------------------------------

###에러 ㅓㅓㅓㅓㅓㅓ

error                                     Traceback (most recent call last)
Cell In[70], line 7
      4 epoch_loss = 0 # 에폭별 손실값 초기화
      6 # '반복 횟수'만큼 반복 
----> 7 for images, labels in loader_train:
      8     # 이미지, 레이블 데이터 미니배치를 장비에 할당 
      9     images = images.to(device)
     10     labels = labels.to(device)

File c:\Users\Admin\miniconda3\envs\myGPU\lib\site-packages\torch\utils\data\dataloader.py:701, in _BaseDataLoaderIter.__next__(self)
    698 if self._sampler_iter is None:
    699     # TODO(https://github.com/pytorch/pytorch/issues/76750)
    700     self._reset()  # type: ignore[call-arg]
--> 701 data = self._next_data()
    702 self._num_yielded += 1
    703 if (
    704     self._dataset_kind == _DatasetKind.Iterable
    705     and self._IterableDataset_len_called is not None
    706     and self._num_yielded > self._IterableDataset_len_called
    707 ):

File c:\Users\Admin\miniconda3\envs\myGPU\lib\site-packages\torch\utils\data\dataloader.py:757, in _SingleProcessDataLoaderIter._next_data(self)
    755 def _next_data(self):
    756     index = self._next_index()  # may raise StopIteration
...
     23 label = self.df.iloc[idx, 1]     # 이미지 레이블(타깃값)
     25 if self.transform is not None:

error: OpenCV(4.11.0) D:\a\opencv-python\opencv-python\opencv\modules\imgproc\src\color.cpp:199: error: (-215:Assertion failed) !_src.empty() in function 'cv::cvtColor'



---------->>>>> google colab에서 run하니까 됨!
