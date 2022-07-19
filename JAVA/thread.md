## 스레드

### 프로세스(process)와 스레드(thread)

- 프로세스 : 실행 중인 애플리케이션
- 스레드 : 데이터와 어플리케니션이 확보한 자원을 활용하여 소스 코드를 실행한다. 즉, 하나의 코드 실행 흐름이다.

### Main thread

- 자바 애플리케이션을 실행하면 가장 먼저 실행되는 메서드는 main메서드 이며, 메인 스레드가 메인 메서드를 실행시킨다.
- 자바 어플이 싱글 스레드로 작성됐다면, 실행되어 프로세스가 될 때, 메인 스레드만 가지는 싱글 스레드 프로세스이다.
- 메인 스레드에서 또 다른 스레드를 생성하여 실행시킨다면 멀티스레드 프로세스가 된다.

### Multi thread

- 하나의 프로세스는 여러개의 스레드를 가질 수 있고 이를 `멀티 스레드 프로세스`라고 한다.
- 여러 스레드가 동시에 작업을 수행할 수 있고 이를 `멀티 스레딩`이라고 한다.
- 여러 작업을 동시에 수행하는 멀티 태스킹을 구현하는 데에 핵심적 역할을 한다.

-------------

## thread의 생성과 실행

- 메인 스레드 외에 별도의 작업 스레드를 활용한다.
- 작업 스레드가 수행할 코드를 작성하고, 작업 스레드를 생성하여 실행시킨다.
    - `Thread 클래스`를 상속 받은 하위 클래스에서 run()메서드를 구현하여 스레드를 생성하고 실행
    - `Runnable 인터페이스`를 구현한 객체에서 run()메서드를 구현하여 스레드를 생성하고 실행.
    - `익명 클래스`를 활용.

### Thread 클래스 상속

```java
class Task1 extends Thread { // 스레드 클래스를 확장한 클래스를 만들어서 실행시킨다.
    public void run() {// 무조건 run()을 쓴다.
        System.out.println("task1 started");
        for (int i = 101; i <= 150; i++) {
            System.out.print(i + " ");
        }
        System.out.println("\ntask1 done");
    }
}

public class Solution {
    public static void main(String[] args) {
        Task1 task1 = new Task1();//객체를 만든다.
        task1.start();//제너릭 메서드의 start를 사용한다. run을 사용하면 순차적으로 실행된다.

        for (int i = 201; i <= 250; i++) {
            System.out.print(i + " ");
        }
        System.out.println("\ntask2 done");

        for (int i = 301; i <= 350; i++) {
            System.out.print(i + " ");
        }
        System.out.println("\nTask3 Done");
        System.out.println("\nMain Done");
    }
}

// main 메서드의 메인 스레드와 스레드 클래스를 상속받아 만든 작업 스레드가 동시에 수행된다.

/*task1 started
101 102 103 104 201 105 202 106 107 108 109 203 110 204 111 205 112 206 113 207 114 208 115 209 116 210 117 211 118 212 119 213 120 214 121 215 122 216 123 217 124 218 125 219 126 220 127 221 128 222 129 223 130 224 131 225 132 226 133 227 134 228 135 229 136 230 137 231 138 232 139 233 140 234 141 235 142 236 143 237 144 238 145 239 240 241 146 242 147 148 149 150 243 
task1 done
244 245 246 247 248 249 250 
task2 done
301 302 303 304 305 306 307 308 309 310 311 312 313 314 315 316 317 318 319 320 321 322 323 324 325 326 327 328 329 330 331 332 333 334 335 336 337 338 339 340 341 342 343 344 345 346 347 348 349 350 
Task3 Done

Main Done*/

```

### Runnable 인터페이스 구현

```java
class Task2 implements Runnable { // Runnable 인터페이스를 구현한다.

    @Override
    public void run() {
        System.out.println("task2 started");
        for (int i = 1; i <= 50; i++) {
            System.out.print("-");
        }
        System.out.println("\nTasks2 Done");
    }

}

public class Runner {
    public static void main(String[] args) {


        System.out.println("\nTask2 kicked off");
        Task2 task2 = new Task2(); // Runnable 인터페이스를 구현한 객체를 만들고
        Thread task2Thread = new Thread(task2); // 그 객체를 다시 쓰레드 생성자에 넣고 쓰레드 객체를 만든다.
        task2Thread.start();
        /* Task2 task2 = new Task2(); -- 이건 왜 안될까?
           task2.start();
           start()메소드가 thread 클래스 안에 정의되어 있는 것이고
           task2는 Runnable 인터페이스를 구현하지만 Thread와는 관련이 없으므로 Thread 클래스를 따로 만들고
           task2를 생성자로 넣어 run메소드를 start를 써서 실행한다. 
         */
        System.out.println("\nTask3 kicked off");
        for (int i = 1; i <= 50; i++) {
            System.out.print("/");
        }
        System.out.println("\nTask3 done");

        // 출력은 위와 비슷

    }
}
```

### 익명 클래스를 활용

```java
public class Thex {
    public static void main(String[] args) {
        Thread thread1 = new Thread(new Runnable() { // 구현 객체를 활용
            public void run() {
                for (int i = 0; i < 100; i++) {
                    System.out.println("%");
                }
            }
        });

        threa1.start();

    }
}
```

