## import/parsers

### @typescript-eslint/parser

- https://github.com/import-js/eslint-plugin-import#importparsers

### import/parser

- parser에서 파일 확장자 배열로의 map, 파일 확장자가 일치하면 dependency parser는 구성된 ESLint 파서 대신 Map key를 parser로 요구하고 사용 

- 이는 webpack을 사용하고 직접 Typescript와 상호 운용하는 경우에 유용 
