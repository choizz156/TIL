## enum(enumerateted type)

> - 여러 상수들을 보다 편리하게 선언하고 관리할 수 있게 해주며, 상숩명의 중복을 피하고, 타입에 대한 안정성을 보장한다.
    > <br/>
> - 간결하고 가독성이 좋은 코드를 작성할 수 있고, swich문에서도 작동 가능하다.

> enum 열거형이름 {상수명1,상수명2,...}

- 순서대로 상수에 정수값이 0부터 할당된다.
- `열거형이름.상수명`을 통해서 선언된 상수에 접근 가능하다.
- enum 객체는 인스턴스 변수가 될 수 있고 메소드에 들어 갈 수 있다.

```jshelllanguage
enum Seasonts {SPRING, SUMMER, FALL, WINTER} // enum선언, 보통 대문자를 사용한다.

    public class Main {
        public static void main(String[] args) {
            Seasons seasons = Seasons.SPRING; // enum에 들어간 요소들은 열거 객체이다.
            switch (seasons) {
                case SPRING:
                    System.out.println("봄");
                case SUMMER:
                    System.out.println("여름");
                case FALL:
                    System.out.println("가을");
                case WINTER:
                    System.out.println("겨울)";
                    break;
            }
        }
    }
// 봄 출력

```

### 메소드

- java.lang.Enum에 정의돼 있음.
    - `name()` : 열거 객체가 가지고 있는 **문자열**을 리턴하며, 리턴되는 문자열은 열거타입을 정의할 때 사용한 상수 이름과 동일하다.
    - `ordinal()` : 열거 객체의 **순번(0부터 시작)을** 리턴합니다.
    - `compareTo(비교값)`: 주어진 매개값과 비교해서 **순번 차이**를 리턴합니다
    - `valueOf(String name)`: 주어진 문자열의 **열거 객체**를 리턴합니다.
    - `values()` : 모든 열거 객체들을 **배열**로 리턴합니다.

```java
enum Level {
    Low, MEDIUM, HIGH
}

public class enums {
    public static void main(String[] args) {
        Level level = Level.MEDIUM;

        Level[] allLevels = Level.values(); // 열거 객체들을 배열로 리턴함.
        for (Level a : allLevels) {
            System.out.printf("%s=%d%n", a.name(), a.ordinal());// name메소드로 객체가 가지고있는 문자열이 리턴,
            // ordinal()로 열거 객체의 순번을 리턴
        }
        Level findLevel = Level.valueOf("Low"); // LEVEL에서 LOW의 열거 객체를 리턴함.
        System.out.println(findLevel);//LOW
        System.out.println(Level.LOW == Level.valueOf("Low")); // true
    }
}

```

### 순서값 할당

```java
enum Season {
    WINTER(4), SPRING(3), FALL(1), SUMMER(2) /* ordinal을 사용하면 열거형 값의 위치에 따라 순서값이 달라지기 때문에 각 열거형 값에
                                           숫자를 할당한다.*/
    private int value; // enum안에서도 필드를 쓸 수 있다.

    public int getValue() { // 메소드도 쓸 수 있다.
        return value;
    }

    private Season(int value) { // 생성자를 이용해서 열거형 값에 다른 값을 할당할 수 있다.
        this.value = value;
    }
    }

public class Enums {

    Season season;

    public static void main(String[] args) {
        System.out.println(Season.SPRING.ordinal()); // 1이 출력
        System.out.println(Season.SPRING.getValue());// 할당된 값인 3이 출력
    }
}


```

----------------------

## Annotation

> 프로그램에 정보 전달을 목적으로 함.

```jshelllanguage

    @Test  // 아래의 메서드가 테스트 대상임을 테스트 프로그램에게 알리는 애너테이션
    public void run() {
    }

    public void stpe() {
    } // 애너테이션이 붙여진 run메서드만 적용됨. 명확한 타멧이 있고 그 외에는 없는 것임.
```

### 애너테이션의 종류

#### 표준 애너테이션: 자바에서 기본적으로 제공하는 애너테이션.

- `@Override` :    컴파일러에게 메서드를 오버라이딩하는 것이라고 알린다.

```jshelllanguage
class Super {
    void run() {
    }
}
    class Sub extends Super {
        @Override
        void rnu() {
        } // 오버라이딩중 오타가 발생했을 때 컴파일 에러가 생긴다.
    }
```

