## no_unsafe_assignment

- 변수 및 properties에 type이 any인 값을 할당하는 것을 허용하지 않음 

- ESLint 구성에서 "plugin:@typescript-eslint/recommended-requiring-type-checking"을 확장하면 이 규칙이 활성화됨 

- 이 규칙을 실행하려면 Type 정보가 필요 

- Tyepscript의 any Type은 Type 시스템의 위험한 탈출구 

  - any를 사용하면 많은 Type 검사 규칙이 비활성화되며 일반적으로 최후의 수단으로 사용하거나 코드를 prototyping할 대만 사용하는 것이 가장 좋음 

- 최선의 의도에도 불구하고 any Type이 때대로 코드베이스에 누출될 수 있음 

  - Type이 지정된 값을 변수에 할당하는 것은 특히 외부 라이브러리에서 유출되는 경우 파악하기 어려울 수 있음 

- 이 규칙은 변수에 any를 할당하고 배열 destructuring에 any[]를 할당하는 것을 허용하지 않음 

- 또한, 이 규칙은 특정 Type을 예상하는 수신자에게 generic 위치의 안전하지 않은 any를 전달하지 않도록 generic Type 인수 타입들을 비교 

  - ex) Set<string>으로 선언된 변수에 Set<any>를 할당하면 오류가 발생 



