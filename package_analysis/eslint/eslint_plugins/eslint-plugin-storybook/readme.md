## eslint-plugin-storybook

https://github.com/storybookjs/eslint-plugin-storybook

- Storybook에 대한 모범 사례 규칙 

### 설치 

1. ESLint를 설치해야 함 

```shell
npm install eslint --save-dev

# or 
yarn add eslint --dev
```

2. `eslint-plugin-storybook`을 설치 

```shell
npm install eslint-plugin-storybook --save-dev
# or 
yarn add eslint-plugin-storybook --dev
```

3. `.eslintignore` 파일에 이것을 추가

```js
// Inside your .eslintignore file
!.storybook
```
- 이를 통해, 이 플러그인은 .storybook 폴더 내부의 구성 파일도 lint할 수 있음 

  - 항상 올바른 구성을 유지함 

    - ex) add-on 이름을 잘못 입력하는 것과 관련된 문제가 직면하지 않음


### 사용법 

- Configure rules에 `.eslintrc.*` 파일을 사용하자

- `.eslintrc` 구성 파일의 extends 섹션에 `plugin:storybook/recommended`를 추가 

  - `eslint-plugin-` 접두사를 생략할 수 있음 

```json
{
  // extend plugin:storybook/<configuration>, such as:
  "extends": ["plugin:storybook/recommended"]
}
```

- 이 플러그인은 `*.stories.*(권장)` 또는 `*.story.*` 패턴을 따르는 파일에만 적용됨 

  - 자동 구성이므로 아무것도 할 필요가 없음 

### Rules 재정의, 비활성화 

- 필요에 따라 rule 설정을 재정의, 추가 또는 비활성화할 수 있음 

  - 이러한 설정이 모든 파일에 적용되는 것을 원하지 않을 수 있음 

- `.eslintrc.*` 파일에 덮어쓰기 section을 추가해 story 파일에만 덮어쓰기를 적용해야 함 

