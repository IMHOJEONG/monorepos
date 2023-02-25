## eslint-plugin-react-hooks

- https://reactjs.org/docs/hooks-rules.html

### Hook 규칙 

- Hook은 React 16.8에 새로 추가되었음 

- 클래스를 작성하지 않고도 상태 및 기타 React 기능을 사용할 수 있음 

- Hook는 Javascript 함수이지만 사용 시 두 가지 규칙을 따라야 함 

  - 이러한 규칙을 자동으로 적용하기 위해 linter Plugin을 제공 

---

## 최상위 레벨에서만 Hook을 호출

- 루프, 조건 또는 중첩 함수 내부에서 Hooks를 호출하지 말라 

- 대신 초기 반환 전에 항상 React 함수의 최상위 수준에서 Hooks를 사용하자 

- 이 규칙을 따르면 Component가 렌더링될 때마다 Hook이 동일한 순서로 호출됨 

  - 이것이 React가 여러 useState, useEffect 호출 간에 Hooks의 상태를 올바르게 보존할 수 있게 해주는 것 

## React 함수에서만 Hooks을 호출 

- 일반 Javascript 함수에서 Hooks를 호출하지 말자 

- 다음을 수행해야 함 

1. React 함수 Component에서 Hook을 호출 

2. Custom Hooks에서 Hook을 호출 

이 규칙을 따르면 Component의 모든 상태 저장 논리가 해당 소스코드에 명확하게 표시됨 

### ESLint 플러그인 

- 이 두 가지 규칙을 적용하는 eslint-plugin-react-hooks라는 ESLint 플러그인을 만듬 

- 기본적으로 CRA에 포함되어 있음 

```shell
npm insall eslint-plugin-react-hooks --save-dev
```

```json
// Your ESLint configuration
{
  "plugins": [
    // ...
    "react-hooks"
  ],
  "rules": {
    // ...
    "react-hooks/rules-of-hooks": "error", // Checks rules of Hooks
    "react-hooks/exhaustive-deps": "warn" // Checks effect dependencies
  }
}
```

### Explanation

- 단일 구성 요소에서 여러 State 또는 Effect Hook을 사용할 수 있음 

```javascript
function() {
    // 1. Use the name state variable
  const [name, setName] = useState('Mary');

  // 2. Use an effect for persisting the form
  useEffect(function persistForm() {
    localStorage.setItem('formData', name);
  });

  // 3. Use the surname state variable
  const [surname, setSurname] = useState('Poppins');

  // 4. Use an effect for updating the title
  useEffect(function updateTitle() {
    document.title = name + ' ' + surname;
  });
}
```

- React는 어떤 상태가 어떤 useState 호출에 해당하는지 어떻게 알 수 있는가?

  - React가 Hooks가 호출되는 순서에 의존한다는 것 

  - ex) Hooks 호출의 순서가 모든 렌더링에서 동일하게 작동하기 때문 

```js
// ------------
// First render
// ------------
useState('Mary')           // 1. Initialize the name state variable with 'Mary'
useEffect(persistForm)     // 2. Add an effect for persisting the form
useState('Poppins')        // 3. Initialize the surname state variable with 'Poppins'
useEffect(updateTitle)     // 4. Add an effect for updating the title

// -------------
// Second render
// -------------
useState('Mary')           // 1. Read the name state variable (argument is ignored)
useEffect(persistForm)     // 2. Replace the effect for persisting the form
useState('Poppins')        // 3. Read the surname state variable (argument is ignored)
useEffect(updateTitle)     // 4. Replace the effect for updating the title

// ...
```

- Hook 호출의 순서가 렌더링 간에 동일하다면, React는 일부 로컬 상태를 각 렌더링과 연결할 수 있음 

- 하지만 조건 내에 Hook 호출을 넣으면 어떻게 될까?

  - persistForm 효과 

```js 

// 조건에서 Hook을 사용해 첫 번째 규칙을 위반
if(name !== '') {
    useEffect(function persistForm() {
        localStorage.setItem('formData', name);
    });
}
```

- `name !==` 조건은 첫 번째 rendering에서 참이므로 이 Hook을 실행 

  - 그러나 다음 rendering에서 사용자가 양식을 지우면 조건이 거짓이 됨 

  - 이제 rendering 중에 이 Hook을 건너뛰므로, Hook 호출 순서가 달라짐 

```js
useState('Mary')           // 1. Read the name state variable (argument is ignored)
// useEffect(persistForm)  // 🔴 This Hook was skipped!
useState('Poppins')        // 🔴 2 (but was 3). Fail to read the surname state variable
useEffect(updateTitle)     // 🔴 3 (but was 4). Fail to replace the effect
```

- React는 두 번째 useState Hook 호출에 대해 무엇을 반환해야 하는지 알지 못함 

- React는 이전 렌더링에서와 마찬가지로 이 Component의 두 번째 Hook 호출이 persistForm 효과에 해당한다고 예상했지만, 더 이상 그렇지 않음 

  - 그 시점부터 우리가 건너뛴 후의 모든 다음 Hook 호출도 하나씩 이동하여 버그로 이어짐 

- `우리 Component의 최상위 수준에서 Hooks를 호출해야 하는 이유 

  - 효과를 조건부로 실행하려면 Hook 안에 넣을 수 있음 

```js
useEffect(function persistForm() {
    // 👍 더 이상 첫 번째 규칙을 어기지 않음 
    if (name !== '') {
      localStorage.setItem('formData', name);
    }
  });
```

- 제공된 lint 규칙을 사용하는 경우 이 문제에 대해 걱정할 필요가 없음 

  - 그러나 이제 Hook이 왜 이런 방식으로 작동하는지, 그리고 규칙이 방지하는 문제도 알 수 있음




