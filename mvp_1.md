# Android MVP - Presenter / View 생성하기

## Presenter ?
* View : Presenter에서 전달받은 View의 이벤트
* Presenter : View에서 전달된 이벤트에 대한 처리(View와 무관한 처리만)

<img src="https://thdev.tech/images/posts/2016/11/Android-MVP-One/mvp-default.png">

## Presenter를 구분하는 방법
* View에 대한 interface만 정의하는 방법
    + interface View : View에 대한 interface만 정의
    + Presenter : interface 정의 없이 함수를 생성하여 사용
    + View : interface View을 상속받아서 정의
* Google architecture를 따른다.
    + Contract : View와 Presenter에 대한 interface을 작성
    + Presenter : Contract.Presenter을 상속받아서 구현
    + View : Contract.View을 상속받아서 구현
* PresenterImpl을 구현
    + Presenter : Presenter와 View에 대한 interface을 구현
    + PresenterImpl : Presenter을 상속받아서 구현
    + View : Presenter.View을 상속받아서 구현

#### interface 정의 시
+ 장점 : 코드 파악이 쉽다.
+ 단점 : interface 정의가 너무 많다.

결국 View와 Presenter 간 통신을 위한 리스너 역할의 interface View에 대한 정의는 처리가 되어야 한다 (?)


## Google Architecture
구글에서 정의하는 Presenter의 생성 방법은 아래와 같다.

<img src="https://thdev.tech/images/posts/2016/11/Android-MVP-One/Google_Architecture.png">

>
1. Presenter의 생성은 View가 아닌 실제 View가 만들어지는 시점의 Activity/Fragment/View등에서 생성을 하고 해당 Presenter에 setView을 실행한다.
2. setView가 호출되는 시점에 자기 자신(this)을 setPresenter함수를 통해서 실제 Presenter가 사용되어야 할 View에 전달한다.
3. View에서는 setPresenter을 통해서 전달받은 Presenter을 가지고 이후 loadItem, OnClickListener 등의 처리를 합니다.


### Activity만 있는 경우?
1. Activity만 있는 경우에도 별도의 View를 생성해야 하는가?
2. 그냥 자기 자신이 받아도 되는가?

    => 자기 자신이 new Presenter를 처리할 수 있어야 한다. 그렇다면 setPresenter라는 메소드가 필요하지 않다. Activity/Fragment/View 등에서 필요한 경우 Presenter를 생성하고, 자기 자신이 사용할 수 있어야 한다.









출처 : https://thdev.tech/androiddev/2016/11/28/Android-MVP-One/