- `@Deprecated`: 기존 메서드를 하위 버전 호환성 문제로 삭제하기 곤란해 남겨두어야만 하지만 더 이상 사용하는 것을 권장하지 않을 때 사용.

```jshelllanguage
class OldClass {
    @Deprecated
    int oldField;

    @Deprecated
    int getOldField() {
        return oldField;
    }

    ;
}
    Note:
    파일명.java uses or overrides a deprecated API. //@Deprected가 붙은 코드를 사용하면 이러한 메시지가 뜬다.
            Note:Recomplie with-Xlint:deprecation for details

```

- `@FunctionalInterface`: 함수형 인터페이스 선언이 바르게 선언됐는지 확인하도록 한다.

```jshelllanguage

    @FunctionalInterface
    public interface Runnable {
        public abstract void run(); // 하나의 추상 메서드만 사용가능하다.
    }
```

- `@SuppressWarning`: 컴파일러가 경고메세지를 나타내지 않는다.

    - `@SuppressWarings(”all”)` :    모든 경고를 억제
    - `@SuppressWarings(”deprecation”)` :    Deprecated 메서드를 사용한 경우 나오는 경고 억제
    - `@SuppressWarings(”fallthrough”)` :    switch문에서 break 구문이 없을 때 경고 억제
    - `@SuppressWarings(”finally”)` :    finally 관련 경고 억제
    - `@SuppressWarings(”null”)` :    null 관련 경고 억제
    - `@SuppressWarings(”unchecked”)`    :검증되지 않은 연산자 관련 경고 억제
    - `@SuppressWarings(”unused”)` :    사용하지 않는 코드 관련 경고 억제
    - @SuppressWarnings({"deprecation", "unused", "null"}) : 한번에 할 수 도 있다.

    <br/>

#### 메타 애너테이션: 애너테이션에 붙이는 애너테이션으로, 애너테이션을 정의하는 데에 사용.

- `@Target`:    애너테이션을 정의할 때 적용 대상을 지정하는데 사용한다.

```jshelllanguage
import static java.lang.annotation.ElementType.*;
//import문을 이용하여 ElementType.TYPE 대신 TYPE과 같이 간단히 작성할 수 있다.

    @Target({FIELD, TYPE, TYPE_USE})    // 적용대상이 FIELD, TYPE, TYPE_USE
    public @interface CustomAnnotation {
    }    // CustomAnnotation을 정의

    @CustomAnnotation    // 적용대상이 TYPE인 경우 사용자 애너테이션을 적용.
    class Main {

        @CustomAnnotation    // 적용대상이 FIELD인 경우 사용자 애너테이션을 적용.
        int i;
    }
``` 

- `@Documented`: 애너테이션 정보를 javadoc으로 작성된 문서에 포함시킨다.

```jshelllanguage

    @Documented
    @Target(ElementType.Type)
    public @interface CustomAnnotation {
    }
```

- `@Inherited` : 애너테이션이 하위 클래스에 상속되도록 한다.

```jshelllanguage

    @Inherited // @SuperAnnotation이 하위 클래스까지 적용
    @interface SuperAnnotation {
    }

    @SuperAnnotation
    class Super {
    }

    class Sub extends Super {
    } // Sub에 애너테이션이 붙은 것으로 인식
```

- `@Retention` : 애너테이션이 유지되는 기간을 정하는데 사용한다.
    - SOURCE : 소스 파일에 존재, 클래스파일에는 존재하지 않음
    - CLASS :    클래스 파일에 존재, 실행시에 사용불가, 기본값
    - RUNTIME : 클래스 파일에 존재, 실행시에 사용가능

```jshelllanguage

    @Target(ElementType.METHOD)
    @Retention(RetentionPolicy.SOURCE)
//오버라이딩이 제대로 되었는지 컴파일러가 확인하는 용도 
//클래스 파일에 남길 필요 없이 컴파일시에만 확인하고 사라짐, 실행 시에는 더이상 사용되지 않음.
    public @interface Override() {
    }
```

- `@Repeatable` : 애너테이션을 반복해서 적용할 수 있게 한다.

