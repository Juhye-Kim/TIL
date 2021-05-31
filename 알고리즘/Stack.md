# Stack

### 1. 개념

데이터(data)를 순서대로 쌓는 자료구조

- 입출력이 한 방향으로 이루어짐 (제한적 접근)
- 후입선출, LIFO(Last In First Out), FILO(First In Last Out)

### 2. 예시

브라우저 뒤로 가기, 앞으로 가기

1. 새로운 페이지 접속시, 현재 페이지를 Prev Stack에 보관
2. 뒤로 가기 클릭시, 현재 페이지는 Next Stack에 보관하고, Prev Stack의 가장 마지막에 있는 페이지를 가져옴
3. 앞으로 가기 클릭시, Next Stack의 마지막에 있는 페이지를 가져옴
4. 마지막으로 현재 페이지를 Prev Stack에 보관
