---
title: "[TypeScript] 파일 데이터 가져오기"
categories:
  - TypeScript
tags:
  - Web
  - TypeScript
date: 2022-10-08
last_modified_at: 2022-10-08
author_profile: true
---

### 파일 데이터를 가져오기 위한 type 처리 (for 파일 업로드)

TypeScript로 파일 업로드를 하기 위해, 선택한 파일의 정보를 가져오기 위한 type을 처리하는 코드는 아래와 같다.

```tsx
const handleUploadImg = (e: React.ChangeEvent<HTMLInputElement>) => {
  e.preventDefault();
  const target = e.target as HTMLInputElement;

  const formData = new FormData();
  formData.append("file", (target.files as FileList)[0]);

  // API 요청 코드 작성
};
```
