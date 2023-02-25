## eslint-plugin-jest

- https://github.com/jest-community/eslint-plugin-jest

- Jest를 위한 eslint plugin

### 설치 

```json
yarn add --dev eslint eslint-plugin-jest 
```

- ESLint를 전역적으로 사용하려면 eslint-plugin-jest를 전역적으로 설치해야 함 

### 사용법 

- '.eslintrc' 구성 파일의 plugins 부분에 jest를 추가해 줍니다 

- 추가할 때 'eslint-plugin-' 생략 가능
```json
{
    "plugins": ["jest"]
}
```

- "rules" 부분 아래에 원하는 rule을 추가할 수 있음 

```json
{
    "rules": {
         "jest/no-disabled-tests": "warn",
    "jest/no-focused-tests": "error",
    "jest/no-identical-title": "error",
    "jest/prefer-to-have-length": "warn",
    "jest/valid-expect": "error"
    }
}
```

- Jest가 제공하는 환경 변수에 대해 ESLint에 알릴 수도 있음 

```json
{
  "env": {
    "jest/globals": true
  }
}
```

- 이것은 이 플러그인이 공유하는 모든 구성에 포함되어 있으므로 확장할 경우 생략할 수 있음 

### Aliased Jest 전역 

- `globalAliases` 설정을 사용하여 별칭을 지정한 전역 Jest에 대해 이 플러그인에 알릴 수 있음 

```json
{
  "settings": {
    "jest": {
      "globalAliases": {
        "describe": ["context"],
        "fdescribe": ["fcontext"],
        "xdescribe": ["xcontext"]
      }
    }
  }
}
```