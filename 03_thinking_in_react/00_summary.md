# 03 - React로 사고하기

## [React로 사고하기](https://react.dev/learn/thinking-in-react)

React로 사고하기는 공식문서에서 제공하는 자료이며 아래 5개의 단계로 나누어진다.

Step 1. UI를 컴포넌트 계층 구조로 나눈다.
Step 2. 리액트로 정적인 버전을 만든다.
Step 3. Find the minimal but complete representation of UI state
Step 4. Identify where your state should live
Step 5. Add inverse data flow

본 강의에서는 그 중 Step 1, 2를 다룬다.

강의에서 HTML코드부터 컴포넌트를 함수로 추출하고, 나아가 파일로 분리하는 과정을 보여준다.
이를 통해 어떤 기준으로 컴포넌트를 분리하는지에 대한 학습을 해야한다.

본 강의는 반복이 필요하며 강의 내용에 대해 스스로 질문하며 답을 찾아야한다.

## Data

학습을 위한 준비물

B/E에서 JSON 형태의 데이터를 돌려주는 API를 제공한다고 가정(대부분은 REST API 또는 GraphQL).

> 💡 [JSON(JavaScript Object Notation)](https://www.json.org)

### REST API

- GET, POST, PUT/PATCH, DELETE (CRUD)
- Resource 중심

### GraphQL 

- Graph 자료 구조
- Query에서 얻고자 하는 걸 지정
- Query(Read), Mutation(Command: Create, Update, Delete), Subscription(구독:Event를 인지하는 용도)

DSL?

[명령형?](https://ko.wikipedia.org/wiki/명령형_프로그래밍)

선언형으로 UI를 선언해두면 내용이 바뀌었을때 자동으로 업데이트된다.

## 목차

1. React Component
2. React State

💡 mockup

