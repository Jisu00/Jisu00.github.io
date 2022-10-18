---
title: "[Recoil] Recoil 사용법 3 - Hooks"
categories:
  - Recoil
tags:
  - Web
  - Recoil
date: 2022-10-18
last_modified_at: 2022-10-18
author_profile: true
---

### Recoil가 제공하는 Hooks

- `useRecoilState()` : atom 혹은 selector의 값을 읽거나 쓸 때 사용
- `useRecoilValue()` : recoil 상태 값 반환
- `useSetRecoilValue()` : recoil 상태의 값 업데이트를 위한 setter 함수 반환
- `useResetRecoilState()` : atom이나 selector 값 default 값으로 초기화할 때 사용

### 적용

```jsx
import {
  useRecoilState,
  useRecoilValue,
  useSetRecoilValue,
  useResetRecoilState,
} from "recoil";

const [count, setCount] = useRecoilState(countState);
const count = useRecoilValue(countState);
const setCount = useSetRecoilValue(countState);
const resetCount = useResetRecoilState(countState);
```

<br/>

#### Reference

- [Recoil 공식 문서](https://recoiljs.org/ko/docs/introduction/getting-started)
