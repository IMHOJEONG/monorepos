## import/resolver

- https://github.com/import-js/eslint-plugin-import#resolvers

- module 번들러의 출현과 module 및 module 구문 사양의 현재 상태로 인해 

  - import x from 'module'이 모듈 뒤에 있는 파일을 찾기 위해 어디를 찾아야 하는지 항상 명확하지 않음 

- v0.10ish까지 이 플러그인은 Node의 가져오기 동작을 구현하는 substack의 resolve 플러그인을 직접 사용했음 

  - 대부분의 경우 꽤 잘 작동했음 

- 그러나 Webpack은 loader(import 'file!./whatever') 및 External과 같은 여러가지 aliasing schema와 같이 노드가 허용하지 않는 import 모듈 소스 문자열의 여러가지를 허용 

  - module ID를 Runtime에 전역 이름에 Mapping 

    - 일부 module이 script tag를 통해 더 전통적으로 포함되도록 허용 

---

- 이 두 가지를 모두 지원하기 위해 v0.11에서는 resolver를 도입 

- 현재 Node 및 Webpack resolver가 구현되었지만 resolver는 npm 패키지일뿐 

  - 타사 패키지가 지원됨 (그리고 권장됨)

- 상대 경로는 source에서 가장 가까운 package.json 또는 package.json이 없는 경우 process의 현재 작업 directory를 기준으로 확인됨 

