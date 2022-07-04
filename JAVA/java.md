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
class practice{
    public static void main(String[] args) {
        int num; //변수 선언
    }
}

```
> 변수를 선언하면 컴퓨터는 값을 저장할 메모리 공간을 확보(type)하고 메모리 공간에 사용자가 입력한 변수 이름을 붙인다.
- 값 할당
```java
class practice {
    public static void main(String[] args) {
        int num; // 변수 선언
        num = 1; // 값 할당
    }
}
```
num = 1에서 우항이 좌항에 할당(대입)된다. 수학적 의미가 아니다.
 
- 초기화 : 변수를 선언하고 처음으로 값을 할당하는 것.
```java
class practice {
    public static void main(String[] args) {
        
        int num; // 변수 선언
        num = 1; // 값 할당 (초기화)
        num = 2; // 값 할당 (재할당)
        
    }
}

```
```java
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
```java
final double PASS_PI = 3.14; 
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
```java
float weight = 23.3`F`;
double score = 22.34`D`
long length = 20394830945`L`
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
  
```java
int a =128;
byte b = (byte)a;

System.out.println(b) // -128 최대값 넘어가서
```
