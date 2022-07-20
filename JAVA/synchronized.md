# Synchronized
## thread safety
> 한 번에 하나의 스레드만이 메소드를 사용할 수 있게 하고, 나머지 스레드는 완료될 때 까지 기다린다.
```jshelllanguage
public class Counter {
		private int i = 0;
		public void increment() {
			i++; // 이러한 연산도 여러가지 스텝을 밟으면서 연산됨. 한번에 수행되는 것이 아님.
		}
		public int getI() {
			return i;
		}
	}
 public class ConcurrencyRunner {
		public static void main(String[] args) { //여러개의 스레드가 동시에 increment()를 사용한다면 오류가 발생할 확률이 있음. 
			Counter counter = new Counter();
			counter.increment();
			counter.increment();
			counter.increment();			
			System.out.println(counter.getI());
		}
	}

public class Counter {
    private int i = 0;

    synchronized public void increment() { // synchronized 키워드를 통해 동기화 시켜 thread-safety를 보장함.
                                            // 한 번에 하나의 쓰레드 만이 이 메소드를 사용할 수 있음.
        i++;
    }
    public int getI() {
        return i;
    }
}

```
### 동기화 단점
```jshelllanguage
public class BiCounter {
		private int i = 0;
		private int j = 0;

		synchronized public void incrementI() {
			i++;
		}

		synchronized public void incrementJ() {
			j++;
		}

		public int getI() {
			return i;
		}

		public int getJ() {
			return j;
		}
	}

    /* incrementI와 incrementJ는 서로 아무런 영향을 주지 않지만
    synchronized 되어서 하나의 메소드가 끝나야만 다른 메소드가 실행된다.
    즉 한 스레드가 incrementI 연산을 끝낼 때 까지 다른 스레드들은 incrementJ도 수행하지 못 하고
    대기해야 한다.*/ 


	public class ConcurrencyRunner {
		public static void main(String[] args) {
			BiCounter counter = new BiCounter();
			counter.incrementI();
			counter.incrementJ();
			counter.incrementI();
			System.out.println(counter.get());
		}
	}
    

```
### lock
> 서로 다른 lock객체를 만들어서 적용하면 하나의 스레드가 method1을 사용할 때, 다른 하나는 method2를 사용할 수 있다.
```jshelllanguage
public class BiCounterWithLocks {
		private int i = 0;
    	private int j = 0;

		private Lock lockForI = new ReentrantLock(); //Lock 인터페이스를 사용해서 Lock객체를 사용해 lock을 걸고 풀수 있다.
        private Lock lockForJ = new ReentrantLock(); // 외부에서 락을 풀지 못하도록 private를 사용한다.
    
    public void incrementI() { 
			lockForI.lock();//lock을 건다.
			i++;    //수행을 한다.
			lockForI.unlock(); //lock을 해제한다.
		}

		public void incrementJ() {
			lockForJ.lock();//lock을 건다.
			j++;//수행을 한다.
			lockForJ.unlock();//lock을 해제한다.
		}

		public int getI() {
			return i;
		}

		public int getJ() {
			return j;
		}
	}

```
### Atomic 클래스
> Atomic 클래스는 기본적인 단일수행을 제공한다.
```java
public class BiCounterWithAtomicInteger {

    private AtomicInteger i = new AtomicInteger();
    private AtomicInteger j = new AtomicInteger();
    /*AtomicInteger 클래스 자체에 thread safe기능이 있어서 단순한 연산을 할 때는 
    lock 클래스를 안 써도됨. 하지만 복잡한 계산을 할 때는 lock을 써주는 게 좋음.*/
    
    public void incrementI() {
        i.incrementAndGet(); // 증가연산자를 제공하고 해당 코드가 thread safe한지 확인할 수 있다.

    }

    public void incrementJ() {
       j.incrementAndGet();
    }

    public AtomicInteger getI() {
        return i.get();
    }

    public AtomicInteger getJ() {
        return j.get();
    }

}
// AtomicInteger 외에도 wrapper클래스에 해당 하는 다른 클래스들도 많다. AtomicDouble 등등


```
### Concurrent collection
> atomic 수행을 제공해 준다.
```jshelllanguage
public class MapRunner {
		public static void main(String[] args) {
			String str = "Hello World";
			Map<Character, Integer> occurrences = new HashMap<>();
			char[] characters = str.toCharArray();
			for(char character:characters) { //이러한 for loop는 thread-safty하지 않다.
				Integer count = occurrences.get(character);
				if(count == null) {
					occurrences.put(character, 1);
				} else {
					occurrences.put(character, count + 1);
				}
			}
		}
	}
```
```jshelllanguage
public class ConcurrentMapRunner {
		public static void main(String[] args) {
			    String str = "ABCD ABCD ABCD";
			    for(char character:str.toCharArray()) {
			      LongAdder longAdder = occurances.get(character); // LongAdder를 통해서 증가연산을 해주면서 약간 더 thread safe하게 만들수는 있다.
			      if(longAdder == null) {
			        longAdder = new LongAdder();
			      }
			      longAdder.increment();
			      occurances.put(character, longAdder); //하지만 스레드들이 여기서 경쟁을 할 가능성이 있다.
			    }
		}
	}
```
```jshelllanguage
public class ConcurrentMapRunner {
		public static void main(String[] args) {
		    ConcurrentMap<Character, LongAdder> occurances = new ConcurrentHashMap<>();
// Concurrent Colletion을 통해 쓰레드 안정성을 보장과 동시에 lock을 걸어서 동시성 또한 보장함.
		    
		    String str = "ABCD ABCD ABCD";

		    for(char character:str.toCharArray()) {
		      occurances.computeIfAbsent(character, ch -> new LongAdder()).increment();
		    }
// computeIfAbsent매소드를 통해 키값이 널이라면 LongAdder를 부여하고 아니면 증가시킨다.
		    
		    System.out.println(occurances);
	  }
	}
```
