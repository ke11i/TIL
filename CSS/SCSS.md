# SCSS
[🎀 SASS(Saas) Documentation](https://sass-lang.com/documentation/)

## ✔️ SCSS란? 
### CSS preprocessor: cool css code =={compile}==> normal css
- css 전처리기로 css가 동작하기 전에 사용되며, 일반 css에서 사용할 수 없는 반복문, 조건문, 연산 등을 사용할 수 있다. 즉 css를 일반적인 프로그램 언어처럼 사용할 수 있는 장점이 있다.
> 이전 프로젝트에서 Sass컴파일러로 scss를 사용한 적이 있는데, 이 둘은 하나의 컴파일러로 모두 사용 가능하다고 한다.(Sass의 상위호환이 SCSS) 결국 SCSS가 Sass의 공식적인 syntax로 둘은 같다고 봐도 무방

```javascript
// watch폴더 내 src/scss/styles.scss파일을 보고 있다가 compile된 css파일을 dist/css 폴더에 생성한다.
const routes = {
  css: {
    watch: "src/scss/*",
    src: "src/scss/styles.scss",
    dest: "dist/css"
  }
};
```

## ✔️ Rule fo SCSS

#### SCSS 파일을 만들때 파일명 앞에 `_`를 붙이는 것은 해당 파일이 css파일로 변환되지 않도록 하기 위함
**[compile 전]**
```shell
.
│── index.html
└── src
    └── scss
        │── _variables.scss
        └── style.scss
```

**[compile 후]**
```shell
.
│── index.html
└── dist
    └── css
        └── style.css
```

<br />

### 🎀 Variables: 자주 사용하는 속성 값(색상코드, 여백크그 등)을 변수화하여 사용해보자
- 변수명 앞에 `$`를 붙여준다.
```scss
/* [파일명]_variables.scss */
$backgroundColor: pink;
```
```scss
/* [파일명]style.scss */
@import '_variables';

body {
  background: $backgroundColor;
}

h1 {
  color: $backgroundColor;
}
```

<br/>

### 🎀 Nesting: 중첩해서 사용하기 
**[일반 CSS]**
```css
h1 {
  color: blue;
}

h1 button {
  color: red;
}
```

**[Nesting 사용한 SCSS]**
```scss
h1 {
  color: blue;
  button {
    color: red;
  }
}
```
- 부모 자식의 style을 다르게 하기 위해 굳이 class나 selector를 사용할 필요가 없어진다!
- hover와 같은 속성을 사용할 때, `&`만 사용할 수 있다.(계층 파악이 가능하므로!)
  ```scss
  h1 {
    /* &만 사용해서 선언 가능! */
    &hover {
      color: pink;
    }
  }
  /* 물론 일반적인 hover도 사용 가능 */
  h1:hover{
    color: pink;
  }
  ```

<br/>

### 🎀 Mixins: scss functionality를 사용할 수 있도록 해주는 기능이다.
> 변수, 조건문을 이용해서 각각 다른 속성을 부여하고 싶을 때 사용한다.

#### 1) `@mixin`을 이용해서 color값을 변수로 받아서 색상을 변경하는 함수를 만들어보자!
```scss
/* [파일명]_mixins.scss */
@mixin link($color)  {
  color: $color;
}
```
```scss
@import '_mixins';

a {
  margin-bottom: 10px;

  &:nth-child(odd){
    @include link(blue);
  }

  &:nth-child(even){
    @include link(red);
  }
}
```
<br/>

#### 2) `@if 조건 {} @else {}`를 사용해서 링크 색상을 변경해보자!
```scss
/* [파일명]_mixins.scss */
@mixin link($word)  {
  @if $word == 'odd' {
    color: blue;
  } @else {
    color:red;
  }
  ;
}
```
```scss
@import '_mixins';

a {
  margin-bottom: 10px;

  &:nth-child(odd){
    @include link("odd");
  }

  &:nth-child(even){
    @include link("even");
  }
}
```

<br/>

### 🎀 Extends: 같은 코드를 중복하고 싶지 않을때 사용한다.
> 여러 태그에 공통적으로 부여하고 싶은 속성을 하나로 묶어줄떄 사용한다.

#### `@extend`를 사용해서 링크와 버튼을 동일한 모양으로 만들어보자!
```html
<a href="#">Log In</a>
<button>Log In</button>
```
```scss
/* [파일명]_buttons.scss */
%button{
  font-family: inherit;
  border-radius: 7px;
  font-size:  12px;
  text-transform: uppercase;
  padding: 5px 10px;
  background-color: pink;
}
```
```scss
@import '_buttons';

a{
  @extend %button;
  text-decoration: none;
}

button{
  @extend %button;
  border:none;
}
```

<br/>

### 🎀 Awesome Mixins and Conclusions
> Mixin allows you to send information to the functions, variable data. Extends just adds CSS to another CSS

#### `@content`로 반응형 레이아웃 만들기
- **💡 (mixin)`@content`를 이용하여 반응형 함수 하나만 잘 만들어두면 프로젝트 어디에서나 대응이 가능하다.**
- 아래처럼 마디어쿼리를 적용하는 함수하나로 모든 태그 내에서 그때그때 적용하여 반응형을 만들 수 있디.
```scss
/* [파일명]_mixins.scss */
$minIphone: 500px;
$maxIphone: 690px;
$minTablet: $minIphone + 1;
$maxTablet: 1120;

@mixin responsive($device) {
  @if $device == 'iphone' {
    @media screen and (min-width: $minIphone) and (max-width:$maxIphone){
      @content;
    }
  }@else if $device == 'tablet'{
    @media screen and (min-width: $minTablet) and (max-width:$maxTablet){
      @content;
    }
  }@else if $device == 'iphone-l'{
    @media screen and (min-width: $minIphone) and (max-width:$maxIphone) and (orientation: landscape){
      @content;
    }
  }@else if $device == 'tablet-l'{
    @media screen and (min-width: $minTablet) and (max-width:$maxTablet) and (orientation: landscape){
      @content;
    }
  }
}
```
```scss
@import '_mixins';

h1 {
  color: red;
  // 각 
  @include responsive("iphone"){
    color:yellow;
  }
  @include responsive("iphone-l"){
    font-size: 60px;
  }
  @include responsive("tablet"){
    color:green;
  }
}
```

<br />

#### *그동안 사용했던 css 라이브러리들(chart, animation 등)은 SASS의 mixins와 variables 기능을 이용한 것임을 알 수 있다.*

> 'SCSS의 Mixins를 활용하여 나만의 UI 라이브러리 만들기'같은 프로젝트도 좋을 듯
> [참고하면 좋은 Mixins 라이브러리들](https://github.com/colourgarden/awesome-scss)