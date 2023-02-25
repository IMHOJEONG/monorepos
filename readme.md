### monorepo 구축

- https://github.com/kowoohyuk/monorepo-template/blob/main/package.json

```shell
# https://yarnpkg.com/cli/set/version
yarn set version latest

yarn init

yarn dlx @yarnpkg/sdks vscode

```

- 그 후, package.json 설정 변경 


  - `"private": true`의 의미는? 

    - https://yarnpkg.com/configuration/manifest#private

    - true인 경우, 패키지는 비공개로 간주되며 Yarn은 상황에 관계없이 게시를 거부, 이 플래그를 설정하면 작업 공간과 같이 게시된 패키지에서 의미가 없는 일부 기능도 잠금 해제됨 

```shell

"private":true,
"workspaces": [
    "packages/*"
]
```

- 패키지 추가 

```shell
yarn add [package명] --dev 
```

1. 기본 패키지들을 설치 

```text
"@types/node": "^18.14.0",
"@types/react": "^18.0.28",
"eslint": "^8.34.0",
"husky": "^8.0.3",
"lint-staged": "^13.1.2",
"prettier": "^2.8.4",
"react": "^18.2.0",
"typescript": "^4.9.5"
```

2. eslint plugin들을 설치해준다.

```text
"@typescript-eslint/eslint-plugin": "^5.53.0",
    "@typescript-eslint/parser": "^5.53.0",
   
 "eslint-config-airbnb": "^19.0.4",
    "eslint-config-prettier": "^8.6.0",
    "eslint-import-resolver-node": "^0.3.7",
    "eslint-import-resolver-typescript": "^3.5.3",
    "eslint-plugin-import": "^2.27.5",
    "eslint-plugin-jest": "^27.2.1",
    "eslint-plugin-jest-dom": "^4.0.3",
    "eslint-plugin-jsx-a11y": "^6.7.1",
    "eslint-plugin-prettier": "^4.2.1",
    "eslint-plugin-react": "^7.32.2",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-storybook": "^0.6.11",
   
```

3.  storybook 공통 패키지를 resolution에 설정해준다 

```text
"resolutions": {
    "@storybook/core-common/webpack": "^5",
    "@storybook/core-server/webpack": "^5",
    "@storybook/react/webpack": "^5"
  }
```

4. .eslintrc.js, .prettierrc.json, .lint-staged.config.js 작성 

