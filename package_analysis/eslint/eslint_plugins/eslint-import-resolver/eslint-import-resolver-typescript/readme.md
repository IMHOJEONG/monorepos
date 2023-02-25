### eslint-import-resolver-typescript

- https://github.com/import-js/eslint-import-resolver-typescript

- eslint-plugin-import에 Typescript 지원을 추가함(또는 더 빠른 속도를 위해 eslint-plugin-i를 시도하고 싶을 수 있음)


- 어떤 것을 할 수 있는가? 

    - 확장자가 .cts/.mts/.ts/.tsx/.d.cts/.d.mts/.d.ts인 파일 import/require

    - tsconfig.json에 정의된 paths 사용 

    - 일반 .js/.jsx보다 @types/* 정의 해결을 선호 

    - 여러 tsconfigs는 평소와 같이 지원 

    - package.json에서 import/export 필드 지원 

### 주목할 부분 

- 버전 2.0.0 이후에는 .d.ts가 @types/* 정의 또는 자체 정의를 위해 node_modules 패키지를 해결할 때 일반 .js/.jsx 파일보다 더 높은 우선 순위를 가짐 
