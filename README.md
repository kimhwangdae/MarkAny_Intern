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

``Kalman filtering`` : 잡음이 포함된 측정치를 바탕으로 상태를 추정하는 재귀 필터. 예측, 업데이트의 두단계로 이루어짐. 예측 단계에서 현재 상태 변수의 값과 정확도를 예측하고, 실제 측정값이 들어오면 업데이트 단계에서 차이를 반영해 현재의 상태 변수를 업데이트 한다.<br>

``Hungarian method``: 내가 이해한대로 Deep Sort에 사용된 Hungarian method 방법을 설명한다면, 찾아낸 객체에 대해 각각 다른 숫자를 부여하는 방법이다.

-------------
## 01-29
#### 1.LSTM
* RNN<br>
LSTM을 공부하기전에 RNN에 대해 먼저 공부하고 넘어갈 필요가 있다.<br>
RNN의 개념은 이렇다. 인간이 생각할때 모든 생각을 밑바닥부터 생각하지 않는다.<br>
인간은 이전에 했던 학습 또는 경험을 바탕으로 생각을 하게되고 생각이 나아가게 된다.<br>
이러한 아이디어에 착안하여  RNN이 개발되었다.<br>
<BR>RNN이미지<BR>
RNN 모델은 이전에 학습 했던 정보를 이후 데이터에 전달하여, 이전 데이터가 이후 데이터의 정보에 영향을 미치게 하는 개념이다.<br>
**이러한 RNN모델은 언어 모델링,번역, 등에서 굉장이 큰 성과를 거뒀지만, 시각의 격차가 커질수록 혹은 문장의 길이가 길어질수록, 데이터가 커질수록 예전 데이터들이 현재의 데이터에 주는 영향은 작아 진다.**<br>
이러한 RNN모델이 단점을 해결하기 위해 나온것이 LSTM 이다.
* LSTM<br>
LSTM 또한 RNN과 비슷한 Chain 구조의 형태를 띄고 있다.<br>
하지만 기존 RNN과 달리, **Cell state**라는 개념을 도입하여 긴 시간 동안의 정보를 기억하는 것을 모델의 기본적인 기능으로 설계하였다.<br>
**Cell state**는 컨베이어 벨트와 같아서, 작은 linear interation만 적용 시기키면서 전체 체인 구조를 활성화 시킨다.<br>
<br> Cell state 이미지<br>
위의 사진의 시그마 표시의 박스를 gate라고 하는데 이 gate는 sigmoid layer와 pointwise 곱셈으로 이루워져있다. <br>
<br> LSTM GATE 이미지<br>
sigmoid layer에서는 0과 1사이의 숫자를 내보내는데, 0에 가까울수록 다음 데이터에 전달되는 정보가 적어지고, 1에 가까울수록 많아진다.<br>
이 첫번째 GATE에서는 이전의 데이터를 0 ~ 1 사이의 값으로 정해 어떤 정보를 저장하고 버릴것인지 결정하는 역할을 한다.<br>
<br> 첫번쨰 LSTM 이미지<br>
LSTM의 두번째 단계는 새로들어오는 데이터를 어떤 데이터를 cell state에 저장할것인지 에대한 게이트이다.<br>
첫번째 gate와 마찬가지로 sigmoid layer를 거친뒤에 어떤 값을 업데이트할것인지 정하고, 그다음 tanh layer에서 새로운 후보 값들의 vector를 만든다.(임베딩)<br>
이후 각 layer에서 만들어진 vector들을 * 연산하여 cell state에 얼마나 업데이트할지 결정하는 scale한 값을 만든다.<br>
<br> 세번쨰 이미지<br>
마지막 세번째 단계는 cell state의 값을 tanh layer를 거치게 하고, 새로운값을 sigmoid layer에 거치게하여 * 연산한 후, 다음 cell state에 전달한다.

이런식으로 LSTM은 시계열 정보를이용할수 있다. 



