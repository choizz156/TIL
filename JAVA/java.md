## java의 특징

- 운영체제에 독립적이다.
- 객체 지향 언어(Object Oriented Programming)이다.
- 함수형 프로그래밍 지원
- 자동 메모리 관리(Garbage Collection);

## JVM과 JDK

### JVM(Java Virtual Machine)

- 컴파일러가 자바 언어를 bytcode로 전환하여 JVM에게 가져다 주면 JVM이 운영체제에 맞게 프로그램을 실행시킬 수 있다.

### JDK(Java Development Kit)

- JRE(Java Runtime Environment) : JVM + 표준 클래스 라이브러리
- JDK : JRE + compilers + debuggers
    - 자바 프로그램을 실행만 할 것이면 JRE로 충분하지만 개발을 해야하기 때문에 JDK를 설치해야한다.

--------------------

## Method(=function)

- 데이터를 입력 받아 데이터에 일련의 처리를 가함으로써 만들어낸 결과값을 반환하는 코드들을 묶어 놓은 것.

> A_B(C_D){
> coding..
> }

- A : Return type (void, int, char,String, boolean..)
- B : Method name (camelcase)
- C : parameter type (int,char,String,boolean..)
- D : parameter name (camelcase)

### Method invoke

- 메서드를 호출한다고 표현함.

> add(1,2);
> 메서드 이름에 ()를 붙여서 호출.

- 매개변수 타입과 parameter가 있으면 괄호안에 값(argument)을 넣어야 메서드가 실행됨.

> add(int a, int b){..}
> <br/>
> add(1,2) -> invoke
> <br/>
> add(1) -> not invoke

### Main method

- 자바로 작성한 소스 코드 파일을 실행하면 가장 먼저 실행되는 메서드(진입점 함수).
- 자바에서 main 메서드는 진입점 함수이며, 자바로 어떤 소스 코드를 작성할 때 반드시 main 메서드가 있어야 한다.

------------

## Variable and Type

### Variable

- 값이 변할 수 있는 데이터를 임시적으로 저장하기 위한 수단.
- 값을 저장할 수 있는 메모리 공간에 사용자가 식별할 수 있는 이름을 붙인 것.

### Variable declaration and allocation

- 변수 선언

```java
class practice {
    public static void main(String[] args) {
        int num; //변수 선언
    }
}

```

> 변수를 선언하면 컴퓨터는 값을 저장할 메모리 공간을 확보(type)하고 메모리 공간에 사용자가 입력한 변수 이름을 붙인다.

- 값 할당

```
class practice {
    public static void main(String[] args) {
        int num; // 변수 선언
        num = 1; // 값 할당
    }
}
```

num = 1에서 우항이 좌항에 할당(대입)된다. 수학적 의미가 아니다.

- 초기화 : 변수를 선언하고 처음으로 값을 할당하는 것.

```
class practice {
    public static void main(String[] args) {

        int num; // 변수 선언
        num = 1; // 값 할당 (초기화)
        num = 2; // 값 할당 (재할당)

    }
}

```

```
class practice {
    public static void main(String[] args) {

        int num = 1;// 선언과 동시에 초기화
    }
}

```

### Naming

- 보통 camelCase 사용
- [자바 명명 규칙](https://www.oracle.com/java/technologies/javase/codeconventions-namingconventions.html)

### Constant

- 변하지 말아야 할 데이터를 임시적으로 저장하기 위한 수단.

```
final double PASS_PI=3.14; 
```

final을 이용해 선언하고 대문자에 언더바를 넣어 사용(SCREAMING_SNAKE_CASE).

- 상수를 사용하는 이유
    - 프로그램이 실행되면서 값이 변하면 안되는 경우
    - 코드 가동성을 높이고 싶은 경우
    - 코드 유지관리를 손쉽게 하고자 하는 경우

---------------------

### Type

- 어떤 값의 유형 및 종류를 의미
- 값이 차지하는 메모리 공간의 크기와 값이 저장되는 방식이 결정.

### Primitive and Reference

- 값이 저장되는 방식
    - primitive type : 데이터의 `실제 값`을 저장함.(int, short byte char boolean...)
    - reference type : 저장하고자 하는 값을 임의의 메모리 공간에 저장한 후, 메모리 공간의 `주소값`를 저장함.(객체)

### Literal

- 문자가 가리키는 값 그 자체

> num = 1(literal);

- 정수형, 실수형, 논리형, 문자형, 문자열 등이 있다.

```
float weight=23.3`F`;
        double score=22.34`D`
        long length=20394830945`L`
```

- float, double, long 등을 할당할 때 각각 f,d,L 접미사를 넣어 준다.

---------------------    

### Integer type

|타입|메모리|
|---|-----|
|byte|1byte|
|short|2byte|
|int|4byte|
|long|8byte|

### Overflow and Underflow(integer)

- overflow
    - 자료형이 표현할 수 있는 범위 중 최대값 이상의 값을 표현한 경우가 발생.
    - 최대값을 넘어가면 해당 데이터 타입의 최소값으로 값이 순환한다.
    - ex) byte의 최대값이 127인데 여기서 1을 더하면 최소값인 -128이 된다.

