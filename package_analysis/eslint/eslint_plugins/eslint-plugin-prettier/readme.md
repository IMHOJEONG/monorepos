## eslint-plugin-prettier

- https://github.com/prettier/eslint-plugin-prettier

- ESLint 규칙으로 Prettier를 실행하고 차이점을 개별 ESLint 문제로 보고 

- 원하는 형식이 Prettier의 출력과 일치하지 않으면 대신 prettier-eslint와 같은 다른 도구를 사용해야 함 

### 설치 

```shell
npm install --save-dev eslint-plugin-prettier
npm install --save-dev --save-exact prettier
```

- `eslint-plugin-prettier`는 Prettier 또는 ESLint를 설치하지 않음

  - 직접 설치해야 함 

- 그런 다음 `.eslintrc.json`에서 다음을 수행 

```json
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```