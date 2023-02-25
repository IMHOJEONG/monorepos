## lint-staged 

- 

### Using JS configuration files 

- https://github.com/okonet/lint-staged#using-js-configuration-files

- Configuration 파일을 JS로 작성하는 것은 lint-staged를 구성하는 강력한 방법 

- Conf 파일에서 단일 function or Object를 내보낼 수 있음 

- export 값이 함수인 경우 모든 staged된 파일 이름의 배열을 받음 

  - 그런 다음 파일에 대한 고유한 Matcher를 빌드하고 명령 문자열 또는 명령 문자열 배열을 반환할 수 있음 

- export 값이 객체인 경우 해당 키는 일반적인 비 js 구성 형식과 같이 glob 일치여야 함 