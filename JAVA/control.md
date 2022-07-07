# 목차
- [if](#if)
  - [else if](#else-if)
- [Switch](#switch)
  - [fall through (중복 코드 방지)](#fall-through-중복-코드-방지)
- [삼항 연산](#삼항-연산) 

# Control Folw Statement(제어문)

## 조건문

### if

- condition의 값은 참이면 true, 거짓이면 false로 나온다.
- 조건문에는 비교연산자가 사용된다.
- 조건문에는 정수만을 쓸수 없다.

```
i = 10;
i > 5;
true;

i < 5;
false;
```

- if 구문

```jshelllanguage
if (condition) {
    statement
}
// condition이 true 일때 statement가 실행

```

```jshelllanguage
int i = 5;

    if (i >= 10) {
        System.out.println("i is less than 10");
    }
    // 조건이 거짓이기 때문에 출력되지 않음.
    --------------------------------------
    if (i > 3) {
        System.out.println("i is less than 10");
    }
    // 조건이 참이기 때문에 i is less than 10이 출력
    -----------------------
    if (i == 4)
        1)i=i+4;
    2)i++;
    3)System.out.println(i);

// if문 한 개에 하나의 statement만 고려되기 때문에
// 이 경우 조건이 false이기 때문에 1)은 수행되지 않는다.
// 하지만 2)와 3)은 조건에 관계없이 수행된다.

```

- if문은 보통 하나의 조건문에 하나의 스테이트먼트를 갖지만,
  여러개의 statement를 가지기 위해 `{}`블록을 한다.


### else if
    - if나 else-if 블록 중 하나만 실행한 후 빠져나간다.
    - 상이한 조건 여러개 중 하나만 특정 조건에 참이되는 케이스에
      사용하기 좋다.

```jshelllanguage
int i = 10;

    if (i == 10) {
        System.out.println("true"); // i = 10이르모 if 블럭을 실행후 제어문을 나감
    } else if (i > 10) {
        System.out.println("not true");
    } else {
        System.out.println("나가");
    }

```

## switch

- 조건문에는 변수가 들어간다.(int,byte,char,short,String,enum)
- 조건에 맞는 case에 가서 그 statement를 수행한다.
- 조건에 맞는 case가 없다면 default에 있는 statement를 수행한다.

```jshelllanguage

    switch (condition) {
        case 1:
            <statements >
            break;
        case 2:
            <statements >
            break;
        //...
        default:
            <statements >
            break;
    }

```

```jshelllanguage
int i = 5;

    switch (i) {
        case 1:
            System.out.println("1");
        case 5:
            System.out.println("5");
        default:
            System.out.println("나가");
    }
    5
    나가

            i = 1;

    jshell > switch (i) {
        case 1:
            System.out.println("1");
        case 5:
            System.out.println("5");
        default:
            System.out.println("나가");
    }
    1
    5
    나가

```

- break문을 쓰지 않으면 제어문을 빠져나가지 않아 바로 아래의
  statement도 모두 출력된다.(`fall through)`



### fall through (중복 코드 방지)

```jshelllanguage
int number = 2;

    switch (number) {
        case 1:
            System.out.println(1);
        case 2:
        case 3:
            System.out.println("Number is 2 or 3");
            break;
        default:
            System.out.println("default");
            break;
    }

            >> Number is 2 or 3
//number가 2나 3일때 출력된다.

```

### 삼항 연산

- 출력되는 것은 같은 타입이어야 한다.

```jshelllanguage
condition ? true일때 : false일때;
```

```jshelllanguage
int i = 6;
    String ifEven = i % 2 == 0 ? "yse" : "no";
    >> yes 출력
   
    i = 5;
    String ifEven = i % 2 == 0 ? "yse" : "no";
    >> no 출력
```
