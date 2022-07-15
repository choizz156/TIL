# 컬렉션 프레임워크(Collection Framework)

> - 자료 구조를 바탕으로 `객체`들을 효율적으로 추가,삭제,검색할 수 있도록 컬렉션을 만든 것.
    > <br/>
> - 객체 지향적이고 재사용성 높은 코드를 작성할 수 있다.

### 구조

[컬렉션 프레임워크 구조](https://hudi.blog/static/1bacac1babc556100455a8c64e7658da/e6c4b/2.png)

- 주요 인터페이스 : `List`,`Set`,`Map`

## List< E >

> 배열과 같이 객체를 일렬로 늘어놓는 구조로 `객체`를 인덱스로 관리하기 때문에 객체를 저장하면 자동으로 인덱스가 부여되고 인덱스로 여러 기능 제공.

- 어느 위치에 어느 객체가 있는지 신경써야 한다.
- 어떤 위치를 특정함으로써 요소들을 추가할 수 있다.
- 특정위치가 없어도 자동으로 맨 끝에 추가된다.
- 요소가 중복되도 된다.

### List 기본 메서드

```jshelllanguage
 List < String > words = List.of("a", "b", "c")//List.of는 불변 리스트임.
    words ==>[a,b,c]

    // Collection에서 상속받은 메서드와 List 메서드가 섞인 것.
    words.isEmpty() // 비었는지
    $2==>false

    words.get(0) // 특정 인덱스 객체 호출
    $3==>"a"

    words.contains("a") // 해당 객체 포함여부 확인
    $4==>true

    words.indexOf("c") // 해당 객체 인덱스
    $5==>2

    words.indexOf("d") // 리스트에 객체가 없으면 -1 출력
    $6==>-1

    jshell>words.contains("d") // 해당 객체가 리스트에 없을 때
    $7==>false
    ]

```

-----------

## ArrayList

> - 기존의 vector를 개선한 것. 객체를 추가하면 객체가 인덱스로 관리됨.
    > <br/>
> - 저장 용량을 초과하여 객체들이 추가되면, 자동으로 저장용량이 늘어나게 된다.
    > <br/>
> - 데이터가 연속적으로 존재하며 순서를 유지한다.

```jshelllanguage
   List < String > words = List.of("a", "b", "c")
    words ==>[a,b,c]

    List<String>wordsArrayList=new ArrayList<>(words);
    wordsArrayList==>[a,b,c] //정적 배열을 동적배열로 바꾼것 

    wordsArrayList.add("d") //arraylist에 객체를 추가했다.
    $3==>true

    wordsArrayList
    wordsArrayList==>[a,b,c,d] // 맨 끝에 추가된다.


    List<String>container=new ArrayList<>(30); // 초기 용량을 30으로 만든 것. 안 써줘도 됨.


```

- 특정 인덱스를 제거하면 , 바로 뒤 인덱스부터 마지막 인덱스까지 모두 앞으로 1씩 당겨진다.

```jshelllanguage
 List < String > list = new ArrayList<>() // 빈 리스트 만듦.
    list ==>[]

    list.add("a") // 객체 추가. 순서대로 추가됨.
    list.add("b")
    list.add("c")

    int size=list.size()//리스트 사이즈
    =>3

    String skill=list.get(0) // 0번째 인덱스의 객체 출력
    =>"a"

    for(int i=0;i<list.size();i++) // 리스트 크기만큼 객체 조회
{String str=list.get(i);
    System.out.println(str);
}

    for(String str:list){
    System.out.println(str);
}

    list.remove(0); // 0번째 인덱스 제거
    "a"

    list==>[b,c]
```

### ArrayList 원소 변경 메서드

```jshelllanguage
 List < String > words = List.of("a", "b", "c");
    words ==>[a,b,c] // 정적 배열

    List<String>wordsArrayList=new ArrayList<String>(words);
    wordsArrayList==>[a,b,c] //동적 배열

    wordsArrayList.add("d")// d 추가
    $21==>true

    wordsArrayList
    wordsArrayList==>[a,b,c,d]

    wordsArrayList.add("e") // e 추가
    $23==>true

    wordsArrayList
    wordsArrayList==>[a,b,c,d,e]

    wordsArrayList.add(2,"f") // 특정 인덱스에 특정 객체 추가

    wordsArrayList
    wordsArrayList==>[a,b,*f*,c,d,e]

    wordsArrayList.add("f") // 중복 객체 추가 가능
    $27==>true

    wordsArrayList
    wordsArrayList==>[a,b,*f*,c,d,e,*f*]

    List<String>newList=List.of("g","y") // 새로운 리스트를 만듦
    newList==>[g,y]

    wordsArrayList.addAll(newList)// 리스트를 통째로 추가
    $30==>true

    wordsArrayList
    wordsArrayList==>[a,b,f,c,d,e,f,*g,y*]
```

- `indexOf()`는 오버로딩이 되지 않아 `유일한 버젼`이지만 `remove()`는 오버로딩이 되어서 `2가지 버젼`이 있다.
    - `remove(int index)` : 정수형이 들어가면 그것을 인덱스로 인식하고 그 인덱스의 값을 제거한다.
    - `remove(Object 0)` : 객체가 들어가면 그 객체 자체를 제거한다.

```jshelllanguage


    List < Integer > values = List.of(101, 102, 103, 104)
    values ==>[101,102,103,104]
    List<Integer>valueAL=new ArrayList<>(values);
    valueAL.indexof(101)
    =>0
    valueAL.remove(101) //정수 기본형이 들어갔기 때문에 101번째 인덱스를 제거한다.
    =>error //outofbound에러가 난다.
    valueAL.remove(Integer.valueOf(101)) // 기본형을 wrapper클래스로 변환했기 때문에 101을 제거한다.
    =>true
    valueAL
    =>[102,103,104]
```

----------------------

## LinkedList

> 데이터를 효율적으로 추가,삭제,변경하기위해 사용함. 불연속적으로 존재하며 서로 연결돼 있다.

- node들은 자신과 연결된 이전 요소 및 다음 요소의 주솟값과 데이터로 구성된다.
- [linkedlist](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ6WWPkmy8AWlTrFasWfk_85PArh36MuaqkYw&usqp=CAU)
- arraylist와 사용방식 동일.

```jshelllanguage
List < String > list = new LinkedList<>() // 빈 리스트 만듦.
    list ==>[]

    list.add("a") // 객체 추가. 순서대로 추가됨.
    list.add("b")
    list.add("c")

    int size=list.size()//리스트 사이즈
    =>3

    String skill=list.get(0) // 0번째 인덱스의 객체 출력
    =>"a"

    for(int i=0;i<list.size();i++) // 리스트 크기만큼 객체 조회
{String str=list.get(i);
    System.out.println(str);
}

    for(String str:list){
    System.out.println(str);
}

    list.remove(0); // 0번째 인덱스 제거
    "a"

    list==>[b,c]
```

-------------

### ArrayList vs LinkedList

> ArrayList의 밑바탕이 되는 데이터 구조는 `배열`이고, LinkedList는 `이중연결리스트`이다.

| 특징  | 장점 |단점|
|------|-----|---|
| ArrayList|접근이 빠르다.|삽입과 삭제가 느리다(중간 인덱스)
|LinkedList|삽입과 삭제가 빠르다|접근이 느리다.

--------------


-------------------

## Iterator

> - `Collection 인터페이스에는` Iterator 인터페이스를 구현한 클래스의 인스턴스를 반환하는 메서드인 `iterator()가 정의돼 있다.`
    > <br/>
> - Collection을 구현하고 있는 모든 컬렉션 프레임워크는 iterator()메소드를 구현하고 있다.

- iterator메서드는 객체를 리턴한다.

### iterator에서 만들어진 객체가 사용하는 메서드

- `hasNext()` : 읽어올 객체가 남아 있으면 true를 리턴하고, 없으면 false를 리턴한다.
- `next()` : 컬렉션에서 하나의 객체를 읽어온다. 이 메서드를 호출하기 전에 hasNext()를 통해 읽어올 요소가 있는지 먼저 확인해야 한다.
- `remove()` : next()를 통해 읽어온 객체를 삭제합니다. next()를 호출한 다음 이 메소드를 호출해야 한다.

```jshelllanguage
List < String > list = List.of("a", "b", "c");
    Iterator < String > iterator = list.iterator(); // list 인스턴스가 iterator()메소드를 사용해 Iterator타입의 객체를 만들었다.

    while (iterator.hasNext()) { //iterator 인스턴스는 위의 메소드를 사용가능 하다.
        String str = iterator.next();
        if (str.equals("a")) {
            iterator.remove();
        }
    }

```

### for vs iterator

> 배열변경 없이 루프만 한다고 하면 향상된 for루프를 사용하는 것이 좋고, 배열이 변경되는 작업을 하려면 iterator를 사용하는 것이 더 좋다.

```jshelllanguage
 List < String > words = List.of("apple", "bat", "cat")
    words ==>[apple,bat,cat]


    List<String>wordsAL=new ArrayList<>(words);
    wordsAL==>[apple,bat,cat]


    for(String word:words){ // 배열 변경없는 리스트는 for를 쓰는 것이 효율적
    ...>if(word.endsWith("at")){
    ...>System.out.println(word);
    ...>}
    ...>}
    bat
    cat

    for(String word:wordsAL){// 배열을 변경 시킴
    ...>if(word.endsWith("at"))
    ...>wordsAL.remove(word);}

    wordsAL
    wordsAL==>[apple,cat] // cat이 삭제가 안됨. bat이 삭제되면서 wordAL의 사이즈가 변해서 cat까지 안가고 종료됨.


    Iterator<String>iterator=wordsAL.iterator(); // 배열을 변경시킬때는 iterator를 사용하는 것이 좋음.
    iterator==>java.util.ArrayList$Itr@50134894


    Iterator<String>iterator=wordsAL.iterator();
    iterator==>java.util.ArrayList$Itr@1376c05c

    while(iterator.hasNext()){
    ...>if(iterator.next().endsWith("at")){
    ...>iterator.remove();}
    ...>}

    wordsAL
    wordsAL==>[apple]
```

### List type 오토박싱

> List 컬렉션은 기본 타입을 저장하지 못하지만 요소에 기본타입을 넣었을 경우 내부족으로 오토박싱을 시켜준다.
> <br/>
> List의 타입이 선언되지 않았을 경우에 해당된다.

 ```jshelllanguage
 List values = List.of("A", 'A', 1, 1.0) //List타입이 정해지지 않았을 때 기본형 타입을 넣으면 오토박싱이 된다.
    values ==>[A,A,1,1.0]

    values.get(2)
    $46==>1

    values.get(2)instanceof Integer //Integer타입에 속한 객체가 됐음.
    $47==>true

    values.get(1)instanceof Character
    $48==>true


    List<String>values=List.of("A",'A',1,1.0)// 타입이 정해지면 오류가 난다.
    |Error:
    |incompatible types:inference variable E has incompatible bounds
    |equality constraints:java.lang.String
    |lower bounds:java.lang.Double,java.lang.Integer,java.lang.Character,java.lang.String
    |List<String>values=List.of("A",'A',1,1.0);
    |^--------------------^
  ```

----------------

## 정렬

### Comparable 정렬

> - 기본 정렬기준을 구현하는데 사용.
    > <br/>
> - 요소들을 비교하려면 Comparable 인터페이스를 구현해야 하는데 wrapper 클래스는 이미 구현하고 있음.
    <br/>
> - 왼쪽이 크면 양수, 같으면 0, 오른쪽이 크면 음수.

```jshelllanguage
jshell > List < Integer > numbers = List.of(123, 12, 3, 45)
    numbers ==>[123,12,3,45]

    jshell>List<Integer>numbersAL=new ArrayList<>(numbers);
    numbersAL==>[123,12,3,45]

    jshell>numbersAL.sort(); // 본래 sort()를 쓰려면 Compratoer가 있어야 한다. 
    |Error:
    |method sort in interface java.util.List<E>cannot be applied to given types;
    |required:java.util.Comparator<?super java.lang.Integer>
    |found:no arguments
    |reason:actual and formal argument lists differ in length
    |numbersAL.sort();
    |^------------^

    jshell>Collections.sort(numbersAL) //Collections클래스에서 sort()를 쓰면 바로 정렬된다.
    // Integer가 Comparable을 구현하고 있기 때문에 대상을 안써도 됨.

    jshell>numbersAL
    numbersAL==>[3,12,45,123]

```

```java
public class Student {...
} // Comparable 인터페이스를 구현하지 않음.

public class StudentRunner {
    public static void main(String[] args) {
        List<Student> stundents = List.of(new Student(1, "a"), new Student(100, "Adam"), new Student(2, "c"));
        ArrayList<Student> studentAL = new ArrayList<>((stundents));
        System.out.println(studentAL);
        Collections.sort(studentAL);// 에러가 난다.
        System.out.println(studentAL);
    }

    public class Student implements Comparable<Student> {//Student는 비교할 객체.
        ...

        @Override
        public int compareTo(Student that) { // 주어진 객체를 자기 자신과 비교.
            return Integer.compare(that.id, this.id); // that부터 쓰면 내림차순.
            return Integer.compare(this.id, that.id); // this부터 쓰면 오름차순.       
        }
    }
}

public class StudentRunner {
    public static void main(String[] args) {
        List<Student> stundents = List.of(new Student(1, "a"), new Student(100, "Adam"), new Student(2, "c"));
        ArrayList<Student> studentAL = new ArrayList<>((stundents));
        System.out.println(studentAL);
        Collections.sort(studentAL);// 출력됨.
        System.out.println(studentAL);
    }
}
  ```

------------

### Comparator 정렬

> 기본 정렬기준 외에 다른 기준으로 정렬하고자할 때 사용.

```java
public class Dsstudent implements Comparator<Student> {

    @Override
    public int compare(Student s1, Student s2) {// 두 객체를 비교
        return Integer.compare(s2.getId(), s1.getId());
    }

    public int compare(Student s1, Student s2) {
        return s2.getName().compareTo(s1.getName());// ID 뿐만아니라 이름이나 다른것도 상황에 맞춰 정렬할 수 있다.
    }                                               //compare가 아니라 compareTO를 쓴다.
    // 비교대상의 위치를 바꿔서 내림차순할 수 있다. (왼쪽부터 오른쪽 순 = 오름차순)

}


```

------------

## SET<E>

> Set 안에서는 중복이 허용되지 않고, 순서가 정해져 있지 않다.

```jshelllanguage
$ jshell
    |Welcome to JShell--Version17.0.2
    |For an introduction type:/help intro

    jshell>Set<String>set=Set.of("a","b","v")
    set==>[a,b,v] // set객체를 만들었다.

    jshell>set.add("aaa") // of를 써서 불변이다.
    |Exception java.lang.UnsupportedOperationException
    |at ImmutableCollections.uoe(ImmutableCollections.java:142)
    |at ImmutableCollections$AbstractImmutableCollection.add(ImmutableCollections.java:147)
    |at(#2:1)

    jshell>Set<String>hashSet=new HashSet<>(set); // 변할 수 있게 hashSet을 만든다.
    hashSet==>[a,b,v]

    jshell>hashSet.add("a") //중복되는 객체는 추가하지 못한다.
    $6==>false

    jshell>hashSet.add("c") // 중복되지 않는 것은 추가가능하다.
    $7==>true

    jshell>hashSet
    hashSet==>[a,b,c,v]

    jshell>hashSet.add(1,"c") //위치는 정해지지 않는다.
    |Error:
    |method add in interface java.util.Set<E>cannot be applied to given types;
    |required:java.lang.String
    |found:int,java.lang.String
    |reason:actual and formal argument lists differ in length
    |hashSet.add(1,"c")
    |^---------^

```

### HashSet

> 정렬 순서와 삽입 순서에 상관없이 저장한다.

```jshelllanguage
jshell > Set < Integer > numbers = new HashSet<>();
    numbers ==>[]
    jshell>numbers.add(765432);
    $1==>true
    jshell>numbers.add(76543);
    $2==>true
    jshell>numbers.add(7654);
    $3==>true
    jshell>numbers.add(765);
    $4==>true
    jshell>numbers.add(76);
    $5==>true
    jshell>numbers
    numbers==>[765432,7654,76,765,76543] // 랜덤으로 저장
```

### LinkedHashSet

> 삽입순서만 상관있다.

```jshelllanguage
Set < Integer > numbers = new LinkedHashSet<>();
    numbers ==>[]
    jshell>numbers.add(765432);
    $1==>true
    jshell>numbers.add(76543);
    $2==>true
    jshell>numbers.add(7654);
    $3==>true
    jshell>numbers.add(765);
    $4==>true
    jshell>numbers.add(76);
    $5==>true
    jshell>numbers
    numbers==>[765432,76543,7654,765,76] //삽입 순서대로 저장
    jshell>numbers.add(7654321);
    $5==>true
    jshell>numbers
    numbers==>[765432,76543,7654,765,**7654321**]
```

### TreeSet

> 정렬순서만 상관있다.

```jshelllanguage
jshell > Set < Integer > numbers = new TreeSet<>();
    numbers ==>[]
    jshell>numbers.add(765432);
    $1==>true
    jshell>numbers.add(76543);
    $2==>true
    jshell>numbers.add(7654);
    $3==>true
    jshell>numbers.add(765);
    $4==>true
    jshell>numbers.add(76);
    $5==>true
    jshell>numbers
    numbers==>[76,765,7654,76543,765432] // 삽입 순서는 상관 없고 들어오는 데로 정렬시킨다.
    jshell>numbers.add(7);//마지막에 7을 넣음
    $5==>true
    jshell>numbers
    numbers==>[**7**,76,765,7654,76543,765432] // 정렬돼서 맨 앞에 추가됨.
```

-------------------------

## Queue<E>

> 프로세싱 순서대로 정렬됨.

### prioriyQueue

> 기본적으로 순서대로 정렬되지만 임의로 기준을 정할 수 있다.

- 기본값

```jshelllanguage
jshell > Queue < String > queue = new PriorityQueue<>();
    queue ==>[] // 우선순위 큐 생성

    jshell>queue.poll() // 맨 앞부터 하나씩 뽑음
    $2==>null

    jshell>queue.offer("a")//큐에 값을 넣는다.
    $3==>true

    jshell>queue.addAll(List.of("bb","cccc","dddd") //한 번에 넣을 수 있다.
    ...>)
    $4==>true

    jshell>queue
    queue==>[a,bb,ccc,dddd] // 기본적으로 오름차순으로 정렬된다.

    jshell>queue.poll()// 맨 앞부터 하나씩 뽑는다.
    $6==>"a"

    jshell>queue
    queue==>[bb,ccc,dddd]

    jshell>queue.poll()
    $8==>"bb"

    jshell>queue
    queue==>[ccc,dddd]

    jshell>queue.poll()
    $10==>"ccc"

    jshell>queue
    queue==>[dddd]

    jshell>queue.poll()
    $12==>"dddd"

    jshell>queue //앞에서 부터 뽑으면 결국 큐에는 아무것도 남지 않는다.
    queue==>[]

```

- 임의로 정렬

```java
public class Queuea {
    public static void main(String[] args) {
        Queue<String> queue = new PriorityQueue<String>(new Length());
        queue.addAll(List.of("a", "bb", "ccc"));
        System.out.println(queue.poll());//ccc
        System.out.println(queue.poll());//bb
        System.out.println(queue.poll());//a
        System.out.println(queue.poll());//null

    }
}

class Length implements Comparator<String> {//Comparator를 이용해서 정렬 기준을 바꾼다.

    @Override
    public int compare(String left, String right) {
        return Integer.compare(right.length(), left.length());//내림차순
    }
}
```

-------------------

## Map<K,V>

> 키와 값(a,3)이 쌍으로 들어가는 인터페이스, 키를 사용하여 그에 대응하는 값을 구할 수 있다.

- Collection 인터페이스를 구현하지 않아서 Collection 인터페이스에 있는 메서드를 사용할 수 없다.
- 함수의 정의역 치역과 비슷하다.

### HashMap

- 순서와 정렬은 신경쓰지 않음.
- key의 hashCode() 값은 해싱함수에서 사용.
- key와 null값을 함께 저장가능.

```jshelllanguage

    jshell > HashMap < String,Integer>hashMap=new HashMap<>();
    hashMap==>{}
    jshell>hashMap.put("Z",5);
    $1==>null
    jshell>hashMap.put("A",15);
    $2==>null
    jshell>hashMap.put("F",25);
    $3==>null
    jshell>hashMap.put("L",250);
    $4==>null
    jshell>hashMap
    hashMap==>{A=15,F=25,Z=5,L=250} //순서,정렬 신경 안씀.
```

### HashTable

- 모든 메서드가 동기화 돼있어서 thread-safe이지만 동시성이 없음
- 순서와 정렬은 신경쓰지 않음
- key의 hashCode() 값은 해싱함수에서 사용.
- null값을 허용하지 않음.

### LinkedHashMap

- 삽입된 순서대로 정렬됨.
- iteration이 빠름.
- 삽입과 삭제가 느림.

```jshelllanguage
jshell > LinkedHashMap < String,Integer>linkedHashMap=new LinkedHashMap<>();
    linkedHashMap==>{}
    jshell>linkedHashMap.put("Z",5);
    $5==>null
    jshell>linkedHashMap.put("A",15);
    $6==>null
    jshell>linkedHashMap.put("F",25);
    $7==>null
    jshell>linkedHashMap.put("L",250);
    $8==>null
    jshell>linkedHashMap
    hashMap==>{Z=5,A=15,F=25,L=250} // 삽입된 순서대로 정렬


```

### TreeMap

- 삽입 순서에 상관없이 정렬 순서가 유지됨(오름차순).
- NavigableMap 인터페이스를 추가로 사용 가능함.

```jshelllanguage
jshell > TreeMap < String,Integer>treeMap=new TreeMap<>();
    treeMap==>{}
    jshell>treeMap.put("Z",5);
    $9==>null
    jshell>treeMap.put("A",15);
    $10==>null
    jshell>treeMap.put("F",25);
    $11==>null
    jshell>treeMap.put("L",250);
    $12==>null
    jshell>treeMap
    treeMap==>{A=15,F=25,L=250,Z=5} // key값을 오름차순 함. 들어오는 순서는 상관없음.


```

### 메서드

```jshelllanguage
jshell > Map < String,Integer>map=Map.of("A",3,"B",5,"Z",10);
    map==>{Z=10,A=3,B=5}

    // key값을 넣었을때 value값 추출
    jshell>map.get("Z");
    $1==>10
    jshell>map.get("A");
    $2==>3

// key값이 map안에 없으면 null을 추출
    jshell>map.get("C");
    $3==>null

// 맵 크기	
    jshell>map.size();
    $4==>3
// 맵이 비었는지
    jshell>map.isEmpty();
    $5==>false

// 해당 키값이 맵안에 있는지
    jshell>map.containsKey("A");
    $6==>true
    jshell>map.containsKey("F");
    $7==>false

// 해당 value가 맵안에 있는지
    jshell>map.containsValue(3);
    $8==>true
    jshell>map.containsValue(4);
    $9==>false

// key값만 추출
    jshell>map.keySet();
    $10==>[Z,A,B]

// value값만 추출
    jshell>map.values();
    $11==>[10,3,5]

    jshell>Map<String,Integer>map=Map.of("A",3,"B",5,"Z",10);
    map==>{Z=10,A=3,B=5}

    // HashMap으로 가변성있게 만든다.
    jshell>Map<String,Integer>hashMap=new HashMap<>(map);
    hashMap==>{A=3,Z=10,B=5}

    // 맵에 F=5를 추가하고 null 값을 리턴한다.
    jshell>hashMap.put("F",5);
    $1==>null
    jshell>hashMap
    hashMap==>{A=3,Z=10,B=5,F=5}

    // z의 value를 11로 바꾸고 이전 값(10)을 추출한다.
    jshell>hashMap.put("Z",11);
    $2==>10
    jshell>hashMap
    hashMap==>{A=3,Z=11,B=5,F=5}



```