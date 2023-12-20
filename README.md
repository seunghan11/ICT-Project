# ICT-Project
ICT 스마트해상물류 Project 주제: 입출입트럭 운전자확인 및 출입기록 관리
항만에서 입출입 운전자들에 대한 보안성 향상을 목적으로, 얼굴 검증	알고리즘을 사용하는 AI 모델을 사용한다.  
기존 얼굴인식 모델은 서양인 얼굴에 맞춰져 있어 한국인 얼굴에 대한 인식성능이 상대적으로 낮았다. 따라서 얼굴인식 모델에 AIHub에서 제공하는 한국인 얼굴 데이터 셋을 추가하고, 서양인과 비교되는 한국인의 특징을 추가하여 얼굴인식을 진행했다.  

## Paper site
https://koreascience.kr/article/CFKO202333855046587.page  <VGG-Kface : An Optimization Study on Korean Face Recognition Using VGG-Face>

## AI Hub Dataset
AI hub의 한국인 안면 이미지 dataset을 사용  
https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=83

## Model & Loss function
모델은 VGG Face를 사용했으며 기존 학습되어 있는 모델에 마지막 레이어만 학습시키는 전이 학습 방식을 채택했다.  
fork되어 있는 repository의 VGGFace 모델에 본 가중치를 적용시켰다. loss funcion은 triplet loss로 양성 image pair와 음성 image pair의 비율을 조정해가면서 최적화했다.
https://drive.google.com/file/d/1nYxqw-soLeMVI70QHpN9vMU7ZfO89iaG/view?usp=sharing

위 코드를 통해 학습한 가중치를 아래 코드에서 성능 평가를 진행했다.
Model performance는 same class와 different class 각각에 해당하는 데이터를 400개씩 샘플링하여 클래스 별 벡터 거리의 분포를 확인하고 모델의 성능 지표로 두 분포가 겹치는 영역의 넓이를 새로 제시했다.  
![image](https://github.com/seunghan11/ICT-Project/assets/88572826/fd7e4dab-dacf-478a-84f6-1c5fab7dab17)  
예시 이미지. same class:different class=6:4
