## eslint-plugin-react

https://github.com/jsx-eslint/eslint-plugin-react

- `eslint`에 대한 특정 linting 규칙 반응 

### 설치

```shell
npm install eslint eslint-plugin-react --save-dev
```

- ESLint를 로컬이 아닌 전역으로 설치할 수도 있음 (npm install -g eslint 사용)

  - 그러나 이것은 권장되지 않으며 사용하는 모든 플러그인 또는 공유 가능한 구성은 두 경우 모두 로컬에 설치해야 함 

### 구성(legacy: .eslintrc*)

- 합리적인 기본값을 얻으려면 사전 설정을 사용하자 

```json
"extends": [
    "eslint:recommended",
    "plugin:react/recommended"
]
```
- React 17의 새로운 JSX 변환을 사용하는 경우 eslint 구성에서 react/jsx-runtime을 확장("extends"에 "plugin:react/jsx-runtime" 추가)하여 관련 규칙을 비활성화함 

- 또한 모든 plugin 규칙에서 공유할 설정을 지정해야 함 


