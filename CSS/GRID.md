# GRID
[์ค์ต][๐ธ Grid Garden](https://cssgridgarden.com/#ko)

## โ๏ธ GRID๋ฅผ ์ฌ์ฉํด์ผํ๋ ์ด์ 
Flexbox๋ฅผ ์ด์ฉํด์ 3x2 ํ๋ฉด์ ๊ทธ๋ฆฐ๋ค๊ณ  ์๊ฐํด๋ณด์. ์๋์ฒ๋ผ ์ ๋ ฌ๋๋ ํํ๋ฅผ ์ป๊ฒ๋๋ค.

```css
.container{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.child{
  flex-basis: 30%;
  background: peru;
  color: white;
}
```
```html
<div class="father">
  <div class="child">1</div>
  <div class="child">2</div>
  <div class="child">3</div>
  <div class="child">4</div>
  <div class="child">5</div>
</div>
```
![flexbox์ ๋ฌธ์ ](./asset/grid_01.png)

#### ์ฆ, flexbox์์ ์ข์ฐ๋ฐฐ์น, ์ค์๋ฐฐ์น๋ ์ฝ์ง๋ง gridํํ๋ฅผ ๋ง๋๋ ๊ฒ์ ์ด๋ ต๋ค. ์์ฐจ์ ์ผ๋ก ์ผ์ชฝ ์ ๋ ฌ๋์ด ๋์ด๋๋ grid ํ๋ฉด์ ์ด๋ป๊ฒ ๊ทธ๋ฆด ์ ์์๊น?

<br/>

## โ๏ธ Rule fo Grid
> Gird ์์ฑ์ container์์ ์ ์๋๋ค.
> ```css
> .container{
>  display:grid;
> }
> ```


### 1) grid-container์์ row, column์ ์ค์ ํ๋ ๋ฐฉ๋ฒ

#### ๐ธ **`grid-template-columns`**: grid column์ ๊ฐ์/๋์ด๋ฅผ ์ ์ํ๋ค.

#### ๐ธ **`grid-template-rows`**: grid row์ ๊ฐ์/๋์ด๋ฅผ ์ ์ํ๋ค.

![grid ๋ ์ด์์](./asset/grid_02.png)

```css
.continer{
  display:grid;
  /* grid column 3๊ฐ์ ๊ฐ ๋์ด๋ฅผ ์ง์ ํ๋ค. */
  grid-template-columns: 40px 80px 160px;
  /* grid row 2๊ฐ์ ๊ฐ ๋์ด๋ฅผ ์ง์ ํ๋ค. */
  grid-template-rows: 40px 60px;
}
```
> `repeat(n, m)`: n๊ฐ์ mํฌ๊ธฐ์ column or row๋ฅผ ์์ฑํ๋ค.
> - `grid-template-columns: repeat(3, 100px)`
> 
> `auto`: row or column์ ์ฌ๋ฐฑ์ ๋จ๊ธฐ์ง ์๊ณ  grid๋ฅผ ๋ง๋ ๋ค. ์ฆ, auto ์์ญ์ container์ ํฌ๊ธฐ ๋ณํ์ ๋ฐ์ํ์ฌ ํฌ๊ธฐ๊ฐ ๋ณ๊ฒฝ๋๋ค.
> - `grid-template-columns: auto 300px`

<br/>

### 2) grid ์ฌ์ด์ ๊ฐ๊ฒฉ์ ์กฐ์ ํ๋ ๋ฐฉ๋ฒ

![grid ๋ ์ด์์](./asset/grid_03.png)

#### ๐ธ **`column-gap`**: grid column ์ฌ์ด์ ๊ฐ๊ฒฉ์ ์กฐ์ ํ๋ค.
```css
.continer{
  display:grid;
  grid-template-columns: 40px 80px 160px;
  grid-template-rows: 40px 60px;
  /* grid column ์ฌ์ด์ ๊ฐ๊ฒฉ */
  column-gap:10px;
}
```

#### ๐ธ **`row-gap`**: grid row ์ฌ์ด์ ๊ฐ๊ฒฉ์ ์กฐ์ ํ๋ค.
```css
.continer{
  display:grid;
  grid-template-columns: 40px 80px 160px;
  grid-template-rows: 40px 60px;
  /* grid row ์ฌ์ด์ ๊ฐ๊ฒฉ */
  row-gap:10px;
}
```

#### ๐ธ **`gap`**: grid ์ฌ์ด์ ๊ฐ๊ฒฉ์ ์กฐ์ ํ๋ค.
- `gird: {row} {column};`: ๊ฐ๊ฐ ์ ์ ๊ฐ๋ฅ

```css
.continer{
  display:grid;
  grid-template-columns: 40px 80px 160px;
  grid-template-rows: 40px 60px;
  /* grid row & column ์ฌ์ด์ ๊ฐ๊ฒฉ */
  gap:10px;
}
```

<br/>

### 3) grid๋ก ํํ๋ฆฟ ์์ญ์ ์ ์ํ์
#### ๐ธ **`grid-template-areas`**: grid ํํ๋ฆฟ ๋ ์ด์์์ ์ ์ํ๋ค.
- ์ค๋ง๋ค ๋ฐ์ดํ๋ก ๊ตฌ๋ถ
- ์ฌ๊ฐํ์ผ๋ก ์ด์ด์ง ์์ญ์๋ง ์ ํจ('ใฑ'๋ก ์ด์ด์ง ์์ญ์ ์ ์ฉ๋์ง ์์)
- ๋น์ด์๋ ์์ญ์ ํ๊ธฐํ๊ณ  ์ถ์ ๋ `.`์ ์ฌ์ฉํ๋ค.
  ![grid ๋ ์ด์์](./asset/grid_05.png)

  ```css
  .continer{
    display: grid;
    grid-template-columns: repeat(4, 50px);
    grid-template-rows: repeat(4, 50px);
    grid-template-areas:
      "header header header header"
      "content . . nav"
      "content . . nav"
      "footer footer footer footer";
  }
  ```

#### ๐ธ **`grid-area`**: grid ์์ญ์ ์ด๋ฆ์ ์ ์ํ๋ค.
- ๋ฐ์ดํ ์ฌ์ฉํ์ง ์์
- ํด๋์ค ์ด๋ฆ๊ณผ ๋ณ๊ฐ

```css
.container{
  display: grid;
  grid-template-columns: repeat(4, 50px);
  grid-template-rows: repeat(4, 50px);
  grid-template-areas:
    "header header header header"
    "content content content nav"
    "content content content nav"
    "footer footer footer footer";
}

.header{
  background: #2ecc71;
  /* grid-area๋ ๋ฐ์ดํ๋ก ํ์ ์ํจ */
  grid-area: header;
}

.content{
  background: #3498db;
  grid-area: content;
}

.nav{
  background: #8e44ad;
  grid-area: nav;
}

.footer{
  background: #f39c12;
  grid-area: footer;
}
```
```html
<body>
  <div class="container">
      <div class="header">.header</div>
      <div class="content">.content</div>
      <div class="nav">.nav</div>
      <div class="footer">.footer</div>
  </div>
</body>
```
์ ์ฝ๋๋ฅผ ๋๋ ค๋ณด๋ฉด ์๋์ผ๋ก grid ์์ญ์ด ์ฑ์์ง๋ ๊ฒ์ ํ์ธํ  ์ ์๋ค.

![grid ๋ ์ด์์](./asset/grid_04.png)


### 4) column๊ณผ row์ ์ ๋ ฌ ์์น๋ฅผ ์ง์ ํด์ ์ ๋ ฌํด๋ณด์.
> grid์ ๋ฒํธ๋ 1๋ถํฐ ์์ํ๋ค.

#### ๐ธ **`grid-column-start: n`**: n๋ฒ์งธ column์์ ์์
#### ๐ธ **`grid-column-end: m`**: m๋ฒ์งธ column์ ์์ ์ด์ (n-1๋ฒ์งธ)์์ ๋๋จ์ ์ ์
- ์ฆ, grid ์๋ฆฌ๋ฒํธ์ ํฌ๊ธฐ๋ m-n์ด ๋๋ค.(n, m >= 1)

  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(4, 50px);
    grid-template-rows: repeat(4, 50px);
  }

  .header {
    background: #2ecc71;
    grid-column-start: 1;
    grid-column-end: 3;
  }
  ```
  ![grid ๋ ์ด์์](./asset/grid_06.png)

#### ๐ธ **`grid-row-start: n`**: n๋ฒ์งธ row์์ ์์
#### ๐ธ **`grid-row-end: m`**: m๋ฒ์งธ row์ ์์ ์ด์ (n-1๋ฒ์งธ)์์ ๋๋จ์ ์ ์

#### `grid-template-areas`๋ก ๋ง๋  ๋ ์ด์์์ `grid-column-*`, `grid-row-*`๋ฅผ ์ด์ฉํด ์ ๋ ฌํด๋ณด์!

```css
.header {
  background: #2ecc71;
  grid-column-start: 1;
  grid-column-end: 5;
}

