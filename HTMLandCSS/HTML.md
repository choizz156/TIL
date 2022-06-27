## HTML(HyperText Markup Langauage)
> 웹 페이지의 내용과 구조를 tag를 이용해서 작성하는 마크업 언어.

- < tag name>으로 시작(open)해서 < /tag name>으로 끝내(closing) 해당 tag가 끝났음을 나타낸다. 예외가 있긴 함

- HTML 기본구조
```
<!DOCYTYPE HTML>
 <html>
  <head>
     <title>HTML 기본구조</title>
     <meta charset="UTF-8">
  </head>
  <body>
   
  </body>
 </html>
```
### 1. 자주 쓰이는 tag

| tag  | 특징 |
|------|-----|
| < html > | < head >와 < body >를 감싼다. 
| < head > | < body >를 설명하는 것(title 등)을 < head >로 묶는다.
| < body > | 본문 내용
| < title > | 제목
| < meta charset="UTF-8"> | 웹페이지 출력 방식
| < h1 > | 구획 제목
| < br > | 한 줄씩 줄바꿈, 여러번 사용해서 단락간 간격 조정 가능
| < P >  | 한 단락씩 줄 바꿈, 간격 조정 못함. -> CSS사용
| < div > | 한 줄을 다 차지
| < span > | 컨텐츠 크기만큼 차지
| < img > | 그림
| < a > (anchor) | 링크
| < section > | 큰 의미 단위로 묶음
| < ul > (unordered line) | 앞에 숫자가 붙지 않는 목록 생성
| < ol > (ordered line) | 앞에 숫자가 붙는 목록 생성
| < li > (list) | < ol >이나 < ul >에 포함돼어 목록을 작성.
| < input > | 입력 폼
| < textarea > | 입력 폼인데 줄 바꿈이 가능
| < button > | 버튼

### 2. Attribute
> tag의 이름만으로 정보가 부족할 때 속성을 부여해서 정보를 추가한다.
- 속성 이름과 속성 값으로 구성된다.
- tag name 바로 뒤에 속성이 붙고 속성끼리 순서는 상관없다.
```
<img src = "~~" width = "100"> //여기는 closing tag가 안 붙어도 된다.
<a href = "https://naver.com" target = "_blank" title = "네이버"> 네이버 </a> 
<input type = "text" placeholder = "type here">
<input type = "radio" name = "aaa">
<input type = "radio" name = "aaa">
<input type = "checkbox">
```

