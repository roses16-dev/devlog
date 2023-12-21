# usehooks-ts

[usehooks-ts](https://usehooks-ts.com/)

모든 Hook에 대한 코드가 웹 사이트에 직접 노출되어있어 위 사이트를 참조하는 것이 좋다.
toggle, increase 등 자주 사용하는 기능을 구현한 hook을 모아두었다.
custom hook을 만들 때 영감을 얻을 수 있다.

## 설치

```bash
npm i usehooks-ts
```

ts로 만들어졌으나 js에서도 사용할 수 있다.

### [useBoolean](https://usehooks-ts.com/react-hook/use-boolean)

참/거짓을 다룰 땐 toggle 같이 의도가 명확한 함수를 쓰는 게 좋다.

### [useEffectOnce](https://usehooks-ts.com/react-hook/use-effect-once)

의존성 배열을 빈 배열로 넣어서 한 번만 실행하는 Effect를 잡아줄 때가 많은데, 이걸 쓰면 더 명확히 드러난다.

→ 위에서 만든 useFetchProducts에 써보자.

### [useFetch](https://usehooks-ts.com/react-hook/use-fetch)

정말 간단히 쓸 때 좋음.

몇 가지 기능이 살짝 더 있는 useFetch 라이브러리가 따로 있다.

- [use-http](https://use-http.com/)

조금 더 복잡해도 괜찮다면, 캐시 이슈를 고려한 좋은 대안이 있다.

- [SWR](https://swr.vercel.app/ko)
  주기적으로 데이터가 바뀌었는지 확인하는 등 추가 기능 및 캐시 이점 제공

- [TanStack Query](https://tanstack.com/query)
  React-query라고 불리던 것.

### [useInterval](https://usehooks-ts.com/react-hook/use-interval)

React에서 setInterval 등을 쓸 때는 주의해야 할 부분이 있어서 Custom Hook을 만들어서 해결해야 함. 
setInterval써야하면 이거 무조건 쓰는게 좋다. 🚩 알아보자.

- [useEffect 관점](https://overreacted.io/ko/a-complete-guide-to-useeffect/)
    - [React에서의 타이머 part 1 : setInterval 말고 이것! - 코드종님 영상](https://youtu.be/2tUdyY5uBSw)
- [Ref 활용](https://overreacted.io/making-setinterval-declarative-with-react-hooks/)

### [useEventListener](https://usehooks-ts.com/react-hook/use-event-listener)

모든 종류의 이벤트를 확인할 수 있음. 특히 dispatchEvent로 전달되는 커스텀 이벤트에 반응하기 좋다. (강력 추천!)

### [useLocalStorage](https://usehooks-ts.com/react-hook/use-local-storage)

localStorage와 JSON으로 객체 영속화.

이벤트를 통해(dispatchEvent + useEventListener) 다른 컴포넌트와 동기화하는 게 매우 중요한 특징.
→ local storage의 값이 바뀌었을 때 Event를 일으켜 local storage값을 참조하는 컴포넌트들이 이를 알게 한다.

### [useDarkMode](https://usehooks-ts.com/react-hook/use-dark-mode)

그 외에도 쓸만한 hook이 많다.
여기있는걸 그대로 써도 좋고, 스스로 만들 때 참조해도 좋다.
