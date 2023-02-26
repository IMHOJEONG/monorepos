## Option Philosophy

- https://prettier.io/docs/en/option-philosophy.html

- Prettier를 채택한 가장 큰 이유는 현재 진행 중인 스타일에 대한 모든 논쟁을 중단하기 위해서 

  - Prettier가 가진 옵션이 많을수록 위의 목표와 멀어짐

- 옵션이 전혀 없는 이유는?

  - Prettier의 유아기에 몇 가지가 추가됨 

  - "큰 수요"에 따라 몇 가지가 추가됨 

  - 일부는 호환성상의 이유로 추가 

- 동기를 부여하기 쉬운 옵션은 다음과 같음 

  - `--trailing-comma es5` : 트랜스파일을 하지 않고도 대부분의 환경에서 후행 쉼표를 사용할 수 있음 

  - `--prose-wrap` : 모든 기발한 Markdown 렌더러를 지원하는 데 중요 

  - `--html-whitespace-sensitivity`: HTML의 불행한 공백 규칙으로 인해 필요함 

  - `--end-of-line`: 팀이 CRLF을 git repository에 더 쉽게 보관할 수 있음 

  - `--quote-props` : Google 클로저 컴파일러의 고급 사용에 중요 

- 다른 옵션들은 동기를 부여하기가 어렵다?

  - ex) `--arrow-parens`, `--jsx-single-quote`, `--bracket-same-line`, `--no-bracket-spacing`

  - 팀에서 많은 bike-shedding를 유발 

- Prettier는 사용량이 많이 증가 

  - 과거의 큰 수요가 지금은?

- Option set가 동결되어야 하는 지점에 도달했다고 결론을 내릴 만큼 확신을 가지고 있음 


