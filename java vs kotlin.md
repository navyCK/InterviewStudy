# java와 kotlin 비교

출처 : https://dev-imaec.tistory.com/36


### 1. 변수 / 상수
```java
String strVar = "";       // 변수
final String strVal = ""; // 상수
```

```kotlin
var strVar = "" // 변수
val strVal = "" // 상수
```

### 2. view 사용
```java
btnTest = findViewById(R.id.btn_test); // 객체를 만들어 findViewById() 함수로 객체에 할당
btnTest.setText("Test");
```

```kotlin
btn_test.text = "Test" // xml에서 정의한 id 값으로 view 사용
```

### 3. null 안정성
```java
@Nullable String strNullable = null;
@NonNull String strNonNull = "";


strNullable.split("/"); // NPE 발생

if (strNullable != null) {
    strNullable.split("/");
}
```

```kotlin
var strNullable: String? = null   // ?는 optional
var strNonNull: String = ""


strNullable.split("/") // NPE 발생

strNullable?.split("/")
```


### 4. 객체 초기화
```java
Intent testIntent = new Intent(this, SecondActivity.class); // 일반적인 객체 초기화 및 초기 작업
testIntent.putExtra("ext1", 1);
testIntent.putExtra("ext2", 2);
testIntent.putExtra("ext3", "3");
testIntent.putExtra("ext4", "4");
testIntent.putExtra("ext5", false);
```

```kotlin
val testIntent = Intent(this, SecondActivity::class.java).apply { // 객체 초기화 시 초기 작업 수행


    putExtra("ext1", 1)
    putExtra("ext2", 2)
    putExtra("ext3", "3")
    putExtra("ext4", "4")
    putExtra("ext5", false)
}
```

### 5. Data Class
```java
public class JavaData {

    JavaData(String s, int i, boolean b) {
        this.s = s;
        this.i = i;
        this.b = b;
    }

    private String s;
    private int i;
    private boolean b;

    public String getS() {
        return s;
    }

    public void setS(String s) {
        this.s = s;
    }

    public int getI() {
        return i;
    }

    public void setI(int i) {
        this.i = i;
    }

    public boolean isB() {
        return b;
    }

    public void setB(boolean b) {
        this.b = b;
    }
}


JavaData data1 = new JavaData("", 0, true); // 생성자로 초기화

JavaData data2 = new JavaData(); // 빈 생성자로 생성 후 set 함수로 초기화
data2.setS("");
data2.setI(0);
data2.setB(true);
```

```kotlin
data class KotlinData(var s: String?,
                      var i: Int,
                      var b: Boolean)
                      
val data1 = KotlinData("hi", 1, false) // 생성자로 초기화                      
```

