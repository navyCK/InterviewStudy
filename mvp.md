# Android로 MVP 사용하기


<img src="https://thdev.tech/images/posts/2016/10/Android-MVP-Intro/MVP.png">

Model, View, Presenter 간 상호 의존성을 떨어뜨리기 위해,
Test Code 작성을 위한 최적의 구조인 MVP를 사용한다.


다른 패턴에 비해 MVP는 각각 독립된 코드의 구현이 가능하다.

View를 완전히 분리하기.



### MVP란?

* Model : 데이터와 관련된 처리 담당
    + 데이터의 전반적인 부분을 모델에서 담당하고, 네트워크, 로컬 데이터 등을 포함한다.

* View : 사용자의 실질적인 이벤트 발생, 이를 처리 담당자인 Presenter로 전달
    + 완전한 View의 형태를 가지도록 설계 / 계산, 데이터를 가져오는 등의 행위는 Presenter에서 처리하도록

* Presenter : View에서 전달받은 이벤트를 처리 후 View에 전달
    + View와는 무관한 데이터를 가지며, 이를 가공하여 View에 다시 전달



### MVP의 기본 패턴

<img src="https://thdev.tech/images/posts/2016/10/Android-MVP-Intro/mvp-default.png">

    1. View : View에서 터치 이벤트 발생
    2. View -> Presenter : Presenter로 이벤트 전달
    3. Presenter : View에서 요청한 이벤트 처리
    4. Presenter -> View : 처리한 결과를 View로 전달
    5. View : 처리된 결과를 바탕으로 UI를 갱신

위의 과정을 반복한다.


#### 면접 시 -

> 뷰에서 터치 이벤트가 발생하면, 뷰에서 프레젠터로 이벤트를 전달합니다. 그럼 프레젠터에서 뷰에서 요청한 이벤트를 처리 후 처리한 결과를 뷰로 전달합니다. 뷰는 처리된 결과를 바탕으로 UI를 갱신합니다.


일반적인 코드라면 한 페이지 안에서 모두 처리되어 보기 편하다.



### MVP에 모델을 더하면?

<img src="https://thdev.tech/images/posts/2016/10/Android-MVP-Intro/mvp-model.png">

    1. View : View에서 터치 이벤트 발생
    2. View -> Presenter : Presenter에 이벤트 전달
    3. Presenter : 이벤트의 형태에 따라 캐시 데이터를 가져오거나, Model에 요청
    4. Presenter -> Model : Presenter에서 데이터를 요청받음
    5. Model : 데이터를 로컬 또는 서버에서 가져온다
    6. Model -> Presenter : Model로부터 데이터를 통보받는다
    7. Presenter : 전달받은 데이터를 가공
    8. Presenter -> View : 가공한 데이터를 View에 전달
    9. View -> Presenter로 전달받은 데이터를 View에 갱신


#### 면접 시 -
> 뷰에서 터치 이벤트가 발생하면, 뷰에서 프레젠터로 이벤트를 전달합니다. 이벤트의 형태에 따라 캐시 데이터를 가져오거나 모델에 요청합니다. 모델이 데이터를 요청받으면 모델은 그 데이터를 로컬 또는 서버에서 가져와 프레젠터에 전달합니다. 프레젠터는 전달받은 데이터를 필요한 형태로 가공하여 뷰에 전달합니다. 뷰는 전달받은 데이터로 UI를 갱신합니다.


상황에 따라 Presenter는 Model을 사용하지 않지만,
기본 형태는 위와 같습니다.


### 마무리
이해하기 어려우니, 무작정 따라해보자.

* Activity
* Fragment
* RecyclerAdapter



출처 : https://thdev.tech/androiddev/2016/10/12/Android-MVP-Intro/