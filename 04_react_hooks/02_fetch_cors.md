# 02 - Fetch API & CORS

## [Fetch API](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API)

[Fetch 사용하기](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch)

[ReadableStream](https://developer.mozilla.org/ko/docs/Web/API/ReadableStream)

[텍스트 디코더와 텍스트 인코더](https://ko.javascript.info/text-decoder)

`json()` 함수를 기본적으로 지원한다.

### 다른 HTTP method 사용하기

```javascript
const response = fetch(url, 
  {
    method: 'POST', 
    headers: {
      "Content-Type": "application/json",
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    body: JSON.stringify(data),
  });
```

더 다양한 옵션은 위 Fetch 사용하기 링크 참조, 위 예시는 자주 사용되는 옵션

## [CORS 교차 출처 리소스 공유](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)

[동일 출처 정책](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy)

웹 브라우저는 동일 출처 정책에 따라 웹 페이지와 리소스를 요청한 곳(일반적으로 REST API 서버)이 서로 다른 출처(포트포함)일 때 서버에서 얻은 결과를 사용할 수 없게 막는다.
(일단, 받아올거 받아오고 나서 막는다! 주의!)

해결방법
REST API 서버에서 교차출처 접근을 허용할 경로를 한다.
어떻게? 헤더 내 `Access-Control-Allow-Origin` 추가하기
자세한 설정 방법이 있지만 BE 전문 분야이므로 생략.

Express에서는 CORS 미들웨어를 설치해서 사용하면 된다.

설치

```bash
npm i cors
npm i -D @types/cors
```

사용

```ts
import express from 'express';
import cors from 'cors';

const app = express();

app.use(cors());
```
