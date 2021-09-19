# let, const 키워드와 블록 레벨 스코프
var 키워드로 선언한 변수의 문제점은 [여기](https://github.com/heejinna/TIL/blob/main/JavaScript/variables.md#var-%ED%82%A4%EC%9B%8C%EB%93%9C%EB%A1%9C-%EC%84%A0%EC%96%B8%ED%95%9C-%EB%B3%80%EC%88%98%EC%9D%98-%EB%AC%B8%EC%A0%9C%EC%A0%90)를 참조

## let
### 1. 중복 선언 불가
var와 달리 let으로 변수 값을 재할당할 경우 `SyntaxError`가 발생한다.

```js
var foo = 123;
var foo = 456;
console.log(foo); // 456

let bar = 123;
let bar = 456;
console.log(bar); // SyntaxError: Identifier 'bar' has already been declared
```

### 2. 블록 레벨 스코프
함수의 코드블록만을 지역 스코프로 인정하는 var와 달리 let은 모든 코드블록을 지역스코프로 인정한다.


### 3. 호이스팅
let 키워드는 호이스팅이 실제로는 일어나지만 일어나지 않는 것처럼 보이도록 동작한다. 런타임 실행 전에 선언 단계가 호이스팅되어 실행되는 것은 var와 같지만, 초기화는 변수 선언문이 실제 위치한 지점에서 이루어진다. 때문에 변수 선언문 이전에 변수를 참조하면 `ReferenceError`가 발생한다.

이렇게 스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간을 **일시적 사각지대(Temporal Dead Zone; TDZ)**라 부른다.

```js
let foo = 1; // 전역 변수

{
  console.log(foo); // ReferenceError
  let foo = 2; // 지역 변수
}
```

맨 위에 let으로 선언된 foo 변수는 전역 변수이기 때문에 `console.log(foo);`를 실행했을 때 값이 출력이 되야 하지만, let 으로 선언된 지역 변수 foo 가 호이스팅되기 때문에 참조 에러가 발생한다.

<br>

## const
const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다. 만약 이를 지키지 않을 경우 `SyntaxError`가 발생한다. 또한 const 키워드로 선언한 변수는 **재할당이 금지**된다. 이 때문에 상수를 할당하는 데 많이 사용되지만, 상수를 할당하는 데만 쓰이는 것은 아니다.

상수는 다른 변수들과 구분하기 위해 **대문자**와 **스네이크 케이스**를 사용해 식별자를 지정하는 것을 권장한다.

```js
const TAX_RATE = 0.1;
```

<br>

> **var vs let vs const**
> 
> - ES6를 사용한다면 var 키워드는 사용하지 않아야 한다.
> - 변수를 선언할 때는 일단 const 키워드를 사용한다.
> - 재할당이 필요하다고 판단될 때에 한해 let으로 변경한다.



