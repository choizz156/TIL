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
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>HTML</title>
</head>
<body>
<h1><u>HTML</u></h1>
<ol>
    <li>html</li>
    <li>CSS</li>
    <li>world wide</li>
</ol>
<input value="blue" type = "radio" name = "color">
<div>
<input type = "text" placeholder="id please">
</div>
<div>
<input type = "text" placeholder="passward">
</div>
<div>
    <input type = "checkbox"> 아이디를 기억할까요?
</div>
<input type  = "radio" name = "aaaa" > yes
<input type = "radio" name = "aaaa"> no

<br>하이퍼 텍스트 마크업 언어(영어: Hyper Text Markup Language, HTML, 문화어: 초본문표식달기언어, 하이퍼본문표식달기언어)는 웹 페이지 표시를 위해 개발된 지배적인 마크업 언어다. 또한, HTML은 제목, 단락, 목록 등과 같은 본문을 위한 구조적 의미를 나타내는 것뿐만 아니라 링크, 인용과 그 밖의 항목으로 구조적 문서를 만들 수 있는 방법을 제공한다. 그리고 이미지와 객체를 내장하여 대화형 양식을 생성하는 데 사용될 수 있다. HTML은 웹 페이지 콘텐츠 안의 꺾쇠 괄호에 둘러싸인 "태그"로 되어있는 HTML 요소 형태로 작성한다. HTML은 웹 브라우저와 같은 HTML 처리 장치의 행동에 영향을 주는 자바스크립트, 본문과 그 밖의 항목의 외관과 배치를 정의하는 CSS 같은 스크립트를 포함하거나 불러올 수 있다. HTML과 CSS 표준의 공동 책임자인 W3C는 명확하고 표상적인 마크업을 위하여 CSS의 사용을 권장한다.
</br>
<br>
1980년, 유럽 입자 물리 연구소(CERN)의 계약자였었던 물리학자 팀 버너스리가 <a href = "https://ko.wikipedia.org/wiki/HTML" target ="_blank" title ="html explain">HTML</a>의 원형인 인콰이어를 제안하였다. 인콰이어는 CERN의 연구원들이 문서를 이용하고 공유하기 위한 체계였다. 1989년에 팀 버너스리는 인터넷 기반 하이퍼텍스트 체계를 제안하는 메모를 작성했다.[2] 버너스 리는 1990년 말에 HTML을 명시하고, 브라우저와 서버 소프트웨어를 작성했다. 그 해에 버너스리와 CERN 데이터 시스템 엔지니어 로버트 카일리아우와 함께 CERN측에 자금 지원을 요청하였지만, 이 프로젝트는 CERN으로부터 정식으로 채택 받지 못했다. 버너스리의 개인적인 기록[3]에 1990년부터 "하이퍼텍스트가 사용되는 여러 분야의 일부"를 열거했고 백과사전을 그 목록의 첫 번째로 두었다.
</br>

<p>HTML 최초의 일반 공개 설명은 1991년 말에 버너스리가 처음으로 인터넷에서 문서를 "HTML 태그"(HTML tag)로 부르면서 시작되었다.[4][5]

    그것은 머릿글자로 이루어진 20개의 요소를 기술하였고, 상대적으로 HTML의 단순한 디자인이었다. 하이퍼링크를 제외한 HTML 태그들은 CERN 자체의 SGML 기반 문서화 포맷인 SGML GUID에 강하게 영향을 받았다. 이 요소 중 13개는 HTML 4 버전에서도 여전히 존재한다.[6]

    HTML은 동적인 웹 페이지의 웹 브라우저를 통한 문자와 이미지 양식이다. 문자 요소의 대부분은 1988년 ISO 기술 보고서 9537 SGML을 이용한 기법에서 찾을 수 있다. 하지만 SGML 개념의 일반적인 마크업은 단지 개별 효과 보다는 요소 기반이고 또한 구조와 처리의 분리(?)(HTML은 CSS와 함께 이 방향으로 점진적으로 이동해 왔다.)
</p>

</body>
</html >
```
