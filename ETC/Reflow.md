## Reflow
html 요소의 크기, 위치 등 레이아웃 수치를 수정하면 자식이나 부모 노드들이 영향을 받을 수 있는데, 이 경우 Layout 과정을 다시 수행
- Render Tree와 각 요소들의 크기와 위치를 다시 계산하는 과정 = Reflow

**Reflow가 발생하는 경우**
- 페이지 초기 렌더링 시(최초 Layout 과정)
- 윈도우 리사이징시
- 노드 추가, 제거
- 요소 위치, 크기 변경 
- 폰트, 이미지 크기 변경

**Reflow 방지하기**
1. 사용하지 않는 노드엔 visibilty: invisible 보다 display: none 사용
  - visibility invisible는 레이아웃 공간을 차지
  - display none는 Layout 공간을 차지하지 않아 Render Tree에서 제외됨
2. Reflow 발생 속성 사용 피하기 (position, width, heignt, margin, padding...)
3. 프레임 줄이기