```jshelllanguage
   @interface Works {  /*같은 이름의 애너테이션이 여러번 적용될 수 있기 때문에. 이 애너테이션들을 하나로 묶어주는 
                       애너테이션을 별도로 작성*/
    Work[] value();
}

    @Repeatable(Works.class) //컨테이너 애너테이션 지정. Works 애너테이션을 여러 번 반복해서 쓸 수 있게 한다.  
    @interface Work {
        String value();
    }

    @Work("코드 업데이트") // 사용자 타입 애너테이션 Work를 정의 하고 이것을 여러번 사용할 수 있도록 한다.
    @Work("메서드 오버라이딩")
    class Main {  
	...생략 ...
    }
```

  <br/>
- 사용자 정의 애너테이션: 사용자가 직접 정의하는 애너테이션.

---------------------

## 람다식

> 메서드를 하나의 식으로 표현한 것으로 코드를 간결하면서 명확하게 표현할 수 있다는 장점이 있음.

```jshelllanguage
int sum(int num1, int num2) {
    return num1 + num2;
}
    >>(int num1,int num2)->{return num1+num2;} //반환 타입과 메서드명을 없애고 화살표를 쓴다.
    >>(num1,num2)->num1+num2 /* 반환값이 있는 메서드의 경우에는 리턴문과 문장 뒤에오는 세미콜론을 생략가능함.
                            실행문이 하나만 존재할 때는 중괄호를 생략할 수 있다.
                            매개변수 타입을 쉽게 유추할 수 있는 경우에는 매개변수의 타입을 생략할 수 있다.*/

```

### 함수형 인터페이스

> - 메서드는 클래스 안에 존재해야 하기 때문에 독립적으로 있을 수 없고 클래스 객체를 먼저 생성해야함.
    > <br/>
> - 람다식 또한 객체이고 이름이 없기 때문에 익명 클래스라고 할 수 있다.
    > <br/>
> - 함수형 인터페이스에는 단 하나의 추상 메서드만 선언될 수 있다. 즉, 람다식과 인터페이스의 메서드가 1:1로 매칭된다.

- 문제점

```jshelllanguage
(num1, num2) -> num1 + num2

    new Object() { // 람다식을 익명클래스로 표현
        int sum(int num1, int num2) {
            return num1 + num2;
        }
    }
```

```jshelllanguage
Object obj = new Object() { // Object클래스에 sum메서드가 없기 때문에 sum메서드를 사용할 방법이 없음. -> 함수형 인터페이스 사용.
    int sum(int num1, int num2) {
        return num1 + num2;
    }
};
```

- 해결책
    - 함수형 인터페이스를 사용하여 이 문제를 해결한다.

```jshelllanguage

    @FunctionalInterface // 컴파일러가 인터페이스가 바르게 정의되있는지 확인할 수 있도록 써주는 것이 좋다.
    interface EF {
        public abstract int sum(int num1, int num2);
    }

    EF eF = (num1, num2) -> num1 + num2 // 함수형 인터페이스 참조변수에 람다식을 넣는다.
    System.out.println(eF, sum(10, 15)) // 인터페이스의 sum메서드를 쓸 수 있게 된다.
```

#### 매개변수와 리턴값이 없는 람다식

```jshelllanguage

    @FunctionalInterface
    public interface MyFI {
        public void accept();
    }
    // MyFI ex = () -> {}; 이 형식으로 만들어 진다.
    MyFI ex;
    ex = () -> {
        String str = "aaa";
        System.out.println(str);
    }
    ex.accept(); // aaa 출력

    ex = () -> System.out.println("bbb");
    ex.accept(); //bbb 출력
```

- `Runnable 인터페이스`

```jshelllanguage
public interface Runnable {
    void run();
}
    Runnable runnable = () -> System.out.println("ur");
    runnable.run();
```

#### 매개변수가 있는 람다식

```jshelllanguage

    @FunctionalInterface
    public interface MyFI {
        public void accept(int x);
    }
    //MyFI ex = (매개변수) -> {}; 이 형식으로 만들어 진다.
    MyFI ex;
    ex = (e) -> {
        int result = e * 3;
        System.out.println(result);
    }
    ex.accept(2); // 6 출력 

    ex = (e) -> System.out.println(e * 4);
    ex.accept(3); // 12 출력
```

- `Consumer`

```jshelllanguage
public interface Consumer<T> {
    void accept(T t);

    default Consumer<T> andThen(Consumer<? super T> after) {
        Objects.requireNonNull(after);
        return (T t) -> {
            accept(t);
            after.accept(t);
        };
    }
}

    Consumer < String > pS = t -> System.out.println("hate " + t + "?");
    printString.accept("you"); //hate you? 출력
```

