1. extends
    - 부모에서 선언 / 정의를 모두하며 자식은 메소드 / 변수를 그대로 사용할 수 있음

2. implements(interface 구현)
    - 부모 객체는 선언만 하며 정의(내용)은 자식에서 오버라이딩 (재정의) 해서 사용해야함

3. abstract
    - extends와 interface 혼합. extends하되 몇 개는 추상 메소드로 구현되어 있음



## extends (상속)
- 사실 extends가 상속의 대표적인 형태다.
- 부모의 메소드를 그대로 사용할 수 있으며 오버라이딩 할 필요 없이 부모에 구현되있는 것을 직접 사용 가능하다.

```java
class Vehicle {
  protected int speed = 3;
  
  public int getSpeed(){
    return speed;
  }
  public void setSpeed(int speed){
    this.speed = speed;
  }
}

class Car extends Vehicle{
  public void printspd(){
    System.out.println(speed);
  }
}

public class ExtendsSample {
  public static main (String[] args){
    Car A = new Car();
    System.out.println(A.getSpeed());
    A.printspd();
  }
}
```

## implements (상속)
- implements의 가장 큰 특징은 이렇게 부모의 메소드를 반드시 오버라이딩(재정의)해야 한다.

```java
interface TestInterface{
  public static int num = 8;
  public void fun1();
  public void fun2();
}

class InterfaceExam implements TestInterface{
  @Override
  public void fun1(){
    System.out.println(num);
  }
  
  @Override
  public void fun2() {
    
  }
}

public class InterfaceSample{
  public static void main(String args[]){
    InterfaceExam exam = new InterfaceExam();
    exam.fun1();
  }
}
```


- extends는 일반 클래스와 abstract 클래스 상속에 사용되고, implement는 interface 상속에 사용된다.
- class가 class를 상속받을 땐 extends를 사용하고, interface가 interface를 상속 받을 땐 extends를 사용한다.
- class가 interface를 사용할 땐 implements를 써야하고
- interface가 class를 사용할 땐 implements를 쓸수 없다.
- extends는 클래스 한 개만 상속 받을 수 있다.
- extends 자신 클래스는 부모 클래스의 기능을 사용한다.
- implements는 여러개 사용 가능하다.
- implements는 설계 목적으로 구현 가능하다.
- implements한 클래스는 implements의 내용을 다 사용해야 한다.

<!-- 출처 - https://velog.io/@hkoo9329/%EC%9E%90%EB%B0%94-extends-implements-%EC%B0%A8%EC%9D%B4 -->