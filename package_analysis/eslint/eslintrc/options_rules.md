## Reference 

https://github.com/prettier/eslint-plugin-prettier#recommended-configuration

- `"extends": ["prettier"]`

  - Prettier와 충돌하는 일부 ESLint 규칙을 해제하는 eslint-config-prettier의 구성을 활성화함 

- `"plugins": ["prettier"]`

  - 플러그인을 등록 

- `"prettier/prettier": "error"

  - ESLint 내에서 Prettier를 실행하는 이 플러그인에서 제공하는 규칙을 켬 

- `"arrow-body-style": "off"` 및 `"prefer-arrow-callback": "off"`

  - 안타깝게도 이 플러그인에서 문제가 되는 두 가지 ESLint 핵심 규칙을 해제 

### rules : { 'import/no-extraneous-dependencies' }

https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/no-extraneous-dependencies.md

- package.json의 dependencies, devDependencies, optionalDependencies, peerDependencies 또는 bundledDependencies에 선언되지 않은 외부 모듈 가져오기를 금지 

- 가장 가까운 부모 package.json이 사용됨 

  - package.json이 없으면 rule은 아무것도 lint하지 않음 

  - rule option인 packageDir로 변경가능. 

  - 일반적으로 내부로 표시된 모듈의 import를 무시하지만 규칙 옵션 includeInternal로 변경할 수 있음 

- Type 가져오기는 includeTypes를 지정하여 확인 가능 

- options

  - globs 배열을 사용해서 설정 가능 

```js
"import/no-extraneous-dependencies": ["error", {"devDependencies": ["**/*.test.js", "**/*.spec.js"]}]
```

- glob 배열을 사용할 때 linting 되는 파일의 이름이 배열의 단일 glob과 일치하면 설정이 true로 설정되고, 그렇지 않으면 false로 설정됨 


### "react-hooks/rules-of-hooks" or "react-hooks/exhastive-deps"

https://reactjs.org/docs/hooks-rules.html

- `"react-hooks/rules-of-hooks": "error" 

  - Hooks의 규칙 확인 

- `"react-hooks/exhastive-deps": "warn"`

  - effect 의존성 확인 

###  'react/react-in-jsx-scope': 'off'

- https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/react-in-jsx-scope.md

- JSX를 사용할 때 누락된 React를 허용하지 않음 

- JSX를 사용할 때 `<a />`는 React.createElement("a")로 확장됨 

- 따라서 React 변수는 범위 내에 있어야 함 

### 'react/jsx-props-no-spreading': 'off'

- https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-props-no-spreading.md

- JSX Props에 대한 spreading이 없도록 강제 

- Component에서 받는 Props에 대해 보다 명시적으로 표시되어 코드의 가독성이 향상됨 

  - 또한, 의도하지 않은 추가 props 전달을 피하고 유효하지 않은 HTML props가 HTML 요소에 전달될 때 react가 경고를 내보낼 수 있도록 함 => 유지 관리에도 좋음 

### react/jsx-filename-extension

- https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-filename-extension.md

- JSX를 포함할 수 있는 파일 확장자를 허용하지 않음 

- ex) 

```js 
// filename: MyComponent.js => incorrect
function MyComponent() {
  return <div />;
}

// filename: MyCompoent.jsx
function MyComponent() {
  return <div />;
}

```
- 이 규칙은 실험적 기능이나 type 주석과 같은 다른 비표준 구문이 아닌 jsx구문만 보고한다는 점에 유의 

### Rule Options 

- allow (default : "always")

- JSX 파일 이름 확장자를 허용하는 경우. 기본적으로 모든 파일에는 JSX 확장자가 있을 수 있음 

- JSX 구문을 포함하는 파일에서 JSX 파일 확장자만 허용하려면 필요에 따라 설정 

```json
"rules": {
  "react/jsx-filename-extension": [1, { "allow": "as-needed" }]
}
```

- extensions (default: [".jsx"])

- 허용되는 확장 집합을 구성할 수 있음. 기본적으로 '.jsx'가 허용됨 

