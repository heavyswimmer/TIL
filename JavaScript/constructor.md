# 생성자 함수에 의한 객체 생성
**new 연산자와 함께** 호출하여 객체를 생성하는 함수를 생성자 함수(constructor)라 한다. 인스턴스는 생성자 함수에 의해 생성된 객체를 지칭한다.

## Object 생성자 함수

```js
// 빈 객체 생성
const person = new Object();

// 프로퍼티 추가
person.name = 'Lee';
person.sayHello = function() {
  console.log('Hello! My name is ' + this.name);
};

console.log(person); // {name: "Lee", sayHello: f}
person.sayHello(); // Hello! My name is Lee
```

Object 생성자 함수를 사용하여 빈 객체를 생성하는 방식은 객체 리터럴을 사용하는 방법보다 복잡하고 비효율적이다.

<br>

## 생성자 함수
객체 리터럴을 사용한 객체 생성 방식은 하나의 객체씩만 생성 가능하다. 따라서 동일한 프로퍼티를 가진 객체를 여러 개 생성해야 할 때는 생성자 함수를 사용하는 것이 효율적이고 간편하다.

```js
// 객체 리터럴을 사용한 객체 생성
const circle1 = {
  radius: 5,
  getDiameter() {
    return 2 * this.radius;
  }
};

const circle2 = {
  radius: 10,
  getDiameter() {
    return 2 * this.radius;
  }
};

// 생성자 함수
function Circle(radius) {
  // 생성자 함수 내부의 this는 생성자 함수가 생성할 인스턴스를 가리킨다.
  this.radius = radius;
  this.getDiameter = function() {
    return 2 * this.radius;
  };
}

// 인스턴스 생성
const circle1 = new Circle(5);
const circle2 = new Circle(10);

console.log(circle1.getDiameter()); // 10
console.log(circle2.getDiameter()); // 20
```

### 생성자 함수의 내부 메소드
함수는 객체이지만 일반 객체와 달리 호출이 가능하다. 따라서 일반 객체가 갖는 내부 슬롯과 내부 메소드에 더해 추가로 함수로서 동작하기 위한 `[[Call]]`, `[[Construct]]` 등의 내부 메소드를 추가로 가지고 있다.

함수가 일반 함수로 호출되면 함수 객체의 내부 메소드 `[[Call]]`이 호출되고, new 연산자와 함께 생성자 함수로 호출되면 `[[Construct]]`가 호출된다.

```js
function foo() {}

// 일반 함수로 호출
foo(); // [[Call]] 호출

// 생성자 함수로 호출
new foo(); // [[Construct]] 호출
```

### callable
내부 메소드 `[[Call]]`을 갖는 함수 객체를 *callable*이라 한다. 호출할 수 없는 객체는 함수 객체가 아니기 때문에 함수 객체는 반드시 *callable*이어야 한다. 따라서 모든 함수 객체는 내부 메소드 `[[Call]]`을 갖고 있으며 호출이 가능하다.

### constructor와 non-constructor
`[[Call]]` 과 달리 모든 함수 객체가 `[[Construct]]`를 갖는 것은 아니다. `[[Construct]]`를 갖는 함수 객체를 *constructor*, `[[Construct]]`를 갖지 않는 함수 객체를 *non-constructor*라 부른다.

이는 즉 모든 함수 객체는 일반 함수로서는 호출이 가능하지만, 반드시 생성자 함수로서 호출할 수 있는 것은 아니라는 의미이다.

### new 연산자
new 연산자와 함께 함수를 호출하면 `[[Construct]]`가 호출되며 생성자 함수로 동작한다. 때문에 new 연산자와 함께 호출할 함수는 *non-constructor*가 아닌 *constructor*이어야 한다.

new 연산자 없이 호출하면 `[[Call]]`이 호출되며 일반 함수로서 동작한다.

### new.target
ES6에서 도입되었다. 함수 내부에서 사용시 new 연산자와 함께 생성자 함수로서 호출이 되었는지 확인이 가능하다. IE에서는 지원되지 않으므로 대신 스코프 세이프 생성자 패턴을 사용할 수 있다.

```js
function Circle(radius) {
  if(!new.target) {
    // new 연산자와 함께 생성자 함수를 재귀 호출하여 생성된 인스턴스 반환
    return new Circle(radius);
  }
  this.radius = radius;
  this.getDiameter = function() {
    return 2 * this.radius;
  };
}

// new 연산자 없이 호출해도 new.target을 통해 생성자 함수로서 호출됨
const circle1 = Circle(5);
console.log(circle1.getDiameter()); // 10
```