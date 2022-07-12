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
- 상속이 연결 가능하다

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

---------------------

## 캡슐화

> 특정 객체 안에 관련된 솏ㅇ과 기능을 하나의 캡슐로 만들어 데이터를 외부로부터 보호하는 것

- 데이터 보호
- 내부적으로만 사용되는 데이터에 대한 불필요한 외부 노출을 방지
- 데이터가 변경되더라도 다른 객체에 영향을 주지 않기에 독립성을 확보할 수 있음.

### 패키지

> 특정한 목절을 공유하는 클래스와 인터페이스의 묶음.
> 클래스를 그룹 단위로 묶어 효과적으로 관리하기 위한 목적.

- 패키지는 하나의 디렉토리이고, 하나의 패키지에 속한 클래스나 인터페이스 파일은 모두 해당 패키지에 속해있다.
- 계층구조를 가지고 있고 `.`으로 구분한다.
- 패키지가 있는 경우 소스 코드의 첫 줄에 반드시 `package 패키지명`이 표시돼야 하고. 없으면 이름없는 패키지에 속함.

```jshelllanguage
package practice.test

    public class packageEx{

}
```

- 클래스의 충돌을 방지해준다.

### import

> 다른 패키지 내의 클래스를 사용하기 위해 사용.

- import문이 없으면 다른 패키지의 클래스를 사용하기 위해 매번 패키지명을 붙여 줘야함.

```jshelllanguage
public class packageEx {
    public static void main(String[] args) {
        pracicepack.test.Examplecalss example = new pracicepack.test.Examplecalss();
    }
}
```

- 입력방식
    - `import 패키지명.클래스명;` 혹은 `import 패키지명.*;`
    - `import.패키지명.*`으로 작성하면 해당 패키지의 모든 클래스를 패키지명 없이 사용 가능.

```jshelllanguage
package practicepack.test2;

    improt practicepack.test.ExampleImp

    public class packageEE{
    public static void main(String[]args){
    ExmapleImp a=new ExampleImp(); //패키지명이 안 붙음.
}
}
```

### 접근제어자

> 클래스, 필드. 메서드, 생성자 등에 부가적인 의미를 부여하는 키워드
> public, protected, default(생략가능), private

- 접근 제어자는 한 번만 사용할 수 있다.

| 접근 제어자    |클래스 내|패키지 내| 다른 패키지의 하위클래스(상속) |패키지 외|
|-----------|-------|--------|-------------------|-------|
| private  | o|x| x                 |x| 
| default |  o|o| x                 |x|
| protected |o|o| o                 |x|
|public|o|o| o                 |o|
|           |     |     |                   |     |

```java
package package1; // 패키지명 package1 

//파일명: Parent.java
class Test { // Test 클래스의 접근 제어자는 default
    public static void main(String[] args) {
        Parent p = new Parent();

//        System.out.println(p.a); // 동일 클래스가 아니기 때문에 에러발생!
        System.out.println(p.b);
        System.out.println(p.c);
        System.out.println(p.d);
    }
}

public class Parent { // Parent 클래스의 접근 제어자는 public
    private int a = 1; // a,b,c,d에 각각 private, default, protected, public 접근제어자 지정
    int b = 2;
    protected int c = 3;
    public int d = 4;

    public void printEach() { // 동일 클래스이기 때문에 에러발생하지 않음
        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(d);
    }
}

// 출력값
                2
                3
                4
```

```java
package package2; // package2 

//파일명 Test2.java

import package1.Parent;

class Child extends package1.Parent {  // package1으로부터 Parent 클래스를 상속
    public void printEach() {
        System.out.println(a); // 에러 발생!
        System.out.println(b); // 에러

        // 다른 패키지의 클래스를 확장하지 못하면 public이든 protected든 다 에러가 난다.
        System.out.println(c); // 다른 패키지의 하위 클래스
        System.out.println(d); // public
    }
}

public class Test2 {
    public static void main(String[] args) {
        Parent p = new Parent();

        System.out.println(p.a); // public을 제외한 모든 호출 에러!
        System.out.println(p.b); // 에러
        System.out.println(p.c); // 에러
        System.out.println(p.d); // 
    }
}
```

