# strict mode
**암묵적 전역**(implicit global)은 오류를 발생시키는 원인이 될 수 있다. 이러한 위험을 해소하기 위해 ES5부터 추가된 strict mode는 자바스크립트의 문법을 좀 더 엄격화하여 문제를 일으킬 가능성이 있는 코드에 명시적인 에러를 발생시키게 한다.

추가로 문법적 오류를 포함해 잠재적 오류와 그 원인까지 리포팅해주는 ESLint가 있는데, 코딩 컨벤션까지 관리할 수 있어 strict mode보다 선호되기도 한다.

ES6에서 도입된 클래스와 모듈에는 strict mode가 기본적으로 적용된다.

<br>

## 적용 방법
strict mode는 반드시 코드의 선두에 `'use strict';`를 추가해야 한다. 전역의 선두에 추가하면 스크립트 전체에 적용되고, 함수 몸체의 선두애 추가하면 해당 함수와 중첩 함수에서만 strict mode가 적용된다.
```js
'use strict';

function foo() {
  x = 10; // ReferenceError: x is not defined
}
foo();
```
strict mode가 코드의 선두에 위치하지 않을 경우 제대로 적용되지 않는다.

<br>

## 주의 사항
1. 전역에 strict mode를 적용하는 것은 바람직하지 않다. 외부 라이브러리를 사용할 경우 strict mode가 적용되지 않은 스크립트와 혼용되어 오류를 발생시킬 수 있기 때문.

  > ### 해결 방법
  > 즉시 실행 함수로 스크립트 전체를 감싸고 즉시 실행 함수의 선두에 strict mode를 위치시킨다.
  > ```js
  > (function () {
  >   'use strict';
  >
  >   // Do something...
  > }());
  > ```


2. 함수 단위로 strict mode를 적용하는 것도 피하는 것이 좋다.

<br>

## strict mode 적용 시 발생하는 에러
1. 암묵적 전역
2. 변수, 함수, 매개변수의 삭제
3. 매개변수 이름의 중복
4. with 문의 사용

<br>

## strict mode 적용으로 인한 변화
1. strict mode에서 일반 함수 호출 시 this에 `undefined`가 바인딩된다.
2. 매개변수에 전달된 인수를 재할당하여 변경해도 arguments 객체에 반영되지 않는다.




