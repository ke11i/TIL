# SCSS
[๐ SASS(Saas) Documentation](https://sass-lang.com/documentation/)

## โ๏ธ SCSS๋? 
### CSS preprocessor: cool css code =={compile}==> normal css
- css ์ ์ฒ๋ฆฌ๊ธฐ๋ก css๊ฐ ๋์ํ๊ธฐ ์ ์ ์ฌ์ฉ๋๋ฉฐ, ์ผ๋ฐ css์์ ์ฌ์ฉํ  ์ ์๋ ๋ฐ๋ณต๋ฌธ, ์กฐ๊ฑด๋ฌธ, ์ฐ์ฐ ๋ฑ์ ์ฌ์ฉํ  ์ ์๋ค. ์ฆ css๋ฅผ ์ผ๋ฐ์ ์ธ ํ๋ก๊ทธ๋จ ์ธ์ด์ฒ๋ผ ์ฌ์ฉํ  ์ ์๋ ์ฅ์ ์ด ์๋ค.
> ์ด์  ํ๋ก์ ํธ์์ Sass์ปดํ์ผ๋ฌ๋ก scss๋ฅผ ์ฌ์ฉํ ์ ์ด ์๋๋ฐ, ์ด ๋์ ํ๋์ ์ปดํ์ผ๋ฌ๋ก ๋ชจ๋ ์ฌ์ฉ ๊ฐ๋ฅํ๋ค๊ณ  ํ๋ค.(Sass์ ์์ํธํ์ด SCSS) ๊ฒฐ๊ตญ SCSS๊ฐ Sass์ ๊ณต์์ ์ธ syntax๋ก ๋์ ๊ฐ๋ค๊ณ  ๋ด๋ ๋ฌด๋ฐฉ

```javascript
// watchํด๋ ๋ด src/scss/styles.scssํ์ผ์ ๋ณด๊ณ  ์๋ค๊ฐ compile๋ cssํ์ผ์ dist/css ํด๋์ ์์ฑํ๋ค.
const routes = {
  css: {
    watch: "src/scss/*",
    src: "src/scss/styles.scss",
    dest: "dist/css"
  }
};
```

## โ๏ธ Rule fo SCSS

#### SCSS ํ์ผ์ ๋ง๋ค๋ ํ์ผ๋ช ์์ `_`๋ฅผ ๋ถ์ด๋ ๊ฒ์ ํด๋น ํ์ผ์ด cssํ์ผ๋ก ๋ณํ๋์ง ์๋๋ก ํ๊ธฐ ์ํจ
**[compile ์ ]**
```shell
.
โโโ index.html
โโโ src
    โโโ scss
        โโโ _variables.scss
        โโโ style.scss
```

**[compile ํ]**
```shell
.
โโโ index.html
โโโ dist
    โโโ css
        โโโ style.css
```

<br />

### ๐ Variables: ์์ฃผ ์ฌ์ฉํ๋ ์์ฑ ๊ฐ(์์์ฝ๋, ์ฌ๋ฐฑํฌ๊ทธ ๋ฑ)์ ๋ณ์ํํ์ฌ ์ฌ์ฉํด๋ณด์
- ๋ณ์๋ช ์์ `$`๋ฅผ ๋ถ์ฌ์ค๋ค.
```scss
/* [ํ์ผ๋ช]_variables.scss */
$backgroundColor: pink;
```
```scss
/* [ํ์ผ๋ช]style.scss */
@import '_variables';

body {
  background: $backgroundColor;
}

h1 {
  color: $backgroundColor;
}
```

<br/>

### ๐ Nesting: ์ค์ฒฉํด์ ์ฌ์ฉํ๊ธฐ 
**[์ผ๋ฐ CSS]**
```css
h1 {
  color: blue;
}

h1 button {
  color: red;
}
```

**[Nesting ์ฌ์ฉํ SCSS]**
```scss
h1 {
  color: blue;
  button {
    color: red;
  }
}
```
- ๋ถ๋ชจ ์์์ style์ ๋ค๋ฅด๊ฒ ํ๊ธฐ ์ํด ๊ตณ์ด class๋ selector๋ฅผ ์ฌ์ฉํ  ํ์๊ฐ ์์ด์ง๋ค!
- hover์ ๊ฐ์ ์์ฑ์ ์ฌ์ฉํ  ๋, `&`๋ง ์ฌ์ฉํ  ์ ์๋ค.(๊ณ์ธต ํ์์ด ๊ฐ๋ฅํ๋ฏ๋ก!)
  ```scss
  h1 {
    /* &๋ง ์ฌ์ฉํด์ ์ ์ธ ๊ฐ๋ฅ! */
    &hover {
      color: pink;
    }
  }
  /* ๋ฌผ๋ก  ์ผ๋ฐ์ ์ธ hover๋ ์ฌ์ฉ ๊ฐ๋ฅ */
  h1:hover{
    color: pink;
  }
  ```

<br/>

### ๐ Mixins: scss functionality๋ฅผ ์ฌ์ฉํ  ์ ์๋๋ก ํด์ฃผ๋ ๊ธฐ๋ฅ์ด๋ค.
> ๋ณ์, ์กฐ๊ฑด๋ฌธ์ ์ด์ฉํด์ ๊ฐ๊ฐ ๋ค๋ฅธ ์์ฑ์ ๋ถ์ฌํ๊ณ  ์ถ์ ๋ ์ฌ์ฉํ๋ค.

#### 1) `@mixin`์ ์ด์ฉํด์ color๊ฐ์ ๋ณ์๋ก ๋ฐ์์ ์์์ ๋ณ๊ฒฝํ๋ ํจ์๋ฅผ ๋ง๋ค์ด๋ณด์!
```scss
/* [ํ์ผ๋ช]_mixins.scss */
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

#### 2) `@if ์กฐ๊ฑด {} @else {}`๋ฅผ ์ฌ์ฉํด์ ๋งํฌ ์์์ ๋ณ๊ฒฝํด๋ณด์!
```scss
/* [ํ์ผ๋ช]_mixins.scss */
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

### ๐ Extends: ๊ฐ์ ์ฝ๋๋ฅผ ์ค๋ณตํ๊ณ  ์ถ์ง ์์๋ ์ฌ์ฉํ๋ค.
> ์ฌ๋ฌ ํ๊ทธ์ ๊ณตํต์ ์ผ๋ก ๋ถ์ฌํ๊ณ  ์ถ์ ์์ฑ์ ํ๋๋ก ๋ฌถ์ด์ค๋ ์ฌ์ฉํ๋ค.

#### `@extend`๋ฅผ ์ฌ์ฉํด์ ๋งํฌ์ ๋ฒํผ์ ๋์ผํ ๋ชจ์์ผ๋ก ๋ง๋ค์ด๋ณด์!
```html
<a href="#">Log In</a>
<button>Log In</button>
```
```scss
/* [ํ์ผ๋ช]_buttons.scss */
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

### ๐ Awesome Mixins and Conclusions
> Mixin allows you to send information to the functions, variable data. Extends just adds CSS to another CSS

#### `@content`๋ก ๋ฐ์ํ ๋ ์ด์์ ๋ง๋ค๊ธฐ
- **๐ก (mixin)`@content`๋ฅผ ์ด์ฉํ์ฌ ๋ฐ์ํ ํจ์ ํ๋๋ง ์ ๋ง๋ค์ด๋๋ฉด ํ๋ก์ ํธ ์ด๋์์๋ ๋์์ด ๊ฐ๋ฅํ๋ค.**
- ์๋์ฒ๋ผ ๋ง๋์ด์ฟผ๋ฆฌ๋ฅผ ์ ์ฉํ๋ ํจ์ํ๋๋ก ๋ชจ๋  ํ๊ทธ ๋ด์์ ๊ทธ๋๊ทธ๋ ์ ์ฉํ์ฌ ๋ฐ์ํ์ ๋ง๋ค ์ ์๋.
```scss
/* [ํ์ผ๋ช]_mixins.scss */
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
  // ๊ฐ 
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

#### *๊ทธ๋์ ์ฌ์ฉํ๋ css ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ค(chart, animation ๋ฑ)์ SASS์ mixins์ variables ๊ธฐ๋ฅ์ ์ด์ฉํ ๊ฒ์์ ์ ์ ์๋ค.*

> 'SCSS์ Mixins๋ฅผ ํ์ฉํ์ฌ ๋๋ง์ UI ๋ผ์ด๋ธ๋ฌ๋ฆฌ ๋ง๋ค๊ธฐ'๊ฐ์ ํ๋ก์ ํธ๋ ์ข์ ๋ฏ
> [์ฐธ๊ณ ํ๋ฉด ์ข์ Mixins ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ค](https://github.com/colourgarden/awesome-scss)