- underflow
    - 자료형이 표현할 수 있는 범위 중 최소값 이하의 값을 표현한 경우.
    - 최소값을 넘어가면 해당 데이터 타입의 최대값으로 값이 순환합니다.

### 데이터 타입의 크기와 표현 범위

> 데이터 타입의 크기가 데이터의 표현 범위를 결정

- 양수와 음수를 표현해야하기 때문에 맨 앞의 비트가 0이면 양수 1이면 음수를 나타낸다.
- 맨 앞의 비트를 제외하고 남은 비트로 숫자를 표현한다.

-------------

### Floating point type

| 타입  |메모리|
|-----|-----|
| float |4byte|
| double |8byte|

- float보다 double이 더 많은 소숫점을 표현할 수 있기 때문에 정밀도가 더 높다.

### Overflow and Underflow(floating point)

- overflow
    - 값이 음의 최소 범위 또는 양의 최대범위를 넘어갔을 때 발생, 값이 무한대가 된다.
- underflow
    - 값이 음의 최대 범위 또는 양의 최소범위를 넘어갔을 때 발생, 값이 0이됨.

 --- ---------

### Boolean type

> true or false 2가지의 값을 갖는다.

- 1byte의 크기를 갖는다.

-------------

### Character type

- char, 2byte 크기를 갖는다.
- 작은 따옴표를 써야한다.
- 문자 타입의 리터럴은 유니코드(ASCII)로 문자를 저장한다.

---------

### Type Casting

- 자동 타입 변환
    - 바이트 크기가 작은 타입에서 큰 타입으로 변환할 때
    - 덜 정밀한 타입에서 더 정밀한 타입으로 변환할 때
  > byte(1) -> short(2)/char(2) -> int(4) -> long(8) -> float(4) -> double(8)
- float은 표현할 수 있는 값이 정수형보다 더 정밀하기 때문에 int나 long에서 자동 변환된다.

- 수동 타입 변환
    - 용량이 더 큰 타입에서 작은 타입으로는 자동으로 타입 변환이 되지 않기 때문에 casting해주어야 함.

```
int a=128;
        byte b=(byte)a;

        System.out.println(b) // -128 최대값 넘어가서
```

------

## String

### String 타입의 변수 선언과 할당

```
String name 1="rudy";
        String name 2=new String("rudy");
```

> String 변수명;으로 선언
> <br/>
> String 변수명 = new String()을 이용하여 할당
> <br/>
> String 변수명 ="문자열";을 이용하여 할당.

```
String name1="jason";
        String name2="jason";

        String name3=new String("jason");
        String name4=new String("jason");
```

- name1과 name2는 동일한 문자열 리터럴을 두 변수에 할당하는 경우, 두 변수는 같은 문자열의 참조값을 공유한다.
  즉, name1과 name2가 저장하게 되는 문자열의 주소값이 같다.
- name3과 name4는 String 클래스의 인스턴스를 생성하게 되면 문자열으 내용이 같아도, 별개의 인스턴스가 따로 생성된다.
  즉, name3과 name4는 서로 다른 인스턴스의 주소값을 저장한다.

### String 클래스의 메서드

- `charAt(위치)`
    - 해당 문자열의 특정 인덱스에 해당하는 문자를 반환합니다.

```
String str=new String("java");

        System.out.println(str.charAt(0)); //j
        System.out.println(str.charAt(1)); //a
        System.out.println(str.charAt(2)); //v
        System.out.println(str.charAt(3)); //a

```

- `compareTo("문자열")`
    - 해당 문자열을 인수로 전달된 문자열과 사전 편찬 순으로 비교한다.
    - 문자열을 비교할 때, 대소문자를 구분하여 비교한다.
    - 문자열이 같으면 0, 해당 문자열이 인수로 전달된 문자열보다 작으면 < 0, 크면 >0
- `compareToIgnoreCase()`
    - 만약 문자열을 비교할 때 대소문자를 구분하지 않음.

```
        String str=new String("abcd");
        System.out.println(str.compareTo("bcef")); //-1
        System.out.println(str.compareTo("abcd")); //0
        System.out.println(str.compareTo("Aced")); // 32
```

- `concat("문자열")`
    - 해당 문자열의 뒤에 인수로 전달된 문자열을 추가한 새로운 문자열을 반환한다.
    - 인수로 전달된 문자열의 길이가 0이면 해당 문자열을 그대로 반환.

