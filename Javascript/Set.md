# Set

- value 들로 이루어진 컬렉션(집합)
- Array와 달리 Set은 같은 value 를 2번 포함할 수 X

  → Set 에 이미 존재하는 값 추가 불가

### 메서드

- new Set(iterable) : 셋생성

  → 이터러블 객체를 전달받으면, 그 안의 값을 복사해 셋에 넣어줌

- set.add(value) : 값을 추가 + 셋 자신을 반환
- set.delete(value) : 값 제거

  → 셋 내에 값이 있어서 제거에 성공하면 true, 아니면 false를 반환

- set.has(value) : 셋 내에 값이 존재하면 true, 아니면 false를 반환

  → indexOf() 보다 빠름 (다만, index 이 존재하지 않기 때문에 index 로 value 로 접근할 수 X)

- set.clear() : 셋 비우기
- set.size : 셋에 몇 개의 값이 있는지 반환

> 셋 내에 동일한 값(value)이 있다면 set.add(value)을 아무리 많이 호출하더라도 아무런 반응이 없을 겁니다. 셋 내의 값에 중복이 없는 이유가 바로 이 때문이죠.

> 방문자 방명록을 만든다고 가정해 봅시다. 한 방문자가 여러 번 방문해도 방문자를 중복해서 기록하지 않겠다고 결정 내린 상황입니다. 즉, 한 방문자는 '단 한 번만 기록’되어야 합니다. 이때 적합한 자료구조가 바로 `셋`입니다.

```jsx
let set = new Set();

// 어떤 고객(john, mary)은 여러 번 방문
set.add({ name: "John" });
set.add({ name: "Pete" });
set.add({ name: "Mary" });
set.add({ name: "John" });
set.add({ name: "Mary" });

// 셋에는 유일무이한 값만 저장됨
alert(set.size); // 3

for (let user of set) {
  alert(user.name); // // John, Pete, Mary
}
```

```jsx
let setA = new Set();
let setB = new Set().add("a").add("b");
setB.add("c");
console.log(setB.size); // 3

console.log(setB.has("b")); // true

setB.delete("b");
console.log(setB.has("b")); // false

setB.clear();
console.log(setB.size); // 0
```
