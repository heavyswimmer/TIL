# Form element
form 태그는 사용자가 입력한 데이터를 수집하기 위한 대화형 컨트롤을 생성할 수 있다.
input, textarea, button, select, checkbox, radio button, submit button 등의 **입력 양식 태그** 를 포함할 수 있다.

```html
<form>
form elements(input, checkbox, radio button, submit button, ...)
</form>
```


## input
input 태그는 form 태그 중에서 가장 중요한 태그로 사용자로부터 데이터를 입력받기 위해 사용된다.<br>
input 태그는 다양한 종류가 있으며 type 속성에 의해 구분된다.
서버에 전송되는 데이터는 name 어트리뷰트를 키로, value 어트리뷰트를 값으로 하여 key=value 의 형태로 전송된다.

## select
여러 개의 리스트에서 여러 개의 아이템을 선택할 때 사용한다.<br>
서버에 전송되는 데이터는 select 요소의 name 속성을 key 로, option 요소의 value 속성을 값으로 하여 key=value 의 형태로 전송된다.

## textarea
여러 줄의 글자를 입력할 때 사용한다.

## button
클릭할 수 있는 버튼을 생성한다.
input 태그는 빈 태그이지만 button 태그에는 텍스트나 이미지 등의 콘텐츠를 사용할 수 있다는 차이가 있다.<br>
type 속성은 반드시 지정하는 것이 바람직하며 속성값으로 button, reset, submit 을 지정할 수 있다.

## fieldset/legend
fieldset 태그는 관련된 입력 양식들을 그룹화할 때 사용한다. legend 태그는 fieldset 태그 내에서 사용되어야 하며 그룹화된 fieldset 의 제목을 정의한다.

## Reference
[MDN 요소 참고서](https://developer.mozilla.org/ko/docs/Web/HTML/Element/form) <br>
[모던 자바스크립트 Deep Dive 문서](https://poiemaweb.com/html5-tag-forms)
