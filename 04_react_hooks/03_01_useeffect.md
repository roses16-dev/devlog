# 03 - useEffect

클래스 컴포넌트 시절 라이프 사이클과 연계하여 설명하는 방식이 많았으나.
관계없이 학습하는 것이 보다 정확하다.

[Synchronizing with Effects](https://beta.reactjs.org/learn/synchronizing-with-effects)
React가 아닌 외부와 싱크를 맞추기 위해 사용하며 그렇지 않다면 사용하지 말아라

[You Might Not Need an Effect](https://beta.reactjs.org/learn/you-might-not-need-an-effect)
[Using the Effect Hook](https://ko.reactjs.org/docs/hooks-effect.html)
[useEffect](https://beta.reactjs.org/reference/react/useEffect)
[useEffect 완벽 가이드](https://overreacted.io/ko/a-complete-guide-to-useeffect/)

렌더링 이후 해야 할 일, 즉 React의 외부와 관련된 일을 정해줄 수 있다.
V-DOM 구성 이후 인지 실제 렌더링 이후 인지는 명확하지 않다. 그 즈음 어딘가

기본적으로 렌더링 때마다 실행되므로, 의존성 배열을 통해 언제 이펙트를 실행할지 지정할 수 있다(= 불필요한 경우에 건너뛸 수 있다).

함수를 리턴함으로써 종료 처리를 할 수 있다. (clean up)

## 타이머 예제

React의 외부에 우아하게 접근. 이 정도는 useEffect를 안 쓴다고 크게 문제가 되지 않지만, 이렇게 쓰는 습관을 들이자.

🚩 예제코드 차후 간단하게 정리해서 기재하기

## Fetch 함수의 위치가 고민된다면, Dan Abramov의 글을 다시 보자.

- [useEffect 완벽가이드 - 함수를 이펙트 안으로 옮기기](https://overreacted.io/ko/a-complete-guide-to-useeffect/#%ED%95%A8%EC%88%98%EB%A5%BC-%EC%9D%B4%ED%8E%99%ED%8A%B8-%EC%95%88%EC%9C%BC%EB%A1%9C-%EC%98%AE%EA%B8%B0%EA%B8%B0)

## Effect가 두 번 실행되는 문제

<React.StrictMode>로 컴포넌트 전체를 감쌀 경우, 예상치 못한 Side Effect를 찾으려고 Effect 등을 두 번씩 실행한다. (개발할때만!)
평소에는 큰 문제가 없지만, API 등을 사용하면 이상하다고 느낄 수 있으니 참고할 것.
번거로울 경우 Strict mode를 사용하지 않아도 되나, 사용하는 것을 추천(🚩왜! 타입스크립트도 쓰는데!)

- [예상치 못한 부작용 검사](https://ko.reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects)

## 의존성 배열을 이용해 Fetch할 때 주의사항 🚩

- [Fetching data](https://beta.reactjs.org/learn/synchronizing-with-effects#fetching-data)
