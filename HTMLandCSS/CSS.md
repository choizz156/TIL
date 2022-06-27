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
#### 4) 굵기 : font-weight
#### 5) 밑줄, 가로줄 : text-decoration
#### 6) 글자 간격 : letter-spacing
#### 7) 행간 : line-height
#### 8) 정렬 : text-align
- left, right, center, justify(양쪽)

### 5. box model
- 웹 페이지 내의 콘텐츠들은 고유의 영역을 가지고 있다.
