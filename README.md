# 🎮 Typescript로 블록체인 만들기

[노마드코더 Typescript 강의 🚀](https://nomadcoders.co/typescript-for-beginners)

## Table of Contents
- [tsconfig.json](https://github.com/Lecture-Summary/typechain#tsconfig.json)
- [Declaration Files](https://github.com/Lecture-Summary/typechain#Declaration-Files)

## tsconfig.json

```json
{
  "include": ["src"], // typescript 소스가 작성되는 경로
  "compilerOptions": {
    "outDir": "build", // build 되는 결과물이 담길 폴더
    "target": "ES6", // build 되는 Javascript의 버전
    "lib": ["ES6", "DOM"], // Javascript 코드가 어떤 환경에서 동작될지 정의
    "strict": true
  }
}
```

lib 은 Javascript 코드가 어떤 환경에서 동작될지를 정의한다.
만약 `DOM`을 넣어주게되면 typescript는 DOM 환경에서 제공되는 `document.`, `window.` 또는 `localStorage.`등을 입력하였을 때 브라우저 환경에서 지원되는 자동완성 목록을 제공해준다.

---

## Declaration Files

npm으로 설치한 node_modules에 존재하는 Javascript 파일에 대한 type 정의 방법

### myPackage.js
```js
export function init(config) {
  return true
}
export function exit(code) {
  return code + 1
}
```
js로 작성된 간단한 파일이 있따.

### index.ts
```ts
import { init, exit } from 'myPackage'

init({ url: 'true' })

exit(1)
```
myPackage를 import하게되면 myPackage에 대한 type을 찾을 수 없다며 에러가 표시된다.

### myPackage.d.ts
```ts
interface Config {
  url: string
}

declare module 'myPackage' {
  function init(config: Config): boolean
  function exit(code: number): number
}
```
`{패키지명}.d.ts` 파일을 작성한 후 js 파일에 있는 함수들의 타입을 정의해준다면 에러가 사라지며 자동완성 기능을 제공한다.

## JSDoc