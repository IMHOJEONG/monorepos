## 작성 방법 

1. package.json 

2. react, webpack 관련 필요 패키지 설정 

3. tsconfig.json, webpack.config.json을 작성 

## Point!

- @types/react-dom, @types/react 패키지는 이 패키지에만 추가해야 할 거 같습니다. 

### '@types/react' should be listed in the project's dependencies, not devDependencies.

### '@types/react-dom' should be listed in the project's dependencies, not devDependencies. 

- 마지막에 devDependencier를 추가 
```json
module.exports = {
  extends: ['airbnb', 'prettier', 'plugin:storybook/recommended'],
  plugins: ['prettier', 'react-hooks', 'jest', 'jest-dom'],
  rules: {
    'prettier/prettier': 'error',
    'import/no-extraneous-dependencies': [
      'error',
      {
        devDependencies: [
          '**/*.stories.tsx',
          '**/*.@(spec|test).@(js|ts)?(x)',
          '**/*.tsx'  
        ]
    }
}
```

- `react-dom/client` import should occur before import of `./Index`eslint(import/order)

  - https://github.com/import-js/eslint-plugin-import/blob/main/docs/rules/order.md

  - import/order가 import 순서를 조정해줌 