.content {
  background: #3498db;
  grid-column-start: 1;
  grid-column-end: 4;
  grid-row-start: 2;
  grid-row-end: 4;
}

.nav {
  background: #8e44ad;
  grid-row-start: 2;
  grid-row-end: 4;
}

.footer {
  background: #f39c12;
  grid-column-start: 1;
  grid-column-end: 5;
}
```

![grid ๋ ์ด์์](./asset/grid_07.png)

<br />

### [shortcut] ๋ ๊ฐ๋จํ๊ฒ column๊ณผ row์ ์ ๋ ฌ ์์น๋ฅผ ์ง์ ํด์ ์ ๋ ฌํด๋ณด์.
#### ๐ธ **`grid-column: {start} / {end}`**: start ~ end ์ฌ์ด์ column์ ์ฐจ์งํ๋ค.
#### ๐ธ **`grid-row: {start} / {end}`**: start ~ end ์ฌ์ด์ row๋ฅผ ์ฐจ์งํ๋ค.
```css
.content {
  background: #3498db;
  grid-column: 1 / 4;
  grid-row: 2 / 4;
}
```

> #### ๋์์๋ถํฐ line ์ธ๊ธฐ
> ๊ทธ๋ฆฌ๋๋ ์์์๋ถํฐ ์ธ๋ฉด 1,2,3,4,... ์์ด์ง๋ง ๋ค์์๋ถํฐ ์ธ๋ฉด -1, -2, -3,...๋ ๊ฐ๋ฅํ๋ค.
> `grid-column: 1 / -2;` => [O,O,O,X]

> #### span ์ฌ์ฉํ๊ธฐ
> span์ ๋น์ด์๋ gird ์์ญ๋ถํฐ ์ผ๋ง๋ ๋ ์ฑ์ธ์ง๋ฅผ ๊ฒฐ์ ํ๋ค.
> `grid-column: span 3;` => [O,O,O,X]
> - span์ ์์์ ์ด ๋ชํํ  ๋๋ ๋ฌธ์ ๊ฐ ๋์ง ์ํ๋ง ๋ถ๋ชํํ  ๋ ์๊ฐ์ฒ๋ผ ๋ฐฐ์ด๋์ง ์๋๋ค. ์๋์ฒ๋ผ ์์์ ์ ์จ์ฃผ์!
> `grid-column: {start} / span {cell count};`

```css
.header {
  background: #2ecc71;
  grid-column: 1 / -1;
}

