# z-index가 없는 경우의 쌓이는 순서

[mdn 참고](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Positioning/Understanding_z_index/Stacking_without_z-index)

모든 엘리먼트들에 z-index가 지정되지 않은 경우, 다음 순서로 **아래**에서 **위**로 쌓인다.

1. root 엘리먼트의 배경, 테두리
2. 자식 엘리먼트들 - HTML 등장 순서대로
3. position이 지정된 자식 엘리먼트들 - HTML 등장 순서대로
