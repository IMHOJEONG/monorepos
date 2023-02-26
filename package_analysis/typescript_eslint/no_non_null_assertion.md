## Forbidden non-null assertion.

- https://typescript-eslint.io/rules/no-non-null-assertion/

- !(! : 후위 연산자)를 사용하여 null이 아닌 assertion을 허용하지 않음 

- ESLint 구성에서 "plugine:@typescript-eslint/recommended"를 확장하면 이 규칙이 활성화됨 

- Typescript의 ! null이 아닌 assertion 연산자는 not null 또는 undefined에서와 같이 식이 null을 허용하지 않는 Type 시스템에 대해 assertion함 

- Assertion을 사용해서 Type 시스템에 새 정보를 알리는 것은 종종 코드가 완전히 type-safe하지 않다는 의미 

  - 일반적으로 Typescript가 값이 null을 허용할 수 있는 경우를 이해할 수 있도록, 프로그램 논리를 구성하는 것이 좋음 


https://github.com/reactjs/reactjs.org/pull/4576

- 위 commit을 참고해서 코드를 수정 

- https://ko.reactjs.org/blog/2022/03/08/react-18-upgrade-guide.html
```
// eslint-disable-next-line @typescript-eslint/no-non-null-assertion
const root = createRoot(container!);
```

- 이게 맞는 걸까?

https://blog.logrocket.com/how-to-use-typescript-with-react-18-alpha/