.content {
  background: #3498db;
  grid-column: 1 / -2;
  /* grid-row: span 2; ์์์ ์ด nav๋ ๊ฒน์ณ์ ๋ชจ์์ด ๊นจ์ง! */
  grid-row: 2 / span 2;
}

.nav {
  background: #8e44ad;
  grid-row-start: 2;
  grid-row-end: 4;
}

.footer {
  background: #f39c12;
  grid-column: span 4;
}
```
> ### [shortcut] `grid-area: {grid-row-start} {grid-column-start} { grid-row-end} {grid-column-end}`
> ```css
> .header{
>   grid-area: 1 / 2 / 4 / -1;
> }
> ```
> ![grid ๋ ์ด์์](./asset/grid_21.png)


<br/>

### 5) fraction์ ์ด์ฉํ์ฌ grid ์์ญ์ ํฌ๊ธฐ๋ฅผ ๋๋ ๋ณด์!
#### ๐ธ `fraction`: grid์ ์ฌ์ฉ๊ฐ๋ฅํ ๊ณต๊ฐ ์ ์ฒด๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํ ๋จ์์ด๋ค.
```css
  .container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
```
![grid ๋ ์ด์์](./asset/grid_08.png)

- `fraction`์ grid๋ก ๋ฐ์ํ ๋ ์ด์์์ ๊ทธ๋ฆด๋ ์ ์ฉํ๋ค.
> ```css
> .container {
>   display: grid;
>   grid-template-columns: 4fr 1fr 1fr 1fr;
> }
> ```
> ![grid ๋ ์ด์์](./asset/grid_09.png)


#### โป grid์ ๋์ด๋ฅผ ์ง์ ํ์ง ์์ผ๋ฉด ๊ธฐ๋ณธ์ ์ผ๋ก ๋์ด๋ 0์ด๋ค. ๋ง์ฝ row์ fraction์ ์ฌ์ฉํ๊ฒ ๋๋ฉด, ์ฌ์ฉ๊ฐ๋ฅํ ๋์ด ์ ์ฒด(0px)๋ฅผ ์ก๊ฒ๋๋ฏ๋ก grid ์์ดํ์ด ํ๋ฉด์์ ์ฌ๋ผ์ง๋ค. ๊ทธ๋ฌ๋ฏ๋ก row์ fraction์ ์ฐ๊ณ  ์ถ๋ค๋ฉด ๋ฐ๋์ grid container์ height๋ฅผ ์ค์ ํด์ฃผ์!

#### ๐ธ `grid-template: "{gird-area}" {row size} / {column sizw}`
- ๋จ repeatํจ์๋ ์ฌ์ฉํ  ์ ์๋ค.

```css
.container{
  display: grid;
  width: 50%;
  height: 10vh;
  grid-template:
    "header header header header" 1fr
    "content content content nav" 2fr
    "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr;
}

