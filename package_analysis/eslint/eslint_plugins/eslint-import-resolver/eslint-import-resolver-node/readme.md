### eslint-import-resolver-node 

- https://www.npmjs.com/package/eslint-import-resolver-node

- `eslint-plugin-import`를 위한 기본 노드 스타일 모듈 resolution plugin

- 주요 변경 사항이 있는 경우 특정 버전으로 pegging 할 수 있도록 별도로 게시됨 

- config

```json
settings:
  import/resolver:
    node:
      extensions:
        # if unset, default is just '.js', but it must be re-added explicitly if set
        - .js
        - .jsx
        - .es6
        - .coffee

      paths:
        # an array of absolute paths which will also be searched
        # think NODE_PATH
        - /usr/local/share/global_modules

      # this is technically for identifying `node_modules` alternate names
      moduleDirectory:

        - node_modules # defaults to 'node_modules', but...
        - bower_components

        - project/src  # can add a path segment here that will act like
                       # a source root, for in-project aliasing (i.e.
                       # `import MyStore from 'stores/my-store'`)
```

- 또는 default Option으로 

```json
settings:
  import/resolver: node
```