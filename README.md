# MarkAny_Intern
------------
## 01-28 
### 1. Cos Similarity
 먼저, 객체를 tracking 하기위해서는 Cos Similarity를 알아야할 필요가있었다.<br>
 CoS Simliarity란, 두백터의 코사인 백터값을 구하는 것인데,<br>
 이것이 1에 가까울 수록 두 벡터의 방향은 같아지고,<br>
 -1에 가까워 질수록 두 벡터의 방향은 정반대가 되어진다.<br>
 Cos Simliarity의 수식과 Cos Simliarity의 결과에 따른 방향은 이렇다.<br>
![코사인 유사도 식](https://user-images.githubusercontent.com/59689327/106098019-a8745500-617b-11eb-8fbd-712295f9dfb9.PNG)<br>
![코사인 유사도 그래프](https://user-images.githubusercontent.com/59689327/106098014-a7432800-617b-11eb-81ae-ca388827af1e.PNG)<br>
이러한 Cos Simliarity의 개념을 이용하여 객체를 tracking 할 수 있을지 모른다는것이 AlexeyAB/darknet 에 올라온 issues 이다.<br> 
### 2. Deep Sort
 Tracking Model은 이미 존재한다. 아래 영상은 Deep Sort라는 알고리즘을 이용해 객체를 추적하는 영상이다.<br>
[![DeppSort](http://img.youtube.com/vi/bkn6M4LAoHk/0.jpg)](https://www.youtube.com/watch?v=bkn6M4LAoHk&feature=youtu.be) 
