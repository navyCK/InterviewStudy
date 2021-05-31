# MVC 구조 이해하기

<img src="https://thdev.tech/images/posts/2016/10/Android-MVC-Architecture/MVC.png">

MVC는 MVP 이전의 구조 중 하나이다.

모델, 뷰, 컨트롤러의 약자로 웹에서 주로 사용되는 구조이다.

안드로이드에 적용된 구조는 조금 다른 형태로 표현된다.

## MVC란?
모델, 뷰, 컨트롤러

주로 웹에서 사용되며, 가장 널리 사용되는 구조

입력은 모두 컨트롤러에서 발생

컨트롤러에 의해 모듈의 정의와 뷰의 용도가 결정된다.

    * Model : 데이터를 가진다.
    * View : 사용자에게 보일 화면 표현
    * Controller : 입력을 받고, 이를 모델에 의해 View 정의


이미지로 정리하면 아래와 같다. (웹)

<img src="https://thdev.tech/images/posts/2016/10/Android-MVC-Architecture/default-mvc.png">


    1. Controller : 사용자 이벤트 발생
    2. Controller : 사용자 이벤트가 발생하였는데 갱신이 필요한지 Model에 확인
    3. Model : 데이터 갱신이 필요하다는 이벤트 발생
    4. View : Model 또는 Controller로부터 갱신 필요 여부 이벤트를 받는다.
    5. View : Model에서 실제 필요한 데이터를 받아와 View를 갱신

#### 면접 시 -

> 컨트롤러에서 사용자 이벤트가 발생하면, 모델에 갱신이 필요한지 확인합니다. 모델에서 데이터 갱신이 필요하다는 이벤트가 발생하면 뷰에서는 모델 또는 컨트롤러로부터 갱신 필요 여부 이벤트를 받습니다. 뷰는 모델에서 실제 필요한 데이터를 받아와 뷰를 갱신합니다.


## Android에서의 MVC
안드로이드에서는 뷰와 컨트롤러가 액티비티, 프래그먼트와 같은 뷰들이 모두 가지고 있습니다.

```java
public class MainActivity extends AppCompactActivity {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    // ...

    FloatingActionButton fab = (FloatingActionButton) findViewById(R.id.fab);
    fab.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View view) {
            // 데이터 갱신 요청
            // Model에 접근해서 최신 데이터를 요청
              // ex) ArrayList<String> getItems()
            // 전달받은 ArrayList를 통해 View를 갱신
        }
    });
  }
}
```

하나의 화면 안에서 컨트롤러인 setOnClickListener이 발생하고, 
이를 뷰에서 모두 처리하는 형태입니다.

웹에서 적용된 MVC 패턴은 뷰와 컨트롤러가 모두 분리된 상태를 말합니다.

따라서 안드로이드에서 발생하는 MVC를 그림으로 정리하면 아래와 같습니다.

<img src="https://thdev.tech/images/posts/2016/10/Android-MVC-Architecture/android-mvc.png">

    1. Activity에서 사용자 이벤트 발생
    2. Model로부터 데이터 갱신이 필요한지 확인
    3. Model로부터 전달받은 데이터를 통해 View 갱신 여부 판단
    4. View에서 UI 갱신 처리

#### 면접 시 - 
> 액티비티에서 사용자 이벤트가 발생하면, 모델로부터 데이터 갱신이 필요한지 확인하여 전달받은 데이터를 통해 뷰 갱신 여부를 판단하여, 뷰에서 UI 갱신을 처리합니다.


## 한 화면에서 모든 데이터를 처리하는 장점

MVC는 class 하나로 처리가 가능한 구조가 만들어진다.

정리만 잘한다면 한 눈에 코드 파악이 가능하지만, 어느 정도 범주를 벗어나면 코드 파악이 어렵다.
함수 분리가 되어있지 않다면 더욱 그렇다.

그렇기 때문에 함수 분리 또는 class 분리를 적절히 해야 복잡도가 낮아진다.

아래와 같이 함수 분리를 할 수 있다.

```java
boolean isLast() {
  return itemList.size() >= 100;
}
```

그 외에도 공통으로 분리될 수 있는 setVisibility()도 여러 번 Visible / Gone이 발생한다면
당연히 함수로 분리할 수 있습니다.

그렇기 때문에 코드 분리만 잘해도 MVC 패턴으로 코드 작성은 문제 없다!


### 장점?

    1. 개발 기간이 짧아짐
    2. 코드만 읽을 수 있다면 누구나 쉽게 파악 가능


### 단점?

1. 코드의 양 증가
2. 스파게티 코드 가능성 -> 복잡도 증가(복붙이 많아지고, 코드 분리가 되어있지 않다면)
3. 유지 보수의 어려움
4. View와 Model 결합도가 높다.
5. 테스트 코드 작성이 어렵다.


## MVC로 작성한 샘플 주요 코드
모델에 대한 데이터 코드는 이미 분리되어있다.

```java
// Adapter를 생성
imageAdapter = new ImageAdapter(this);
// Adapter에 itemList를 data를 통해 불러와서 저장
imageAdapter.setImageItems(SampleImageData.getInstance().getImages(this, 10));
// RecyclerView에 adapter를 세팅
recyclerView.setAdapter(imageAdapter);
```
만약 메뉴에서 reload를 호출하면 다음의 코드가 동작
```java
// reload 액션이 발생
if (id == R.id.action_reload) {
    // 기존 itemList clear
    imageAdapter.clear();
    // 새로운 ImageList 불러와서 교체
    imageAdapter.setImageItems(SampleImageData.getInstance().getImages(this, 10));
    // UI Change
    imageAdapter.notifyDataSetChanged();
    return true;
}
```

Android Studio를 통해 실제로 빌드해보기.








<출처 : https://thdev.tech/androiddev/2016/10/23/Android-MVC-Architecture/>