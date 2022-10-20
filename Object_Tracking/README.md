# Object detection with Transformer


![image](https://user-images.githubusercontent.com/83709985/196996040-6440f0fc-36d0-4b95-a4cb-883995bf0d7f.png)


## 주제

ViT 모델 중 DETR 알고리즘과 기존 객체 검출 알고리즘인 YOLO v4 알고리즘의 객체 검출 성능 비교

## 배경

대부분의 image detection은 CNN 구조를 사용하는 반면, NLP 분야에서 인기있는 Transformer 기반의 DETR 모델은 기존의 RPN, NMS의 과정이 필요 없는 direct set prediction 방식의 end-to-end 모델로서 간결한 구조를 가지고 있습니다. 이러한 모델 특징으로 객체 탐지 속도 개선 가능성을 기대하고 DETR 모델을 구현했습니다.

## 수행 내용
- 데이터
    - YOLO v4
        - COCO 데이터셋으로 pre-trained 된 가중치 사용하여 학습
        - test 데이터로는 MOT17 데이터셋에서 시내 주행 영상을 VideoCapture한 이미지
    - DETR
        - COCO 데이터 셋으로 학습
        - 백본 네트워크로 RESNET 사용
        - test 데이터로는 MOT17 데이터셋에서 시내 주행 영상을 VideoCapture한 이미지
- Pytorch, OpenCV, Google Colab의 GPU를 통해 모델 개발 및 학습을 진행 
- COCO 데이터 셋으로 pre-trained 된 가중치를 사용해 학습을 진행 
- FPS 성능 지표 기준으로 높은 성능을 보이는 YOLO v4 detection 모델 구현 및 ViT 모델과의 성능을 비교

## 수행 결과
![image](https://user-images.githubusercontent.com/83709985/196995694-165cf7a8-084e-43a9-ac9a-b46a51936939.png)

YOLO 모델이 약 15배가량 FPS 성능이 높게 나오는 결과를 얻었습니다. 


## Reference
YOLO v4 + DEEPSORT : https://github.com/theAIGuysCode/yolov4-deepsort/tree/9e745bfb3ea5e7c7505cb11a8e8654f5b1319ad9

DETR : https://arxiv.org/pdf/2005.12872v3.pdf

## 아쉬운 점
- Transformer 모델 특성상 많은 데이터의 학습이 동반되어야 큰 물체에서 효과적인 객체 탐지 성능을 발휘하는데 이 점을 충족시키지 못했기 때문에 YOLO 모델보다 낮은 성능을 보여줬을 것이라 예상
- Transformer 기반의 MOTR 객체 추적 알고리즘까지 구현하고 싶었지만 시간 상의 이유로 구현하지 못함
- 사전 학습된 가중치가 아닌 실제 데이터로 학습시켜 객체 탐지를 수행하지 못해 아쉽지만 짧은 시간 내에 객체 탐지에는 성공해서 만족스러운 결과
