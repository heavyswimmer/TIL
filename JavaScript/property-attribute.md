# 프로퍼티 어트리뷰트
프로퍼티 생성 시 자동으로 정의되는 프로퍼티의 내부 상태값들을 프로퍼티 어트리뷰트라 한다. 프로퍼티 어트리뷰트에는 **데이터 프로퍼티**와 **접근자 프로퍼티**가 있다.

<br>

> **내부 슬롯, 내부 메서드**
>
> 자바스크립트 엔진의 구현 알고리즘을 설명하기 위해 ECMAScript에서 사용하는 **의사 프로퍼티** 와 **의사 메서드**. 프로퍼티나 메소드를 이중 대괄호 `[[...]]` 로 감싸 사용한다. 일부에 한해서 제한된 방법을 통해 간접적으로 접근이 가능한 비공개 슬롯(또는 메서드)이다.

<br>

## 데이터 프로퍼티
`key:value` 로 구성된 일반적인 프로퍼티를 말한다. 프로퍼티 생성 시 기본값으로 자동 정의된다.

<table>
  <thead>
    <th>프로퍼티 어트리뷰트</th>
    <th>설명</th>
  </thead>
  <tbody>
    <tr>
      <td>[[Value]]</td>
      <td>- 해당 프로퍼티 키의 값을 반환해준다. <br>
      - 프로퍼티 키를 통해 프로퍼티 값을 변경하면 [[Value]]에 값을 재할당한다. 이때 프로퍼티가 없으면 프로퍼티를 동적 생성하고 생성한 프로퍼티의 [[Value]]에 값을 저장한다.</td>
    </tr>
    <tr>
      <td>[[Writable]]</td>
      <td>- 프로퍼티 값의 변경 가능 여부를 나타낸다. <br>
      - 값이 false인 경우 해당 프로퍼티의 value 값을 변경할 수 없는 읽기 전용 프로퍼티가 된다.</td>
    </tr>
    <tr>
      <td>[[Enumerable]]</td>
      <td>- 프로퍼티의 열거 가능 여부를 나타낸다.<br>
      - 값이 false인 경우 해당 프로퍼티는 for...in문이나 Object.Keys 메서드 등으로 열거할 수 없다.</td>
    </tr>
    <tr>
      <td>[[Configurable]]</td>
      <td>- 값을 false로 설정하면 해당 프로퍼티를 객체에서 제거하거나 수정할 수 없게 된다. <br>
      - 해당 프로퍼티에서 delete를 호출해도 무시된다.</td>
    </tr>

  </tbody>
</table>

## 접근자 프로퍼티
**접근자 함수**(getter/setter)의 식별자를 접근자 프로퍼티라고 한다.

다음의 소스코드에서 get/set 함수가 접근자 함수, `fullName()` 으로 정의된 함수 식별자가 접근자 프로퍼티이다.

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

<br>

## 🔍 How to read?
`Object.getOwnPropertyDescriptor` 메서드를 호출하면 프로퍼티 어트리뷰트의 정보를 읽을 수 있는 **프로퍼티 디스크립터 객체**를 반환한다. 프로퍼티가 포함된 객체명과 정보를 읽을 프로퍼티 이름을 매개변수로 받는다. 한번에 여러 프로퍼티들의 정보를 읽어야 할 때는 `Object.getOwnPropertyDescriptors` 메서드를 사용한다.
```js
const person = {
  name: 'Lee'
};

console.log(Object.getOwnPropertyDescriptor(person, 'name'));
// {value: "Lee", writable: true, enumerable: true, configurable: ture}
```