.header{
  background: #2ecc71;
  grid-area: header;
}

.content{
  background: #3498db;
  grid-area: content;
}

.nav{
  background: #8e44ad;
  grid-area: nav;
}

.nav{
  background: #f39c12;
  grid-area: footer;
}
```
```html
<body>
  <div class="container">
      <div class="header">.header</div>
      <div class="content">.content</div>
      <div class="nav">.nav</div>
      <div class="footer">.footer</div>
  </div>
</body>
```
![grid ๋ ์ด์์](./asset/grid_10.png)

<br />

### 6) Place Items ์์ฑ์ ์ด์ฉํ์ฌ grid cell์์ ๊ฐ grid item์ ํฌ๊ธฐ์ ์ ๋ ฌ์ ์ง์ ํด๋ณด์! 
#### ๐ธ `justify-items`: gird cell์์ item์ **์ํ์ ๋ ฌ**์ ์ง์ ํ๋ค.
#### ๐ธ `align-items`: gird cell์์ item์ **์์ง์ ๋ ฌ**์ ์ง์ ํ๋ค.
- stretch: gird cell์์ญ์ ๊ฐ๋ ์ฑ์ด๋ค.(๊ธฐ๋ณธ๊ฐ)
- start: grid cell ์์ญ ์์์ ์ ์ ๋ ฌ
- end: grid cell์์ญ ๋์ ์ ์ ๋ ฌ
- center: grid cell ์์ญ ๊ฐ์ด๋ฐ ์ ๋ ฌ


```css
.container{
  display: grid;
  width: 50%;
  height: 10vh;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 1fr);
  justify-items: start;
  align-items: end;
}
```
![grid ๋ ์ด์์](./asset/grid_11.png)

> [์ฃผ์]grid item์ ํฌ๊ธฐ๊ฐ ์ง์ ๋ ๊ฒฝ์ฐ, stretch๋ ์ ์ฉ๋์ง ์๋๋ค!
> ```css
> .container {
>   /* ์๋ถ๋ถ ์๋ต */
>   justify-items: stretch;
>   align-items: stretch;
> }
> .container > div {
>   width: 50px;
>   height: 50px;
> }
> ```
> ![grid ๋ ์ด์์](./asset/grid_12.png)

#### ๐ธ[Shortcut] `place-items: {align-items} {justify-items}`
```css
.container{
  /* ์๋ถ๋ถ ์๋ต */
  place-items: start center;
}
```
![grid ๋ ์ด์์](./asset/grid_13.png)

<br />

#### *Place Items๊ฐ grid cell ์์ item์ ๋ํ ์์ฑ์ด์๋ค๋ฉด, Place Content๋ gird์ ๋ํ ์์ฑ์ ์ ์ํ๋ค.*

### 7) Place Content ์์ฑ์ ์ด์ฉํ์ฌ grid์ ์์น๋ฅผ ์ ์ํด๋ณด์
#### ๐ธ `justify-content`: gird ์์ฒด์ **์ํ์ ๋ ฌ**์ ์ง์ ํ๋ค.
> ๊ฒ์ ์ ์์ญ์ ํ์ธํด๋ณด๋ฉด grid element(container) ์์ฒด์ ํฌ๊ธฐ๋ ๋ณํ์ง ์๋๋ค. ๊ทธ ๋ด๋ถ์ ๋ค์ด๊ฐ๋ grid์ ์์น๋ง ์กฐ์ ํ๋ ์์ฑ์ด๋ค.
> ```css
> .container {
>   /* ์๋ถ๋ถ ์๋ต */
>   justify-content: center;
>   background-color: black;
> }
> ```
> ![grid ๋ ์ด์์](./asset/grid_14.png)

#### ๐ธ `align-content`: gird ์์ฒด์ **์์ง์ ๋ ฌ**์ ์ง์ ํ๋ค.
- start: grid๋ฅผ container์ ์์์ ์ ์ ๋ ฌ
- end: grid๋ฅผ container์ ๋์ ์ ์ ๋ ฌ
- center: grid๋ฅผ container์  ๊ฐ์ด๋ฐ๋ก ์ ๋ ฌ
- space-between: grid ํ/์ด ์ฌ์ด์ ๋์ผํ ๊ฐ๊ฒฉ์ ๋ (์๋์ ์์๊ฐ ์์)
- space-around: grid ํ/์ด ์ฃผ์์ ๋์ผํ ๊ฐ๊ฒฉ์ ๋ (์๋์ ์ฌ๋ฐฑ์ด ์์)

#### ๐ธ[Shortcut] `place-content: {align-content} {justify-content}`
```css
.container{
  display: grid;
  height: 30vh;
  grid-template-columns: repeat(4, 50px);
  grid-template-rows: repeat(4, 50px);
  place-content: center space-between;
  background-color: black;
}
```
![grid ๋ ์ด์์](./asset/grid_15.png)

<br />

### 8) fraction์ ์ฌ์ฉํ์๋, ๋ธ๋ผ์ฐ์  ํฌ๊ธฐ๊ฐ ์์์ง๊ฑฐ๋ ์ปค์ง๋๋ง grid cell์ ํฌ๊ธฐ๊ฐ ์ ๋์ ์ผ๋ก ๋ณํ๋ค. ์ต๋๋ก ์ปค์ง ์ ์๋ ๊ฐ๊ณผ ์ต์ํ ์ ์ง๋์ด์ผํ๋ ํฌ๊ธฐ๋ฅผ ์ง์ ํ  ์ ์์๊น?
#### ๐ธ `minmax(min, max)`: ํด๋น grid cell์ maxr๊ฐ๋ณด๋ค ์ปค์ง ์ ์๊ณ  min๋ณด๋ค ์์์ง ์ ์๋ค.
```css
.container{
  /* ์๋ถ๋ถ ์๋ต */
  grid-template-columns: repeat(4, minmax(50px, 1fr)); /* ์ต์ 100px, ์ต๋ 1fr */
}
```

<br>

### 9) repeatํจ์์ auto-fit, auto-fill์ ์ด์ฉํ์ฌ ๋ฐ์ํ ๋ ์ด์์์ ๋ง๋ค์ด๋ณด์!
```css
.auto-fill{
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}

