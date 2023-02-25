
### Extending Configuration Files

https://eslint.org/docs/latest/use/configure/configuration-files#extending-configuration-files

- 확장된 구성 파일은 다른 구성 파일의 모든 특성(규칙, 플러그인 및 언어 옵션 포함)을 상속하고 모든 옵션을 수정할 수 있음 

    - 기본 구성 : 확장된 구성 

    - 파생 구성 : 기본 구성을 확장하는 구성 

    - 결과 실제 구성 : 파생된 구성을 기본 구성에 병합한 결과 

- `extends` 속성 값은 다음 중 하나 

  - 구성을 지정하는 문자열(구성 파일의 경로, 공유 가능한 구성의 이름, `eslint:recommended` 또는 `eslint:all`)

  - 각 추가 구성이 이전 구성을 확장하는 문자열 배열 

- ESLint는 재귀적으로 구성을 확장하기 때문에, 기본 구성도 `extends` 속성을 가질 수 있음 

  - extends 속성의 상대 경로 및 공유 가능한 구성 이름은 나타나느 구성 파일의 위치에서 확인됨 

  