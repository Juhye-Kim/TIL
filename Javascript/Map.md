# 1. Map

- key에 다양한 자료형 허용

### 주요 메서드

- new Map() : 맵 생성
- map.set(key, value) : key로 value를 저장
- map.get(key) : key에 해당하는 값 가져오기 (존재X → undefined)
- map.has(key) : key가 존재하면 true, 존재하지 않으면 false 반환
- map.delete(key) : key에 해당하는 값을 삭제
- map.clear() : 맵 안의 모든 요소 제거
- map.size : 요소의 개수 반환

> **map[key]는 Map을 쓰는 바른 방법이 아닙니다.**
> map[key] = 2로 값을 설정하는 것 같이 map[key]를 사용할 수 있긴 합니다. 하지만 이 방법은 map을 일반 객체처럼 취급하게 됩니다. 따라서 여러 제약이 생기게 되죠.
> map을 사용할 땐 map전용 메서드 set, get 등을 사용해야만 합니다.

```jsx
let map = new Map();

map.set("1", "str1"); // 문자형 키
map.set(1, "num1"); // 숫자형 키
map.set(true, "bool1"); // 불린형 키

// 객체 : 키를 문자형으로 변환, 맵 : 타입 변환 X
alert(map.get(1)); // 'num1'
alert(map.get("1")); // 'str1'
alert(map.size); // 3
```

```jsx
let me = new Map();
me.set('name', 'kevin');
me.set('age', 28);
console.log(me.get('age'); // 28

// 대괄호를 사용해서 map 을 선언하는 방법
const roomTypeMap = new Map(
  [
    ["01", "원룸(오픈형)"],
    ["02", "원룸(분리형)"],
    ["03", "원룸(복층형)"],
    ["04", "투룸"],
    ["05", "쓰리룸"]
  ]
);

let you = new Map().set('name', 'paul').set('age', 34);

console.log(you.get('name')); // 'paul'

console.log(me.has('name')); // true

console.log(you.size); // 2

me.delete('age');
console.log(me.has('age')); // false

you.clear();
console.log(you.size); // 0
```

### 체이닝

`map.set` 은 호출할 때마다 맵 자신이 반환되기 때문에, 이를 이용해 '체이닝(chaining)' 가능

```jsx
map.set("1", "str1").set(1, "num1").set(true, "bool1");
```

**for..of 로 순회 가능**

- `map.keys()` : 모든 키를 모은 이터러블 객체 반환
- `map.values()` : 모든 값을 모은 이터러블 객체를 반환
- `map.entries()` : 모든 `[키, 값]` 쌍을 모은 이터러블 객체 반환

```jsx
let recipeMap = new Map([
  ["cucumber", 500],
  ["tomatoes", 350],
  ["onion", 50],
]);

for (let vegetable of recipeMap.keys()) {
  alert(vegetable); // cucumber, tomatoes, onion
}

for (let amount of recipeMap.values()) {
  alert(amount); // 500, 350, 50
}

for (let entry of recipeMap) {
  // = recipeMap.entries()
  alert(entry); // cucumber,500 ...
}
```

### Map vs Object

- Object 의 key 는 string, symbol 만 가능

  Map 은 어떤 값도 가능

- Object 에서는 크기를 추적해서 알 수 있지만

  Map 은 size로 바로 얻을 수 있음

### [Object.fromEntries: 맵 → 객체](https://ko.javascript.info/map-set#ref-616)

Object.fromEntries : 각 요소가 `[키, 값]` 쌍인 배열을 객체로 바꿔줌

```jsx
let prices = Object.fromEntries([
  ["banana", 1],
  ["orange", 2],
  ["meat", 4],
]);
// now prices = { banana: 1, orange: 2, meat: 4 }

alert(prices.orange); // 2
```

```jsx
let map = new Map();
map.set("banana", 1);
map.set("orange", 2);
map.set("meat", 4);

let obj = Object.fromEntries(map.entries());
let obj = Object.fromEntries(map); // 위에랑 같은말
// obj = { banana: 1, orange: 2, meat: 4 }

alert(obj.orange); // 2
```
