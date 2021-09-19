# 프로퍼티 어트리뷰트
프로퍼티 생성 시 자동으로 정의되는 프로퍼티의 내부 상태값들을 프로퍼티 어트리뷰트라 한다. `[[value]]`, `[[writable]]`, `[[enumerable]]`, `[[configurable]]`이 있다. 

<br>

## 내부 슬롯, 내부 메소드
자바스크립트 엔진의 구현 알고리즘을 설명하기 위해 ECMAScript에서 사용하는 **의사 프로퍼티** 와 **의사 메소드**. 프로퍼티나 메소드를 이중 대괄호 `[[...]]` 로 감싸 사용한다. 일부에 한해서 제한된 방법을 통해 간접적으로 접근이 가능한 비공개 슬롯(또는 메소드)이다.

<br>

## 프로퍼티 디스크립터 객체
```js
const person = {
  name: 'Lee'
};

console.log(Object.getOwnPropertyDescriptor(person, 'name'));
// {value: "Lee", writable: true, enumerable: true, configurable: ture}
```
`Object.getOwnPropertyDescriptor` 메소드를 호출하면 프로퍼티 어트리뷰트의 정보를 보여주는 **프로퍼티 디스크립터 객체**를 반환한다.

<br>

## 프로퍼티의 구분
### 데이터 프로퍼티
`key:value` 로 구성된 일반적인 프로퍼티를 말한다. 프로퍼티 생성 시 기본값으로 자동 정의된다.

### 접근자 프로퍼티
**접근자 함수**의 식별자를 접근자 프로퍼티라고 한다. 접근자 함수는 getter/setter 함수라고도 부른다.

위의 소스코드에서 get/set 함수가 접근자 함수, `fullName()` 으로 정의된 함수 식별자가 접근자 프로퍼티이다.

```js
const person = {
  // 데이터 프로퍼티
  firstName = 'Heejin',
  lastName = 'Na',

  // getter
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },

  // setter
  set fullName() {
    // 배열 디스트럭처링 할당
    [this.firstName, this.lastName] = name.split(' ');
  }
};

console.log(person.firstName + ' ' + person.lastName); // Heejin Na
```

접근자 프로퍼티는 데이터 프로퍼티의 값을 읽거나 저장할 때 호출하기 위해 사용된다.
```js
// 접근자 프로퍼티 fullName에 값을 저장하면 setter 함수가 호출된다.
person.fullName = 'Yeejin Na';
console.log(person); // {firstName: "Yejin", lastName: "Na"}

// 접근자 프로퍼티 fullName에 접근하면 getter 함수가 호출된다.
console.log(person.fullName); // Yejin Na
```


아래의 소스코드는 데이터 프로퍼티와 접근자 프로퍼티의 프로퍼티 어트리뷰트를 각각 호출했을 때 반환되는 프로퍼티 디스크립터 객체이다. 접근자 프로퍼티는 값이 없기 때문에 프로퍼티 어트리뷰트 `[[value]]`를 갖지 않는다.

```js
// 데이터 프로퍼티 'firstName'
let descriptor = Object.getOwnPropertyDescriptor(person, 'firstName');
// {value: "Heejin". writable: true, enumberable: true, configurable: true}

// 접근자 프로퍼티 'fullName'
descriptor = Obejct.getOwnPropertyDescriptor(person, 'fullName');
// {get: f, set: f, enumerable: true, configurable: true}

```


