## @babel/runtime

https://babeljs.io/docs/babel-runtime

- Babel 모듈식 런타임 도우미가 포함된 라이브러리 

### 설치 

```shell
npm install --save @babel/runtime 
```

- Babel 플러그인 `@babel/plugin-transform-runtime`과 함께 런타임 종속성으로 사용하기 위한 것 

### 왜?

- 때때로 Babel은 파일 전체에서 동일한 출력에 일부 코드를 삽입할 수 있으므로 잠재적으로 재사용할 수 있음 

- ex) class transform을 사용하면 (loose mode 없이)

```javascript
class Circle

// turns into 
function _classCallCheck(instance, Constructor) {
    // ...
}

var Circle = function Circle() {
    _classCallCheck(this, Circle);
};
```

- 클래스를 포함하는 모든 파일에 매번 반복되는 `_classCallCheck` 함수가 있음을 의미 

- `@babel/plugin-transform-runtime`을 사용하면 함수에 대한 참조를 `@babel/runtime` 버전으로 대체 

```javascript
var _classCallCheck = require("@babel/runtime/helpers/classCallCheck");

var Circle = function Circle() {
  _classCallCheck(this, Circle);
};
```

- `@babel/runtime`은 모듈 방식으로 함수 구현을 포함하는 패키지일 뿐 




