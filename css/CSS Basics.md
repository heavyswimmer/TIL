# CSS(Cascading Stylesheets)
CSS는 HTML 이 정의한 요소들의 스타일과 레이아웃을 어떻게 나타낼지를 지정하기 위한 언어이다.
따라서 콘텐츠의 글꼴, 색상, 크기 및 간격을 변경하거나 여러 열로 분할하거나 애니메이션 및 기타 장식 기능을 추가하는 등의 웹 페이지 스타일 및 레이아웃에 사용된다.

## CSS를 HTML 문서에서 사용하는 방법
### 1. Inline CSS
HTML요소의 style property에 CSS를 기술하는 방식이다. JavaScript가 동적으로 CSS를 생성할 때 사용되는 경우가 있으나, 일반적인 경우 CSS 파일을 따로 링크해서 사용한다.
```html
<!DOCTYPE html>
  <body>
    <h1 style="color: red">Hello World</h1>
  </body>
</html>
```

### 2. Internal CSS (Embedding style)
HTML 내부에 CSS 를 포함시키는 방식이다. `<head>` 태그 안에 `<style>` 태그를 정의하여 사용한다.
매우 간단한 웹 페이지의 경우에는 문제될 것이 없으나, 복잡한 웹 페이지의 경우 일일이 수정해야 한다는 단점이 있다.
또한 HTML과 CSS는 서로 역할이 다르기 때문에, 각각 다른 파일로 구분하여 작성하고 관리하는 것이 바람직하다.
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 {
      color: red
      }
    </style>
  </head>
</html>
```


### 3. External CSS (Link style)
HTML에서 외부에 있는 CSS 파일을 로드하는 방식으로 가장 일반적으로 사용된다.
```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="css/style.css">
  <head>
  <body>
  </body>
</html>
```


## CSS의 구조
CSS는 규칙 기반 언어이며, 웹 페이지의 특정 요소 또는 요소 그룹에 적용할 스타일 그룹을 지정하는 규칙을 정의한다. 
```css
h1 {
  color: red;
}
```
- 규칙은 선택자(selector) 와 함께 열린다. 스타일을 지정할 HTML 요소를 *선택*한다.
- 그런 다음 중괄호 안에 `속성: 값;` 형태의 하나 이상의 선언을 지정한다. 선언은 선택한 요소의 속성을 지정하고 속성에 부여할 값을 지정한다.

## 선택자(Selector)
![CSS selector](https://poiemaweb.com/img/css-syntax.png)
> CSS는 HTML 요소의 style을 정의하는 데 사용된다. 이를 위해서 선행되어야 하는 것은 **스타일을 적용하고자 하는 HTML 요소를 선택**할 수 있어야 한다.
> 선택자(selector)는 스타일을 적용하고자 하는 HTML 요소를 선택하기 위해 CSS 에서 제공하는 수단이다.
### 1. Type 선택자
```css
h1 {}
```
Type 선택자는 요소 이름을 선택해 스타일을 지정하는 선택자이다. 따라서 HTML 문서 내에 선택된 요소는 모두 포함되어 스타일이 지정된다.

### 2. Class 선택자
```css
.box {}
```
HTML 요소에 class 어트리뷰트 값은 공백으로 구분하여 어려 개 지정할 수 있다.
아래와 같이 클래스 선택자를 사용하여 미리 스타일을 정의해 두고, HTML 요소는 이미 정의되어 있는 클래스를 지정하는 것으로 필요한 스타일을 지정할 수 있다.
이것은 **재사용**의 측면에서 유용하다.

### 3. ID 선택자
```css
#unique {}
```
ID 속성값을 지정하여 일치하는 요소를 선택한다. ID 속성값은 한 HTML 문서 안에서 중복해서 사용할 수 없다.

### 4. Pseudo 선택자
요소의 특정 **상태**를 스타일링하는 선택자이다.

예를 들어,
```css
a:hover {}
```
`:hover` 라는 Pseudo 선택자는 마우스 포인터가 요소를 가리킬 때만 스타일이 지정되는 선택자이다.

## Reference
[MDN](https://developer.mozilla.org/ko/docs/Learn/CSS/)<br>
[모던 자바스크립트 Deep Dive](https://poiemaweb.com/)
