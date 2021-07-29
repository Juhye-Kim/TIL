## fs 모듈

### 폴더 생성, 존재여부 체크

- fs.existsSync(dir) : 존재여부 체크
- fs.mkdirSync(dir) : 폴더 생성

```jsx
if (!fs.existsSync(`local/${repoName}`)) {
  fs.mkdirSync(`local/${repoName}`);
  if (fs.existsSync(`local/${repoName}`)) {
    fs.mkdirSync(`local/${repoName}/git`);
  }
}
```

### 파일 읽기

```jsx
var fs = require("fs");
fs.readFile("sample.txt", "utf8", function (err, data) {
  console.log(data);
});
```

### 파일 목록 가져오기

- 배열형태로 리턴

```jsx
var fs = require("fs");
fs.readdir("./test", function (err, filelist) {
  console.log(filelist);
});
```

### 파일 생성

```jsx
var fs = require("fs");
fs.writeFile("파일경로/파일명", "파일에들어갈내용", function (err) {
  err === null ? 성공 : 실패;
});
```

### 파일명 수정

```jsx
fs.rename(oldPath, newPath, callback);
```

### 파일 삭제

```jsx
fs.unlink(Path, callback);
```

### 파일 복제

- `fs.open` : 파일 열기 (a 옵션 = 없으면 생성하고, 있으면 원래꺼 쓴다)
- readFile로 읽어온 내용을 writeFile로 다른 파일에 써줌

```jsx
fs.open(기존파일경로, "a", (err, _) => {
  fs.readFile(기존파일경로, "utf8", (err, data) => {
    let prev = {};
    if (data) prev = JSON.parse(data);
    fs.writeFile(옮길파일경로, JSON.stringify(prev), "utf8", (err) => {
      if (err) console.error(err);
    });
  });
});
```
