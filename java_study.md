

## 21/12/22 수요일

throw vs throws 차이점 (https://devlog-wjdrbs96.tistory.com/141)

EditText 입력 변화 이벤트 처리 - addTextChangedListener, TextWatcher (https://mine-it-record.tistory.com/272)

ViewBinding- getRoot() - (https://charlezz.medium.com/view-binding-%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0-df3526d909a7)

ViewHolder / Adapter (https://minggu92.tistory.com/4)

Fragment / .commit 왜하니? (https://tedrepository.tistory.com/6)

Glide Image Load (https://blog.yena.io/studynote/2020/06/10/Android-Glide.html)

Toolbar 뒤로가기 버튼 setDisplayHomeAsUpEnabled(true) - (https://dreamaz.tistory.com/109)

setAdapter (https://ehpub.co.kr/tag/setadapter/)

HashSet (https://coding-factory.tistory.com/554)

LayoutInflater attachToParent parameter mean? (https://whyprogrammer.tistory.com/624)

LayoutInflater이란? (https://www.crocus.co.kr/1584)

setSupportActionBar (https://whyprogrammer.tistory.com/447)

HashMap, LinkedHashMap 차이점 및 사용법 https://fruitdev.tistory.com/141 

DAO, DTO, VO 란? http://melonicedlatte.com/2021/07/24/231500.html


## 21/12/23 목요일

웹뷰 뒤로가기 https://deumdroid.tistory.com/entry/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-%EC%8A%A4%ED%8A%9C%EB%94%94%EC%98%A4-%EC%9B%B9%EB%B7%B0WebView-%EB%92%A4%EB%A1%9C%EA%B0%80%EA%B8%B0-%EC%A0%9C%EC%96%B4

추상화, 인터페이스 https://forceson.github.io/android/%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%ED%99%9C%EC%9A%A9-(Feat.-Android)/

생성자와 초기화 https://velog.io/@ikerbm94/%EC%83%9D%EC%84%B1%EC%9E%90Constructor%EC%99%80-%EC%B4%88%EA%B8%B0%ED%99%94Initialization

enum https://www.nextree.co.kr/p11686/

getCurrentFocus()  http://gonacon.blogspot.com/2016/05/android-view.html

WebView 설정 https://jaehoon0210.tistory.com/entry/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-WebSettings%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-WebView-%EC%84%A4%EC%A0%95

onKeyDown https://lktprogrammer.tistory.com/184

extends vs implements https://velog.io/@hkoo9329/%EC%9E%90%EB%B0%94-extends-implements-%EC%B0%A8%EC%9D%B4

context https://roomedia.tistory.com/entry/Android-Context%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C

e.printStackTrace() => 경로까지 보여주는 흔히보는 에러 메시지 https://lnsideout.tistory.com/entry/JAVA-etoString-egetMessage-eprintStackTrace-%EC%98%88%EC%99%B8%EC%B2%98%EB%A6%AC

set HashSet https://tosuccess.tistory.com/145

LinkedList<>() https://devlog-wjdrbs96.tistory.com/64

Collection<> https://gangnam-americano.tistory.com/41


## 21/12/27 월요일
안드로이드 달력 커스텀 https://namget.tistory.com/entry/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%8B%AC%EB%A0%A5-%EC%98%88%EC%A0%9C-Android-Custom-CalendarView-Example


## 21/12/28 화요일
안드로이드 웹뷰 https://jhshjs.tistory.com/57

## 21/12/29 수요일
안드로이드 커스텀리스트뷰 https://recipes4dev.tistory.com/43
 
## 22/01/03 월요일
테스트케이스 https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=wisestone2007&logNo=221064272586

## 22/01/05 수요일
AndroidManifest.xml 확인 사항
1. android:configChanges="keyboard|keyboardHidden" - “keyboardHidden”: User 가 Hardware Keyboard를 보이고 감추는 등의 Keyboard의 Accessibility가 변경되었을 때 : http://jinyongjeong.github.io/2018/09/30/configchange_option/

2. android:windowSoftInputMode="adjustResize|adjustPan"

   adjustPan
   소프트 키보드에 의해 EditText 가 가려지지 않도록 위쪽으로 이동.
   하단 그림과 같이 위, 아래가 잘리게 된다.

   adjustResize
   소프트 키보드가 보이도록 공간을 확보하기 위해 activity window 을 resize 한다.
   하단 그림과 같이 위, 아래 모두 표시된다.
https://parkho79.tistory.com/59

3. android:noHistory="true"

Manifest에서 흔적을

남기고 싶지 않은 Activity에

android:noHistory="true"

이렇게 넣어주시면 됩니다.

https://itpangpang.tistory.com/341
