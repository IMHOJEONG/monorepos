## import/extensions

- https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/extensions.md

- 일부 파일 확인 알고리즘을 사용하면 import source 경로 내에서 파일 확장자를 생략할 수 있음 

  - ex) Node resolver는 .js 확장자가 기본적으로 자동으로 해석되기 때문에 ./foo/bar를 절대 경로 /User/someone/foo/bar.js로 해석할 수 있음 

- resolver에 따라 자동으로 해결되도록 더 많은 확장을 구성할 수 있음 

- 코드 베이스 전체에서 파일 확장자를 일관되게 사용하기 위해 이 규칙은 특정 파일 확장자의 사용을 적용하거나 허용하지 않을 수 있음 

### 규칙 세부정보 

- 이 규칙은 하나의 문자열 옵션, 하나의 객체 옵션 또는 문자열과 객체 옵션을 사용 

  - 문자열 "never"(기본값)인 경우 규칙은 모든 extension에 대한 사용을 금지 

  - 문자열 "always"인 경우 규칙은 모든 import 문에 extension을 사용하도록 함 

  - "ignorePackages"인 경우 규칙은 패키지 import를 제외한 모든 import 문에 extension 사용을 적용 

## import/order 

- https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/order.md

- require() / import 문 순서로 규칙을 적용 +(수정 가능)

- group option이 ["builtin", "external", "internal", "parent", "sibling", "index", "object", "type"]으로 설정된 경우 순서는?

```javascript
// 1. node "builtin" modules
import fs from 'fs';
import path from 'path';
// 2. "external" modules
import _ from 'lodash';
import chalk from 'chalk';
// 3. "internal" modules
// (if you have configured your path or webpack to handle your internal paths differently)
import foo from 'src/foo';
// 4. modules from a "parent" directory
import foo from '../foo';
import qux from '../../foo/qux';
// 5. "sibling" modules from the same or a sibling's directory
import bar from './bar';
import baz from './bar/baz';
// 6. "index" of the current directory
import main from './';
// 7. "object"-imports (only available in TypeScript)
import log = console.log;
// 8. "type" imports (only available in Flow and TypeScript)
import type { Foo } from 'foo';
```

- 할당되지 않은 import는 import 순서가 중요할 수 있으므로 무시됨 

  - ES6 import 구문을 사용하는 문은 require()문 앞에 나타나야 함 

```javascript
// FAIL

import _ from 'lodash';
import path from 'path'; // `path` import should occur before import of `lodash`

// -----

var _ = require('lodash');
var path = require('path'); // `path` import should occur before import of `lodash`

// -----

var path = require('path');
import foo from './foo'; // `import` statements must be before `require` statement
```

```javascript
// PASS! 

import path from 'path';
import _ from 'lodash';

// -----

var path = require('path');
var _ = require('lodash');

// -----

// Allowed as ̀`babel-register` is not assigned.
require('babel-register');
var path = require('path');

// -----

// Allowed as `import` must be before `require`
import foo from './foo';
var path = require('path');
```

## 'jsx-a11y/label-has-associated-control' 

- https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/blob/main/docs/rules/label-has-associated-control.md

- label 태그에 text label과 관련 control이 있는지 확인 

- label을 control과 연결하는 데 지원되는 두 가지 방법이 있음 

- Control을 label 태그로 래핑 

  - 레이블에 htmlFor를 추가하고 페이지의 입력을 나타내는 DOM ID 문자열을 할당 

  - 이 규칙은 모든 label 태그(또는 label 태그를 출력할 표시될 custom component) 가
    - 1. input element를 래핑하는지 (또는 input tag를 출력할 표시된 custom element) 

    - 2. htmlFor 속성이 있는지 확인하고 label 태그에 text 콘텐츠가 있는지 확인 

### 이 오류를 어떻게 해결?

- ex) input과 관련된 text label만 원한다?

  - label과 input 간의 연결을 달성하는 가장 간단한 방법은 input을 label로 래핑하는 것 

```html
<label>
  Surname
  <input type="text" />
</label>
```
- 모든 최신 브라우저와 보조 기술은 label을 control과 연결함 

- ex) label이 control의 형제?

  - 이 경우 htmlFor 및 ID를 사용해 control을 연결 

```javascript 
<label htmlFor={domId}>Surname</label>
<input type="text" id={domId} />
```

- ex) 내 label 및 input component는 custom component?

  - custom component를 인식하도록 규칙을 구성할 수도 있음 

```javascript
<CustomInputLabel label="Surname">
  <CustomInput type="text" value={value} />
</CustomInputLabel>
```

- 구성 

```json
{
  "rules": {
    "jsx-a11y/label-has-associated-control": [ 2, {
      "labelComponents": ["CustomInputLabel"],
      "labelAttributes": ["label"],
      "controlComponents": ["CustomInput"],
      "depth": 3,
    }],
  }
}
```

- ex) 동일한 input에 대해 두 개의 label이 있음 

  - 두 번째 label이 HTML의 다른 부분에 있는 경우 두 번째 label은 htmlFor만 포함할 수 있지만, 중첩은 포함할 수 없음 

  - 아마도 두 번째 label에 eslint 재정의 주석이 필요할 것 

```html
{/* eslint jsx-a11y/label-has-associated-control: ["error", { assert: "either" } ] */}
<label htmlFor="a">
  Username:
</label>
...
<label htmlFor="a">
  <input id="a" />
</label>
```

### input의 ID 관리 방법 

- React와 같은 라이브러리에서 ID를 생각하는 일반적인 방법 

  - 페이지에서 고유해야 하고 component를 재사용할 수 있어야 하므로 ID를 피해야 한다는 것 

  - id가 필요한 경우 렌더링 시간 동안 id를 생성하려는 유혹을 받지만...

- 서버 및 클라이언트 렌더링이 결정적이도록 브라우저에서 ID를 생성하면 안 됨 

  - 렌더링 시간 uuid는 단순한 해킹이 아니라 실제로 깨지고 절대 사용해서는 안 됨 

- 모든 ID는 서버와 클라이언트에서 결정적이어야 하며 페이지에서 고유해야 함 

  - eg: 각 input에 대해 고유성을 보장하기 위해 가능한 한 tree에서 필요한 ID 소품을 전달할 수 있음 