#

#### 리턴값이 있는 람다식

```jshelllanguage

    @FunctionalInterface
    public interface MyFI {
        public int accept(int x, int y);
    }
    //MyFI ex = (매개변수) -> {return ~}; 이 형식으로 만들어 진다.
    MyFI ex;
    ex = (x, y) -> {
        int result = x + y;
        return result;
    };
    int result1 = ex.accept(2, 5);

    ex = (x, y) -> {
        return x + y
    };
    int result2 = ex.accept(2, 5);

    ex = (x, y) -> x + y
    int result3 = ex.accept(2, 5);

    ex = (x, y) -> sum(x, y);
    int result4 = ex.accept(2, 5);


    public static int sum(int x, int y) {
        return x + y;
    }

```

- `Function`

```jshelllanguage
public interface Function<T, R> { // t타입의 인자를 받고 r타입의 인자를 리턴.
    R apply(T t);

    default <V> Function<V, R> compose(Function<? super V, ? extends T> before) {
        Objects.requireNonNull(before);
        return (V v) -> apply(before.apply(v));
    }

    default <V> Function<T, V> andThen(Function<? super R, ? extends V> after) {
        Objects.requireNonNull(after);
        return (T t) -> after.apply(apply(t));
    }

    static <T> Function<T, T> identity() {
        return t -> t;
    }
}

    Function < Integer,Integer>multiply=(value)->value*2;
    Integer result=multiply.apply(3);
    System.out.println(result);
```

### 메서드 레퍼런스

> 불필요한 매개변수를 제거할 때 사용

```jshelllanguage
//클래스이름 :: 메서드 이름;
    System.out::println; // 이것도 익명클래스의 객체라고 봐야함.
```

#### 정적 메서드와 인스턴스 메서드 참조

- 정적 메서드

> 클래스 :: 메서드

- 인스턴스 메서드

> 참조 변수 :: 메서드

```java
import java.util.function.IntBinaryOperator;//실제로 있는 함수형 메소드

class Calculator {
    public static int staticMethod(int x, int y) {//정적메서드
        return x + y;
    }

    public int instanceMethod(int x, int y) { //인스턴스메서드
        return x * y;
    }
}


public class MR {
    public static void main(String[] args) {
        IntBinaryOperator operator;
        operator = Calculator::staticMethod; // 정적메서드 = 클래스이름::메서드
        System.out.println(operator.applyAsInt(3, 5)); // 8
        Calculator cal = new Calculator(); // 인스턴스 메서드 = 인스턴스이름 :: 메서드
        operator = cal::instanceMethod;
        System.out.println(operator.applyAsInt(3, 5)); // 8
    }

}
```

#### 생성자 참조

> 생성자를 참조한다는 것은 객체 생성을 의미한다.

> (a,b) ->{return new 클래스(a,b);};
> <br/>
> `클래스 :: new` 로 기술한다.

- 생성자가 오버로딩 되어 여러개 있을 경우 컴파일러는 함수혀 인터페이스의 추상 메서드와 동일한 매개 변수 타입과 개수를 가지고 있는 생성자를
  찾아 실행한다.

```java
 class Member {
    private String name;
    private String id;

    public Member() {
        System.out.println("Member() 실행");
    }

    public Member(String id) {
        System.out.println("Member(String id) 실행");
        this.id = id;
    }

    public Member(String name, String id) {
        System.out.println("Member(String name, String id) 실행");
        this.id = id;
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public String getId() {
        return id;
    }
}


public class CR {
    public static void main(String[] args) {
        Function<String, Member> function1 = Member::new;
        Member member1 = function1.apply("dddd"); // Memeber(String id) 생성자를 실행

        BiFunction<String, String, Member> function2 = Member::new;
        Member member2 = function2.apply("dfdf", "dfdf");// Member(String name, String id) 생성자 실행
    }
}
```

## Stream

> - 배열, 컬렉션의 저장 요소를 하나씩 참조해서 람다식으로 처리할 수 있도록 해주는 반복자.
    > <br/>
> - 다량의 복잡한 데이터에 복잡한 연산을 수행하면서, 가독성과 재사용성이 높은 코드를 작성할 수 있다.

### 특징

