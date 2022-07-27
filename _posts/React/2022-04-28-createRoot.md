---
title: "[React] React v18 - createRoot"
categories:
  - React
tags:
  - Web
  - React
date: 2022-04-28
last_modified_at: 2022-04-28
author_profile: true
---

### createRoot?

평소처럼 React 프로젝트를 clone을 하고 실행하는데 아래와 같은 에러가 출력됐다.


![React18 error](https://user-images.githubusercontent.com/62230430/165764218-cc59e9b8-a3b1-427b-8003-ef5afd08a809.png)


처음 보는 오류라 [공식 문서](https://ko.reactjs.org/docs/concurrent-mode-reference.html#createroot)를 찾아보니, React v18에서는 `ReactDOM.render`이 아닌 `createRoot`를 사용해야 한다고 한다.  
공식 문서를 참고하여 코드를 수정하였다.

- index.js

```java
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

이렇게 수정하면 오류 없이 잘 동작한다!