- 접근 제어자는 내가 접근 가능을 말하는 것이 아니라 `내가 접근 받는 것을 관리하는 것이다.`

### getter와 setter 메서드
> private 접근제어자가 포함되어 있는 객체의 변수의 데이터 값을 추가하거나 수정하고 싶을때 사용.
> 
> setter 메서드(set-)는 외부에서 메서드에 접근하여 데어티 값을 변경 가능하게 해준다.
> 
> getter 메서드는(get-) setter로 설정한 변수 값을 읽어오는 데 사용한다.

```java
 public class GetterSetterTest {
    public static void main(String[] args) {
        Worker w = new Worker();
        w.setName("김코딩"); // private 변수를 추가하거나 수정할때 사용
        w.setAge(30);
        w.setId(5);

        String name = w.getName(); // 출력은 getter로 한다.
        System.out.println("근로자의 이름은 " + name);
        int age = w.getAge();
        System.out.println("근로자의 나이는 " + age);
        int id = w.getId();
        System.out.println("근로자의 ID는 " + id);
    }
}

class Worker {
    private String name; // 변수의 은닉화. 외부로부터 접근 불가
    private int age;
    private int id;

    public String getName() { // 멤버변수의 값 
        return name;
    }

    public void setName(String name) { // 멤버변수의 값 변경
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if(age < 1) return;
        this.age = age;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }
}
```
- 데이터를 효과적으로 보호하면서 의도하는 값으로 값을 변경할 수 있다.

--------------------
## 다형성
> 한 타입의 참조변수를 통해 여러 타입의 객체를 참조할 수 있도록 만든 것.

> 상위 클래스 타입의 참조변수를 통해서 하위 클래스의 객체를 참조할 수 있도록 허용한 것.

```java
class Friend {
  public void friendInfo() {
    System.out.println("나는 당신의 친구입니다.");
  }
}

class BoyFriend extends Friend {

  public void friendInfo() {
    System.out.println("나는 당신의 남자친구입니다.");
  }
}

class GirlFriend extends Friend {

  public void friendInfo() {
    System.out.println("나는 당신의 여자친구입니다.");
  }
}

public class FriendTest {

  public static void main(String[] args) {
    Friend friend = new Friend(); // 객체 타입과 참조변수 타입의 일치
    BoyFriend boyfriend = new BoyFriend();
    Friend girlfriend = new GirlFriend(); // 객체 타입과 참조변수 타입의 불일치

    friend.friendInfo();
    boyfriend.friendInfo();
    girlfriend.friendInfo();// 수행가능함.
  }
}
```
- 상위 클래스를 참조변수의 타입으로 지정하면 참조변수가 사용할 수 있는 멤버의 개수는 상위 클래스의 멤버의 수가 된다.
```jshelllanguage
public class FriendTest {

  public static void main(String[] args) {
    Friend friend = new Friend(); // 객체 타입과 참조변수 타입의 일치 -> 가능
    BoyFriend boyfriend = new BoyFriend();
    Friend girlfriend = new GirlFriend(); // 객체 타입과 참조변수 타입의 불일치 -> 가능
    GirlFriend friend1 = new Friend(); // -> 하위클래스 타입으로 상위클래스 객체 참조 -> 불가능

    friend.friendInfo();
    boyfriend.friendInfo();
    girlfriend.friendInfo();
  }
}
```
- 객체인 상위 클래스의 멤버의 수보다 참조 변수의 멤버 개수가 더 많기 때문에 하위클래스에서 상위클래스 
객체 참조는 안 된다.

### 참조변수의 타입변환
> 사용할 수 있는 멤버의 개수를 조절하는 것을 의미한다.
- 서로 상속관계에 있는 상위 클래스 - 하위 클래스 사이에만 타입변환이 가능하다.
- 하위 클래스 타입에서 상위 클래스 타입으로의 타입 변환(업 캐스팅)은 형변환 연산자(괄호)를
생략할 수 있다.
- 상위 클래스에서 하위 클래스 타입으로 변환(다운캐스팅)은 형변환 연산자(괄호)를 반드시 명시해야 한다.

