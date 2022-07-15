# Generic

> 타입을 구체적으로 지정하는 것이 아니라 추후에 지정할 수 있도록 일반화 해두는 것을 의미.

- 특정 타입으로 고정시키지 않는 것.
- < T >는 타입 매개변수 느낌이다.

```jshelllanguage
Generic < Integer > generic = new Generic<Integer>(1);
```

- 인스턴스를 생성할 때 <>안에 타입을 넣으면 T가 매개가 되어서 클래스안의 T를 Integer로 바꾼다.
- primitive 타입은 wrapper클래스를 쓴다.
- 타입 매개변수는 대문자를 사용한다.

### 제네릭 클래스

```jshelllanguage
class Generic<T> {
    private T item;

    public Generic(T item) {
        this.item = item;
    }

    public T getItem() {
        return item;
    }

    public void setItem(T item) {
        this.item = item;
    }

    class Main<K, V> {
    }

}
```

### 특징

- static 변수에는 타입 매개변수를 사용할 수 없다.
    - 클래스 변수타입이 인스턴스별로 달라질 수 있으므로 같은 변수를 공유할 수 없다.
- 타입에 다형성을 적용할 수 있다.

```jshelllanguage
class Animal {
}
    class Dog extends Animal {
    }
    class Cat {
    }


    class Monkey<T> {
        private T item;

        public T getItem() {
            return item;
        }

        public void setItem(T item) {
            this.item = item;
        }

        public static void main(String[] args) {
            Monkey<Animal> monkey = new Monkey<>(); // Animal을 상속받은 클래스는 타입으로 가능
            monkey.setItem(new Dog());//다형성적용됨
            monkey.setItem(new Cat());//에러
        }
    }

```

### 제한된 제너릭 클래스

```jshelllanguage
class Animal {
}
    class Dog extends Animal {
    }
    class Cat {
    }


    class Monkey<T extends Animal> {// Animal의 하위클래스만 타입으로 받는다.
        private T item;

        public T getItem() {
            return item;
        }

        public void setItem(T item) {
            this.item = item;
        }

        public static void main(String[] args) {
            Monkey<Dog> monkey = new Monkey<>();
            Monkey<Cat> monkey = new Monkey<>();//에러가난다.
        }
    }



```

```jshelllanguage
interface Plant {
}
    class Flower implements Plant {
    }
    class Rose extends Flower implements Plant {
    }

    class Basket<T extends Plant> { // 특정인터페이스를 구현한 타입만 들어오게 함.
    }
    class Package<T extends Plant & Flower> {
    } // 특정 클래스를 상속받으면서 특정 인터페이스를 구현한 타입만 지정
    ...

    Basket<Flower>a=new Baseket<>();
    Basket<Rose>b=new Basket<>();

    Package<Flower>c=new Package<>();
```

### 제너릭 메서드

> 클래스 내부의 특정 메서드만 제너릭으로 선언할 수 있다.

```jshelllanguage
class Animal {
    public <T> void add(T elemnet) {
    } //메서드의 파라미터 타입을 결정한다.
}
```

-----------

- 제네릭 메서드의 타입 매개변수는 제네릭 클래스의 타입 매개변수와 별개의 것이다.

```jshelllanguage
class Animal<T> {
    public <T> void add(T element) {
    } // T라는 동일한 매개변수명을 사용했지만 다른 타입의 매개변수로 간주된다.
}
```

----------

- 클래스명 옆에 선언한 타입 매개변수는 클래스가 인스턴스화 될 때 타입이 지정된다.

```jshelllanguage
Animal < String > a = new Animal<>(); // 클래스의 타입 매개면수가 String으로 지정된다.
    a.<Integer>add(10); // 메서드의 타입매개변수는 Integer로 지정된다.
    a.add(10); // 타입 지정을 생략할 수도 있다.
```

----------

- 클래스 타입 매개변수와 달리 메서드 타입 매개변수는 static메서드에서도 선언하여 사용할 수 있다.

```jshelllanguage
class Animal {
    static <T> int add(T element) {
    }
}
```

------

- 메서드가 호출되는 시점에서 제네릭 타입이 결정되므로, 실제 어떤 타입이 입력되는지 알 수 없다.
  <br/>
  따라서 length()와 같은 String 클래스의 메서드는 제네릭 메서드를 정의한 시점에 사용할 수 없다.
- 최상위 클래스인 Object클래스의 메서드는 사용가능하다.
