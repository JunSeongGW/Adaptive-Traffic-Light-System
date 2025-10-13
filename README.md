# Adaptive Traffic Light System (ROS2 + YOLOv8 + DeepSORT)

[![ROS2](https://img.shields.io/badge/ROS2-Humble-blue)](https://docs.ros.org/en/humble/)
[![Python](https://img.shields.io/badge/Python-3.10+-yellow)](https://www.python.org/)
[![DeepSORT](https://img.shields.io/badge/Detector-YOLO-green)](https://github.com/MuhammadMoinFaisal/YOLOv8-DeepSORT-Object-Tracking)
[![DeepSORT](https://img.shields.io/badge/Tracker-DeepSORT-green)](https://github.com/MuhammadMoinFaisal/YOLOv8-DeepSORT-Object-Tracking)

---

## 프로젝트 개요

 본 프로젝트는 **교차로의 실시간 교통 상황을 인식하여 신호 주기를 자동으로 조정하는 적응형 신호등 시스템(Adaptive Traffic Light System)** 입니다.  
USB 카메라로부터 입력된 실시간 영상을 **ROS2 (Humble)** 환경에서 수신하고,  
[Muhammad Moin Faisal의 YOLOv8 + DeepSORT 오픈소스 프레임워크](https://github.com/MuhammadMoinFaisal/YOLOv8-DeepSORT-Object-Tracking)를 기반으로  
차량 및 보행자 객체를 탐지·추적합니다.  
이를 바탕으로 **교통 점수를 계산하여 신호 상태를 시각화(빨강/초록)** 하는 시스템입니다.

<p align="center">
  <img src="docs/system_architecture.png" width="720">
</p>

---

## 주요 기능

- **USB 카메라 영상 입력**  
  - ROS2 `/camera/image_raw` 토픽으로 영상 수신  

- **객체 탐지 (YOLOv8)**  
  - YOLOv8 모델을 통해 차량 및 보행자 탐지  

- **객체 추적 (DeepSORT)**  
  - [YOLOv8-DeepSORT-Object-Tracking](https://github.com/MuhammadMoinFaisal/YOLOv8-DeepSORT-Object-Tracking)을 활용하여  
    동일 객체를 프레임 간 ID로 추적 (중복 계수 방지)  

- **대기시간 및 점수 계산**  
  - 교차로 내부(정지선, 횡단보도) 체류시간 기반 평균 대기시간 계산  

- **교통상황 점수화 알고리즘**
  - 차량 수, 보행자 수, 평균 대기시간을 기반으로 가중 합산하여 점수 계산

- **신호 상태 시각화 (Visualization)**  
  - OpenCV를 이용해 영상에 빨강·초록 색상 바를 오버레이  

- **ROS2 기반 모듈형 구조**  
  - 각 노드(detector, tracker, scorer, visualizer)가 독립적으로 동작  

---