- 선언형으로 데이터 소스를 처리한다.
    - 선언형 방식으로 코드를 작성하면 내부 동작 원리를 모르더라도 코드가 무슨 일을 하는지 이해할 수 있다.
    - "어떻게"의 영역은 추상화 되어있고 `무엇을` 수행하는 지에 중점을 둔다.
- 변수의 변이는 피한다.
- 람다식으로 요소 처리 코드를 제공한다.
    - Stream이 제공하는 대부분의 요소 처리 메서드는 함수형 인터페이스 매개타입을 가지기 때문에 람다식이나 메서드 참조를 이용해서 요소 처리
      내용을 매개값으로 전달할 수 있다.

 ```java
public class Student {
    private String name;
    private int score;

    public Student(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public int getScore() {
        return score;
    }
}


public class StreamLambdaExample {
    public static void main(String[] args) throws Exception {
        List<Student> list = Arrays.asList(new Student("a", 34), new Student("bb", 365));

        Stream<Student> stream = list.stream(); // 람다식이 객체가 돼어 매개변수로 들어감.
        stream.forEach(s -> {
                    String name = s.getName();
                    int score = s.getScore();
                    System.out.print(name + score);//a34bb365
                }
        );

    }
}

``` 

- 내부 반복자(internal iterator)를 사용해서 병렬처리가 쉽다.
    - 컬렉션 내부에서 요소들을 반복시키고 개발자는 요소당 처리해야할 코드만 제공하는 코드 패턴.
    - 개발자는 요소 처리 코드에만 집중하면 된다.
    - 요소들의 반복 순서를 변경하거나 멀티 코어 CPU를 최대한 활용하기 위해 요소들을 분배시켜 병렬 작업을 할 수 있게 도와주기 때문에
      하나씩 처리하는 순차적 외부 반복자보다 효율적으로 요소를 반복시킬 수 있다.
    - 병렬 처리 : 한 가지 작업을 서브 작업으로 나누고, 서브 작업들을 분리된 스레드에서 병렬적으로 처리하는 것.

- 중간 연산과 최종 연산을 할 수 있다.

### 파이프라인 구성(.)

> 대량의 데이터를 가공해서 축소하는 것을 리덕션(reduction)이라고 하는데, 컬렉션의 요소를 리덕션의 결과물로 바로 집계할 수 없을 때는
> 중간연산이 필요하다.

#### 파이프 라인

> 여러개의 스트림이 연결돼 있는 구조. 최종 연산을 제외하고 모두 중간 연산 스트림이다.

```jshelllanguage
import java.lang.reflect.Member;
    double ageAve = list.stream() //오리지널 스트림
            .filter(m -> m.getGender() == Member.MALE) // 중간 연산 스트림
            .mapToInt(Member::getAge)// 중간 연산 스트림
            .average()//최종연산
            .getAsDouble();
```

### 스트림 생성, 중간 연산, 최종 연산

#### 스트림 생성

> Collection 인터페이스에는 stream()이 정의돼 있기 때문에 , Collection 인터페이스를 구현한 객체들은 모두 이 메서드를 이용해 스트림을 생성할 수 있다.

```jshelllanguage
List < String > list = Arrays.asList("a", "b", "c");
    Stream < String > listStream = list.stream(); // 스트림 생성
    listStream.forEech(System.out::println);// 스트림의 요소 출력
```

- 배열을 원소들을 소스로 하는 Stream을 생성하기 위해서는 of나 Arrays의 stream메서드를 사용한다.

```jshelllanguage
Stream < String > stream = Stream.of("a", "b", "c"); //가변인자
    Stream < String > stream = Stream.of(new String[]{"a", "b", "c"});
    Stream < String > stream = Arrays.stream(new String[]{"a", "b", "c"});
    Stream < String > stream = Arrays.stream(new String[]{"a", "b", "c"}, 0, 3); //end 범위 미포함
```

- 스트림은 데이터 소스로 부터 데이터를 읽기만 할 뿐 변경하지 않는다.
- 스트림은 일회용이다. 한번 사용하면 다시 새로운 스트림을 만들어야 한다.

#### 중간 연산

