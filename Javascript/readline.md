## readline 모듈

- node.js 에서 입출력 처리하는 모듈
- 인터페이스 객체 생성 후(`createInterface`), 실행시켜 사용(`prompt, on ...`)

**반복입력받는 코드**

```js
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

rl.setPrompt("명령을 입력하세요 > ");
rl.prompt();
rl.on("line", (line) => {
  rl.prompt();
}).on("close", () => {
  process.exit();
});
```
