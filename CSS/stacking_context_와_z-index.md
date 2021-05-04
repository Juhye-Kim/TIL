# Stacking Contexts, z-index

[What no one told you about z-index](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/)

### 기본적인 쌓임 순서

- HTML에 나타나는 순서와 같음
- position 속성을 요소들에 사용 시,
  - position 속성이 <u>있는</u> 모든 요소(+ 자식 요소)가 <u>없는</u> 요소들보다 앞에 나타남
  - position 속성이 있다 = static 말고 relative, absolute 같은 것들

### z-index

- z-index 값이 더 높은 요소가 앞쪽에 옴
  - z-index는 오직 position 속성이 있는 요소에서만 작동
  - z-index 값은 쌓임 맥락을 만들 수 있음

### 쌓임 맥락(Stacking Contexts)

- 모든 쌓임 맥락에는, root 요소인 HTML 존재
- 쌓임 맥락이 새로 만들어질 때, 자식 요소들이 순서에서 특정 범위를 벗어나지 못하도록 한계 지정
  - 맨 뒤의 쌓임 맥락 요소는 앞쪽 쌓임 맥락 요소보다 앞에 올 수 x!

### 쌓임 맥락 생성 조건

- 쌓임 맥락은 다음 셋 중 하나에 속할 때 만들어진다.
  1. 문서의 최상위 요소일 때 (html)
  2. position 값이 static이 아니고, z-index가 auto가 아닐 때
  3. opacity 값이 1보다 작을 때
- 모바일 웹킷 & 크롬 22 이상에서, position: fixed는 무조건 새로운 쌓임 맥락 생성 (z-index가 auto여도)

### 같은 단계의 쌓임 맥락에서의 순서

1. 쌓임 맥락의 root 요소
2. position 값이 있고, z-index 값이 음수인 요소(와 자식들)
3. position 값이 없는 요소
4. position 값이 있고 z-index 값이 auto인 요소(와 그 자식들)
5. position 값이 있고 z-index 값이 양수인 요소(와 그 자식들)

- z-index가 음수 + position 속성이 있는 요소
  - 쌓임 맥락에서 맨 먼저 쌓임 (제일 뒤)
  - 같은 맥락 안에 있는 자기 부모보다 뒤에 올 수도
    - 물론 맥락의 최상위 요소보다 뒤로 갈 수는 x
