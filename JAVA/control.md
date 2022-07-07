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

### switch

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
    >>yes 출력

    i=5;
    String ifEven=i%2==0?"yse":"no";
    >>no 출력
```

## 반복문

> 코드들이 반복적으로 실행되도록 할 때 사용(`반복 횟수를 알고있을 때`)

- for안의 로컬 변수와 상관없이 조건식에 부합하여 for문에 들어오면 블럭안의 코드가 무조건 실행됨.

## for

- 조건식이 참인 동안 주어진 횟수만큼 statement를 반복.

```jshelllanguage
for (초기화; 조건식; 증감식) {
    statement
}

    int sum = 0;
    for (int i = 0; i < 10; i++) {
        sum += i;
    }
//sum = 45가 출력
```

1. 초깃값 i = 0.
2. 조건식에 맞는지 확인(i < 10).
3. 맞으면 실행문 수행
4. 수행 후 i에 대해 증감식 적용.
5. i = 9 까지 수행.
6. 수행 후 증감식 적용하여 i = 10
7. 조건식과 비교.
8. 맞지 않으면 빠져나옴.

- for 문에 statement를 적지 않으면 i값만 늘어난다.

```jshelllanguage
int i = 1;
    for (; i <= 10; i++) ;

    i = 11;
```

- for 안에 있는 식중 3 가지중 1 가지는 공백이어도 된다.(;은 넣어줘야한다)

```jshelllanguage
int sum = 0;
    for (int i = 0; i < 5; ) {
        sum += i;
    }
    // 아무것도 출력되지 않음. 증감식이 비어버리면 
// 계속 조건식에 맞기 때문에 무한루프로 빠져나올 수 없음.

    int i = 0;
    for (i <= 10; i++) {

    }
// i = 11이 출력 된다.
// for문 앞에 변수를 초기화 용도로 사용하면 초기화식은 생략해도 된다.

```

- 조건부가 공백이면 항상 true이므로 무한반복 된다.(ctrl c로 해제)

```jshelllanguage
for (int i = 0; ; i++)
// 조건부가 없어서 항상 참이므로 무한반복된다.
```

## while

> 조건이 거짓일 때까지 while안의 블럭을 계속 실행(`조건에 따라 반복해야 할때`).

- 실행문을 수행 후 마지막에 로컬 변수를 증감시켜 줘야한다.

```jshelllanguage
while (i < 5) {
    System.out.print(i);
    i++
}
//12345가 출력
```

- 조건식이 true이면 무한반복된다. 그래서 탈출 코드를 적어줘야 한다.

```jshelllanguage
boolean a = true;
    int i = 0;
    while (a) {
        i++;
        System.out.println("무한반복");
        if (i == 5) {
            a = false;
        }

    }
```

### do while

> 한 번 실행한 후 조건식이 참이면 거짓이 나올 때까지 while 블럭 반복.(`무조건  한 번은 수행한다.`)

- 마지막에 조건식을 쓴다.

```jshelllanguage
int i = 5;
    do {
        System.out.println(i);
        i++;
    } while (i < 5);
```

### break

> 반복문이나 조건문에서 조건이 충족되면 빠져나오게 한다.

- 라벨을 붙여 반복문을 빠져나올 수 있게 한다.

```jshelllanguage 

Outer :for (int i = 3; i < 10; i++) {
            for (int j = 5; j > 0; j--) {
                System.out.println("i " + i + " j "+ j);
                if (i == 5) {
                    break Outer;
                }
            }
        }

```

### while

> 반복문에서 조건이 맞다면 아래의 코드를 수행하지 않고 바로 증감으로 넘어간다.

```jshelllanguage
for (int i = 0; i < 8; i++) {
    if (i % 2 == 0) { // 조건에 맞으면
        continue; // 다음반복으로 넘어간다.
    }
    System.out.println(i);
}
// 1,3,5,7가 출력된다.
```