```java
public class VehicleTest {
    public static void main(String[] args) {
        Car car = new Car();
        Vehicle vehicle = (Vehicle) car; // 상위 클래스 Vehicle 타입으로 변환(생략 가능)
        Car car2 = (Car) vehicle; // 하위 클래스 Car타입으로 변환(생략 불가능)
        MotorBike motorBike = (MotorBike) car; // 상속관계가 아니므로 타입 변환 불가 -> 에러발생
    }
}

class Vehicle {
    String model;
    String color;
    int wheels;

    void startEngine() {
        System.out.println("시동 걸기");
    }

    void accelerate() {
        System.out.println("속도 올리기");
    }

    void brake() {
        System.out.println("브레이크!");
    }
}

class Car extends Vehicle {
    void giveRide() {
        System.out.println("다른 사람 태우기");
    }
}

class MotorBike extends Vehicle {
    void performance() {
        System.out.println("묘기 부리기");
    }
}
```
- 상속관계에 있는 클래스 간에는 상호 타입변화이 자유롭게 수행될 수 있다.

### instanceof 연산자
> 참조변수의 타입변환, 즉 캐스팅이 가능한 지 여부를 boolean, 타입으로 확인가능.
- `참조변수(인스턴스) instanceof 클래스이름`

### 예시 코드
```java
package package2;

public class PolymorphismEx {
  public static void main(String[] args) {
    Customer customer = new Customer();
    customer.buyCoffee(new Americano()); //Americano는 Coffee를 상속 받는다
    // new Americano() instanceof Coffee
    customer.buyCoffee(new CaffeLatte());

    System.out.println("현재 잔액은 " + customer.money + "원 입니다.");
  }
}

class Coffee {
  int price;

  public Coffee(int price) {
    this.price = price;
  }
}

class Americano extends Coffee {
  public Americano() {
    super(4000); // 상위 클래스 Coffee의 생성자를 호출
  }

  public String toString() {return "아메리카노";}; //Object클래스 toString()메서드 오버라이딩
};

class CaffeLatte extends Coffee {
  public CaffeLatte() {
    super(5000);
  }

  public String toString() {return "카페라떼";} // 객체를 출력하려 할때 정보들을 문자열로 출력하는 메소드오버라이딩
};

class Customer {
  int money = 50000;

  void buyCoffee(Coffee coffee) {//Coffee타입을 받는다.
    if (money < coffee.price) { // 물건 가격보다 돈이 없는 경우
      System.out.println("잔액이 부족합니다.");
      return;
    }
    money = money - coffee.price; // 가진 돈 - 커피 가격
    System.out.println(coffee + "를 구입했습니다.");
  }
}
```

## 추상화
> 기존 클래스들의 공통적ㅇ니 요소들을 뽑아서 상위 클래스를 만들어 내는것

> 상향식, 하향식은 상과이 없음. 

### abstract
> abstract라는 키워드가 클래스나 메서드 앞에 사용되는데, 메서드 앞에 붙은 경우 추상메서드,
> 클래스 앞에 붙은경우 추상 클래스라고 불림.
- 추상 메서드 : 메서드의 시그니처만 있고 바디가 없는 메서드를 의미.
- 추상클래스 : 클래스 안에 추상 메서드가 최소 하나 이상 포함돼 있는 경우.
```jshelllanguage
abstract class AbstractExample{ // 추상 메서드가 최소 하나 이상 포함돼 있는 추상 클래스
    abstract void start(); // 메서드 바디가 없는 추상메서드
}
```
### 특징
  - 어떤 클래스에 추상 메서드가 포함되어 있으면 해당 클래스는 자동으로 추상 클래스가 된다.
  - 추상 클래스로 인스턴스를 만들 수 없다.
  - 추상 클래스를 상속할 때 추상 클래스 안의 메소드를 구체화시키지 않으면 생성되지 않는다.
  - 추상클래스를 상속하는 하위클래스는 인스턴스를 만들 수 있다.
  - 클래스 앞에 abstract 키워드를 붙이면 메소드도 abstract를 붙여야한다.(정의하지 않으면)
  - 메소드를 정의하면 추상 클래스 앞에 abstract를 붙이지 않아도 생성된다.
  - 메소드가 없어도 추상 클래스는 생성가능하지만 의미가 없다.
  - 추상 클래스도 멤버변수를 가질 수 있다.
  - 추상 클래스는 하위 클래스로 추상클래스를 가질 수 있다.(추상 메소드 오버라이딩 없이)
  - 사용 이유
    - 상속 관계에 있어서 새로운 클래스를 작성하는데 유용하다.
    - 추상화를 구현하는데 적합하다. 즉 상속계층도의 상층부에 위치할 수혹 추상화의 정도가 높고 아래로
      내려갈수록 구체화된다.