```java
public class Thex {
    public static void main(String[] args) {
        Thread thread2 = new Thread() { // thread 객체를 사용.
            public void run() {
                for (int i = 0; i < 100; i++) {
                    System.out.println("%");
                }
            }
        };

        threa2.start();

    }
}
```
-------------
## Thread Life-cycle
- New : 스레드가 생성됨. 아직 start()메서드로 인보크되지 않음.
- Terminated/Dead : run() 메서드 안의 코드가 모두 실행 완료됨.
> start() 메서드(실행 대기 상태로 만듦)가 수행된 후 3가지 상태
- Running : 현재 스레드가 수행 중.
- Runnable : 현재 스레드가 수행 중 이지는 않지만 언제든 수행 준비가 돼있음.
- Blocked/Wating : 현재 스레드가 수행 중 이지도 않고, 준비도 안된 상태. 외부 리소스나 다른 스레드를 기다리고 있는
상태 일 수 있음.

---------
## Thread 우선순위
> 우선 순위를(1~10) 부여할 수는 있지만 그냥 참고사항이다. 상황에 따라 반영되지 않을 수 있다.
```java
public class Runner {
    public static void main(String[] args) {

        Task1 task1 = new Task1();
        task1.setPriority(10);//setPriority를 사용한다.
        task1.start();

        Thread task2 = new Thread(new Task2());
        task2.setPriority(1);
        task2.start();

        for (int i = 1; i <= 10; i++) {
            System.out.print("#");
        }
        System.out.println("세번째 작업이 종료되었습니다.");
        
    //결과는 랜덤으로 나온다.
    }
}
```
----------------------
## Thread 이름
> 메인 스레드는 main, 추가적으로 생성한 스레드는 기본적으로 Thread-n이라는 이름을 가진다.
### 스레드 이름 조회하기
- `스레드참조변수.getName()`으로 조회할 수 있다.
### 스레드의 이름 설정하기
- `스레드의_참조값.setName()`으로 설정할 수 있다.
### 스레드 인스턴스의 주소값 얻기
- Thread 클래스의 정적 메서드인 `currentThread()`를 사용하면 된다.

----------------
## Thread 상태와 실행 제어
> start() 메서드는 실행을 시키는 메서드가 아니라 `실행 대기 상태`로 만드는 메서드이다. 실행은 운영체제가 한다.
### 스레드 실행 제어 메서드
- `sleep(long milliSecond)` : millisecond 동안 스레드를 잠시 멈춘다.
  - sleep은 thread의 클래스 메서드이기 때문에 Thread.sleep(1000)과 같이 클래스를 통해서 호출되는 것이 권장된다.
  - sleep을 호출하면 스레드의 상태가 실행 상태에서 time_wating 상태로 전환된다.
  - 정지된 스레드는 시간이 경과한 경우나, interrupt()를 호출한 경우.
    - interrupt를 호출한 경우는 try catch문을 사용해서 예외 처리를 해주어야한다.
  - sleep 또한 try catch문으로 감싸주고 사용한다.
- `interrupt()` : 일시 중지 상태인 스레드를 실행 대기 상태로 복귀 시킨다.
- `yield()` : 다른 스레드에게 실행을 양보한다.(static 메서드)
  - yield()를 호출하면 자신에게 남은 실행 시간을 실행 대기열 상 우선순위가 높은 다른 스레드에게 양보한다.
- `join()` : join을 호출한 스레드가 다 끝난 후 다음 스레드가 실행된다.
- 예외가 발생할 수 있으므로 try catch문을 사용한다.
- `notify(), wait()` : 두 스레드가 교대로 작업을 처리해야할 때 사용.
  - 스레드1 작업완료 -> notify() 호출 -> 스레드 2가 실행대기 상태가 됨-> 스레드1 wait()호출해서 일시 정지
-> 스레드2 작업완료 notify() 호출 -> 일시 중지 됐던 스레드1 실행 대기 상태 -> 스레드2 wait()호출해서 일시정지.

---------------------
## Thread 동기화
> 두 스레드가 동일한 데이터를 공유하게 되어 문제가 발생할 수 있다. 이를 위해 스레드 동기화가 필요하다.
- `임계 영역(critical section)` :오로지 하나의 스레드만 코드를 실행할 수 있는 코드 영역.
- `락(Lock)` : 임계 영역을 포함하고 있는 객체에 접근할 수 있는 권한.
>임계 영역으로 설정된 객체가 다른 스레드에 의해 작업이 이루어지고 있지 않을 때, 임이의 스레드 A는 해당 객체에 대한
락을 획득하여 임계 영역 내의 코드를 실행할 수 있다.
이때 , 다른 스레드들은 락이 없으므로 이 객체의 임계 영역 내의 코드를 실행할 수 없다.
스레드가 임계 영역 내의 코드를 모두 실행하면 락을 반납하고 다른 스레드가 락을 획득한다.

### 임계 영역 설정(`synchronized`)
- 메서드 전체를 임계 영역으로 지정
  - 메서드의 반환 타입 좌측에 synchronized 키워드를 작성한다.
  - 메서드가 호출되었을 때, 메서드를 실행할 스레드는 메서드가 포함된 객체의 락을 얻는다.
- 특정 영역을 임계영역으로 지정
  - synchronized 키워드와 함께 소괄호 안에 해당 영역이 포함된 객체의 참조를 넣고. 중괄호로 블럭을 열어 블럭내에 코드를 작성한다.
  - 코드 실행 흐름이 진입할 때 코드를 실행하고 있는 스레드가 소괄호 안의 객체에 락을 얻고, 배타적으로 코드를 실행한다.
```jshelllanguage
ublic boolean withdraw(int money) {
			synchronized (this) {
			    if (balance >= money) {
			        try { Thread.sleep(1000); } catch (Exception error) {}
			        balance -= money;
			        return true;
			    }
			    return false;
			}
	}
```