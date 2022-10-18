---
title: "[Recoil] Recoil 사용법 2 - Selector"
categories:
  - Recoil
tags:
  - Web
  - Recoil
date: 2022-10-11
last_modified_at: 2022-10-11
author_profile: true
---

### Recoil의 Selector와 비동기 처리

## Selector

```js
import { DefaultValue, selector } from "recoil";
import countState from "../atom/countState";

export default selector({
  key: "countSelector",
  get: ({ get }): number => {
    const count = get(countState);
    return count + 1;
  },
  set: ({ set, get }, newCount) => {
    return set(countState, newCount + 10);
  },
});
```

atom에서는 불가능한 비동기 처리와 복잡한 로직을 구현할 수 있다.

### key

- selector을 식별하는 데 필요한 고유 문자열
- 프로젝트 전체에서 다른 atom, selector에 대해 고유해야 함.

### get

```js
get: ({ get }): number => {
  const count = get(countState);
  return count + 1;
},
```

- 파생된 상태를 반환 (read-only)
- `countState`가 바뀔 때마다 새로운 값 리턴
- `get()`은 여러번 사용 가능, 그 중 하나라도 변하면 리렌더링

### set

```js
set: ({ set, get }, newCount) => {
  const count = get(countState);
  return set(countState, newCount + 10);
},
```

- `set()`은 쓰기 가능한 상태 반환
- `set()`의 첫 번째 매개변수는 RecoilState, 두 번째는 새로운 값
- set 안에서의 `get()`은 구독하지 않고, 단순히 atom이나 selector의 값을 찾는 데 사용

### 비동기 Selector

```js
export const customState = selector({
  key: "customState",
  get: async ({ get }) => {
    const res = await MyAPI.getAPI(get(myState));
    return res.data;
  },
});
```

위 코드처럼 selector 안에서 비동기 통신을 마친 후 값을 사용할 수 있다.

<br/>

#### Reference

- [Recoil 공식 문서](https://recoiljs.org/ko/docs/introduction/getting-started)
- [Recoil 정리 1편 - Recoil시작하기 (atom, selector)](https://talkwithcode.tistory.com/75)