```java
abstract class Animal {
  public String kind; // 추상 클래스안에서 필드를 가짐
  public abstract void sound();
}

class Dog extends Animal { // Animal 클래스로부터 상속
  public Dog() {
    this.kind = "포유류";
  }

  public void sound() { // 메서드 오버라이딩 -> 구현부 완성(이거 안하면 안만들어짐)
    System.out.println("멍멍");
  }
}

class Cat extends Animal { // Animal 클래스로부터 상속
  public Cat() {
    this.kind = "포유류";
  }

  public void sound() { // 메서드 오버라이딩 -> 구현부 완성
    System.out.println("야옹");
  }
}

class DogExample {
  public static void main(String[] args) throws Exception {
    Animal dog = new Dog(); //상속받은 거라 이렇게 만들어도 상관 없음.
    dog.sound();

    Cat cat = new Cat();
    cat.sound();
  }
}

```
### fianl 키워드
> 변경이 불가능하거나 확장되지 않는 성질.

|위치|의미|
|-------|-----------------------------------|
| 클래스 | 변경 또는 확장 불가능한 클래스, 상속 불가|
 메소드 | 오버라이딩 불가|
변수 | 값 변경이 불가한 상수|
```jshelllanguage

  final class FinalEx { // 확장/상속 불가능한 클래스
  final int a = 1; // 변경되지 않는 상수

  final void getNum() { // 오버라이딩 불가한 메서드
    final int Var = a; // 상수
    return a;
  }
}

```
--------------------
## 인터페이스
> 클래스들을 연결시켜주는 접속장치
- 추상 메서드와 상수만을 멤버로 가질수 있다.
### 인터페이스 기본 구조
> 내부의 모든 필드가 public static final로 정의가되고, 모든 메서드가 public abstract로 정의된다.

```jshelllanguage
public interface InterfaceEx {
  public static final int rock =  1; // 인터페이스 인스턴스 변수 정의
  final int scissors = 2; // public static 생략
  static int paper = 3; // public & final 생략

  public abstract String getPlayingNum();
  void call(); //public abstract 생략 
}
```
- 생략된 부분은 자동으로 추가해 준다.

### 인터페이스 구현
> 해당 인터페이스에 정의된 모든 추상메서드를 구현해야 한다. 즉, 메서드 바디를 완성시켜야 한다.
```jshelllanguage
class 클래스명 implements 인터페이스명 {
		... // 인터페이스에 정의된 모든 추상메서드 구현
}
```
### 특징
- 인터페이스를 써서 새로운 객체를 만들 수 있다.
- 인터페이스가 인터페이스를 상속 가능.
- 모든 상위의 인터페이스의 메소드를 포함해야 새로운 클래스를 만들 수 있음.
- 모든 메소드를 포함하고 싶지 않다면 abstract를 써야 함.
- abstract 클래스를 상속하는 클래스를 만들려면 상위 인터페이스의 모든 메소드를 적어야 함.
- default를 써서 추상메소드가 아닌 메소드를 인터페이스에 넣을 수 있음.
- default 메소드는 오버라이드도 가능함.
- 컴파일 에러를 방지할 수 있음.