# Box model

모든 HTML 요소는 Box 형태의 영역을 가지고 있다.
이 Box 는 Content, Padding, Border, Margin 으로 구성된다.

명칭     |  설명
---------|--------------------------------------------------------------------------------------
Content  | 요소의 텍스트나 이미지 등의 실제 내용이 위치하는 영역. width, height 속성을 갖는다.
Padding  | 테두리(Border) 안쪽에 위치하는 요소의 내부 여백 영역이다. padding 속성값은 패딩 영역의 두께를 의미하며 기본색은 투명(transparent)이다. 요소에 적용된 배경의 컬러, 이미지는 패딩 영역까지 적용된다.
Border   | 테두리 영역으로 border 속성값은 테두리의 두께를 의미한다.
Margin   | 테두리(Border) 바깥에 위치하는 요소의 외부 여백 영역이다. margin 속성값은 마진 영역의 두께를 의미한다. 기본적으로 투명(transparent)하며 배경색을 지정할 수 없다.

![Box Model](https://s3.amazonaws.com/viking_education/web_development/web_app_eng/css_box_model_chrome.png)

## 1. width / height
- 요소의 너비와 높이를 지정하기 위해 사용된다. 이때 지정되는 너비와 높이는 콘텐츠 영역을 대상으로 한다.
- 만약 width 와 height 로 지정한 콘텐츠 영역보다 실제 콘텐츠가 크면 콘텐츠 영역이 넘치게 된다.
- width 와 height 를 지정하기 위해서는 px, % 등의 크기 단위를 사용한다.

## 2. margin / padding
- margin 과 padding 속성은 content의 4개 방향(top,right,left,bottom)의 값을 각각 지정할 수 있다.
- 방향의 값을 각각 지정하지 않고 margin, padding 프로퍼티에 top, right, bottom, left 값순으로 속성값을 입력하면 4개 방향의 프로퍼티를 한번에 지정할 수가 있다.

## 3. border
### border-style 속성
```css
p { 
  border-style: solid;
}
```
`border-style` 속성은 4개 방향의 테두리에 어떤 스타일의 선을 나타낼지 지정한다.

![border-style](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile21.uf.tistory.com%2Fimage%2F254B5A3858C17901244D49)

### border-width
```css
p { 
  border-width: 10px;
}
```
`border-width` 속성은 테두리의 두께를 지정한다. 속성값의 개수에 따라 4면(top,right,left,bottom)에 대하여 지정이 가능하다.
> `border-width` 속성은 `border-style`과 함께 사용하지 않으면 적용되지 않는다.

### border-color
```css
p { 
  border-color: red;
}
```
`border-color` 속성은 테두리의 색상을 지정한다. 속성값의 개수에 따라 4면(top,right,left,bottom)에 대하여 지정이 가능하다.
> `border-color` 속성은 `border-style`과 함께 사용하지 않으면 적용되지 않는다.

### border
```css
p {
  border: solid 10px red;
}
```
`border` 는 `border-style`,`border-width`,`border-color`를 한번에 설정하기 위한 **shorthand** 속성이다.


## Reference
[웹 프로그래밍 튜토리얼](https://poiemaweb.com/)