```
        String str=new String("Java");
        System.out.println(str.concat("수업"));//Java수업
```

- `indexOf(위치)`
    - 해당 문자열에서 특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스를 반환.(0부터 시작)
    - 해당 문자열에 전달된 문자나 문자열이 포함되어 있지 않으면 -1을 반환.

```
        String str=new String("Oaul Java");
        System.out.println(str.indexOf('o')); //-1
        System.out.println(str.indexOf('a'));//1
        System.out.println(str.indexOf("Java"));//5
```
- `trim()`
  - 해당 문자열의 맨 앞과 맨 뒤에 포함된 모든 공백 문자를 제거해 줍니다.
```
String str = new String(" java   ");
System.out.println(str + "|") //java   |
System.out.println(str.trim() + "|"); //java|
```
- `toLowerCase(),toUpperCase()`
  - 해당 문자열의 모든 문자를 소문자와 대문자로 변환시켜 줍니다.
## StringToKenizer
- 이 클래스는 사용자가 지정한 구분자로 문자열을 쪼개준다. 쪼개어진 문자를 token이라고 부른다.
```
import java.util.StringTokenizer;
class StringTokenizer {
  public static void main(String[] args) {
    String str = "this is a string value";
    StringTokenizer tokenizer = new StringTokenizer(str);
    System.out.println(tokenizer.countTokens()); // 5
    
    while (tokenizer.hasMoreTokens()){
      System.out.print(tokenizer.nextToken());
    } // thisisastringvalue
    System.out.println(tokenizer.countTokens());//0
    

  }
}
```
### int countTokens()
     - 남아있는 토큰의 개수를 반환한다. 
### boolean hasMoreElements(), boolean hasMoreTokens()
    - 둘다 똑같음, 현재 위치 다음에 문자열에서 하나 이상의 토큰이 남아 있는 경우 true, 없으면 false.
### Object nextElement(), String nextToken()
    - 둘다 토큰을 반환한다. nextElement()는 object를 nextToken()은 String을 반환한다.

## StringBuilder, StringBuffer
### StringBuilder
> 한번 생성된 클래스의 인스턴스는 불변객체가 된다. 그래서 여러 개의 문자를 더할 때 매번 새로운 인스턴스를 생성해야 한다.
> <br/>
> 너무 많은 문자열이 있다면 인스턴스 생성 과정은 비효율적이 되고 StringBuilder로 해결 가능하다.

```java
public class Main{
  public static void main(String[] args) {
    StringBuilder stringBuilder = new StringBuilder();
    stringBuilder.append("ㅇfdf").append("dfdf");
    String str = stringBuilder.toString();
    System.out.println(stringBuilder); //ㅇfdfdfdf
    System.out.println(str);//ㅇfdfdfdf
    
  }
}

```
StringBuilder의 객체를 생성한 후, append()로 연결하고자 하는 문자열을 넣어서 호출, 문자열을 출력하거나 변수에 문자열을 할당할 때는
toString() 메서드를 활용한다.

### StringBuffer
>StringBuffer 클래스의 인스턴스는 값을 변경할 수도 있고 추가도 가능하다.
> <br/> 
> 내부적으로 버퍼라고 하는 독립적인 공간을 가진다. 기본적으로 16개의 문자를 저장할 수 있는 크기이고,
> <br/>
> 생성자를 통해 그 크기를 별도로 설정할 수도 있다. 기본적으로 사용자가 설정한 크기보다 16개의 문자 공간을 더 확보한다.

- `append("문자열")`
  - 인수로 전달된 값을 문자열로 변환한 후 , 해당 문자열의 마지막에 추가한다. concat()과 비슷하지만 내부적인 처리속도가 빠르다.
- `capacity()`
  - StringBuffer 인스턴스의 현재 버퍼 크기를 반환한다.
```
StringBuffer str1= new StringBuffer();
StrringBuffer str2 = new StringBuffer("java");
System.out.println(str1.capacity()); //16
System.out.println(str2.capacity)(); // 20
```
길이가 4인 문자열로 StringBuffer 인스턴스를 생성하면 기본적으로 생성되는 여유 버퍼 크기인 16에 
문자 길이인 4가 더해져 저장 공간이 20이 되는 것을 알 수 있다.
- `delete(시작,끝+1)`
  - 전달된 인덱스에 해당하는 부분 문자열을 해당 문자열에서 제거한다.
- `deleteCharAt()`
  - 특정 위치의 문자 한 개만 제거할 수도 있다.
- `insert(시작,"문자열"")`
  - 인수로 전달된 값을 문자열로 변환 후, 해당 문자열의 지정된 인덱스 위치에 추가합니다.