---
title: "[React] forwardRef"
categories:
  - React
date: 2022-05-24
last_modified_at: 2022-05-24
author_profile: true
---

### React 컴포넌트를 ref로 제어하기

React의 `ref` props는 **HTML element에 직접 접근하기 위해**서 사용된다.  
<br />
아래는  input에 focus를 주는 예시이다.

```jsx
import { forwardRef, useRef } from "react";

const Input = ({ ref }) => {
  return <input type="text" ref={ref} />;
};

const Field = () => {
  const inputRef = useRef(null);

  const handleFocus = () => {
    inputRef.current.focus();
  }

  return (
    <>
      <Input ref={inputRef} />
      <button onClick={handleFocus}>input focus</button>
    </>
  );
}
```
위 코드를 동작시키면 console에서 다음과 같은 경고 메시지를 출력한다.

> Warning: Input: `ref` is not a prop. Trying to access it will result in `undefined` being returned. If you need to access the same value within the child component, you should pass it as a different prop. (https://reactjs.org/link/special-props)
    at Input (https://nqxh4.csb.app/src/Field.jsx:18:18)
    at Field (https://nqxh4.csb.app/src/Field.jsx:30:36)
    at div
    at App

경고 메시지에 따르면 `ref`가 props가 아니기 때문에 `undefined` 설정이 되어 오류 메시지를 출력한 것이다.  
위 예시의 `<Input />` component와 같이 HTML element가 아닌 **React 컴포넌트에서 `ref` props를 사용하기 위해서 `forwardRef()` 함수를 사용**해야 한다. React 컴포넌트를 `forwardRef()` 함수로 감싸주면 외부에서 `ref` props를 넘길 수 있다.
<br/>

이제 `forwardRef`를 사용하여 위의 input focus 예시를 완성해보자.

```jsx
import { forwardRef, useRef } from "react";

const Input = forwardRef((props, ref) => {
  return <input type="text" ref={ref} />;
});

const Field = () => {
  const inputRef = useRef(null);

  const handleFocus = () => {
    inputRef.current.focus();
  }

  return (
    <>
      <Input ref={inputRef} />
      <button onClick={handleFocus}>input focus</button>
    </>
  );
}
```

위와 같이 `forwardRef`를 사용하면 오류 없이 잘 동작하는 것을 확인할 수 있다!