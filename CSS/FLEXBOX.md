# FLEXBOX

## ✔️ flexbox를 사용해야하는 이유
기존 display 속성들은 모두 픽셀단위로 선언된 크기가 고정된다.
화면 크기가 달라딜 떄마다 미디어속성으로 이 크기를 각각 조절해야하는데, 이는 `flexbox`로 해결이 가능하다.

또한, `display:inline-block`로 정의된 엘리먼트를 원하는 위치에 놓기 위해 `margin`을 사용했다면, `flexbox`에서는 그럴 필요가 없다. 정렬하기 원하는 엘리먼트 상위에 flex container만 정의해두면 된다.

## ✔️ Rule fo Flexbox
> flexbox에서는 부모가 자식의 위치를 결정한다.

> flex continer의 `flex-direction` 기본값은 `row`이다.

### A. flex-container가 어떻게 자식 엘리먼트를 옮길 수 있을까?
A-1) **`flex-direction`**: 자식의 정렬 방향을 정의한다.
- row
- column

> ![flex axis](https://samanthaming.gumlet.io/flexbox30/4-flexbox-axes.jpg.gz?format=auto)

A-2) **`justify-content`**: flex-direction의 수평축(main axis)에 있는 모든 flex-child의 위치를 조절한다.
- center
- space-between
- space-around

A-3) **`align-items`**: flex-direction의 수직축(cross axis)에 있는 모든 flex-child의 위치를 조절한다.
- center
- flex-end
- flex-start
- stretch
- initial
- inherit
- unset
- baseline


### B. flex-child는 어떻게 자신의 위치를 조절할 수 있을까?
B-1) **`align-self`**: 부모의 cross-axis를 기준으로 자신의 위치를 조절한다.
- center

B-2) **`align-order`**: 부모의 main-axis 축에서 자신의 정렬위치를 조절한다.
> 모든 flexbox의 order 값은 `0`이다.

