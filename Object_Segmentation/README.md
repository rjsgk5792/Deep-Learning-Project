# 중고차 외관 손상(Scratch) 인식 알고리즘 구현

### 딥러닝 기술 연구 기업과 차량 외관 손상 인식 알고리즘 구현을 주제로 4주간 협업 프로젝트 진행
<br>

#### 사용 데이터
- 협업 기업 제공 차량 외관 손상 데이터 약 3000개
- AI HUB 차량 파손 데이터 약 13,000

#### 진행 일정
- 1주 : 데이터 라벨링 및 기술 스택 학습
- 2주 : 데이터 처리 및 알고리즘 구현
- 3주 : 알고리즘 구현 및 테스트

#### 사용 기술 스택
- PixelAnnotationTool (라벨링 툴)
- Pytorch, cv2, albumentations

#### 구현한 UNet Architecture

![image](https://user-images.githubusercontent.com/83709985/183290794-9db1a8b2-ac28-456e-b4e9-fbf45f77daf7.png)

#### 일부 코드
<img width="676" alt="image" src="https://user-images.githubusercontent.com/83709985/196980224-140d7eb3-1f6b-4ce0-a431-1520ad5a924c.png">


#### 사용한 방법
- image patching 을 통해 한 이미지를 여러 이미지로 분할 저장 후 학습
- 640 x 640, 1080 x 1440, 4000 x 3000 등 다양한 image size가 존재하여 이미지 크기 resizing 수행
- image augmentation을 통해 학습 데이터 확보
- One Hot Encoding을 통해 다양한 손상 형태 구분

#### 예측 결과 
<img width="361" alt="image" src="https://user-images.githubusercontent.com/83709985/196983517-8dd47051-2430-448a-9177-58229565e9e7.png">
<img width="261" alt="image" src="https://user-images.githubusercontent.com/83709985/196987626-a48a46b3-a736-42d6-af1d-aa7c0dbff977.png">


#### 미흡한 점
- GPU 성능과 이미지 저장 공간이 부족해 충분한 데이터로 충분한 학습을 시키지 못함
- 빛 반사 현상을 제거하기 위해 Gray scale로 바꾸어 학습했다면 더 좋은 성능 예상
- 손상 부위가 전체 이미지에 비해 상대적으로 작은 부위를 차지하기에 image patching 과정에서 손상 부위가 없는 이미지는 제거해야 함
- Learning rate와 Optimizer, Epochs 등 여러 가지 파라미터 튜닝을 시도하지 못한 것이 아쉬움