- '.jsx'와 '.js'를 모두 허용하려는 경우

```json
"rules": {
  "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"]}]
}
```

### 'react/function-component-definition': 'off'

- https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/function-component-definition.md

- 함수 컴포넌트에 대한 특정 함수 Type 적용 

- 이 규칙은 --fix CLI 옵션으로 자동으로 수정할 수 있음 

- Rule Details

- 이 규칙은 함수 컴포넌트에 대해 일관된 기능 타입을 적용하는 것을 목표로 함 

- 기본적으로 명명된 컴포넌트에 대한 함수 선언과 명명되지 않은 함수 컴포넌트에 대한 함수 표현식을 선호 

```javascript 

// Incorrect! 
// function expression for named component
const Component = function (props) {
  return <div>{props.content}</div>;
};

// arrow function for named component
const Component = (props) => {
  return <div>{props.content}</div>;
};

// arrow function for unnamed component
function getComponent() {
  return (props) => {
    return <div>{props.content}</div>;
  };
}

```

### 규칙 옵션 

- 이 규칙은 Option 개체를 Component의 기본 함수 type을 지정할 수 있는 두 번째 매개변수로 사용 

- option 객체의 첫 번째 속성 

  - "function-declartion", "function-expression", "arrow-function" 또는 이러한 항목을 포함하는 배열일 수 있는 "namedComponents"이며 기본값으로 'function-declaration'이 있음 

- option 객체의 두 번째 속성

  - "unnamedComponents" 이며, "function-expression", "arrow-function" 또는 이들을 포함하는 배열일 수 있으며 기본값으로 "function-expression"이 있음 

```json
...
"react/function-component-definition": [<enabled>, {
  "namedComponents": "function-declaration" | "function-expression" | "arrow-function" | Array<"function-declaration" | "function-expression" | "arrow-function">,
  "unnamedComponents": "function-expression" | "arrow-function" | Array<"function-expression" | "arrow-function">
}]
...
```

- Incorrect한 예 

```javascript
// only function declarations for named components
// [2, { "namedComponents": "function-declaration" }]
const Component = function (props) {
  return <div />;
};

const Component = (props) => {
  return <div />;
};

// only function expressions for named components
// [2, { "namedComponents": "function-expression" }]
function Component (props) {
  return <div />;
};

const Component = (props) => {
  return <div />;
};

// only arrow functions for named components
// [2, { "namedComponents": "arrow-function" }]
function Component (props) {
  return <div />;
};

const Component = function (props) {
  return <div />;
};

// only function expressions for unnamed components
// [2, { "unnamedComponents": "function-expression" }]
function getComponent () {
  return (props) => {
    return <div />;
  };
}

// only arrow functions for unnamed components
// [2, { "unnamedComponents": "arrow-function" }]
function getComponent () {
  return function (props) {
    return <div />;
  };
}

```

- 이 규칙에 Correct한 코드 

```javascript
// only function declarations for named components
// [2, { "namedComponents": "function-declaration" }]
function Component (props) {
  return <div />;
}

// only function expressions for named components
// [2, { "namedComponents": "function-expression" }]
const Component = function (props) {
  return <div />;
};

// only arrow functions for named components
// [2, { "namedComponents": "arrow-function" }]
const Component = (props) => {
  return <div />;
};

// only function expressions for unnamed components
// [2, { "unnamedComponents": "function-expression" }]
function getComponent () {
  return function (props) {
    return <div />;
  };
}

// only arrow functions for unnamed components
// [2, { "unnamedComponents": "arrow-function" }]
function getComponent () {
  return (props) => {
    return <div />;
  };
}
```

- 고칠 수 없는 패턴 

- Javascript에는 고칠 수 없는 패턴이 하나 있음 

  - 이것이 유효한 구문이라는 사실과 관련 있음 

```js
export default function getComponent () {
  return <div />;
}
```

- 그렇지 않은 경우 

```javascript
export default var getComponent = () => {
  return <div />;
}

export default var getComponent = function () {
  return <div />;
}
```