- 연산 결과를 스트림으로 반환하기 때문에 연속해서 여러 번 수행할 수 있다.
- `filter()` : Stream에서 조건에 맞는 데이터만을 정제하여 더 작은 컬렉션을 만들어 낸다. 매개값으로 조건이 주어지고 참이 되는 요소만 필터링한다.
- `distinct()` : 중복된 데이터가 존재하는 경우, 중복을 제거하기 위해 사용한다.
- `map()` : 기존의 스트림 요소들을 대체하는 요소로 구성된 Stream을 형성하는 연산.
- `flatMap` : 스트림의 스트림을 하나의 스트림으로 변환 시킨다.
- `sorted()` : 오름차순, 알파벳순 정렬을 한다.
    - Comparator 인자 없이 호출할 경우 오름 차순으로 정렬되며. 내림차순으로 정렬하기 위해서는 Comparator.reverseOrder()를 인자로 사용한다.
- `peek()` : 요소를 하나씩 돌려가면서 출력, 중간 연산자이므로 forEach와 다르게 연속해서 사용가능. 디버깅하고자 할때 사용.

```jshelllanguage
jshell > List < Integer > numbers = List.of(2, 3, 6, 234, 1, 7, 5)
    numbers ==>[2,3,6,234,1,7,5]

    jshell>numbers.stream().sorted().forEach(e->System.out.println(e)); // 오름차순 정렬 된다.
    1
    2
    3
    5
    6
    7
    234

    jshell>List<Integer>numbers=List.of(2,3,3,5,234,5)
    numbers==>[2,3,3,5,234,5]

    jshell>numbers.stream().distinct().forEach(e->System.out.println(e));//중복제거 된다.
    2
    3
    5
    234

    jshell>List<Integer>numbers=List.of(2,3,3,5,234,5,45,2334,6)
    numbers==>[2,3,3,5,234,5,45,2334,6]

    jshell>numbers.stream().sorted().distinct().forEach(e->System.out.println(e)); // 동시에 여러개를 쓸 수 있다.
    2
    3
    5
    6
    45
    234
    2334

    jshell>numbers.stream().map(num->num*num).forEach(e->System.out.println(e));// 새로운 스트림을 반환한다.
    4
    9
    9
    25
    54756
    25
    2025
    5447556
    36

    jshell>numbers.stream().filter(e->e%2==0).distinct().forEach(e->System.out.println(e)); // 필터로 조건을 넣었다.
    2
    234
    2334
    6

    jshell>numbers.stream().sorted(Comparator.reverseOrder()).forEach(e->System.out.println(e));
    //Comparator.reverseOrder를 이용해서 내림차순 했다.
    2334
    234
    45
    6
    5
    5
    3
    3
    2

```

#### 최종연산

- 한 번만 연산 가능
- `forEach` : 파이프라인 마지막에서 요소를 하나씩 연산한다.
- `match` : 특정한 조건을 충족하는지 검사한다. boolean으로 반환한다.
    - `allMatch`() : 모든 요소들이 매개값으로 주어진 Predicate의 조건을 만족하는지 조사
    - `anyMatch`() : 최소한 한 개의 요소가 매개값으로 주어진 Predicate의 조건을 만족하는지 조사
    - `noneMatch`() : 모든 요소들이 매개값으로 주어진 Predicate의 조건을 만족하지 않는지 조사

```jshelllanguage
jshell > int[] inArr = {2, 4, 6};
    inArr ==>int[3]{2,4,6}

    jshell>boolean result=Arrays.stream(inArr).allMatch(a->a%2==0);
    result==>true // 모두 짝수

    jshell>boolean result=Arrays.stream(inArr).allMatch(a->a%3==0);
    result==>false // 모두 3의 배수는 아님

    jshell>boolean result=Arrays.stream(inArr).anyMatch(a->a%3==0);
    result==>true // 3의 배수가 하나 있음

    jshell>boolean result=Arrays.stream(inArr).noneMatch(a->a%3==0);
    result==>false // 3의 배수가 없는 것이 아님.

```

- `sum(), count(), average(), max(), min()`

```jshelllanguage
int[] intArr = {1, 2, 3, 4, 5};

    long count = Arrays.stream(intArr).count(); //5

    long sum = Arrays.stream(intArr).sum(); // 15

    double avg = Arrays.stream(intArr).average().getAsDouble(); // 3.0

    int max = Arrays.stream(intArr).max().getAsInt(); // 5

    int min = Arrays.stream(intArr).min().getAsInt(); // 1

    int first = Arrays.stream(intArr).findFirst().getAsInt(); //1

```

- `reduce()`

> 하나로 응축하는 방식. 앞의 두 요소의 연산 결과를 바탕으로 다음 요소와 연산.

