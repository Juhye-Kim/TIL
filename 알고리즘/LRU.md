# 캐시교체 알고리즘: LRU(Least Recently Used)

### LRU

- 사용하는 캐시에서 새로운 데이터가 발생했을 때

  1. 가장 오래전에 사용된 데이터를 제거하고
  2. 새로운 데이터를 삽입하는 알고리즘

### 구현방법

1. 새로운 데이터가 들어온 경우
   - 캐시에 넣기
2. 캐시가 가득찼다면
   - 가장 오래된 데이터 제거 + 넣기
3. 존재하는 데이터가 들어온 경우
   - 해당 데이터를 꺼내기 + 최근 데이터 위치로 보내기
