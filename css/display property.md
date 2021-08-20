# display 속성

display 속성은 layout 정의에 자주 사용되는 중요한 프로퍼티이다.
모든 HTML 요소는 CSS 적용없이도 기본적으로 표현되는 고유한 default 값을 가진다.
HTML 요소들은 block 또는 inline 의 속성값을 기본값으로 갖게 된다.

예를 들면 문단을 나타내는 `<p>` 요소는 크롬 브라우저에서 아래의 default 속성값을 갖고 있다.
```css
  p {
    display: block;
  }
```

> display 속성은 상속되지 않는다.

## 1. block 레벨 요소
`block` 값을 가진 요소들은 아래와 같은 특징을 갖는다.
> - 항상 새로운 라인에서 시작한다.
> - 화면 크기 전체의 가로폭(width)을 차지한다. (width: 100%)
> - width, height, margin, padding 속성의 지정이 가능하다.
> - block 레벨 요소 내에 inline 레벨 요소를 포함할 수 있다.

ex) div, heading, p, ol, ul, li, hr, table, form


## 2. inline 레벨 요소
`inline` 값을 가진 요소들은 아래와 같은 특징을 갖는다.
> - 새로운 라인에서 시작하지 않으며 문장의 중간에 들어갈 수 있다. 즉, 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치한다.
> - content의 너비만큼 가로폭(width)을 차지한다.
> - width, height, margin-tom, margin-bottom 속성을 지정할 수 없다. 상, 하 여백은 line-height로 지정한다.
> - inline 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동으로 지정된다.
> - inline 레벨 요소 내에 block 레벨 요소를 포함할 수 없다. inline 레벨 요소는 일반적으로 block 레벨 요소에 포함되어 사용된다.

ex) span, a, strong, img, br, input, select, textarea, button


## 3.inline-block 레벨 요소
block과 inline 레벨 요소의 특징을 모두 갖는다.
**inline 레벨 요소와 같이 한 줄에 표현되면서 width, height, margin 속성을 모두 지정할 수 있다.**
> - 기본적으로 inline 레벨 요소와 흡사하게 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치시킬 수 있다.
> - block 레벨 요소처럼 width, height, margin, padding 속성을 모두 정의할 수 있다. 상,하 여백을 margin과 line-height 두가지 속성 모두를 통해 제어할 수 있다.
> - content의 너비만큼 가로폭(width)을 차지한다.
> - inline-block 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동으로 지정된다.