- 초기값이 있는 경우 초기값과 스트림의 첫 번째 요소로 첫 연산을 수행.
- 초기값이 없는 경우 스트림의 첫 번째 요소와 두 번째 요소로 첫 연산을 수행.

```jshelllanguage
int[] intArr = {1, 2, 3, 4, 5};

    Arrays.stream(intArr).sum(); // 15


    Arrays.stream(intArr)
            .map(el -> el * 2)
            .reduce((a, b) -> a + b) // 스트림에 요소가 없을 경우 예외가 발생함.
            .getAsInt(); // 30

    Arrays.stream(intArr)
            .map(el -> el * 2)
            .reduce(0, (a, b) -> a + b); // 30 스트림에 요소가 없을 경우 초기값을 리턴함.

```

- `collect`

> Stream의 요소들을 List나 Set, Map 등 다른 종류의 결과로 수집하고 싶은 경우 사용.

```java
 class Student {
    public enum Gender {Male, Female}

    ;
    private String name;
    private int score;
    private Gender gender;

    public Student(String name, int score, Gender gender) {
        this.name = name;
        this.score = score;
        this.gender = gender;
    }

    public Gender getGender() {
        return gender;
    }

    public String getName() {
        return name;
    }

    public int getScore() {
        return score;
    }
}

public class CollectExample {
    public static void main(String[] args) throws Exception {
        List<Student> totalList = Arrays.asList(
                new Student("김코딩", 10, Student.Gender.Male),
                new Student("김인기", 8, Student.Gender.Male),
                new Student("이자바", 9, Student.Gender.Female),
                new Student("최민선", 10, Student.Gender.Female)
        );

        List<Student> maleList = totalList.stream()
                .filter(s -> s.getGender() == Student.Gender.Male)
                .collect(Collectors.toList()); //List로 나옴 순서지켜서

        maleList.stream().forEach(n -> System.out.println(n.getName()));

        Set<Student> femaleSet = totalList.stream()
                .filter(s -> s.getGender() == Student.Gender.Female)
                .collect(Collectors.toCollection(HashSet::new)); // set으로 나옴. 순서 상관 없음

        femaleSet.stream().forEach(n -> System.out.println(n.getName()));
    }
}
```

---------

## Optional<T>

> null 값으로 인해 에러가 발생하는 현상을 객체 차원에서 효율적으로 방지하고자 도입됐다.

- 모든 타입의 객체를 담을 수 있는 wrapper 클래스이다.

```jshelllanguage
public final class Optional<T> {
    private final T value; // T타입의 참조변수
}
```

- Optional 객체를 생성하려면 `of()`나 참조변수의 값이 null일 가능성이 있다면, `ofNullable()`을 사용한다.

```jshelllanguage
Optional < String > opt1 = Optional.ofNullable(null);
    Optional < String > opt2 = Optional.ofNullable("123");
    System.out.println(opt1.isPresent()); //Optional 객체의 값이 null인지 여부를 리턴한다. false
    System.out.println(opt2.isPresent()); //true

```

- 참조변수를 기본값으로 초기화하려면 `empty()` 메서드를 사용한다.
- 참조변수의 값이 null일 가능성이 있다면 `orElse()`메서드를 사용해 디폴트 값을 지정할 수 있다. get()이랑 같이 못씀.

```jshelllanguage
Optional < String > opt3 = Optional.<String>empty();
    String name = Optional.ofNullable(nullName).orElse("aaa");
```

- 객체에 저장된 값을 가져오려면 `get()`을 사용한다.

```jshelllanguage
jshell > List.of(23, 45, 67, 12).stream().filter(num -> num % 2 == 0).max((n1, n2) -> Integer.compare(n1, n2))
    $1 ==>Optional[12] //스트림은 optional 값을 반환한다.
    jshell>$1.get() //get을 사용하여 optional에서 값을 추출할 수 있다.
    $2==>12
```

- 스트림과 유사하게 여러 메서드를 연결해서 작성할 수 있다.

```jshelllanguage
public class OptionalExample {
    public static void main(String[] args) {
        List<String> languages = Arrays.asList(
                "Ruby", "Python", "Java", "Go", "Kotlin");
        Optional<List<String>> listOptional = Optional.of(languages);

        int size = listOptional
                .map(List::size) //리스트의 크기로 바꾼다.
                .orElse(0); //초기값을 0으로 한다.
        System.out.println(size); //list의 크기 5
    }
}
```
