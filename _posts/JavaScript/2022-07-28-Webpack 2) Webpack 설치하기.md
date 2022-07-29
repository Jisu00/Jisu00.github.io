---
title: "[JS] Webpack) 2: Webpack 및 Babel 설치하기"
categories:
  - JavaScript
tags: 
  - Web
  - JavaScript
  - Webpack
  - Babel
date: 2022-07-28
last_modified_at: 2022-07-28
author_profile: true
---

### npm 설정

(node.js 설치 필요)  
웹팩을 이용할 폴더에 아래 명령어로 package.json을 생성한다.

```
$ npm init
```
이후 다양한 설정이 나오지만 특별하게 지정해야할 것이 없으면 계속 enter을 누르면 된다.

### Webpack 설치

```
$ npm install -D webpack webpack-cli
```

여기서 `-D`의 의미는 개발할 때에만 모듈을 사용한다는 의미이다. 이렇게 설치하게 되면 package.json에서 `devDependencies`에만 webpack이 등록되어 있는 것을 확인할 수 있다.

### webpack.config.js 생성

package.json 파일과 동일한 위치에 webpack.config.js이라는 파일을 생성한다. 이 webpack.config.js라는 파일은 해당 프로젝트 안에서 Webpack이 어떤 식으로 구상되어 실행될 것인지 설정하는 파일이다. 

```js
const path = require('path');

module.exports = {
  name: '서비스 이름',
  mode: 'development',
  devtool: 'eval',
    resolve: {
    extensions: ['.js', '.jsx'] // 
  },
  entry: ['./src/index'],
  output: {
    path: path.join(__dirname, 'dist'),
    filename: 'app.js'
  }
}
```
- **mode**
  - development : 개발 모드
  - production : 실 서비스
- **entry** : 입력
- **output** : 출력
- **extension** : 파일의 확장자를 자동으로 적용 (이후 파일 확장자 생략 가능)

결국 최종적으로 Webpack이 확인하게 되는 파일은 위에서 설정한 index.js 파일이다. Webpack이 실행되면 index.js 파일을 참고해 최종적으로 dist 폴더의 app.js가 만들어진다. (dist 폴더는 Webpack 실행 시 생성)

### Webpack으로 build하기

1. package.json의 scripts를 아래와 같이 변경 후 `npm run dev` 실행

```json
...
  "scripts": {
    "dev": "webpack"
  }
...
```

2. `npx webpack` 실행


<br/>

<br/>

### Babel 설치하기

```
$ npm i -D @babel/core
$ npm i -D @babel/preset-env
$ npm i -D @babel/preset-react
$ npm i -D babel-loader
```
- **@babel/core** : Babel의 기본적 구성 포함
- **@babel/preset-env** : 자신의 브라우저에서 사용되는 최신 문법을 ES5로 변경
- **@babel/preset-react** : jsx 지원
- **babel-loader** : Babel과 Webpack 연결


### Babel 연결

- webpack.config.js

```js
const path = require('path');

module.exports = {
  name: '서비스 이름',
  mode: 'development',
  devtool: 'eval',
    resolve: {
    extensions: ['.js', '.jsx'] // 
  },

  entry: ['./src/index'],
  module : {
    rules: [{
      test: /\.jsx?/, // js와 jsx파일에 babel-loader 적용
      loader: 'babel-loader',
      options: { // babel 옵션 적용
        presets: ['@babel/preset-env', '@babel/preset-react']
      }
    }]
  }
  output: {
    path: path.join(__dirname, 'dist'),
    filename: 'app.js'
  }
}
```

- **presets** : plugin들의 모음

### @babel/preset-env의 설정

preset-env에 설정을 적용하고 싶다면 `['@babel/preset-env', { ... }]`의 객체 안에서 가능하다.

- webpack.config.js

```js
const path = require('path');
const webpack = require('webpack');

module.exports = {
  name: '서비스 이름',
  mode: 'development',
  devtool: 'eval',
    resolve: {
    extensions: ['.js', '.jsx'] // 
  },

  entry: ['./src/index'],
  module : {
    rules: [{
      test: /\.jsx?/, // js와 jsx파일에 babel-loader 적용
      loader: 'babel-loader',
      options: { // babel 옵션 적용
        presets: [
          ['@babel/preset-env', {
            targets: {
              browsers: ['> 5% in KR']
            },
            debug: true
          }], '@babel/preset-react']
      }
    }]
  },
  plugins: [
    new webpack.LoaderOptionsPlugin({ debug: true }), // loader의 options에 debug: true 모두 설정
  ],
  output: {
    path: path.join(__dirname, 'dist'),
    filename: 'app.js'
  }
}
```

- **targets**
  - **browsers** : 원하는 브라우저에만 설정 가능 
    - 모두 설정을 하면 babel 작업량이 증가해 속도 저하
    - 옵션 값은 [여기](https://github.com/browserslist/browserslist)에서 확인 가능
- **debug** : 개발용에서 디버그 설정
- **plugins** : 확장 프로그램 설정
