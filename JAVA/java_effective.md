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
