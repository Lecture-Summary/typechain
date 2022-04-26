## TypeChain

노마드코더 Typescript 강의

## tsconfig.json

```json
{
  "include": ["src"], // typescript 소스가 작성되는 경로
  "compilerOptions": {
    "outDir": "build", // build 되는 결과물이 담길 폴더
    "target": "ES6", // build 되는 Javascript의 버전
    "lib": ["ES6", "DOM"] // Javascript 코드가 어떤 환경에서 동작될지 정의
  }
}
```

lib 은 Javascript 코드가 어떤 환경에서 동작될지를 정의한다.
만약 `DOM`을 넣어주게되면 typescript는 DOM 환경에서 제공되는 `document.`, `window.` 또는 `localStorage.`등을 입력하였을 때 브라우저 환경에서 지원되는 자동완성 목록을 제공해준다.