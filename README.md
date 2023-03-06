# Vuetro-UI ESLint
- [Vuetro-UI ESLint](#vuetro-ui-eslint)
  - [목표](#목표)
  - [준비 사항](#준비-사항)
  - [빠른 시작](#빠른-시작)
    - [공통 적용](#공통-적용)
  - [주의할 점](#주의할-점)
  - [적용 방법](#적용-방법)
    - [Javascript](#javascript)
    - [Typescript](#typescript)
    - [Vue2](#vue2)
    - [Vue3](#vue3)
    - [Vue3 + Typescript](#vue3--typescript)
  - [IDE Setting (선택 사항)](#ide-setting-선택-사항)
    - [VSCode](#vscode)
      - [Save 시 자동으로 포맷팅 되도록 설정](#save-시-자동으로-포맷팅-되도록-설정)

## 목표
* 잘못된 Javascript, Typescript 코드로 인한 Runtime 오류 방지
* 여러 개발자가 참여하여도 일관된 코드 스타일 유지
* Vuetro-UI 개발에 적합한 맞춤 `ESLint` 룰 적용
* 룰 충돌 문제를 해소하기 위해 `Prettier`는 제한하고 `ESlint`만 사용 
* `ESlint extension` 사용으로 코드 작성 시간 단축 및 코드 품질 향상

<br/>

## 빠른 시작
### 공통 적용
`package.json` 에 eslint 실행 script 를 등록 합니다.

```json
... 

"scripts": {
  ...,
  "lint": "eslint . --ext .vue,.js,.jsx,.cjs,.mjs,.ts,.tsx,.cts,.mts --ignore-path .gitignore",

},

...
```
> 커맨드에 `--fix` flag를 추가하면 일부 오류들이 자동 수정됩니다.  

<br/>

프로젝트 스택에 해당하는 ESLint Config를 찾아 적용 방법을 참고하세요.

* [Javascript](#javascript)
* [Typescript](#typescript)
* [Vue2](#vue2)
* [Vue3](#vue3)
* [Vue3 + Typescript](#vue3-typescript)

<br/>

## 주의사항
* 프로젝트가 [`module` 타입](https://nodejs.org/api/packages.html#type)이라면 ESLint config는 `.eslintrc.js`가 아닌`.eslintrc.cjs`를 사용해야 합니다.
  * 자신의 프로젝트의 타입을 확인을 하시려면 `package.json` 에서 `type`을 확인하시면 됩니다. 만약 `type`이 없다면 `module` 타입이 아닙니다.

<br/>

## 적용 방법
### Javascript
**NPM**
```bash
npm install --save-dev eslint @babel/core @babel/eslint-parser eslint-config-vuetro
```

**YARN**
```bash
yarn add --dev eslint @babel/core @babel/eslint-parser eslint-config-vuetro
```

`.eslintrc.js` 혹은 [`.eslintrc.cjs`](#주의할-점)를 root 디렉토리에 생성 후 아래 내용을 입력하세요.
```javascript
module.exports = {
  extends: [
    'vuetro',
  ],
};
```

### Typescript
**NPM**
```bash
npm install --save-dev eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-vuetro
```
**YARN**
```bash
yarn add --dev eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-vuetro
```
`.eslintrc.js` 혹은 [`.eslintrc.cjs`](#주의할-점)를 root 디렉토리에 생성 후 아래 내용을 입력하세요.
```javascript
module.exports = {
  extends: [
    'vuetro',
  ],
  overrides: [
    {
      files: ['src/**/*.ts', 'src/**/*.tsx'],
      extends: [
        'vuetro/typescript',
      ],
      parserOptions: {
        project: './tsconfig.json', // tsconfig 파일 등록
      },
    },
  ],
};
```

### Vue2
**NPM**
```bash
npm install --save-dev eslint @babel/core @babel/eslint-parser vue-eslint-parser eslint-plugin-vue eslint-config-vuetro
```
**YARN**
```bash
yarn add --dev eslint @babel/core @babel/eslint-parser vue-eslint-parser eslint-plugin-vue eslint-config-vuetro
```
`.eslintrc.js` 혹은 [`.eslintrc.cjs`](#주의할-점)를 root 디렉토리에 생성 후 아래 내용을 입력하세요.
```javascript
module.exports = {
  extends: [
    'vuetro',
  ],
  overrides: [
    {
      files: ['src/**/*.vue'],
      extends: [
        'vuetro/vue2',
      ],
    },
  ],
};
```

### Vue3
**NPM**
```bash
npm install --save-dev eslint @babel/core @babel/eslint-parser vue-eslint-parser eslint-plugin-vue eslint-config-vuetro
```
**YARN**
```bash
yarn add --dev eslint @babel/core @babel/eslint-parser vue-eslint-parser eslint-plugin-vue eslint-config-vuetro
```
`.eslintrc.js` 혹은 [`.eslintrc.cjs`](#주의할-점)를 root 디렉토리에 생성 후 아래 내용을 입력하세요.
```javascript
module.exports = {
  extends: [
    'vuetro',
  ],
  overrides: [
    {
      files: ['src/**/*.vue'],
      extends: [
        'vuetro/vue3',
      ],
    },
  ],
};
```

### Vue3 + Typescript
**NPM**
```bash
npm install --save-dev eslint @babel/core @babel/eslint-parser @typescript-eslint/eslint-plugin @typescript-eslint/parser @vue/eslint-config-typescript eslint eslint-plugin-vue vue-eslint-parser eslint-config-vuetro
```
**YARN**
```bash
yarn add --dev eslint @babel/core @babel/eslint-parser @typescript-eslint/eslint-plugin @typescript-eslint/parser @vue/eslint-config-typescript eslint eslint-plugin-vue vue-eslint-parser eslint-config-vuetro
```
`.eslintrc.js` 혹은 [`.eslintrc.cjs`](#주의할-점)를 root 디렉토리에 생성 후 아래 내용을 입력하세요.

> :exclamation: `overrides`값의 순서가 아래와 동일 해야합니다.

```javascript
module.exports = {
  extends: [
    'vuetro',
  ],
  overrides: [
    {
      files: [
        'src/**/*.ts',
        'src/**/*.tsx',
        'src/**/*.vue',
      ],
      extends: [
        'vuetro/typescript',
      ],
      parserOptions: {
        project: './tsconfig.json', // tsconfig 파일 등록
      },
    },
    {
      files: ['src/**/*.vue'],
      extends: [
        'vuetro/vue3',
      ],
      parserOptions: {
        parser: '@typescript-eslint/parser',
      },
    },
  ],
};
```


<br/>

## IDE Setting (선택 사항)
### VSCode
#### 파일 저장시 자동 포맷팅 설정 (Auto formatting on save)  
1. ESlint extension 설치  
  VSCode에서 설정한 `eslint` 룰을 기반으로 파일 저장 시 자동 포맷팅을 하기 위해서는 [eslint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)을 설치해야 합니다.  

2. VSCode setting 수정  
  설치 완료 후 `.js`, `.ts`, `.vue` 파일 저장 시 자동 포맷팅 기능을 활성화 하기 위해선 VSCode 설정이 필요합니다.

    **VSCode 전체 설정**  
    `File > Preferences > Settings > Open Settings (JSON)`에서 아래의 옵션을 설정합니다.

    **특정 프로젝트에만 설정**  
    프로젝트 루트 폴더 내의 `.vscode/settings.json` 파일에 아래의 옵션을 설정합니다.

    ```JSON
    {
      "[vue]": {
        "editor.codeActionsOnSave": {
          "source.fixAll.eslint": true,
        },
        "editor.defaultFormatter": "dbaeumer.vscode-eslint",
      },
      "[javascript]": {
        "editor.codeActionsOnSave": {
          "source.fixAll.eslint": true,
        },
        "editor.defaultFormatter": "dbaeumer.vscode-eslint",
      },
      "[typescript]": {
        "editor.codeActionsOnSave": {
          "source.fixAll.eslint": true,
        },
        "editor.defaultFormatter": "dbaeumer.vscode-eslint",
      },
    }
    ```

    `.js`, `.ts`, `.vue`에 한해 기본적으로 `eslint`의 자동 포멧팅 툴을 사용할 것이므로, 해당 파일들의 기본 포맷터를 `dbaeumer.vscode-eslint`로 설정합니다. 그리고 `editor.codeActionsOnSave`의 `source.fixAll.eslint` 설정을 `true`로 설정하여 파일이 저장될 때마다 `eslint`가 자동 포맷팅을 수행하도록 합니다.  

3. Vue3 + Typescript extension 설치     
  아래 항목을 모두 설치합니다.
    * Vue Language Features (Volar)
    * TypeScript Vue Plugin (Volar)  

    **주의사항**  
    Vetur는 삭제해야 합니다.