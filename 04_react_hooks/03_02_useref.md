# useRef

[beta 문서의 useRef](https://beta.reactjs.org/reference/react/useRef)
위 문서는 꼭 보는 걸 추천. 

[공식 문서의 useRef](https://ko.reactjs.org/docs/hooks-reference.html#useref)

컴포넌트의 생애주기 전체에 걸쳐서 유지되는 객체. 즉, 컴포넌트가 없어질 때까지 동일한 객체가 유지된다.

```js

// 모든 Home 컴포넌트가 하나의 ref 변수를 공유한다.
const ref = { val:0 };


function Home () {
  // Home 컴포넌트마다 ref 변수를 사용할 수 있으나 update, rendering 등 컴포넌트 생애주기에 따라 값이 초기화될 수 있다. (는 것 같다.)🚩
  const ref = { val:0 };

  // Home 컴포넌트마다 ref 변수를 사용할 수 있으며 컴포넌트가 unmount될때까지 하나의 값을 유지한다.
  const ref = useRef({ val:0 });
  ref.current // ref의 현재 값에 접근
}

```

객체 자체가 값은 아니고, 값을 참조하기 위한 객체. 즉, 언제든지 값을 변경할 수 있다.

상태(state)와 같은 기능이라 예상될 수 있으나,
State는 변경되면 해당 컴포넌트와 하위 컴포넌트를 다시 렌더링하지만, 레퍼런스는 객체의 현재 값(current)이 바뀌더라도 렌더링에 영향을 주지 않는다.

주요 용도:

1. 컴포넌트가 사라질 때까지 동일한 값을 써야 하는 경우. ⇒ input 등의 ID 관리.
2. (특히 useEffect 등과 함께 쓰면서 만나게 되는) 비동기 상황에서 현재 값을 제대로 쓰고 싶은 경우. (실무에서 쓸 일은 많지 않다.)
  Closure → 변수를 capture, bind를 깜빡하는 문제가 종종 일어남.
  