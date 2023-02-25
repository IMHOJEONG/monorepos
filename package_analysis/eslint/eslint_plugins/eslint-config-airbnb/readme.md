## eslint-config-airbnb

- https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb

- 이 패키지는 Airbnb의 .eslintrc를 확장 가능한 공유 구성으로 제공

- 사용을 위해 3가지 ESLint 구성을 내보냄 

### 1. eslint-config-airbnb

- 기본 export 결과에는 ECMAScript 6+ 및 React를 포함한 대부분의 ESLint 규칙이 포함되어 있음 

- eslint, eslint-plugin-import, eslint-plugin-react, eslint-plugin-react-hooks, eslint-plugin-jsx-a11y가 필요함 

- React Hooks 규칙을 활성화하지 않음 

- 이를 활성화하려면 eslint-config-airbnb/hooks 를 참고하자 

### eslint-config-airbnb/hooks

- 이 진입점은 React hooks (v16.8 필요)에 대한 Linting 규칙을 활성화함 

- 사용하려면 .eslintrc에 아래 json 부분을 추가

```json
"extends": ["airbnb", "airbnb/hooks"]
```
