# FLEXBOX

## ✔️ flexbox를 사용해야하는 이유
기존 display 속성들은 모두 픽셀단위로 선언된 크기가 고정된다.

화면 크기가 달라질 떄마다 미디어속성으로 이 크기를 각각 조절해야하는데, 이는 `flexbox`로 해결이 가능하다.

또한, `display:inline-block`로 정의된 엘리먼트들의 간격을 조절하기 위해 `margin`을 사용해야 했다면, `flexbox`에서는 그럴 필요가 없다.

정렬하기 원하는 엘리먼트 상위에 flex container만 정의해두면 된다.

## ✔️ Rule fo Flexbox
> flexbox에서는 부모가 자식의 위치를 결정한다.

> flex 선언된 continer의 `flex-direction` 기본값은 `row`이다.

### 💡 conatiner, child에서 사용되는 속성
```html
<div class="container" style="display:flex;">
  <div class="child">1</div>
  <div class="child">2</div>
</div>
```
|속성|설명|continer| child |
|---|---|:---:|:---:|
|flex-direction|기본값: row|O||
|justify-content|main axis상의 child 정렬|O||
|align-items|cross-axis상의 child 정렬|  |  |
|align-self|부모의 cross-axis를 기준으로 자신의 위치|  |O|
|align-items|부모의 main-axis를 기준으로 자신의 위치|  |O|
|flex-wrap|자식의 속성을 유지여부|O||
|align-content|main-axios사이의 줄간격 조절|O||


### A. flex-container가 어떻게 자식 엘리먼트를 옮길 수 있을까?
A-1) **`flex-direction`**: 자식의 정렬 방향을 정의한다.
- row
- column

> ![flex axis](https://samanthaming.gumlet.io/flexbox30/4-flexbox-axes.jpg.gz?format=auto)
> *-reverse는 각각의 속성에서 main-axis만 reverse된다.

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

B-2) **`align-order`**: 부모의 main-axis 축에서 오름차순으로 자신의 정렬 순서를 조절한다.
> 모든 flexbox의 order 값은 `0`이다.



#### ***flex container 아래에 있는 child에 width값이 선언되어 있어도 기본적으로 한줄로 정렬된다. 즉, child에 선언된 width보다 부모의 justify-content 속성이 우선되어 정렬된다.***

### C. flex-child의 속성을 유지할 수 있을까?
C-1) **`flex-wrap`**: 부모쪽에서 선언되며, 자식의 속성을 유지할지를 정의한다.
> 강제로 한줄에 배치되게 할 것인지, 또는 가능한 영역 내에서 벗어나지 않고 여러행으로 나누어 표현 할 것인지 결정하는 속성
- wrap : child의 크기를 유지
- nowrap : main-axios에 한줄로 정렬되게 자식의 크기를 변경

#### D. flex-child가 wrap속성으로 여러줄로 출력될 때, 각 줄 사이의 간격을 어떻게 조절 할 수 있을까?
D-1) **`align-content`**: main-axis 방향으로 child가 여러 줄로 정렬될때, 그 간격을 조절한다.
> `align-items`은 한줄을 기준으로 사용되며, `align-content`는 두 줄 이상부터 사용된다.