- 이러한 패턴은 수동으로 수정해야 함 

- 조심하세요, Typescript 사용자 

  - Autofixer는 Typescript 사용자에게 다소 제약이 있음 

  - 다음 패턴은 Typescript에서 자동 수정될 수 없음 

```javascript
// function expressions and arrow functions that have type annotations cannot be autofixed to function declarations
// [2, { "namedComponents": "function-declaration" }]
const Component: React.FC<Props> = function (props) {
  return <div />;
};

const Component: React.FC<Props> = (props) => {
  return <div />;
};

// function components with one unconstrained type parameter cannot be autofixed to arrow functions because the syntax conflicts with jsx
// [2, { "namedComponents": "arrow-function" }]
function Component<T>(props: Props<T>) {
  return <div />;
};

const Component = function <T>(props: Props<T>) {
  return <div />;
};

// [2, { "unnamedComponents": "arrow-function" }]
function getComponent() {
  return function <T>(props: Props<T>) => {
    return <div />;
  }
}
```

- Type 매개변수는 여려 Type 매개변수가 있거나 제한된 Type 매개변수가 하나만 있는 경우 구문 충돌을 생성하지 않음 

  - Typescript에서 다음 패턴을 자동으로 수정할 수 있음 

```javascript
 // autofix to function expression with type annotation
// [2, { "namedComponents": "function-expression" }]
const Component: React.FC<Props> = (props) => {
  return <div />;
};

// autofix to arrow function with type annotation
// [2, { "namedComponents": "function-expression" }]
const Component: React.FC<Props> = function (props) {
  return <div />;
};

// autofix to named arrow function with one constrained type parameter
// [2, { "namedComponents": "arrow-function" }]
function Component<T extends {}>(props: Props<T>) {
  return <div />;
}

const Component = function <T extends {}>(props: Props<T>) {
  return <div />;
};

// autofix to named arrow function with multiple type parameters
// [2, { "namedComponents": "arrow-function" }]
function Component<T1, T2>(props: Props<T1, T2>) {
  return <div />;
}

const Component = function <T1, T2>(props: Props<T2>) {
  return <div />;
};

// autofix to unnamed arrow function with one constrained type parameter
// [2, { "unnamedComponents": "arrow-function" }]
function getComponent() {
  return function <T extends {}> (props: Props<T>) => {
    return <div />;
  };
}

// autofix to unnamed arrow function with multiple type parameters
// [2, { "unnamedComponents": "arrow-function" }]
function getComponent() {
  return function <T1, T2>(props: Props<T1, T2>) => {
    return <div />;
  }
}
```

### 'import/no-duplicates'

- https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/no-duplicates.md

- 확인된 경로를 두 번 이상 가져오는 경우 보고함 

- ESLint core에 유사한 규칙(no-duplicated-imports)이 있지만 이 버전은 두 가지 주요 방식에서 다름 

1. 소스 코드의 경로는 정확히 일치할 필요가 없으며 파일 시스템의 동일한 모듈을 가리키기만 하면 됨 

  - ex) ./foo 및 ./foo.js

2. 이 버전은 Flow type import를 표준 import와 구별함 

- 자세한 규칙 사항 

```javascript
// Vaild

import SomeDefaultClass, * as names from './mod'
// 동일한 모듈에서 Flow `type` import는 정상  
import type SomeType from './mod'
```

```javascript
// ./mod 가져오기가 둘 다 보고됨 

import SomeDefaultClass from './mod'

// oops, some other import separated these lines
import foo from './some-other-mod'

import * as names from './mod'

// will catch this too, assuming it is the same target module
import { something } from './mod.js'
```
- 동기 : 이것이 두 명의 개발자가 서로 다른 시간에 동일한 모듈에서 서로 다른 이름을 가져온 결과일 가능성이 높다는 것 

  - 잠재적으로 파일에서 크게 다른 위치 

- 이 규칙은 둘 다 (n개의 다수) 주의를 환기시킴 

