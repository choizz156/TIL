# 목차

- [클래스(class)](#클래스class)
- [객체(Object,Instance)](#객체objectinstance)
- [필드](#필드)
- [static](#static)
- [메서드(method)](#메서드method)
    - [메서드 호출](#메서드-호출)
    - [메서드 오버로딩](#메서드-오버로딩)
- [생성자](#생성자)
    - [기본 생성자](#기본-생성자)
- [this() vs this](#this-vs-this)
    - [this()](#this)
    - [this](#this)

### 클래스(class)

> 객체를 생성하는 데 사용되는 하나의 틀.
> <br/>
> 클래스를 통해 생성된 객체를 인스턴스(instance)라고 하고 이 과정을 인스턴스화라고 한다.

- 클래스 생성

```jshelllanguage
class 클래스명 { // 일반적으로 대문자로 시작.

}

```

- 클래스 구성 요소
    - 필드(field) :인스턴스 속성을 타나내는 변수.
    - 생성자(constructor) : 객체를 생성하는 역할 / new Person();
    - 메서드(method) : 인스턴스가 하는 행동.
    - 내부 클래스(inner class) : 클래스 내부의 클래스

```jshelllanguage
public class Person {
    int eyes; // 필드

    Person {...}

    ; // 생성자

    void move() {
    }

    ; // 메소드

    class Person2 {
    }//내부클래스
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
class Car { // car 클래스 에서 찍어냄
    int doors; // 속성들
    int tires;
    String color;

    void startCar

    { // 행동
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
        Car tesla = new Car("m3", "red");
        System.out.println("내 차의 모델은 " + tesla.model + " 이고 색은 " + tesla.color + "지리오");
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

        void stop() {
            System.out.println("멈춰");
        }
    }

}
```

## 필드

> 클래스의 포함된 변수를 의미. 객체의 속성을 정의한다.

- `클래스 변수(static)`와 `인스턴스 변수`를 필드라고 한다.

```jshelllanguage
class Example {
    int istanceVariable; // 인스턴스 변수
    static int classVariable; // 클래스 변수,static 변수, 공유 변수

    void method() {
        int localVariable = 0; // 로컬 변수, {} 블럭에서만 유효하다.
    }
}
```

- `인스턴스 변수`
    - 인스턴스가 가지는 각각의 고유한 속성을 저장하기 위한 변수.
    - 인스턴스가 생성될 때 만들어진다.
    - 비록 동일한 클래스로부터 생성됐지만 객체의 고유한 개별성을 갖는다.(차에도 종류가 다르고 색깔도 다르니까)
- `static 변수`
    - 공통된 저장공간을 공유.
    - 클래스에서 생성되는 모든 인스턴스들이 특정한 값을 공유해야 하는 경우에 사용.
    - 인스턴스를 따로 생성하지 않고도 클래스명으로 사용 가능함.

> - 객체가 존재하는한 필드변수는 사라지지 않음.
    > <br/>
> - 직접적으로 초기화를 실행하지 않아도 강제로 초기화가 이루어진다.
>

- `지역 변수`
    - 매서드 내에서 선언.
    - 블록에서만 사용가능한 변수.

> - 스택 메모리에 저장돼 메서드가 종료됨과 동시에 함께 없어짐.
    > <br/>
> - 한동안 사용되지 않는 경우 가상 머신에 의해 자동으로 삭제.
    > <br/>
> - 직접 초기화하지 않으면 값을 출력할때 에러가 나옴.

## static

> static이 붙어있는 멤버를 '정적 멤버'라고 부르고 인스턴스 생성 없이도 사용가능하다.

- static은 클래스 영역에 저장되기 때문에 객체 생성없이도 사용가능하다.
- 정적 멤버들은 인스턴스 변수나 메서드를 사용할 수 없다.(인스턴스 변수는 인스턴스가 생성되면 만들어짐)

```jshelllanguage

    public class StaticEx {
        int num1 = 1; // 인스턴스 변수
        static int num2 = -10; // 클래스 변수
    }

    public class asdf {
        public static void main(String[] args) {
            StaticEx staticEx = new StaticEx();
            System.out.println("인스턴스 변수 : " + staticEx.num2); // 출력됨
            System.out.println("클래스 변수 : " + StaticEx.num1); // 출력되지 않음
        }
    }
```

- `클래스명.인스턴스` 변수는 사용할 수 없다. 인스턴스 변수는 인스턴스가 생성돼야 사용할 수 있다.
- `인스턴스명.클래스` 변수는 사용은 가능하다. static이 공유되니까. 하지만 static변수라는 것을
  알려주기위해 안쓰는것이 좋다.

- static은 메서드에도 동일하게 적용된다.

```jshelllanguage

    public class StaticEx {
        int num1 = 10; // 인스턴스 변수
        static int num2 = -10; // 클래스 변수
    }
    public class asdf {
        public static void main(String[] args) {
            StaticEx staticEx1 = new StaticEx();
            StaticEx staticEx2 = new StaticEx();

            staticEx1.num1 = 100; // 인스턴스는 클래스 값을 복제를 하지만 공유하지는 않음
            staticEx2.num1 = 1000;// 인스턴스는 클래스 값을 복제를 하지만 공유하지는 않음

            System.out.println(staticEx1.num1); // 100
            System.out.println(staticEx2.num1); // 1000

            staticEx1.num2 = 150; // static은 클래스 내에 저장소가 있어서 값의 변화가 모든 객체에 공유됨.
            staticEx2.num2 = 1500;// static은 클래스 내에 저장소가 있어서 값의 변화가 모든 객체에 공유됨.
            // 150으로 바뀌었다가 1500으로 다시 바뀜
            System.out.println(staticEx1.num2); // 1500 
            System.out.println(staticEx2.num2); // 1500
        }
    }
```

## 메서드(method)

> 특정 작업을 수행하는 일련의 명령문들의 집합 == `행동`

```jshelllanguage
접근 제어자 반환타입 메서드명(매개 변수) { // 메서드 시그니처
    내용 // 메서드 바디
}
```

- 반환 타입이 void가 아닌 경우는 body안에 return문이 반드시 존재해야 한다.
  결과값은 반환타입이거나 자동 형변환이 가능해야 한다.

### 메서드 호출

> 메서드도 클래스 멤버이므로 힙에 저장돼 있다. 그래서 클래스 외부에서 메서드를 사용하기 위해서는
> 인스턴스를 생성해야 한다.

```jshelllanguage
인스턴스명.메서드명(인자)
```

- 메서드를 만들 때는 매개변수이고 실행할 때 들어가는 것은 인자(argument)이다.
- 인자의 개수와 순서, 타입은 선언된 매개변수와 일치되어야 메서드가 수행된다.(자동형변환은 가능)

### 메서드 오버로딩

> 하나의 클래스 안에 같은 이름의 메서드를 여러개 정희하는 것이다.
> <br/>
> 하나의 메서드로 여러 경우의 수 해결 가능.

- 조건
    - 메서드의 이름이 같아야 함.
    - 매개변수의 개수 또는 타입이 달라야함.

```jshelllanguage

    public class Overloding {
        public static void main(String[] args) {
            Shapes s = new Shapes();
            s.area(); // 넓이
            s.area(5);//원의넓이
            s.area(3, 4);//직사각형넓이
            s.area(2, 2);//삼각형넓이 
        }
    }
    public class Shapes {
        public void area() {
            System.out.println("넓이");
        }

        public void area(int r) {
            System.out.println("원의넓이");
        }

        public void area(int w, int l) {
            System.out.println("직사각형넓이");
        }

        public void area(double a, double b) { // 타입이 다름
            System.out.println("삼각형넓이");
        }

    }
```

## 생성자

> 인스턴스가 생성될 때 호출되는 인스턴스 초기화 메서드

- 생성자의 이름은 반드시 크래스의 이름과 같아야 한다.
- 생성자는 리턴 타입이 없다.
- 오버로딩이 가능해서 클래스 내에 여러 개의 생성자가 존재할 수 있다.

```java
public class ConstructorEx {
    public static void main(String[] args) {
        Constructor cons1 = new Constructor();
        Constructor cons2 = new Constructor("Hello World");
        Constructor cons3 = new Constructor(5, 10);
    }
}

class Constructor {
    Constructor() { //생성자 오버로딩
        System.out.println("1번");
    }

    Constructor(String str) { // (2) 
        System.out.println("2번");
    }

    Constructor(int a, int b) { // (3) 
        System.out.println("3번");
    }
}

```

### 기본 생성자

> 매개변수가 없는 생성자.

- 모든 클래스에는 반드시 하나 이상의 생성자가 존재해야 함.
- 클래스 안에 생성자가 없는 경우 자바 컴파일러가 기본 생성자를 자동으로 추가.
- 생성자가 추가돼 있다면 그 생성자를 기본으로 사용.
- 매개변수가 있는 경우 개수와 타입에 맞게 생성자를 호출해줘야 함.

## this() vs this

### this()

> 자신이 속한 클래스에서 다른 생성자를 호출하는 경우에 사용.

- 반드시 생성자의 내부에서만 사용할 수 있다.
- 반드시 생성자의 첫 줄에 위치해야 한다.

```jshelllanguage

    class Example {
        public Example() {
            System.out.println("기본 생성자");
        };

        

        public Example(int x) {
            this();
            System.out.println("두 번째 생성자 호출");
        }
    }

    //Output
         기본 생성자 호출!
         기본 생성자 호출!
         생성자 호출!
```
### this
> 인스턴스 변수와 이름만으로 구분하기 어려울 때(멤버 변수,지역변수), 이를 구분해주기 위한 용도로 사용.
- 모든 메서드에는 자신이 포함된 클래스의 객체를 가리키는 this라는 참조변수가 있는데,
일반적인 경우에 컴파일러가 this.을 추가해주기 때문에 생략하는 경우가 많다.
- this는 인스턴스 자신을 가리키는 것이다. 
- 지역 변수와 필드 몯를 사용할 수 있는 영역에서는 사용 범위가 좁은 변수 즉, 지역 변수로 인식한다.
