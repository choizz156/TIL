## 배열(Array)

> 동일한 타입의 값들을 하나의 묶음으로 묶은 자료구조.

- 선언부에 배열의 갯수를 쓰는게 아니라 대입 부분 배열안에 갯수를 써야한다. 즉, 크기가 정해져서 나오고 한 번 만들면 바꿀 수 없다.
- 인덱스를 벗어나면 에러가 나온다.
- 요소들은 같은 타입이어야 한다.
- 배열을 그냥 출력하면 힙안의 주소가 나온다.`Arrays.toString`을 써야한다.

### 1차원 배열

- 배열 생성
    - new int[10]이면 10개의 int형을 저장할 수 있는 배열이 메모리에 오름차순으로 할당된다.
    - int[] marks로 참조변수를 만들어 할당하면 생성된 배열의 첫 번째 요소의 주소값이 참조변수에 할당된다.

 ```jshelllanguage
// 배열 만드는 방법 1
    int[] marks = {1, 2, 3, 4} //타입 앞에 []를 붙이고 요소(element)들을 {}로 묶는다. 
    marks =>int[4]{1,2,3,4};

// 배열만드는 방법 2
    int[]marks=new int[배열의 크기]; // 참조변수를 만들어서 할당한다.


```

- 배열의 인덱스

> 0번 부터 시작해서 배열의 크기 - 1까지 인덱스 된다.

```jshelllanguage
    marks[0] = 1;
    marks[1] = 2;
    marks[2] = 3;
    marks[3] = 4;
```

- 향상된 for문

```jshelllanguage

    int[] marks = {1, 2, 3, 4, 5, 6};
    int sum = 0;
    for (int mark : marks) { // mark
        sum = sum + mark;
    }
// mark 변수에 배열의 요소가 차례대로 할당되면서 실행문을 수행한다.
// sum = 21이 나온다.(1부터 6까지의 합)
```

- 배열의 크기는 상관없다. 비어있어도 된다.
- 인덱스를 이용하여 배열 안에 값을 할당할 수 있다.

```jshelllanguage
int[] marks1 = new int[3];
    marks1 = int[3]{0,0,0}; // int의 기본값 = 0 이다.

    marks1[0]=1;
    marks1[1]=2;
    marks1[2]=2;

    marks1=int[3]{1,2,2}

```

### 배열의 기본 매소드

- `.length`
    - 배열의 길이를 알 수 있다.

- `Arrays.fill(배열이름,값)`
    - 배열을 메소드안의 값으로 채운다.
- `Arrays.sort(배열이름)`
    - 배열의 값을 오름차순으로 정렬한다.

### 가변인수로 배열을 생성해서 할당하기
- 배열의 크기를 먼저 정하지 않아도 된다.
```jshelllanguage
class Something {
    public void doSomething(int... values(배열 이름)) { //인수로 int값을 받아 values 배열을 만든다.
        System.out.println(Arrays.toString(values)); // 배열 출력
    }
}

    Something thing = new Something(); // 인스턴스 생성
    thing.doSomething(1);
    // [1] 배열을 생성해서 인스턴스에 할당
    thing.doSomething(2, 3, 4);
    // [2,3,4] 배열 생성해서 인스턴스에 할당
    
  int sum = 0;
    void sum(int... values) {
        for (int value : values) {
            sum += value;
        }
        System.out.println(sum);
    }
    
    sum(1, 2, 3, 4, 5)
    // 15가 나온다.
```
## 2차원 배열
> 배열의 각 요소가 또다른 배열의 구조를 이룬다.

- 2차원 배열 생성 
```jshelllanguage
int[][] marks = new int[2](2행)[2](2열); // 2행 2열 구조의 배열을 만든다. 내부배열의 크기는 2이다.
  {
      {0,0},
      {0,0}
  }
```
- 외부 배열은 내부 배열의 주소값을 저장한다.

| int[2][2] | 0열  | 1열  | 
|-----------|-----|-----|
| 0행        | 0   | 0   |
| 1 행       | 0   | 0   |
