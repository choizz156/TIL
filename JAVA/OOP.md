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
        }

        ;


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

-----------------------------------

## 상속

> 기존 클래스를 재사용하여 새로운 클래스를 작성하는 것.
> 상위 클래스의 멤버를 하위 클래스와 공유하는 것으로 서로 `상속관계(ia a~)`에 있다고 하며, 하위 클래스는 상위클래스가 가진 모든 멤버를 상속받는다.

- 하위 클래스으 멤버 개수는 항상 상위 클래스의 멤버보다 같거나 많다.
- `extends`키워드를 사용한다.
- 상속을 사용하면 코드를 재사용하여 보다 적은 양의 코드로 새로운 클래스를 작성할 수 있어 `코드의 중복을 제거`할 수 있다.
- 다형적 표현을 가능하게 한다.
- 단일상속만 가능하다.

```java
class Person {
    String name;
    int age;

    void learn() {
        System.out.println("공부를 합니다.");
    }

    ;


}

class Programmer extends Person { // Person 클래스로부터 상속. extends 키워드 사용 
    String companyName;

    void coding() {
        System.out.println("코딩을 합니다.");
    }

    ;
}

class Dancer extends Person { // Person 클래스로부터 상속
    String groupName;

    void dancing() {
        System.out.println("춤을 춥니다.");
    }

    ;
}

class Singer extends Person { // Person 클래스로부터 상속
    String bandName;

    void singing() {
        System.out.println("노래합니다.");
    }

    ;

    void playGuitar() {
        System.out.println("기타를 칩니다.");
    }

    ;
}

public class HelloJava {
    public static void main(String[] args) {

        //Person 객체 생성
        Person p = new Person();
        p.name = "김코딩";
        p.age = 24;
        p.learn();


        System.out.println(p.name);

        //Programmer 객체 생성
        Programmer pg = new Programmer();
        pg.name = "박해커";
        pg.age = 26;

        pg.coding(); // Programmer의 개별 기능
        System.out.println(pg.name);

    }
}

    //출력값
    공부를 합니다.
        김코딩
        공부를 합니다.
        코딩을 합니다.
        박해커
```

- Person클래스로 부터 확장되어 Person클래스에 있는 속성과 기능들을 사용할 수 있다.

### 포함 관계

> 클래스를 재사용하는 방법으로, 클래스의 멤버로 다른 클래스의 타입의 참조변수를 선언하는 것.

```java
public class Employee {
    int id;
    String name;
    Address address;

    public Employee(int id, String name, Address address) {
        this.id = id;
        this.name = name;
        this.address = address;
    }

    void showInfo() {
        System.out.println(id + " " + name);
        System.out.println(address.city + " " + address.country);
    }

    public static void main(String[] args) {
        Address address1 = new Address("서울", "한국");
        Address address2 = new Address("도쿄", "일본");

        Employee e = new Employee(1, "김코딩", address1);// Address 타입에 객체가 들어간다.
        Employee e2 = new Employee(2, "박해커", address2);

        e.showInfo();
        e2.showInfo();
    }
}

class Address {
    String city, country;

    public Address(String city, String country) {
        this.city = city;
        this.country = country;
    }
}

// 출력값
1김코딩
        서울 한국
        2박해커
        도쿄 일본
```

- Address 클래스로 해당 변수들을 묶어준다음 Employee 클래스의 안에 참조변수를 선언하는 방식(has a-)으로
  코드의 중복을 없애고 재사용한다.

### 메서드 오버라이딩(Method Overriding)

> 상위 클래스로부터 상속받은 메서드와 동일한 이름의 메서드를 재정의 하는 것.

- 세가지 조건
    - 메서드의 선언부(메서드 이름,매개변수, 반환타입)이 상위 클래스와 일치해야 한다.
    - 접근 제어자의 번위가 상위 클래스의 메서드보다 같거나 넓어야 한다.
    - 예외는 상위 클래스의 메서드보다 많이 선언할 수 없다.

```jshelllanguage
class Vehicle {
    void run() {
        System.out.println("Vehicle is running"


        );
    }
}

    public class Bike extends Vehicle { // Vehicle 클래스 상속
        void run() {
            System.out.println("Bike is running"


            ); // 메서드 오버라이딩
        }

        public static void main(String[] args) {
            Bike bike = new Bike();
            bike.run();
        }
    }

// 출력값
    "Bike is running"
```

