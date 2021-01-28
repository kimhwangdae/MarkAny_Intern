# MarkAny_Intern
------------
## Issue
<img src="https://user-images.githubusercontent.com/59689327/106101776-baf18d00-6181-11eb-911b-76e849e622e4.PNG" width="40%"><br>
<img src="https://user-images.githubusercontent.com/59689327/106101782-bc22ba00-6181-11eb-98ae-6bba27633785.PNG" width="40%"><br>

 현재 CCTV Object detection 에 가장 많이 활용되고 있는 Yolu 4 에 올라온 Issue이다.<br>
이 Issue의 내용은 대략적으로 Yolo 4를 이용하여 Object detection 뿐만 아니라, Object Traking까지 가능할 수 있다고 말하고있다.<br>
이 Issue에 대한 내용을 공부해보자.<br>
 
-----------
### 01-28 
#### 1. Cos Similarity
 먼저, 객체를 tracking 하기위해서는 Cos Similarity를 알아야할 필요가있었다.<br>
 CoS Simliarity란, 두백터의 코사인 백터값을 구하는 것인데,<br>
 이것이 1에 가까울 수록 두 벡터의 방향은 같아지고,<br>
 -1에 가까워 질수록 두 벡터의 방향은 정반대가 되어진다.<br>
 Cos Simliarity의 수식과 Cos Simliarity의 결과에 따른 방향은 이렇다.<br>
![코사인 유사도 식](https://user-images.githubusercontent.com/59689327/106098019-a8745500-617b-11eb-8fbd-712295f9dfb9.PNG)<br>
![코사인 유사도 그래프](https://user-images.githubusercontent.com/59689327/106098014-a7432800-617b-11eb-81ae-ca388827af1e.PNG)<br>
이러한 Cos Simliarity의 개념을 이용하여 객체를 tracking 할 수 있을지 모른다는것이 AlexeyAB/darknet 에 올라온 issues 이다.<br> 
#### 2. Deep Sort
 Tracking Model은 이미 존재한다.<br>
 아래 영상은 Deep Sort라는 알고리즘을 이용해 객체를 추적하는 영상이다.<br>
[![DeppSort](http://img.youtube.com/vi/bkn6M4LAoHk/0.jpg)](https://www.youtube.com/watch?v=bkn6M4LAoHk&feature=youtu.be) <br>
Deep Sort Model을 요약하자면 이렇다.<br>
최근 object detection의 진보로 인해 tracking-by-detection 은 multiple object tracking에서 leading paradigm이 되었다.<br>
Deep SORT는 이미지 공간에서 ``Kalman filtering``을 수행하고 bounding box overlap을 측정하는 association metric과 함께 ``Hungarian method``를 사용하여 frame-by-frame data association을 수행하는 더 간단한 framework이다.<br>

``Kalman filtering`` :잡음이 포함된 측정치를 바탕으로 상태를 추정하는 재귀 필터. 예측, 업데이트의 두단계로 이루어짐. 예측 단계에서 현재 상태 변수의 값과 정확도를 예측하고, 실제 측정값이 들어오면 업데이트 단계에서 차이를 반영해 현재의 상태 변수를 업데이트 한다.<br>
