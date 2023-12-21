# 01 - TDD(Test Driven Development)

## TDD (Test Driven Development)

[테스트 주도 개발](https://github.com/ahastudio/til/blob/main/agile/test-driven-development.md)

[TDD FAQ](https://github.com/ahastudio/til/blob/main/blog/2016/12-03-tdd-faq.md)

[Jest를 이용한 간단한 TDD 예제](https://github.com/ahastudio/til/blob/main/jest/20201204-simple-tdd-example.md)

TDD(Test Driven Development) : 테스트주도개발
테스트 코드를 먼저 작성하는, 즉 구현보다 인터페이스와 스펙을 먼저 정의함으로써 개발을 진행하는 방식

🚩시그니처와 인터페이스

### TDD Cycle

1. Red → 실패하는 테스트 코드를 작성. 인터페이스와 스펙에 집중한다.
2. Green → 재빨리 테스트를 통과시킨다. 올바른 방법이 아니어도 괜찮다.
3. Refactor → 리팩터링을 통해 코드를 올바르게 만든다. TDD에서 가장 중요한 부분이지만, 간과될 때가 많다.

제대로 작성하는 클린코드를 만드는 것이 목적

#### TDD Cycle 연습 방법

작은 단계를 찾고, 코드에서 피드백을 얻는 게 (어렵고) 중요하다. 2번이 어렵다면 1번으로 돌아가서 더 작고 쉬운 문제를 정의하고, 3번을 위해 의도를 드러내고 중복을 찾아 제거하는 연습을 해야 한다. 이 둘이 익숙하지 않으면 TDD를 하는 게 거의 불가능하고, 사실 이 둘이 어려우면 일반적인 개발 또는 클린 코드를 작성하는 것 또한 매우 힘들다.

10분 안에 한 사이클을 돌릴 수 있어야한다.

## Jest

[Jest](https://jestjs.io/)
[Given-When-Then](https://github.com/ahastudio/til/blob/main/blog/2018/12-08-given-when-then.md)

테스트 케이스를 정의하는 두 가지 방법
1. test 함수 사용.

```js
test('add', () => {
  // 인자가 없을 때
  expect(add()).toBe(0);
  // 인자가 하나일 때
  expect(add(1)).toBe(1);
  // 일자가 2개일 때
	expect(add(1, 2)).toBe(3);
  // 인자가 3개일 때
  expect(add(1, 2, 3)).toBe(6);

});
```

2. BDD 스타일로 테스트의 대상과 행위를 드러내는 방법.

```js
describe('add', () => {
  context('with no argument', () => {
    it('returns zero', () => {
      expect(add()).toBe(0);
    });
  });

  context('with only one argument', () => {
    it('returns the same number', () => {
      expect(add(2)).toBe(2);
    });
  });

  context('with two arguments', () => {
    it('returns sum of two numbers', () => {
      expect(add(1, 2)).toBe(3);
    });
  });

  context('with three arguments', () => {
    it('returns sum of three numbers', () => {
      expect(add(1, 2, 3)).toBe(6);
    });
  });
});
```

🚩 알고리즘 풀 때도 테스트코드 응용할 수 있다.