- 상위 클래스와 메서드 명이 같지만 다른 일을 한다.

```jshelllanguage
public class Main {
    public static void main(String[] args) {
        Bike bike = new Bike(); // 각각의 타입으로 선언 + 각각의 타입으로 객체 생성
        Car car = new Car();
        MotorBike motorBike = new MotorBike();

        bike.run();
        car.run();
        motorBike.run();

        Vehicle bike2 = new Bike(); // 상위 클래스 타입으로 선언 + 각각 타입으로 객체 생성
        Vehicle car2 = new Car();
        Vehicle motorBike2 = new MotorBike();

        bike2.run();
        car2.run();
        motorBike2.run();
    }
}

    class Vehicle {
        void run() {
            System.out.println("Vehicle is running");
        }
    }

    class Bike extends Vehicle {
        void run() {
            System.out.println("Bike is running");
        }
    }

    class Car extends Vehicle {
        void run() {
            System.out.println("Car is running");
        }
    }

    class MotorBike extends Vehicle {
        void run() {
            System.out.println("MotorBike is running");
        }
    }

    // 출력값
    Bike is running
    Car is running
    MotorBike is running
```

- 모든 객체를 상위 클래스 타입 하나로 선언하면 간편하게 배열로 선언하여 관리할 수 있다.

```jshelllanguage
// 배열로 한번에 관리하기

    Vehicle[] vehicles = new Vehicle[]{new Bike(), new Car(), new MotorBike()};
    for (Vehicle vehicle : vehicles) {
        vehicle.run();
    }

    // 출력값
    Bike is running
    Car is running
    MotorBike is running
```

- 메서드 오버라이딩이 된다면 일일이 객체를 만들고 run메서드를 실행하지 않아도 한꺼번에 같은 결과를 출력할 수 있다.

### super와 super()

> super는 상위 클래스의 객체, super()는 상위 클래스의 생성자를 호출. (this와 비슷)

- 상위 클래스의 존재를 상정해서 상속 관계를 전제로 한다.

```jshelllanguage
   public class Super {
    public static void main(String[] args) {
        Lower l = new Lower();
        l.callNum();
    }
}

    class Upper {
        int count = 20; // super.count
    }

    class Lower extends Upper {
        int count = 15; // this.count

        void callNum() {
            System.out.println("count = " + count);// 자기에게 가장 가까운 count를 선택.
            System.out.println("this.count = " + this.count //현재 클래스의 count

            );
            System.out.println("super.count = " + super.count // 상위 클래스의 count
            );
        }
    }

// 출력값
    count = 15
    count = 15
    count = 20

```

- super 키워드를 붙이지 않는다면, 자바 컴파일러가 해당 객체는 자신이 속한 인스턴스 객체의 멤버를 먼저 참조.

```jshelllanguage

    public class Test {
        public static void main(String[] args) {
            Student s = new Student();
        }
    }

    class Human {
        Human() {
            System.out.println("휴먼 클래스 생성자");
        }
    }

    class Student extends Human { // Human 클래스로부터 상속
        Student() {
            super(); // Human 클래스의 생성자 호출
            System.out.println("학생 클래스 생성자");
        }
    }

    // 출력값
    휴먼 클래스 생성자
    학생 클래스 생성자
```
- 생성자의 첫 줄에 this()나 super()를 선언해야 한다.
- 없는 경우 생성자의 첫줄에 자동으로 super()를 삽입한다.

### Object 클래스
> Object 클래스는 자바의 클래스 상속계층도에서 최상위에 위치한 상위클래스이다.
> 모든 클래스는 Object 클래스로부터 확장된다.
> Object 클래스의 메서드는 따로 정으하지 않아도 사용가능하다.

|메서드명|반환타입| 내용                            |
|------|------|-------------------------------|
|toString|String| 객체 정보를 문자열로 출력                |
|equals|boolean| 등가 비교 연산{==}과 동일하게 스택 메모리값 비교 |
|hashCode()|int|객체 위치정보 관련. Hashtable이나 Hashmap에서 동일 객체여부 판단.|
|notify()|void|일시정지 중인 쓰레드 재동장|
|wait()|void|현재 쓰레드 일시정지|