# 전역 변수의 문제점

## 변수의 생명 주기
변수가 선언에 의해 생성되고 소멸하기까지의 한 과정을 변수의 **생명 주기**라 한다.

### 1. 지역 변수의 생명주기
지역 변수는 함수의 실행이 종료됨과 동시에 소멸되기 때문에 변수가 선언된 함수가 실행되는 동안에만 유효하다.

```js
var x = 'global';

function foo() {
  console.log(x);
  var x = 'local';
}

foo();
console.log(x); // global
```

### 2. 전역 변수의 생명주기
전역 변수는 프로그램의 실행이 종료되어야 비로소 소멸된다.

<br>

## 전역 변수의 문제점
1. 암묵적 결합
   - 전역 변수는 모든 코드가 전역 변수를 참조하고 변경할 수 있는 암묵적 결합을 허용한다. 
   - 코드의 가독성이 나빠지고 의도치 않게 상태가 변경될 수 있는 위험이 증가한다.
2. 긴 생명 주기
   - 생명주기가 길어 메모리 리소스를 오랜 기간 소비한다.
   - 의도치 않은 재할당이 이뤄질 수 있어 불안정적이다.
3. 스코프 체인 상에서 종점에 존재
   - 변수 검색 시 전역 변수의 검색 속도가 가장 느리다.
4. 네임스페이스 오염
   - 파일이 분리되어 있다 해도 전역 스코프는 하나를 공유한다.
   - 다른 파일에 동일한 식별자를 가진 전역 변수나 전역 함수가 존재할 경우 예상치 못한 결과가 나올 수 있다.

<br>

## 전역 변수의 사용을 억제하는 방법

### 즉시 실행 함수
즉시 실행 함수는 단 한 번만 호출되므로, 이러한 점을 이용해 전역 변수들을 즉시 실행 함수의 지역 변수로 만들어 한 번만 호출이 가능하도록 제한하는 방법이다.
```js
(function() {
  var foo = 10; // 즉시 실행 함수의 지역 변수
  // ...
}());

console.log(foo); // ReferenceError: foo is not defined
```

### 네임스페이스 객체
네임스페이스 역할을 할 객체를 생성한 뒤, 객체 안의 프로퍼티들을 전역 변수처럼 사용하는 방법이다.

```js
var MYAPP = {}; // 전역 네임스페이스 객체

MYAPP.person = {
  name: 'Lee',
  address: 'Seoul'
};

console.log(MYAPP.person.name); // Lee
```

### 모듈 패턴

모듈 패턴은 클래스 즉시 실행 함수로 만들어 모듈을 만든다.
모듈 패턴은 다음과 같은 특징을 갖고 있다.

- 전역 네임스페이스의 오염 방지
- 캡슐화의 구현

> 캡슐화(encapsulation)는 객체의 상태를 나타내는 프로퍼티와 프로퍼티를 동작하는 메소드를 하나로 묶는 것을 말한다.

```js
var Counter = (function() {
  // private 변수
  var num = 0;

  return {
    increase() {
      return ++num;
    },
    decrease() {
      return --num;
    }
  };
}());

console.log(Counter.num); // undefined

console.log(Counter.increase()); // 1
console.log(Counter.increase()); // 2
console.log(Counter.decrease()); // 1
console.log(Counter.decrease()); // 0
```


### ES6 모듈
ES6 모듈은 독자적인 모듈 스코프를 제공한다. ES6 모듈에서 전역 변수는 사용이 불가능하다. `<script>` 태그에 `type="module"` 어트리뷰트를 추가하여 사용한다.

```js
<script type="module" src="lib.mjs"></script> 
<script type="module" src="app.mjs"></script> 
```
ES6 모듈은 IE 등의 구형 브라우저에서는 동작하지 않으며, 사용하더라도 트랜스파일링이나 번들링이 필요하다. 따라서 아직까지는 ES6 모듈보다는 Webpack 등의 모듈 번들러를 사용하는 것을 선호한다.  
