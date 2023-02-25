## env

- https://eslint.org/docs/latest/use/configure/language-options

- Configuration files 

  - 구성 파일에서 환경을 지정하려면 env 키를 사용 

  - 각 환경을 true로 설정하여 활성화할 환경을 지정 

- ex) 브라우저 및 Node.js 환경을 활성화 

```json
{
    "env": {
        "browser": true,
        "node": true
    }
}
```

- 'jest/globals': 이거는 테스트가 필요할 듯 