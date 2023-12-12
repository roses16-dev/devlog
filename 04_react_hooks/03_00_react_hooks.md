# 03 - React Hooks

React 16.8에서 Hooks가 도입됨. 기존 방식에 있던 몇 가지 문제를 해결.

[React Conf 2018 Hooks 소개 영상](https://youtu.be/dpw9EHDh2bM)

기존 방식의 문제점:

- Wrapper Hell (HoC)
- Huge Components
- Confusing Classes

기존:

- 상태를 가진 컴포넌트는 Class Component로 만들고, props만 사용하는 재사용이 용이한 작은 컴포넌트는 Function Component로 작성.
- Redux에서도 비슷한 구분이 존재했다.
    - [Presentational and Container Components - Dan Abramov](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

현재:

- Function Component만 사용한다.
- 상태 관리 유무를 바로 알기 어려움 = 신경쓰지 않아도 됨.
- 복잡한 요소는 전부 Hook으로 격리 및 재사용 가능.

## 대표적인 Hooks

- useState → State Hook ⇒ React의 State
- useEffect ⇒ Side-effect
- useContext
- useRef
- useLayoutEffect → useEffect와 조금 다르다.
