# 클로저

> *"A closure is the combination of a function and the lexical environment within that function was declared."*

## 렉시컬 스코프
렉시컬 환경의 outer lexical environment reference에 저장할 참조값, 즉 상위 스코프에 대한 참조는 함수 정의가 평가되는 시점에 함수가 정의된 환경(위치)에 의해 결정된다.

## 함수 객체의 내부 슬롯 [[Environment]]
함수는 자신의 내부 슬롯 [[Environment]]에 자신이 정의된 환경, 즉 상위 스코프의 참조를 저장한다.