.auto-fit{
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}

.container{
  display: grid;
  gap: 5px;
}

.container > div {
  height: 50px;
}

.container > div:nth-child(2n-1){
  background: #2ecc71;
}
.container > div:nth-child(2n){
  background: #f39c12;
}
```
```html
auto-fill
<div class="auto-fill container">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
</div>
auto-fit
<div class="auto-fit container">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
</div>
```
![grid ๋ ์ด์์](./asset/grid_17.png)

#### ๐ธ `auto-fill`: ์ ํด์ง ํฌ๊ธฐ n์ ๋ง์ถฐ ๊ฐ๋ฅํ ๋ง์ ๋น column&row๋ฅผ ๋ง๋ ๋ค.(๋น๊ณต๊ฐ์ ๋์ผํ ํฌ๊ธฐn์ empty cell๋ก ๊ฐ๋ ์ฑ์)
- repeat(auto-fill, minmax(n, 1fr));
- grid cell์ ๊ฐ์๋ฅผ ์ ํํ๊ฒ ๋ชจ๋ฅด์ง๋ง ๋ชจ๋ ๋์ผํ ํฌ๊ธฐ๋ก ๋ณด์ฌ์ ธ์ผํ  ๋ ์ ์ฉํ๊ฒ ์ฌ์ฉ๊ฐ๋ฅํ๋ค. 
 ![grid ๋ ์ด์์](./asset/grid_16.png)

#### ๐ธ `auto-fit`: grid ์์ญ์ ๋ง์ถฐ์ ํ์ฌ cell์ ํฌ๊ธฐ๋ฅผ ๋๋ ค์ค๋ค.
- repeat(auto-fit, minmax(n, 1fr));
- ํ๋ฉด ํฌ๊ธฐ์ ๋ง์ถฐ์ ๋ฐ์ํ๋ฏ๋ก, ๋ฐ์ํ์์ ๊ฐ์ฅ ๋ง์ด ์ฌ์ฉ๋๋ค.
 ![grid ๋ ์ด์์](./asset/grid_18.png)

<br/>

### 10) min-content, max-content๋ฅผ ์ฌ์ฉํด๋ณด์!
#### ๐ธ `min-content`: content์ ํฌ๊ธฐ๋ฅผ ์ค์ฌ์ ๊ฐ๋ฅํ ๊ฐ์ฅ ์์ cell์ ๋ง๋ ๋ค.
- ์ฆ, content(๊ธ์,์ฌ๋ฐฑ ๋ฑ)๊ฐ ์๋ค๋ฉด ํด๋น cell์ ํฌ๊ธฐ๋ 0์ผ๋ก ํ๋ฉด์ ๋ณด์ด์ง ์์
- ๊ธ์๊ฐ ์ค๋ฐ๊ฟ ๋จ

#### ๐ธ `max-content`: content์ ํฌ๊ธฐ ๋งํผ cell์ ๋๋ฆฐ๋ค.
- ๊ธ์๊ฐ ์ค๋ฐ๊ฟ์ฒ๋ฆฌ๋์ง ์์. ์ค๋ฐ๊ฟ์ด ๋์ฌ๋๊น์ง ๋์ด๋จ

```css
.grid{
  display: grid;
  gap: 5px;
  grid-template-columns: max-content min-content;
  grid-auto-rows: 100px;
}

.grid > div:nth-child(2n-1){
  background: #2ecc71;
}
.grid > div:nth-child(2n){
  background: #f39c12;
}
```
```html
<div class="grid">
  <div class="item">This is a very long text</div>
  <div class="item">This is a very long text</div>
</div>
```
![grid ๋ ์ด์์](./asset/grid_19.png)

<br/>


### [ํ์ฉ] max-content์ repeat, minmax ํ์ฉํ๊ธฐ
```html
<div class="grid">
  <div class="item">This is a very long text</div>
  <div class="item">This is a very longer longer long text</div>
  <div class="item">This is a text</div>
  <div class="item">Not long at all, or maybe, who...</div>
  <div class="item">This is a very longer long text</div>
</div>
```
```css
.grid{
  display: grid;
  gap: 5px;
  grid-template-columns: repeat(5, minmax(max-content, 1fr));
  grid-auto-rows: 100px;
}
```
![grid ๋ ์ด์์](./asset/grid_20.png)

