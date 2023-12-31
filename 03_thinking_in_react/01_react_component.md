# React Component

## 컴포넌트 계층구조?

React의 강력한 특징

- 기반이 되는 간단한 컴포넌트를 만든다.
- 간단한 컴포넌트를 조합해 복잡한 기능을 만든다.
 ex) 자동차 조립

하나의 컴포넌트를 구분짓는 몇가지 기준 : 컴포넌트를 쪼개는 기준

- [SRP (Single Responsibility Principle)](https://ko.wikipedia.org/wiki/단일_책임_원칙)
단일 책임 원칙 : 모든 클래스(컴포넌트의 기초가 되는 개념)는 하나의 책임만을 가지며, 그 책임을 완전히 캡슐화 해야한다 = 단일 클래스는 1개의 일만하고, 사소한 변경은 간단하게 고치게 한다.

로버트 마틴이 애자일과 패턴에 관한 책을 냈고 거기에서 나온 SOLID 원칙 중 하나
(🚩해당 원칙은 총 5가지라고한다. 읽어보자.😍)

마이클 패더스, 레거시 코드를 효율적으로 사용하는 리팩토링, 테스트코드 등에 대한 이야기 하신 분이 위 원칙에 대해 무언가를 했다. (중요한가? 이름만 기억해두자.)

- CSS
HTML이 너무 커질때는 CSS에서 쓰는 셀렉터(주로 class)를 기준으로 쪼갠다.

- Design's Layer
디자인이 대체로 트리형태로 나온다. 그 형태를 따라 쪼갠다. (CSS랑 무슨 차이지?)

- Information Architecture (JSON Schema의 영향) → 실제로 엄청 많이 쓰게 됨. 자연스러운 SRP를 위해서 사실상 강제됨
(🚩이해 못함)

> 💡 [아토믹 디자인](https://bradfrost.com/blog/post/atomic-web-design/)
>
> : 계층형 구조를 카테고리로 묶은 방법? 방법보다 개념에 가깝다

리팩토링 팁
주석으로 설명해야하는 부분은 이름지어서 함수로 빼자.

1. 디자인을 보고 HTML부터 만든다.
2. 위 기준에 따라 분리될 부분을 일단 해당 내부 컴포넌트로 분리한다.
짜다가 괴로운 부분을 느끼면 뺄 생각을 하라는 것 같음.
3. 내부 컴포넌트로 잘 분리 되었으면 외부 컴포넌트로 분리한다.
4. 2~3 과정을 촘촘하게 반복한다.

💡 서버에서 주어진 데이터에 맞추어 컴포넌트를 작성할 수도 있지만, 데이터를 컴포넌트 구조화에 용이하게 가공해서 작성할 수도 있다.
(이 방법이 더 좋아 보인다.)
ex) [{과일, 사과}, {과일, 딸기}, {야채, 오이}, {야채, 당근}] → [{과일, [사과, 딸기]}, {야채, [오이, 당근]}]

컴포넌트 뿐 아니라 함수와 타입도 외부 파일로 빼내어 쪼갤 수 있다.
함수 : `src/utils/함수명.ts`
타입 : `src/types.ts` 한가지 파일에 간단하게 모아두기 또는 `src/types/타입이름.ts` 폴더에 여러 타입이름 파일을 모아두기

```ts
// src/types/Product.ts
interface Product {
	category: string;
	price: string;
	stocked: boolean;
	name: string;
}

export default Product
```

Props
나눠진 컴포넌트를 연결하는 방법
ts에서는 컴포넌트별 Props type을 따로 만드는게 편한것같다.
Props로 name, price 등등 한땀한땀 넘겨주고받는 것에도 장점은 있지만 이미 만들어진 interface 또는 type 통째로 주고 받는게 편하다.
type이나 interface 내 요소를 따로따로 쓰는 경우보다 한꺼번에 사용하는 경우가 더 많고, 나중에 갑자기 다른 요소를 추가하게되는 경우도 많기때문에 (이건 좀 더 겪어봐야 맞는 말이구나, 하겠다.)

interface와 type 내 확장 기능들을 이용하여 다양한 방식으로 Props를 사용할 수 있다.


🚩 Reflect.get() 알아보자

💬 그동안 여러 페이지에서 반복되는 컴포넌트만 분리했었는데 극한의 컴포넌트 쪼개기를 만나고 나니 가독성이 좋아진다는게 이런거구나. 깨달았다.
다만 이런 방식으로 큰 페이지를 제작하면 components폴더가 터져나가지 않을까?
