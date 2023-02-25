## eslint-plugin-jsx-a11y

https://github.com/jsx-eslint/eslint-plugin-jsx-a11y

- JSX 요소의 접근성 규칙에 대한 정적 AST 검사기 

### 왜?

- 이 플러그인은 JSX의 정적 평가를 수행하여 React 앱의 접근성 문제를 찾아냄 

- 정적 코드에서만 오류를 포착함 `@axe-core/react`와 함께 사용하여 렌더링된 DOM의 접근성을 테스트

- 이러한 도구를 대규모 a11y 테스트 프로세스의 한 단계로 간주하고 항상 보조 기술로 앱을 테스트하자 

### 설치 

- `eslint-config-airbnb`를 통해 이 플러그인을 설치하는 경우 

  - https://github.com/airbnb/javascript/tree/HEAD/packages/eslint-config-airbnb#eslint-config-airbnb-1

  - 위의 방법을 따라서 해보자 

- ESLint를 먼저 설치하고 eslint-plugin-jsx-a11y를 설치

```shell
npm install eslint --save-dev
npm install eslint-plugin-jsx-a11y --save-dev

# or
yarn add eslint --dev
yarn add eslint-plugin-jsx-a11y --dev

```

- 참고: ESLint를 전역으로 설치한 경우 `eslint-plugin-jsx-a11y`도 전역으로 설치해야 함 

### 사용법 

- `.eslintrc` 구성 파일의 plugin 섹션에 jsx-a11y를 추가 

- `eslint-plugin-` 접두사를 생략할 수 있음

```json
{
  "plugins": ["jsx-a11y"]
}
```

- 그 이후에, rules 부분 아래에 규칙을 구성할 수 있음 

```json
{
  "rules": {
    "jsx-a11y/rule-name": 2
  }
}
```

- `extends` 안에 `plugin:jsx-a11y/recommended` 또는 `plugin:jsx-a11y/strict`를 추가하는 방식 

  - 한 번에 추천하는 규칙과 엄격한 규칙을 적용할 수 있음 

```json
{
  "extends": ["plugin:jsx-a11y/recommended"]
}
```

- 구성을 확장할 때 `.eslintrc` 구성 파일에서 `"plugins": ["jsx-ally"]`를 생략할 수 있음 

- Custom Component가 DOM 요소로 확인되도록 하려면 각 Custom Component 이름을 DOM 요소 타입에 매핑하여 구성 파일에서 전역 설정을 지정할 수 있음 

```json
{
  "settings": {
    "jsx-a11y": {
      "components": {
        "CityInput": "input",
        "CustomButton": "button",
        "MyButton": "button",
        "RoundButton": "button"
      }
    }
  }
}
```
