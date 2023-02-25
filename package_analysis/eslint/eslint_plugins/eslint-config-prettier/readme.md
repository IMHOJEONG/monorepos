## eslint-config-prettier

- https://github.com/prettier/eslint-config-prettier

- 불필요하거나 Prettier와 충돌할 수 있는 모든 규칙을 끔 

- 이렇게 하면 Prettier를 사용할 때 스타일 선택을 방해하지 않고 좋아하는 공유 가능한 구성을 사용할 수 있음 

- 이 구성은 규칙만 해제하므로 다른 구성과 함께 사용하는 경우에만 의미가 있음 

### 설치 

- eslint-config-prettier를 설치 

```shell
# eslint-config-prettier
npm install --save-dev eslint-config-prettier
```

- 그리고, `.eslintrc.*` 파일에 `extends`배열에 `prettier`를 추가

- 다른 구성을 재정의할 기회를 얻을 수 있도록 마지막에 넣어야 함 

```json
{
  "extends": [
    "some-other-config-you-use",
    "prettier"
  ]
}
```

- 마지막으로, CLI 도우미 도구를 실행하여 .eslintrc.* 파일의 "rules" 섹션에서 문제를 찾음 

  - "rules"은 항상 "extends"보다 더 우선순위가 높다는 점

- "prettier"를 확장하면 핵심 ESLint 규칙과 다음 플러그인의 몇 가지 규칙이 해제됨 

@typescript-eslint/eslint-plugin
@babel/eslint-plugin
eslint-plugin-babel
eslint-plugin-flowtype
eslint-plugin-react
eslint-plugin-standard
eslint-plugin-unicorn
eslint-plugin-vue

- eslint-plugin-prettier를 사용하면 eslint-plugin-prettier의 권장 구성을 확인해보자!

