## CSS(Cascading Style Sheets)
> 웹 페이지의 스타일 및 레이아웃을 정의하는 언어(stylesheet).

### 1. CSS 구조
```
body{
    color : blue;
    font-size : small;
    background : black;
}
```
- body = `selector`
    - 특정 태그의 이름, id, class를 선택한다는 걸 의미.
- {} = `declaration block`
    - 중괄호 안에서 해당 요소에 적용할 내용을 작성할 수 있다.
- color : blue; = `declaration`
    - color = property
    - blue = value
    - ; = end
### 2. selector 적용 방법
#### 1) id
- id에 이름을 붙여서 특정한 태그에만 속성을 부여할수 있다.
- 이름 앞에 #을 붙인다.
- 문서 내에서 하나의 요소에만 적용되는 유일한 이름이어서 다른 코드에는 사용할 수 없다.
```
<h1 id = "actor"> he is actor. </h1>
```
```
#actor{
    color : black;
}
```
#### 2) class
- class name 앞에 .을 찍어서 적용시킨다.
- 동일한 기능을 하는 CSS를 class name을 가진 여러 곳에 적용시킬 수 있다.
```
<ol>
    <li class = "animal"> dog </li>
    <li class = "animal"> cat </li>
</ol>    
```
```
.animal{
    color : blue;
}
```
- 하나의 요소에 여러 CSS 기능을 적용시킬 수도 있다.
```
<li class = "animal legs"> dog </li>
```
```
.legs{
    font-size : large;
}
```

> 우선순위
> 1. inline css( htmlm style attribute)가 style tag나 css 파일보다 우선한다.
> 2. 더 구체적인 selector가 덜 구체적인 selector보다 우선순위를 갖는다. (id>class)
> 3. 만약 같은 우선순위를 갖는 css가 있다면 나중에 나온 것이 우선순위를 갖는다.


### 3. CSS파일 연결
```
<link rel = "stylesheet" href = " practice.css" />
```
- < link > tag는 html 파일과 다른 파일을 연결하는 역할을 함.
- rel = 연결하려는 파일의 특징을 나타낸다.
- href에는 파일의 위치를 추가한다. 한 폴더 안에 두 파일이 있다면 파일명만 적으면 되지만 다른 폴더에 존재하는 경우 결로를 입력해야 연결이 된다.



### 4. 텍스트
#### 1) 색상 : `color`
#### 2) 글꼴 : `font-family`
- 원하는 글꼴이 없을 수 있으니 여러개 적어 놓는다.(fallback)
#### 3) 크기 : `font-size`
- 절대 단위 : `px` ,pt 등
- 상대 단위 : %, em ,`rem`, ch 등등
#### 4) 굵기 : `font-weight`
#### 5) 밑줄, 가로줄 : `text-decoration`
#### 6) 글자 간격 : `letter-spacing`
#### 7) 행간 : `line-height`
#### 8) 정렬 : `text-align`
- left, right, center, justify(양쪽)

### 5. box model
- 웹 페이지 내의 콘텐츠들은 고유의 영역을 가지고 있다.
[layout](http://tcpschool.com/html/html_space_layouts)
#### 1) block vs inline vs inline block
- block : 줄바꿈이 가능하고 크기 지정이 가능한 박스.
- inline : 줄바꿈이 가능하지 않고 크기를 지정할 수 없는 박스.
- inline-block : 줄바꿈이 일어나지 않고 block 박스의 특징을 가지는 박스.
[https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)
[https://developer.mozilla.org/en-US/docs/Web/HTML/inline_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/inline_elements)

|    |block|inline-block|inline|
|----|-----|------------|-------|
|줄바꿈|o   |    x       |  x     |
|기본 너비|100%|글자가 차지하는 만큼|글자가 차지하는 만큼|
|크기조정|o|o|x|
####  2) box 구성요소
##### 1) border
```
p{
    border : 1px solid black;
}
```
- 테두리 두께(`border-width`), 테두리 스타일(`border-style`), 테두리 색상(`border-color`) 등등 속성이 있다.
##### 2) margin(바깥 여백), padding(콘텐츠와 테두리 사이 간격)
```
p{
    margin : 10px 10px 10px 10px
    padding : 10px 10px 10px 10px
}
```
- 각각 top, right, bottom, left 시계방향이다.

```
p{
    margin : 10px 20px 
    padding : 10px 20px 
}
```
- top과 bottom, left와 right가 각각 10px와 20px이다.
```
p{
    margin : 10px  
    padding : 10px  
}
```
- 값을 하나만 넣으면 사방에 여백이 적용된다.

##### 3) box를 벗어나는 컨텐츠
```
p{
overflow : auto;    
}
```
- overflow 속성을 auto로 설정하면 컨첸츠가 box를 벗어나는 경우 스크롤을 생성한다.

##### 4) 박스 크기 측정
```
*{
    box-sizing : border-box;
}
```
- 디자인을 할 때 여백을 고려하여 box의 크기를 디자인해야 한다.

이해위주로 공부하자.