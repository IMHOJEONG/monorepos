## eslint-plugin-jest-dom

https://github.com/testing-library/eslint-plugin-jest-dom

- 모범 사례를 따르고 jest-dom으로 테스트를 작성할 때 일반적인 실수를 예상하는 ESLint 플러그인 

### 설치 

- 이 모듈은 node와 함께 번들로 제공되는 npm을 통해 배포되며 프로젝트의 devDependencies 중 하나로 설치되어야 함 

```shell
npm install --save-dev eslint-plugin-jest-dom
```
- 이 라이브러리에는 ESLint에 대한 필수 peerDependencies 목록이 있음 

- `.eslintrc.js` 구성 파일의 plugin 섹션에 jest-dom을 추가하자 

  - `eslint-plugin-` 접두사를 생략할 수 있음 

```js
module.exports = {
    plugins: ["jest-dom"],
    rules: {
        // your configuration
    },
};
```

- 그 이후에, rules 섹션에서 사용할 규칙을 구성

```js
module.exports = {
    rules: {
        "jest-dom/prefer-checked": "error",
        "jest-dom/prefer-enabled-disabled": "error",
        "jest-dom/prefer-required": "error",
        "jest-dom/prefer-to-have-attribute": "error"
    }
};
```

### 추천하는 Configuration

- 좋은 jest-dom 사례를 수행하는 권장 구성을 export함 

- 이 구성을 활성화하려면 `.eslintrc.js` 구성 파일에서 `extends` 속성을 사용하자 

```js
module.exports = {
  extends: "plugin:jest-dom/recommended",
  rules: {
    // your configuration
  },
};
```


