---
layout: page
title: TOF 카메라를 이용한 제스처 인식기술 개발
description: (주)와이즈오토모티브 산학협력 프로젝트, 2020.12~2021.3
img: assets/img/project1_thumbnail.gif
importance: 3
category: work
---

> Time of Flight(TOF) 카메라를 통해 물체와의 거리 정보를 활용하여 얼굴 제스처 인식 알고리즘 기술 개발 <br/> _2020.12 ~ 2021.3_

<br/>
<br/>

Role:

Depth 이미지 데이터 패턴 분석 (Matlab)
제스처 인식 알고리즘 개발 (C++, OpenCV)

<br/>
<br/>

Action to Result 1:

Optical Flow의 연산량을 줄이기 위한 ROI 영역 감지 알고리즘 개발
사람이 움직이면서 ROI 영역을 벗어나는 경우 영역을 보정하는 기능 추가

<br/>
<br/>

Action to Result 2:

고개를 움직이는 순간의 Optical Flow Y축 벡터 데이터 분석 후 제스처 패턴 파악
ROI 영역 내에서 Optical Flow Y값이 특정 Threshold를 넘을 때 위(+), 아래(-), 정면(0)의 3가지 경우로 분류
매 프레임마다 3가지 경우를 Key로 입력한 뒤 제스처 Serial Key가 완성될 때 마다 제스처 인식

<br/>
<br/>

Achievements:

선행 연구의 알고리즘보다 인식률 및 속도 향상
본 연구 성과물로 기술 입찰
