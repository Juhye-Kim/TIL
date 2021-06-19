# `<script>`

## **`<script>`, `<script async>`, `<script defer>` 태그**

`<script>`

- html 파싱을 중지시키고 실행, js 파싱이 전부 끝난 후 HTML 파싱 재개

`<script async>`

- 파싱과 동시에, js 파싱도 병렬적으로 진행

`<script defer>`

- 파싱 중에 병렬적으로 js파일은 fetch 되고, 실행은 html파싱이 끝난 후에 됨
- 이 요소가 여러개 존재하면, 순서대로 수행됨

## **`<script>`를 `</body>`에 두는 이유**

브라우저는 HTML 파일을 위에서 아래로 한 줄씩 파싱한다. 그러다가 JS를 불러오는 <script>를 만나면 잠시 멈추고, JS 파싱이 끝나면 다시 시작한다.

- head같이 앞 부분에 넣으면, 무거운 파일인 경우에는 한참동안 미완성의 화면을 보여주게 됨
  - DOM 구조가 필요한 script면 에러도 날 수 있음
- body 앞에 넣으면, DOM은 완성된 상태라 이런 일을 방지할 수 있음
