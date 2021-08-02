# HTML (Hypertext Markup Language)
HTML 은 웹을 다루는 가장 기본적인 구성 요소로, 웹 콘텐츠의 **의미와 구조를 정의**할 때 사용한다.
하이퍼텍스트(Hypertext) 란 웹 페이지를 다른 페이지로 연결하는 링크를 의미한다. (링크는 웹의 근본적인 속성이다.)

 

## 요소 (Element)

```html
<tagname> contents </tagname>

```

- HTML 은 웹 브라우저에 표시되는 글과 이미지 등의 콘텐츠를 나타내기 위해서 "요소"를 사용해 마크업한다.
- 요소는 "태그"를 사용해서 문서의 다른 텍스트와 구분한다. `<태그명>` 으로 이루어진다.
- HTML 의 요소는 기본적으로 시작 태그(start tag)와 종료 태그(end tag), 그리고 그 사이에 위치한 content 로 구성된다.
- HTML document 는 요들의 집합으로 이루어진다.
- 태그는 대소문자를 구별하지 않으나, 소문자를 사용하는 것이 일반적이다.
- 종료 태그에는 `/` 가 붙는다.

### Headings 

```html
<h1>Heading 1</h1>
```

- Headings 태그는 제목을 나타낼 때 사용하며,  <h1>부터 <h6> 까지 사용할 수 있다.
- <h1> 의 크기가 가장 크며, h6 의 크기가 가장 작다.
- 제목 단계를 건너뛰어서 사용하는 것보다, 순서대로 사용하는 것이 좋다.
- 페이지 당 하나의 `<h1>` 만 사용하는 것이 좋다. 전체 페이지의 목적을 설명하는 가장 중요한 제목이기 때문.

## 빈 요소 (Empty/Self-closing Element)

컨텐츠를 갖지 않는 요소를 빈 요소라고 한다. 빈 요소는 컨텐츠가 없으므로 종료 태그를 사용하지 않으며, 속성(Attribute) 만을 가질 수 있다.

### br 요소

```html
<h1>Title</h1>
<br>
<h2>Subtitle</h2>
```

- html 에서 줄바꿈(line break)을 하는데 사용된다.
- 문단과 문단 사이 여백을 줄 수 있다.
- 빈 요소로, 종료 태그가 없다.
- 1개 이상의 줄바꿈 태그를 입력해도, 1개의 공백으로 표시된다.

## 속성 (Attribute)

속성은 element 안에 사용하여 default 값을 변경해줌으로써 태그에 특정한 성격을 부여해 준다.
ex) `size`, `color`, `align`, `width`

### hr 요소

```html
<hr size="3" color=blue align=left noshade>
```

- `<hr>` 은 'horizontal rule' 의 약자로, 가로로 된 줄을 삽입할 수 있다.
- `<hr>` 은 attribute 값을 지정해 스타일을 바꿀 수 있다.

## 주석 (Comments)

```html
<!-- This is a comment -->
```

문장이나 문단의 시작에 `<!--` , 맨 끝에 `-->` 를 붙이면 주석(comments)을 달 수 있다. 

주로 코드에 대한 설명을 덧붙이거나 코드를 잠시 비활성화하는 데 사용된다.

브라우저는 주석을 화면에 표시하지 않는다.

## 웹페이지를 구성하는 기본 태그

### 1. HTML5 의 문서 형식 정의 태그

문서 형식 정의(Document Type Definition, DTD) 태그는 출력할 웹 페이지의 형식을 브라우저에게 전달한다. 문서의 최상위에 위치해야 하며 대소문자를 구별하지 않는다.

```html
<!DOCTYPE html>
```

### 2. html 

html 요소 HTML 요소의 부모 요소로, 웹페이지에 단 하나만 존재한다.

따라서 모든 요소는 html 요소의 자식 요소이며 html 요소 안에 기록되어야 한다.

단, `<!DOCTYPE>` 은 예외이다.

```html
<!DOCTYPE html>
	<html>
	</html>
```

### 3. head 요소

`<head>` 요소는 컴퓨터가 식별할 수 있는 문서 정보(메터데이터)를 담는 요소이다.

정보로는 문서가 사용할 제목, 스크립트, 스타일 시트 등이 있다.

```html
<!DOCTYPE html>
	<html>
		<head>
		</head>
	</html>
```

### 4. title 요소

`<title>` 요소는 브라우저의 제목 표시줄이나 페이지 탭에 보이는 문서 제목을 정의한다.

```html
<!DOCTYPE html>
	<html>
		<head>
			<title>This is title</title>
		</head>
	</html>
```

### 5. meta 요소

base, link, script, style, title 과 같은 다른 메타관련 요소로 나타낼 수 없는 Metadata 를 나타낸다.

`charset` 속성은 브라우저가 사용할 문자셋을 정의한다.

```html
<!DOCTYPE html>
	<html>
		<head>
			<meta charset="utf-8">
			<title>This is title</title>
		</head>
	</html>
```

### 6. body 요소

HTML 문서의 내용을 나타내는 요소이다. 한 문서에는 하나의 `<body>` 요소만 존재할 수 있다.

```html
<!DOCTYPE html>
	<html>
		<head>
			<meta charset="utf-8">
			<title>This is title</title>
		</head>
		<body>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
		</body>
	</html>
```

## 텍스트 태그

### 1. p 요소

```html
<!DOCTYPE html>
<html>
	<body>
		<h1>This is Heading</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
	</body>
</html>
```

- 하나의 문단(paragraph)을 나타내는 요소
- HTML 에서 문단은 이미지나 입력 폼 등 서로 관련있는 컨텐츠 무엇이든 될 수가 있다.
- 컨텐츠를 문단으로 나누면 페이지의 접근성을 높일 수 있다.

### 2. i 요소

```html
This text is <i>italic</i>.
```

- Italic 체를 지정해주는 요소
- 의미X

### 3. em 요소

```html
This text is <em>emphasized</em>
```

- 중요한 부분을 이탤릭체로 강조(emphasize) 하는 시멘틱 요소
- `<em>` 을 중첩하면 더 큰 강세를 의미하게 된다.

### 4. b 요소

```html
This text is <b>bold</b>.
```

- 텍스트를 굵게 표현해주는 요소. 의미론적 중요성이 없다.

### strong 요소

```html
This text is <strong>strong</strong>.
```

- 중요한 부분을 굵은 글씨로 나타내주는 시멘틱 요소이다.

### ul 요소

```html
<ul>
	<li>first item</li>
	<li>second item</li>
	<li>third item</li>
</ul>
```

- 정렬되지 않은 목록(unordered list) 을 나타낼 때 사용하는 요소
- 보통 불릿으로 표현한다.

### ol 요소

```html
<ol>
	<li>first item</li>
	<li>second item</li>
	<li>third item</li>
</ol>
```

- 정렬된 목록(ordered list) 을 나타내는 요소
- 보통 숫자로 표현한다.
	
	
### Reference
[MDN Web Docs] (https://developer.mozilla.org/ko/docs/Web/HTML)
