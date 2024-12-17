### **Setting up Project**

1. index.html
2. normalize.css(https://necolas.github.io/normalize.css) in css/normalize.css
3. style.css in css folder
   index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="css/normalize.css" />
    <link rel="stylesheet" href="css/style.css" />
  </head>
  <body></body>
</html>
```

css/style.css

```css
body {
  background: gold;
}
```

### **Some Photoshop tools**

1. Eyedrop Tool(to peek color)
2. Ruler(to measure pixel values)
3. Select font using Text Tool

### **Identifying the Components**

Modular/Component CSS: Break down page into reuseable components ie. button, list, batch, layout, Heading, Text, Card. Then compose them together to build a complex layout. Build each component in isolation(there is nothing in the page) <br />

Later on, Do variation on this component using CSS

### **Color Pallette**

**CSS variables**

1. CSS variables are defined using a -- prefix and are scoped within a selector, such as :root, for global scope.

```css
:root {
  --main-color: #3498db;
  --padding: 10px;
}
```

They are accessed using the var() function.

```css
button {
  background-color: var(--main-color);
  padding: var(--padding);
}
```

Normally 3 colors

1. Primary
2. Secondary
3. Accent

```css
:root {
  --color-primary: #2584ff;
  --color-secondary: #00d9ff;
  --color-accent: #ff3400;
  --color-heading: #1b0760;
  --color-body: #918ca4;
}
```

### **Typography: Font & Sizes**

For better rem calculation 62.5% of 16px = 10px; 1 rem = 10px

```css
html {
  /* 62.5% of 16px = 10px; 1 rem = 10px */
  font-size: 62.5%;
}

body {
  font-family: "Inter", sans-serif;
  font-size: 2.4rem;
  line-height: 1.5;
  color: var(--color-body);
}

h1,
h2,
h3 {
  color: var(--color-headings);
  margin-bottom: 1rem;
}

h1 {
  font-size: 7rem;
}

h2 {
  font-size: 4rem;
}

h3 {
  font-size: 3rem;
}

p {
  margin-top: 0;
}

@media screen and (min-width: 1024px) {
  body {
    font-size: 1.8rem;
  }

  h1 {
    font-size: 8rem;
  }

  h2 {
    font-size: 4rem;
  }

  h3 {
    font-size: 2.4rem;
  }
}
```

Typography: h1, h2..., P all these

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<p>
  Lorem, ipsum dolor sit amet consectetur adipisicing elit. Tenetur laudantium
  beatae suscipit reprehenderit quis praesentium.
</p>
```

NB: Mobile version: Font and everything will be large then desktop version

### **Links**

```css
/* Links */
a {
  text-decoration: none;
}

.link-arrow {
  color: var(--color-accent);
  text-transform: uppercase;
  font-size: 2rem;
  font-weight: bold;
}

.link-arrow::after {
  content: "-->";
  margin-left: 5px;
  transition: margin ease 0.15s;
}

.link-arrow:hover::after {
  content: "-->";
  margin-left: 10px;
}

@media screen and (min-width: 1024px) {
  .link-arrow {
    font-size: 1.5rem;
  }
}
```

NB: [Sort all css Properties using Command Palette](https://prnt.sc/cS10hYVx1cME)

## Create a components folder and keep all markup of individual component

### **Badges**

Block Element Modifier (BEM): CSS class naming convention.

```jsx
"badge badge--primary", "block__element--modifier";
```

BEM divides a class name into three parts:

1. Block (badge): A "block" is a reusable UI element such as a button, card, or badge.
2. Element (block\_\_element): Represents a part or child of the block, separated by \_\_ (double underscores).
3. Modifier (badge--primary): Represents a variation or state of a block/element, separated by -- (double dashes).

```html
<span class="badge badge--primary">10% Off 1</span>
<span class="badge badge--secondary">10% Off 1</span>
<span class="badge badge--primary badge--small">10% Off 1</span>
<span class="badge badge--secondary badge--small">10% Off 1</span>
```

```css
/* Badges */

.badge {
  border-radius: 20px;
  font-size: 2rem;
  font-weight: 600;
  padding: 0.5rem 2rem;
  white-space: nowrap;
}

.badge--primary {
  background: var(--color-primary);
  color: #fff;
}

.badge--secondary {
  background: var(--color-secondary);
  color: #fff;
}

.badge--small {
  font-size: 1.6rem;
}

@media screen and (min-width: 1024px) {
  .badge {
    font-size: 1.5rem;
  }

  .badge--small {
    font-size: 1.2rem;
  }
}
```

### **Lists**

Emmit Tricks

```html
<!-- "ul.list>li{Item $} * 3" becomes -->
<ul class="list">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

```html
<ul class="list list--tick">
  <li class="list__item">Item 1</li>
  <li class="list__item">Item 2</li>
  <li class="list__item">Item 3</li>
</ul>
```

```css
/* Lists */
.list {
  list-style: none;
  padding-left: 0;
  color: var(--color-headings);
}

.list--inline .list__item {
  display: inline-block;
  margin-right: 2rem;
}

.list--tick {
  list-style-image: url(../images/tick.svg);
  padding-left: 3rem;
}

.list--tick .list__item {
  padding-left: 0.5rem;
  margin-bottom: 1rem;
}

@media screen and (min-width: 1024px) {
  .list--tick .list__item {
    padding-left: 0;
  }
}
```

### **Icons**

.svg are vector image. Combine all svg into one image using svgsprit.es <br>
Search in Google "svg sprite generator" <br>
[Wrap with container Easy in VS Code](https://prnt.sc/ev-0kyMo4z3x)

```jsx
<span class="icon-container">
  <svg class="icon icon--primary">
    <use xlink:href="images/sprite.svg#wordpress"></use>
  </svg>
</span>
```

**span are inline element. Inline element has no effect of height and width. So use display: block, inline-block, inline-flex**<br>

```css
/* Icons */
.icon {
  width: 40px;
  height: 40px;
}

.icon--primary {
  fill: var(--color-primary);
}

.icon-container {
  background: #f3f9fa;
  width: 64px;
  height: 64px;
  border-radius: 100%;
  display: inline-flex;
  justify-content: center;
  align-items: center;
}
```

**We can use display: block; but there is some other element so it will break to next line. [See](https://prnt.sc/S34aVgxHHX-H)**<br>
icon-container is totall new class no link with BEM of CSS

### **Buttons**

```html
<button class="btn btn--primary btn--block">Button</button>
<button class="btn btn--secondary btn--block">Button</button>
<button class="btn btn--accent">Button</button>
<button class="btn btn--outline">Button</button>
```

```css
/* Buttons */
*,
*::after,
*::before {
  box-sizing: border-box;
}

.btn {
  border-radius: 40px;
  border: 0;
  color: #fff;
  cursor: pointer;
  font-size: 1.8rem;
  font-weight: 600;
  margin: 1rem 0;
  padding: 2rem 3rem;
  text-align: center;
  text-transform: uppercase;
  white-space: nowrap;
}

.btn--primary {
  background: var(--color-primary);
  color: #fff;
}

.btn--primary:hover {
  background: #3a8ffd;
}

.btn--secondary {
  background: var(--color-secondary);
  color: #fff;
}

.btn--secondary:hover {
  background: #00c8eb;
}

.btn--accent {
  background: var(--color-accent);
  color: #fff;
}

.btn--accent:hover {
  background: #ec3000;
}

.btn--outline {
  background: #fff;
  color: var(--color-headings);
  border: 2px solid var(--color-headings);
}

.btn--outline:hover {
  background: var(--color-headings);
  color: #fff;
}

.btn--block {
  width: 100%;
  display: inline-block;
}

@media screen and (min-width: 1024px) {
  .btn {
    font-size: 1.5rem;
  }
}
```

NB: Always test your code as you go. Don't assume your code is always gonna work

### **Inputs**

```html
<input type="text" class="input" placeholder="Enter domain name here..." />
```

```css
/* Inputs */
.input {
  border-radius: 30px;
  border: 1px solid #ccc;
  color: var(--color-headings);
  font-size: 2rem;
  outline: 0;
  padding: 1.5rem 3.5rem;
}

::placeholder {
  color: #cdcdd7;
}

@media screen and (min-width: 1024px) {
  .input {
    font-size: 1.5rem;
  }
}
```

### **Input Groups**

Input Group is a illusion where input element has not border but border with input-group and it contains input and button element

```html
<div class="input-group">
  <button class="btn btn--accent">Search</button>
  <input type="text" class="input" placeholder="Enter domain name here..." />
</div>
```

```css
/* Input Group */
.input-group {
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  display: flex;
}

.input-group .input {
  flex-grow: 1;
  border: 0;
  padding: 1.5rem 1rem;
}

.input-group .btn {
  margin: 4px;
}
```

### **Cards**

```html
<div style="width: 30%; padding: 2rem">
  <!-- This line is for dedemonstration -->
  <div class="card card--secondary">
    <header class="card__header">Card Title</header>
    <div class="card__body">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Numquam, esse!
    </div>
  </div>
</div>
```

NB: By default overflow is visiable. To hide it need to set overflow: hidden; in parent element. Here overflow is internal content ".card--primary .card--header"

```css
/* Cards */
.card {
  border-radius: 7px;
  box-shadow: 0 0 20px 10px #f3f3f3;
  overflow: hidden;
}

.card__header,
.card__body {
  padding: 2rem 3rem;
}

.card--primary .card__header {
  background: var(--color-primary);
  color: #fff;
}

.card--secondary .card__header {
  background: var(--color-secondary);
  color: #fff;
}
```

### **Plans**

```html
<div class="card-container" style="width: 35%; padding: 2rem">
  <div class="plan">
    <div class="card card--secondary">
      <header class="card__header">
        <h3 class="plan__name">Entry</h3>
        <span class="plan__price">$14</span>
        <span class="plan__billing-cycle">/month</span>
        <span class="badge badge--secondary badge--small">10% off</span>
        <span class="plan__description">East start on the cloud</span>
      </header>
      <div class="card__body">
        <ul class="list list--tick">
          <li class="list__item">Unlimited Websites</li>
          <li class="list__item">Unlimited Bandwidth</li>
          <li class="list__item">100 GB SSD Storage</li>
          <li class="list__item">3 GB RAM</li>
        </ul>
        <button class="btn btn--outline btn--block">BUY NOW</button>
      </div>
    </div>
  </div>
</div>
```

.card--secondary .badge--secondary: Means if .card--secondary and .badge--secondary then following background will be.

```css
.card--secondary .badge--secondary {
  background: #02cdf1;
}

/* Plans */
.plan__name {
  color: #fff;
  margin: 0;
  font-weight: 500;
  font-size: 2.4rem;
}

.plan__price {
  font-size: 6rem;
}

.plan__bulling-cycle {
  font-size: 2.4rem;
  font-weight: 300;
  opacity: 0.8;
  margin-right: 1rem;
}

.plan__description {
  font-size: 2rem;
  font-weight: 300;
  letter-spacing: 1px;
  display: block;
}

.plan .list__item {
  margin-bottom: 2rem;
}

@media screen and (min-width: 1024px) {
  .plan__name {
    font-size: 1.4rem;
  }

  .plan__price {
    font-size: 5rem;
  }

  .plan__bulling-cycle {
    font-size: 1.6rem;
  }

  .plan__description {
    font-size: 1.7rem;
  }
}
```
