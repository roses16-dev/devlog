# 01 - Express

## [Express](https://expressjs.com/)

역사가 오래된 Node.js web framework.

## 환경설정

Express 설치 및 환경 설정
※ node.js 설치되어있다는 가정 하에 진행

패키지 초기화

```bash
.npm init -y
```

.gitignore 파일

```bash
touch .gitignore
echo "/node_modules/" > .gitignore
```

echo로 입력하면 vscode에서 바로 안보일 수 있다!

typescript 설치 및 초기화

```bash
npm i -D typescript
npx tsc --init
```

ts-node 설치

```bash
npm i -D ts-node
```

.ts파일은 JavaScript로 컴파일한 후 실행되는데, ts-node는 TypeScript로 작성된 코드를 바로 실행할 수 있게 해준다.

ESLint 설치 및 초기화

```bash
npm i -D eslint
npx eslint --init
```

Express 설치

```bash
npm i express
npm i -D @types/express
```

## 기본 코드

```typescript
import express from 'express';
// express 패키지 내 express 함수 import

const port = 3000;

const app = express();
// express 함수는 인스턴스를 반환한다.

app.get('/', (req, res) => {
  res.send('Hello, world!');
});
// app.get('경로', (Request, Response) => {
//  인스턴스에 원하는 작업을 추가한다.
// })

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
// listen 함수는 서버를 시작하게한다.
```

작성한 코드를 반영시키려면 서버를 재시작해야한다.
아무래도 브라우저에서 동작하는 코드가 아니라서 그런것같다.

코드를 세이브할 때 마다 서버를 재시작하는 nodemon 패키지가 있다.(당연한 이야기지만 개발할때만 사용해야한다.)
https://github.com/remy/nodemon

- ts-node가 설치되어있어야 실행이 가능하다.
- .ts 파일뿐 아니라 전혀 관계없는 파일을 세이브해도 서버가 재시작된다.

설치

```bash
npm i -D nodemon
```

실행 : `npx ts-node app.ts` 대신 아래 명령어로 실행한다.

```bash
npx nodemon app.ts
```

## REST API

Roy Fielding : HTML 표준 만드는데 참여하신 분
 “[Architectural Styles and the Design of Network-based Software Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)” (2000)
[Richardson Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html)

대개는 🚩 “필딩 제약 조건” 4가지를 모두 만족하지 않고, Resource와 HTTP Verb만 도입하는 수준으로 사용.

### Resource

URL 명명 시 리소스의 이름을 따르게 작성한다.

`/write-post` 와 같이 특정한 행동을 포함하지 않고 `/posts`와 같이 리소스를 표시하게 작성한다.

### HTTP Verb

CRUD에 대해 HTTP Method를 한다.

Read는 Collection(복수)과 Item(Element)(단수)로 나누어 작업하게 한다.

### 예시

기본 리소스 URL: /products

1. Read (Collection) → GET /products ⇒ 상품 목록 확인
2. Read (Item) → GET /products/{id} ⇒ 특정 상품 정보 확인
3. Create (Collection Pattern 활용) → POST /products ⇒ 상품 추가 (JSON 정보 함께 전달)
4. Update (Item) → PUT(덮어쓰기) 또는 PATCH(일부만업데이트/최근새로생김) /products/{id} ⇒ 특정 상품 정보 변경 (JSON 정보 함께 전달)
5. Delete (Item) → DELETE /products/{id} ⇒ 특정 상품 삭제
