---
title: "[Recoil] Recoil 사용법 1 - Atom"
categories:
  - Recoil
tags:
  - Web
  - Recoil
date: 2022-10-06
last_modified_at: 2022-10-06
author_profile: true
---

### React를 위한 상태 관리 라이브러리, Recoil

지금까지 React 상태 관리 라이브러리로 Redux를 주로 사용해왔다. 하지만 Redux 사용을 위해 필요한 action, reducer, selector, store의 초기 세팅에는 보일러플레이트 코드가 너무 많고 사용하기 불편하다는 생각이 들었다.

그러던 중, 인턴으로 들어오게 된 회사의 프론트엔드 레거시 코드에서 상태 관리 라이브러리로 Recoil을 채택하여 사용하고 있었다. 이 때 Recoil을 처음 접하게 되었고, 현재까지도 유용하게 잘 사용하고 있어 오늘은 Recoil의 사용법에 대해서 정리해보려 한다.

## Atom

- atom은 **상태의 단위**이다.
- atom이 업데이트 되면, 해당 atom을 구독하고 있던 모든 컴포넌트들의 state가 새롭게 리렌더 된다.

### key

- atom을 식별하는 데 필요한 고유 문자열
- 프로젝트 전체에서 다른 atom, selector에 대해 고유해야 함.

### default

- state의 초기값 지정

<br/>

### 설치

```
$ npm i recoil
$ yarn add recoil
```

### 적용

- index.js

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { RecoilRoot } from "recoil";
import App from "./App";

ReactDOM.render(
  <React.StrictMode>
    <RecoilRoot>
      <App />
    </RecoilRoot>
  </React.StrictMode>,
  document.getElementById("root")
);
```

<br/>

- state.js

```js
import { atom } from "recoil";

export const countState = atom({
  key: "countState",
  default: "",
});
```

<br/>

- Menu.jsx

```jsx
import { useRecoilState } from "recoil";
import { countState } from "../../state";

const Menu = () => {
  const [count, setCount] = useRecoilState(countState);

  return <div>{count}</div>;
};
```

<br/>

#### Reference

- [Recoil 공식 문서](https://recoiljs.org/ko/docs/introduction/getting-started)
- [[Recoil] Recoil 200% 활용하기](https://velog.io/@juno7803/Recoil-Recoil-200-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0)
- [Recoil 정리 1편 - Recoil시작하기 (atom, selector)](https://talkwithcode.tistory.com/75)
