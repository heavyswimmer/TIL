# 클로저

> *"A closure is the combination of a function and the lexical environment within that function was declared."*

중첩 함수가 상위 식별자를 참조하고, 외부 함수가 중첩 함수를 반환하여 외부 함수보다 생명주기가 길 경우, 이러한 중첩 함수를 **클로저**라 부른다.

<br>

## 렉시컬 스코프
렉시컬 환경의 outer lexical environment reference에 저장할 참조값, 즉 상위 스코프에 대한 참조는 함수 정의가 평가되는 시점에 함수가 정의된 환경(위치)에 의해 결정된다.

<br>

## 함수 객체의 내부 슬롯 [[Environment]]
함수는 자신의 내부 슬롯 [[Environment]]에 자신이 정의된 환경, 즉 상위 스코프의 참조를 저장한다.

<br>

## 클로저의 활용
```js
// 카운트 상태 변수
let num = 0;

// 카운트 상태 변경 함수
const increase = function () {
  // 카운트 상태를 1만큼 증가시킨다.
  return ++num;
};

console.log(increase()); // 1
console.log(increase()); // 2
console.log(increase()); // 3
```
 전역 변수를 통해 관리된다면 누구나 접근 및 변경이 가능해(암묵적 결합) 의도치 않게 상태가 변경될 수 있다. 클로저는 상태를 안전하게 **은닉**하고 특정 함수에게만 상태 변경을 허용하기 위해 사용된다. 정보 은닉은 객체 간의 **결합도**(coupling)을 낮추는 효과가 있다.
