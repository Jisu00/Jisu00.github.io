---
title: "[Styled-Components] Cannot create 에러"
categories:
  - Styled-Components
tags:
  - Web
  - Styled-Components
  - Error
date: 2022-10-04
last_modified_at: 2022-10-04
author_profile: true
---

### React 컴포넌트를 스타일링 할 때 발생하는 에러

평소처럼 React 컴포넌트를 스타일링 하기 위해 아래처럼 코드를 작성하였다.

```jsx
const StyledBtn = styled(Btn)``;
```

하지만 다음과 같은 에러가 발생하였다.

> Error: Cannot create styled-component for component: undefined.

### 에러 발생 이유

`StyledBtn`이 `Btn`보다 먼저 생성되기 때문이다.
<br/>

### 해결

```jsx
const StyledBtn = styled((props) => <Btn {...props} />)``;
```

<br/>

#### Reference

- [[Styled Component] 적용안되는경우2](https://lily-im.tistory.com/101)
