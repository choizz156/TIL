## 객체지향 프로그램(Object-Oriented Programming)
### 클래스(class)
> 객체를 생성하는 데 사용되는 하나의 틀.
> <br/>
>클래스를 통해 생성된 객체를 인스턴스(instance)라고 하고 이 과정을 인스턴스화라고 한다.

- 클래스 생성
```jshelllanguage
class 클래스명{ // 일반적으로 대문자로 시작.
    
}

```
- 클래스 구성 요소
  - 필드(field) :인스턴스 속성을 타나내는 변수.
  - 생성자(constructor) : 객체를 생성하는 역할 / new Person();
  - 메서드(method) : 인스턴스가 하는 행동.
  - 내부 클래스(inner class) : 클래스 내부의 클래스
```jshelllanguage
public class Person{
    int eyes; // 필드
    Person{...}; // 생성자
    void move(){}; // 메소드
    class Person2{}//내부클래스
}
```
> 필드, 메서드, 내부 클래스를 `멤버`라고 한다.

### 객체(Object,Instance)
> 클래스에서 만들어진 복제품 같은 것으로 실제로 속성과 행동을 갖는다.

- 객체의 생성
```jshelllanguage
클래스명 참조변수 = new 생성자();
// 인스턴스를 참조하기 위한 참조변수를 선언하고 인스턴스를 생성 후 참조 변수에 저장한다.
```
```jshelllanguage
class Car{ // car 클래스 에서 찍어냄
    int doors; // 속성들
    int tires;
    String color;
    
    void startCar{ // 행동
        ...
    }
}

Car bmw2 = new Car(); //bmw2라는 인스턴스를 class에서 찍어냄(생성)
Car tesla = new Car();// 마찬가지
Car audi = new Car();// 마찬가지

// 여기 인스턴스들은 Car 클래스의 속성과 행동을 복제한다.



```
> 참조 변수가 데이터를 참조하는 방법??
  
- 참조 변수는 stack영역에 저장돼있다.
- 생성된 객체는 힙 메모리에 저장돼 있고 그 주소값을 참조 변수에 할당한다.
- 참조 변수는 힙 메모리에 저장돼있는 데이터를 참조하여 사용한다. 
- 만들어진 인스턴스 내부에는 멤버들이 위치한다. 
- 모든 인스턴스는 클래스에서 만들어진 메서들을 공유하기 때문에 클래스 영역에 저장된 메서드를 찾아서 사용한다.

- 객체가 행동하는 방법

```jshelllanguage
인스턴스.필드; // 필드명 불러오기
인스턴스.메서드(); // 메서드 호출
```


```java
public class Practice {
    public static void main(String[] args) {
     Car tesla = new Car("m3","red");
        System.out.println("내 차의 모델은 " + tesla.model+" 이고 색은 " + tesla.color+"지리오");
        tesla.power();
        tesla.accelerate();
        tesla.stop();
    }


  public class Car {
    public String model;
    public String color;

    public Car(String model, String color) {
      this.model = model;
      this.color = color;
    }

    void power() {
      System.out.println("시동 온");
    }

    void accelerate() {
      System.out.println("속도업");
    }
    void  stop(){
      System.out.println("멈춰");
    }
  }

}
```