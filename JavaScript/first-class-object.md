# 함수와 일급 객체

## 일급 객체
일급 객체는 다음의 조건을 만족하는 객체를 뜻한다.

> 1. 런타임에 생성 가능
> 2. 변수나 자료구조에 저장 가능
> 3. 함수의 매개변수에 전달 가능
> 4. 함수의 반환값으로 사용 가능

자바스크립트의 함수는 위의 조건을 모두 만족시키는 일급 객체이다.

<br>

## 함수 객체의 프로퍼티

### arguments 프로퍼티
함수 객체의 arguments 프로퍼티 값은 arguments 객체이다.
자바스크립트에서는 함수를 호출할 때 전달되는 인수의 개수를 확인하지 않기 때문에 가변 인자 함수를 구현할 때 arguments 객체가 유용하게 사용된다.
arguments 객체는 **유사 배열 객체**이기 때문에 배열 메소드를 직접 접근해서 사용할 수 없다. ES6에서 **Rest 파라미터**가 새로 도입되면서 arguments 객체의 중요성이 줄어 들었다.

> #### 유사 배열 객체
> 배열의 형태로 인자 정보를 갖고 있지만 실제로 배열은 아닌 객체

### caller 프로퍼티
ECMAScript 사양에 포함되지 않은 비표준 프로퍼티이므로 사용하지 않는다.

### length 프로퍼티
함수를 정의할 때 선언한 매개변수의 개수를 가리키는 프로퍼티이다.
arguments 객체의 length 프로퍼티와 함수 객체의 length 프로퍼티의 값이 다를 수 있으므로 주의해야 한다.

### name 프로퍼티
함수 이름을 나타내는 프로퍼티이다. ES5와 ES6에서 다르게 동작하므로 주의해야 한다. 익명 함수 표현식의 경우 ES5에서는 **빈 문자열**을 값으로 갖지만, ES6에서는 함수 객체를 가리키는 **식별자**를 값으로 갖는다.

### \_\_proto\_\_ 접근자 프로퍼티
`[[Prototype]]` 내부 슬롯이 가리키는 프로토타입 객체에 접근하기 위해 사용한다.

```js
const obj = { a:1 };
console.log(obj.__proto__ === Object.prototype); // true

console.log(obj.hasOwnProperty('a'));         // true
console.log(obj.hasOwnProperty('__proto__')); // false
```

### prototype 프로퍼티
constructor만 소유할 수 있는 프로퍼티이다. 생성자 함수가 생성할 인스턴스의 프로토타입 객체를 나타내주는 프로퍼티이다.

```js
(function () {}).hasOwnProperty('prototype'); // true
({}).hasOwnProperty('prototype'); // false
```
