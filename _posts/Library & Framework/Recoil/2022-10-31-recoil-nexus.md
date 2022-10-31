---
title: "[Recoil] recoil-nexus"
categories:
  - Recoil
tags:
  - Web
  - Recoil
date: 2022-10-31
last_modified_at: 2022-10-31
author_profile: true
---

### React 컴포넌트 외부에서 atom 값 접근 및 수정하기

기본 recoil을 사용하는 경우, React 컴포넌트 외부에서 atom 값을 가져오거나 업데이트할 수 없다. recoil-nexus를 사용하면 외부에서도 간단하게 사용이 가능하다.

#### 설치

```
$ npm i recoil-nexus
$ yarn add recoil-nexus
```

#### method

- `getRecoil(state)`: atom 값 가져오는 함수
- `getRecoilPromise(state)`: atom 값 가져온 뒤 Promise를 반환하는 함수, 비동기 selector와 함께 사용
- `setRecoil(state, value)`: atom 값 업데이트하는 함수
- `resetRecoil(state)`: atom 값을 default value로 리셋하는 함수

#### 사용법

- App.js

```jsx
import { RecoilRoot } from "recoil";
import RecoilNexus from "recoil-nexus";

export default function App() {
  return (
    <RecoilRoot>
      <RecoilNexus />
      {/* ... */}
    </RecoilRoot>
  );
}

export default App;
```

<br/>

#### Reference

- [npm) recoil-nexus](https://www.npmjs.com/package/recoil-nexus)
