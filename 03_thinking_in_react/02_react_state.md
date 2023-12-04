# React State

Thinking in react 3~5 스텝을 다룬다.

- “Step 3: Find the minimal but complete representation of UI state”
- “Step 4: Identify where your state should live”
- “Step 5: Add inverse data flow”

일관성과 효율을 위해 DRY 원칙을 따르는 SSOT
- [DRY (Don’t Repeat Yourself)](https://ko.wikipedia.org/wiki/중복배제)
- [SSOT (Single Source of Truth)](https://ko.wikipedia.org/wiki/단일_진실_공급원)

React State의 조건:

1. 변경되어야한다. 변경되지 않는 건 state로 다룰 가치가 없다.
2. 부모 컴포넌트가 props를 통해 전달한다면 state가 아니다.
3. 다른 state나 props를 이용해 계산 가능하다면 state가 아니다.
🚩 이해못했다...! 다시 보기 !

TypeScript를 잘 쓰면 직접 관리하는 상태의 수를 줄일 수 있다.
△ 잘 정의된 interface/type은 props의 갯수를 줄여주고 안정성을 보장하므로...

상태의 소유자를 결정하는게 중요하다.
(React만 쓴다면) 해당 상태에 의존적인 컴포넌트를 모두 포함하는 컴포넌트가 상태를 소유해야 한다. 🚩

- [“Lifting State Up”](https://ko.reactjs.org/docs/lifting-state-up.html)
상태를 위로 끌어올린다.
같은 State를 공유해야하는 컴포넌트가 다수일 경우 부모 노드를 타고 올라가 하나로 만나는 노드에서 State를 갖는다.
하위 컴포넌트에서 State를 변경해야할 경우, Props로 Setter 함수를 넘겨 사용한다.

- [Sharing State Between Components](https://beta.reactjs.org/learn/sharing-state-between-components)
