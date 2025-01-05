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

# **Components**

As we are following bottom up approach. First we build components and build blocks using this components.

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

### **BEM: Block Element Modifier**

CSS class naming convention. -- indecates variation. \_\_ indecates inside class

```jsx
"badge badge--primary", "block__element--modifier";
```

BEM divides a class name into three parts:

1. Block (badge): A "block" is a reusable UI element such as a button, card, or badge.
2. Element (block\_\_element): Represents a part or child of the block, separated by \_\_ (double underscores).
3. Modifier (badge--primary): Represents a variation or state of a block/element, separated by -- (double dashes).

### **Badges**

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

### **Popular Badge**

No use extra image tag. Just insert plan--popular variation. and add sudo class ::before
By doing so if you add plan--popular class to any plan it will works

```html
<div class="plan plan--popular">
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
```

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  display: inline-block;
  position: absolute;
  right: 5%;
  top: -5px;
  width: 40px;
}
```

### **Media Objects: Image on left, Right Title followed by some text**

```jsx
<div class="media">
  <div class="media__image">
    <svg class="icon icon--primary">
      <use xlink:href="images/sprite.svg#snap"></use>
    </svg>
  </div>
  <div class="media__body">
    <h3 class="media__title">Easy Start & Managed Updates</h3>
    <p class="media__description">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
      incidunt temporibus delectus voluptate, omnis earum illum harum iste
      dolores? Excepturi!
    </p>
  </div>
</div>
```

Basic Rule: 1st: Do markup. then see what is not align with the design fix that with css. Here only 3 class element need to fix to align with design

```css
/* Media Objects */
.media {
  display: flex;
  gap: 2rem;
}

.media__title {
  margin-top: 0;
}

.media__image {
  margin-top: 1rem;
}
```

### **Quotes**

```jsx
<blockquote class="quote">
  <p class="quote__text">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam soluta cumque
    cum architecto nemo. Ex veritatis eos tempore dolores recusandae!
  </p>
  <footer>
    <div class="media">
      <div class="media__image">
        <svg class="icon icon--primary">
          <use xlink:href="images/sprite.svg#line"></use>
        </svg>
      </div>
      <div class="media__body">
        <h3 class="media__title">John Smith</h3>
        <p class="media__description">ABC Company</p>
      </div>
    </div>
  </footer>
</blockquote>
```

```css
/* Quotes */
.quote {
  font-size: 3rem;
  font-style: italic;
  color: var(--color-body-darker);
  line-height: 1.3;
}

.quote__text::before {
  content: open-quote;
}

.quote__text::after {
  content: close-quote;
}

.quote .media__image {
  margin-top: 0;
}

.quote .media__title {
  font-size: 3rem;
  margin-bottom: 0;
  font-weight: 500;
  font-style: normal;
}

.quote .media__description {
  font-size: 2rem;
  font-style: normal;
  opacity: 0.4;
}

@media screen and (mid-width: 1024px) {
  .quote {
    font-size: 2rem;
  }

  .quote .media__title {
    font-size: 2.4rem;
  }

  .quote .media__description {
    font-size: 1.6rem;
  }
}
```

### **Grid**

```html
<!-- 2 columns grid  -->
<div class="grid grid--1x2">
  <div style="height: 100px; background: gold"></div>
  <div style="height: 100px; background: dodgerblue"></div>
  <div style="height: 100px; background: chocolate"></div>
</div>

<!-- 3 columns grid  -->
<div class="grid grid--1x3">
  <div style="height: 100px; background: gold"></div>
  <div style="height: 100px; background: dodgerblue"></div>
  <div style="height: 100px; background: chocolate"></div>
</div>
```

```css
/* Grid */
.grid {
  display: grid;
}

@media screen and (min-width: 768px) {
  .grid--1x2 {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 1024px) {
  .grid--1x3 {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

### **Testimonials**

It combine gird, image, quotes section

```jsx
<div class="card testimonial">
  <div class="grid grid--1x2">
    <div class="testimonial__image">
      <img src="images/testimonial.jpg" alt="A Happy, Smiling Customer" />
      <span class="icon-container icon-container--accent">
        <svg class="icon icon--white icon--small">
          <use xlink:href="images/sprite.svg#quotes"></use>
        </svg>
      </span>
    </div>
    <blockquote class="quote">
      <p class="quote__text">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam soluta
        cumque cum architecto nemo. Ex veritatis eos tempore dolores recusandae!
      </p>
      <footer>
        <div class="media">
          <div class="media__image">
            <svg class="icon icon--primary">
              <use xlink:href="images/sprite.svg#line"></use>
            </svg>
          </div>
          <div class="media__body">
            <h3 class="media__title">John Smith</h3>
            <p class="media__description">ABC Company</p>
          </div>
        </div>
      </footer>
    </blockquote>
  </div>
</div>
```

Do some variation(Modifire) on Icons
Then Work on testimonials

```css
/* Icons: Add some icon Modifire */
.icon--small {
  width: 30px;
  height: 30px;
}

.icon--white {
  fill: #fff;
}

.icon-container--accent {
  background: var(--color-accent);
}

/* Testimonial */
.testimonial {
  padding: 3rem;
}

.testimonial__image {
  position: relative;
}

.testimonial__image > img {
  width: 100%;
}

.testimonial__image > .icon-container {
  position: absolute;
  top: 2rem;
  right: -32px;
}

@media screen and (min-width: 768px) {
  .testimonial .quote,
  .testimonial .media__title {
    font-size: 2.4rem;
  }

  .testimonial .quote {
    margin-left: 6rem;
  }
}
```

### **Callouts**

Add this class .btn--streatched in buttons section

```jsx
<div class="callout callout--primary">
  <div class="grid grid--1x2">
    <div class="callout__content">
      <h2 class="callout__heading">Ready to Get Started?</h2>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Veniam, harum
        maxime. Nisi dolores suscipit distinctio voluptate, veritatis nulla ad
        labore!
      </p>
    </div>
    <a class="btn btn--secondary btn--streatched" href="">
      Get Stared
    </a>
  </div>
</div>
```

By default: justify-items is stretch

```css
.grid {
  display: grid;
  justify-items: stretch; /* Default: It need to have "center" */
  aligin-items: stretch; /* Default */
}
/* Both are same: justify-items(For Parent) and justify-self(For Grid Item(Children)) */
.grid .grid-item {
  justify-self: stretch; /* Default: It need to have */
  aligin-self: stretch; /* Default */
}
```

.callout .grid--1x2: last column fit content and rest space will taken by first column

```css
/* Calloutes */
.callout {
  padding: 4rem;
  border-radius: 5px;
}

.callout--primary {
  background: var(--color-primary);
  color: #fff;
}

.callout__heading {
  color: #fff;
  margin-top: 0;
  font-size: 3rem;
}

.callout .btn {
  align-self: center;
  justify-self: center;
}

.callout__content {
  text-align: center;
}

@media screen and (min-width: 768px) {
  .callout__content {
    text-align: left;
  }

  .callout .btn {
    justify-self: start;
    margin: 0 2rem;
  }

  .callout .grid--1x2 {
    grid-template-columns: 1fr auto; /* last column fit content and rest space will taken by first column */
  }
}
```

### **Collapsibles**

Principles: First do style for Collapsible then styel for Extended.<br>
.collapsible\_\_chevron is added to icon. We can do it with ".collapsible .icon" but it is another way. we can do depended up on our need

```jsx
<div class="collapsible">
  <header class="collapsible__header">
    <h2 class="collapsible__heading">Item 1</h2>
    <span class="icon-container icon-container--small icon-container--grey">
      <svg class="icon icon--extra--small icon--white collapsible__chevron">
        <use xlink:href="images/sprite.svg#chevron"></use>
      </svg>
    </span>
  </header>
  <div class="collapsible__content">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Exercitationem,
    sapiente.
  </div>
</div>
```

Here: collapsible--expanded is very wise codding. First create collapsible--expanded version how it looks like. Then toggle the class using javascript<br>
transition is also great.

```css
/* Collapsibles */
.collapsible__header {
  display: flex;
  justify-content: space-between;
}

.collapsible__heading {
  margin-top: 0;
  font-size: 3rem;
}

.collapsible__chevron {
  transform: rotate(-90deg);
  transition: transform 0.3s;
}

.collapsible__content {
  max-height: 0;
  opacity: 0;
  overflow: hidden;
  transition: all 0.3s;
}

.collapsible--expanded .collapsible__chevron {
  transform: rotate(0);
}

.collapsible--expanded .collapsible__content {
  max-height: 100vh;
  opacity: 1;
}
```

1. querySelectorAll: select all ".collapsible" class
2. addEventListener: register "click" event to all ".collapsible" class useing forEach loop
3. toggle all "collapsible--expanded"

```js
const collapsibles = document.querySelectorAll(".collapsible");
collapsibles.forEach((item) =>
  item.addEventListener("click", function () {
    this.classList.toggle("collapsible--expanded");
  })
);
```

### **Blocks**

1. .block--skewed-left class we use a google search "css path generator"
2. [bennettfeely.com](https://bennettfeely.com/clippy)

- .container (max-widht: 1140px) is a individual class we can use it anywhere. For black background we need to add extra div.container

```html
<section class="block container">
  <header class="block__header">
    <h2 class="block__heading">Heading</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum iusto
      officia sint maxime expedita deserunt maiores assumenda omnis ratione et.
    </p>
  </header>
  <div class="card card--primary">
    <header class="card__header">Card Title</header>
    <div class="card__body">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Numquam, esse!
    </div>
  </div>
</section>
<section class="block block--dark block--skewed-left">
  <div class="container">
    <h2 class="block__heading">Heading</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum iusto
      officia sint maxime expedita deserunt maiores assumenda omnis ratione et.
    </p>
  </div>
</section>
```

1. --padding-vertical: 6rem; creating a variable inside .block class. We can only use it in this section not outside.
2. calc(var(--padding-vertical) + 4rem) add extra padding for skewed(তির্যক)
3. clip-path: polygon(x% y%);

```css
/* Blocks */
.block {
  --padding-vertical: 6rem;
  padding: var(--padding-vertical) 2rem;
}

.block__header {
  text-align: center;
}

.block__heading {
  margin-top: 0;
}

.block--dark {
  background: #000;
  color: #7b858b;
}

.block--dark .block__heading {
  color: #fff;
}

.block--skewed-right {
  padding-bottom: calc(var(--padding-vertical) + 4rem);
  clip-path: polygon(0% 0%, 100% 0%, 100% 100%, 0% 80%);
}

.block--skewed-left {
  padding-bottom: calc(var(--padding-vertical) + 4rem);
  clip-path: polygon(0% 0%, 100% 0%, 100% 80%, 0% 100%);
}

.container {
  max-width: 1140px;
  margin: 0 auto;
}
```

NB: Styling in html tag is not entertained here. But if necessary you may.

### **Navigation Bars: Most Important and Difficult**

```jsx
<nav class="nav collapsible">
  <a class="nav__brand" href="/" class="">
    <img src="./images/logo.png" alt="" />
  </a>
  <svg class="icon icon--white nav__toggler">
    <use xlink:href="images/sprite.svg#menu"></use>
  </svg>
  <ul class="list nav__list collapsible__content">
    <li class="nav__item">
      <a href="#">Hosting</a>
    </li>
    <li class="nav__item">
      <a href="#">VPS</a>
    </li>
    <li class="nav__item">
      <a href="#">Domain</a>
    </li>
    <li class="nav__item">
      <a href="#">Pricing</a>
    </li>
  </ul>
</nav>
```

```css
/* Navigation Bars */
.nav {
  align-items: center;
  background: #000;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  padding: 0 1rem;
}

/* better then .nav .list */
.nav__list {
  width: 100%;
  margin: 0;
}

.nav__item {
  padding: 0.5rem 2rem;
  border-bottom: 1px solid #222;
}

.nav__item > a {
  color: #d2d0db;
  transition: color 0.3s;
}

.nav__item > a:hover {
  color: #fff;
}

.nav__toggler {
  cursor: pointer;
  opacity: 0.5;
  transition: box-shadow 0.15s;
}

/* <nav class="nav collapsible"> if both class has .nav__toggler then it works */
.nav.collapsible--expanded .nav__toggler {
  opacity: 1;
  box-shadow: 0 0 0 3px #666;
  border-radius: 5px;
}

.nav__brand {
  transform: translateY(5px);
}

@media screen and (min-width: 768px) {
  .nav__toggler {
    display: none;
  }

  .nav__list {
    display: flex;
    font-size: 1.6rem;
    max-height: 100%;
    opacity: 1;
    width: auto;
  }

  .nav__item {
    border: 0;
  }
}
```

# **Blocks**

Use different component to build bloks

### **Hero / Banner**

Notice: First place generic class then specific section class ie. hero

```jsx
<section class="block block--dark block--skewed-left hero">
  <div class="container grid grid--1x2">
    <header class="block__header hero__content">
      <h1 class="block__heading">Cloud Hosting for Pros</h1>
      <p class="hero__tagline">Deploy your websites in less than 60 seconds.</p>
      <a href="#" class="btn btn--accent btn--stretched">
        Get Started
      </a>
    </header>
    <img class="hero__image" src="./images/banner.png" alt="" />
  </div>
</section>
```

Custom polygon

```css
/* Hero */
.hero {
  clip-path: polygon(0% 0%, 100% 0%, 100% 90%, 0% 100%);
}

.hero__tagline {
  font-size: 2rem;
  color: #b9c3cf;
  letter-spacing: 1px;
  margin: 2rem 0 5rem;
}

.hero__image {
  width: 100%;
}

@media screen and (min-width: 1024px) {
  .hero {
    padding-top: 0;
  }

  .hero__content {
    text-align: left;
    align-self: center;
  }
}
```

### **Image Optimization**

1. [Some Terms](https://prnt.sc/-rd8gbrj9bwx)

**Basic Idea(A): High density image Retina Display**

```html
<img src="meal.jpg" class="meal" alt="My Samon Food" />
<img
  src="meal-full.jpg"
  class="meal"
  alt="My Samon Food"
  srcset="meal.jpg 1x, meal@2x.jpg 2x, meal@3x.jpg 3x"
/>
```

Here 400px; is logical size

```css
.meal {
  width: 400px;
}
```

NB: Zoom in/out the browser and reload page and see the effect. When we zoom browser then device resulation is fixed but logical web page resulation reduce. So more image need to accumudate in small logical size that increase display density.

- [zoom 1](https://prnt.sc/0zB8SVrkKtfN) Basic
- [zoom 1.25](https://prnt.sc/aeCn4Vsh1DGN) 2x display: DPR: 2 (Device Pixel Ratio)
- [Zoom 2.5](https://prnt.sc/JtbLQ11SpCEl) 3x
- [Network Tab](https://prnt.sc/HlpvAh3BxqBN)

**Resolution Switching(B): [Mobile, Tab, Laptop](https://prnt.sc/XT5zyDM7OXeJ)**<br />
src: A default fallback image used if srcset isn't supported by the browser. <br>
srcset: Provides multiple image options with different resolutions for the browser to choose from. Talling the browser what is the size of this image(When we click properties). Here we can miss guide browser like meal.jpg 900w where it should be meal.jpg 400w. Browser follow our instruction, although actual image size is 400px. here 400w means 400px width <br>
sizes: What will be the size of the image in that certain viewport. Then browser use algorith and download most suitable image. <br>
NB: What is for sure here: if viewport max width is 480px then image width will be 300px. Now see on srcset which image has 300px or nearest bigger size. But it mainly identify by brower which image will be load. The browser selects the most appropriate image based on the device's resolution and viewport size.

```html
<img
  src="meal-full.jpg"
  srcset="
    meal.jpg       400w,
    meal@2x.jpg    800w,
    meal@3x.jpg   1200w,
    meal-full.jpg 2396w
  "
  class="meal"
  sizes="(max-width: 480px) 70vw, (max-width: 768px) 700px, (max-width: 1140px) 100vw, 2300px"
  alt="Responsive design example image"
/>
```

```css
/* No css like before. CSS width depending on different viewport */
.meal {
  /* width: 400px; */
}
```

Purpose:
This code improves performance and responsiveness:<br>
Performance: Ensures that only the most appropriate image is downloaded based on the device resolution and viewport size, reducing unnecessary bandwidth usage. <br>
Responsiveness: Adapts the image's size to fit the screen dimensions, providing a better user experience on different devices.

**Picture**<br />
<picture>: The image content changes entirely based on the viewport or device.

```html
<picture>
  <source media="(min-width:650px)" srcset="img_pink_flowers.jpg" />
  <source media="(min-width:465px)" srcset="img_white_flower.jpg" />
  <img src="img_orange_flowers.jpg" alt="Flowers" style="width:auto;" />
</picture>
```

- If you need simplicity and performance → <img> with srcset and sizes is better.
- If you need flexibility and different image content → <picture> is better.
  src: A default fallback image used if srcset isn't supported by the browser.

### **Domain Block**

```jsx
<div class="section block container block-domain">
  <header class="block__header">
    <h2>Starting at $9 per month</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Quasi,
      cupiditate.
    </p>
  </header>
  <div class="input-group">
    <input type="text" class="input" placeholder="Enter domain name here..." />
    <button class="btn btn--accent">
      <svg class="icon icon--white">
        <use xlink:href="images/sprite.svg#search"></use>
      </svg>
      Search
    </button>
  </div>
  <ul class="list block-domain__prices">
    <li>.com $9</li>
    <li>
      <span class="badge badge--secondary">.sg $10</span>
    </li>
    <li>.space $11</li>
    <li>.info $14</li>
    <li>.net $10</li>
    <li>.xyz $10</li>
  </ul>
</div>
```

```css
/* Buttons: Right Place to add this */
.btn {
  outline: 0; /* added */
}

.btn .icon {
  /* added */
  width: 2rem;
  height: 2rem;
  margin-right: 1rem;
  vertical-align: middle;
}

/* Domain Block */
.block-domain .input-group {
  box-shadow: 0 0 30px 20px #e6ebee;
  border: 0;
  margin: 4rem auto;
  max-width: 670px;
}

.block-domain__prices {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 6rem);
  justify-items: center;
  font-size: 2rem;
  font-weight: 600;
  max-width: 700px;
  margin: 0 auto;
}

@media screen and (min-width: 768px) {
  .block-domain__prices {
    grid-template-columns: repeat(auto-fit, minmax(10rem, 1fr));
  }
}
```

grid-template-columns: repeat(auto-fit, minmax(10rem, 1fr)): Columns number is not fixed, minmax() takes two argument minmum and maximum width. If we give 1fr then if extra space available then it will equally distributed to this column. <br>
margin: 0 auto: Taking any content center as horizontally. <br>
vertical-align: middle: If there is a height then we can use this instade of flex or grid

### **Plans Block**

```jsx
<section class="block container block-plans">
  <div class="grid grid--1x3">
    <div class="plan">
      <div class="card card--secondary">
        <header class="card__header">
          <h3 class="plan__name">Entry</h3>
          <span class="plan__price">$14</span>
          <span class="plan__billing-cycle">/month</span>
          <span class="badge badge--primary badge--small">10% off</span>
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
    <div class="plan plan--popular">
      <div class="card card--primary">
        <header class="card__header">
          <h3 class="plan__name">Business</h3>
          <span class="plan__price">$24</span>
          <span class="plan__billing-cycle">/month</span>
          <span class="badge badge--secondary badge--small">20% off</span>
          <span class="plan__description">East start on the cloud</span>
        </header>
        <div class="card__body">
          <ul class="list list--tick">
            <li class="list__item">Unlimited Websites</li>
            <li class="list__item">Unlimited Bandwidth</li>
            <li class="list__item">100 GB SSD Storage</li>
            <li class="list__item">3 GB RAM</li>
            <li class="list__item">2 CPU Cores</li>
          </ul>
          <button class="btn btn--outline btn--block">BUY NOW</button>
        </div>
      </div>
    </div>
    <div class="plan">
      <div class="card card--secondary">
        <header class="card__header">
          <h3 class="plan__name">Business plus</h3>
          <span class="plan__price">$54</span>
          <span class="plan__billing-cycle">/month</span>
          <span class="badge badge--primary badge--small">10% off</span>
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
</section>
```

```css
/* Plans */
.plan {
  transition: transform 0.2s ease-out;
}

.plan--popular {
  transform: scale(1.1);
}

.plan:hover {
  transform: scale(1.05);
}

.plan--popular:hover {
  transform: scale(1.15);
}

/* Plans Block */
.block-plans .grid {
  gap: 8rem 4rem;
}

@media screen and (min-width: 768px) {
  .block-plans .card {
    max-width: 500px;
    margin: 0 auto;
  }
}
```

### **Features Block**

First need to create small thing then go for big (bottom up). First do work of <grid grid--1x2 freature> then <block container>

- To see proper image is loading or not we can verify using network tab. Zoom 200, 300 and [See](https://prnt.sc/vjtKS8-MHQ4M)

```jsx
<section class="block container">
  <header class="block__header">
    <h2>Host on the Cloud to Keep Growing</h2>
    <p>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Consectetur
      blanditiis quo deserunt accusantium.
    </p>
  </header>
  <article class="grid grid--1x2 feature">
    <div class="feature__content">
      <span class="icon-container">
        <svg class="icon icon--primary">
          <use xlink:href="images/sprite.svg#easy"></use>
        </svg>
      </span>
      <h3 class="feature__heading">Super Easy to Use</h3>
      <p>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptatibus,
        totam eius temporibus ea delectus quos nihil sed, neque, consectetur hic
        expedita explicabo.
      </p>
      <a href="#" class="link-arrow">
        Learn More
      </a>
    </div>
    <picture>
      <source
        type="image/webp"
        srcset="
              images/easy.webp    1x,
              images/easy@2x.webp 2x,
              images/easy@3x.webp 3x
            "
      />
      <source
        type="image/jpg"
        srcset="
              images/easy.jpg    1x,
              images/easy@2x.jpg 2x,
              images/easy@3x.jpg 3x
            "
      />
      <img class="feature__image" src="images/easy@2x.jpg" alt="Easy" />
    </picture>
  </article>
  <article class="grid grid--1x2 feature">
    <div class="feature__content">
      <span class="icon-container">
        <svg class="icon icon--primary">
          <use xlink:href="images/sprite.svg#easy"></use>
        </svg>
      </span>
      <h3 class="feature__heading">Simply Fast Websites</h3>
      <p>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptatibus,
        totam eius temporibus ea delectus quos nihil sed, neque, consectetur hic
        expedita explicabo.
      </p>
      <a href="#" class="link-arrow">
        Learn More
      </a>
    </div>
    <picture>
      <source
        type="image/webp"
        srcset="
              images/fast.webp    1x,
              images/fast@2x.webp 2x,
              images/fast@3x.webp 3x
            "
      />
      <source
        type="image/jpg"
        srcset="
              images/fast.jpg    1x,
              images/fast@2x.jpg 2x,
              images/fast@3x.jpg 3x
            "
      />
      <img class="feature__image" src="images/fast@2x.jpg" alt="Easy" />
    </picture>
  </article>
  <article class="grid grid--1x2 feature">
    <div class="feature__content">
      <span class="icon-container">
        <svg class="icon icon--primary">
          <use xlink:href="images/sprite.svg#easy"></use>
        </svg>
      </span>
      <h3 class="feature__heading">Super Easy to Use</h3>
      <p>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptatibus,
        totam eius temporibus ea delectus quos nihil sed, neque, consectetur hic
        expedita explicabo.
      </p>
      <a href="#" class="link-arrow">
        Learn More
      </a>
    </div>
    <picture>
      <source
        type="image/webp"
        srcset="
              images/easy.webp    1x,
              images/easy@2x.webp 2x,
              images/easy@3x.webp 3x
            "
      />
      <source
        type="image/jpg"
        srcset="
              images/easy.jpg    1x,
              images/easy@2x.jpg 2x,
              images/easy@3x.jpg 3x
            "
      />
      <img class="feature__image" src="images/easy@2x.jpg" alt="Easy" />
    </picture>
  </article>
</section>
```

grid grid--1x2 feature: First keep more generic class then specific class

```css
/* Feature Block */
.feature {
  gap: 4rem 2rem;
  margin: 8rem 0;
}

.feature:first-of-type {
  margin-top: 6rem;
}

.feature__heading {
  margin-top: 1rem 0;
}

.feature__image {
  width: 100%;
}

@media screen and (min-width: 768px) {
  .feature:nth-of-type(even) .feature__content {
    order: 2;
  }
}
```

### **ShowCase Block**

Here more tricky part is image is growing beyond container for larger screen. In tab or small laptop it will not show down scrollbar.

```jsx
<section class="block block--dark block--skewed-right block-showcase">
  <header class="block__header">
    <h2>User-friendly Control Panel</h2>
  </header>
  <div class="grid grid--1x2 container">
    <picture class="block-showcase__image">
      <source
        type="image/webp"
        srcset="images/ipad.webp 1x, images/ipad@2x.webp 2x"
      />
      <source
        type="image/png"
        srcset="images/ipad.png 1x, images/ipad@2x.png 2x"
      />
      <img src="images/ipad.png" alt="" />
    </picture>
    <ul class="list">
      <li>
        <div class="media">
          <div class="media__image">
            <svg class="icon icon--primary">
              <use xlink:href="images/sprite.svg#snap"></use>
            </svg>
          </div>
          <div class="media__body">
            <h3 class="media__title">Easy Start & Managed Updates</h3>
            <p class="media__description">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
              incidunt temporibus delectus voluptate, omnis earum illum harum
              iste dolores? Excepturi!
            </p>
          </div>
        </div>
      </li>
      <li>
        <div class="media">
          <div class="media__image">
            <svg class="icon icon--primary">
              <use xlink:href="images/sprite.svg#growth"></use>
            </svg>
          </div>
          <div class="media__body">
            <h3 class="media__title">Staging Git & WP-CLI</h3>
            <p class="media__description">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
              incidunt temporibus delectus voluptate, omnis earum illum harum
              iste dolores? Excepturi!
            </p>
          </div>
        </div>
      </li>
      <li>
        <div class="media">
          <div class="media__image">
            <svg class="icon icon--primary">
              <use xlink:href="images/sprite.svg#wordpress"></use>
            </svg>
          </div>
          <div class="media__body">
            <h3 class="media__title">Dynamic Caching & More</h3>
            <p class="media__description">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
              incidunt temporibus delectus voluptate, omnis earum illum harum
              iste dolores? Excepturi!
            </p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</section>
```

1. width: auto: In situation where image has a width: 100% but we do not want it. We just want original image width.
2. grid-template-columns: [50% 50%: 1fr 1fr will not work here. Because of image size increase](https://prnt.sc/rJ55eeCaF6Iw)

```css
/* ShowCase Block */
.block-showcase__image > img {
  width: 100%;
}

@media screen and (min-width: 768px) {
  .block-showcase .grid {
    grid-template-columns: 50% 50%;
  }

  .block-showcase__image {
    justify-self: end;
  }

  .block-showcase__image > img {
    width: auto;
    max-width: 700px;
  }
}

/* Typography */
::selection {
  background: var(--color-primary);
  color: #fff;
}

/* Blocks */
.block--dark h1,
.block--dark h2,
.block--dark h3 {
  color: #fff;
}
```

### **Testimonials Block**

Just use testimonials card and add blcok header section

```jsx
<div class="block">
  <header class="block__header">
    <h2>What our Customer are Saying</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam,
      possimus.
    </p>
  </header>
  <div class="container">
    <div class="card testimonial">
      <div class="grid grid--1x2">
        <div class="testimonial__image">
          <img src="images/testimonial.jpg" alt="A Happy, Smiling Customer" />
          <span class="icon-container icon-container--accent">
            <svg class="icon icon--white icon--small">
              <use xlink:href="images/sprite.svg#quotes"></use>
            </svg>
          </span>
        </div>
        <blockquote class="quote">
          <p class="quote__text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam
            soluta cumque cum architecto nemo. Ex veritatis eos tempore dolores
            recusandae!
          </p>
          <footer>
            <div class="media">
              <div class="media__image">
                <svg class="icon icon--primary">
                  <use xlink:href="images/sprite.svg#line"></use>
                </svg>
              </div>
              <div class="media__body">
                <h3 class="media__title">John Smith</h3>
                <p class="media__description">ABC Company</p>
              </div>
            </div>
          </footer>
        </blockquote>
      </div>
    </div>
  </div>
</div>
```

Adding css to Blocks section so all margin after header will be consistant.

```css
/* Blocks */
.block__header {
  margin-bottom: 4rem;
}
```

### **Footer Block**

```jsx
<section class="block block--dark footer">
  <div class="grid container footer__sections">
    <section class="collapsible collapsible--expanded footer__section">
      <header class="collapsible__header">
        <h2 class="collapsible__heading footer__heading">Item 1</h2>
        <span class="icon-container icon-container--small icon-container--grey collapsible__chevron-container">
          <svg class="icon icon--extra--small icon--white collapsible__chevron">
            <use xlink:href="images/sprite.svg#chevron"></use>
          </svg>
        </span>
      </header>
      <div class="collapsible__content">
        <ul class="list">
          <li>
            <a href="">Website Hosting</a>
          </li>
          <li>
            <a href="">Free Automated Wordpress</a>
          </li>
          <li>
            <a href="">Migrations</a>
          </li>
        </ul>
      </div>
    </section>
    <section class="collapsible footer__section">
      <header class="collapsible__header">
        <h2 class="collapsible__heading footer__heading">Item 2</h2>
        <span class="icon-container icon-container--small icon-container--grey collapsible__chevron-container">
          <svg class="icon icon--extra--small icon--white collapsible__chevron">
            <use xlink:href="images/sprite.svg#chevron"></use>
          </svg>
        </span>
      </header>
      <div class="collapsible__content">
        <ul class="list">
          <li>
            <a href="">About</a>
          </li>
          <li>
            <a href="">Affiliates</a>
          </li>
          <li>
            <a href="">Blog</a>
          </li>
        </ul>
      </div>
    </section>
    <section class="collapsible footer__section">
      <header class="collapsible__header">
        <h2 class="collapsible__heading footer__heading">Item 3</h2>
        <span class="icon-container icon-container--small icon-container--grey collapsible__chevron-container">
          <svg class="icon icon--extra--small icon--white collapsible__chevron">
            <use xlink:href="images/sprite.svg#chevron"></use>
          </svg>
        </span>
      </header>
      <div class="collapsible__content">
        <ul class="list">
          <li>
            <a href="">Contact</a>
          </li>
          <li>
            <a href="">Knowledge Base</a>
          </li>
          <li>
            <a href="">FAQ</a>
          </li>
        </ul>
      </div>
    </section>
    <section class="collapsible footer__section">
      <header class="collapsible__header">
        <h2 class="collapsible__heading footer__heading">Item 2</h2>
        <span class="icon-container icon-container--small icon-container--grey collapsible__chevron-container">
          <svg class="icon icon--extra--small icon--white collapsible__chevron">
            <use xlink:href="images/sprite.svg#chevron"></use>
          </svg>
        </span>
      </header>
      <div class="collapsible__content">
        <ul class="list">
          <li>
            <a href="">About</a>
          </li>
          <li>
            <a href="">Affiliates</a>
          </li>
          <li>
            <a href="">Blog</a>
          </li>
        </ul>
      </div>
    </section>
    <section class="footer__brand">
      <img src="images/logo.svg" alt="" />
      <p class="footer__copyright">Copyright 2025 Subroto</p>
    </section>
  </div>
</section>
```

.footer .collapsible\_\_content { opacity: 1; max-height: 100%; }: We hide element using opacity: 0. So we are not using display: none here<br>
order: -1: by default order: 0, So it take content to first

```css
/* Footer Block */
.footer {
  background: #232323;
}

.footer__section {
  padding: 2rem;
  border-bottom: 1px solid #393939;
}

.footer__heading {
  text-transform: uppercase;
  font-weight: 600;
}

.footer__brand {
  margin-top: 5rem;
  text-align: center;
}

.footer__brand > img {
  max-width: 230px;
}

.footer__copyright {
  font-style: 2.1rem;
  color: #fff;
  opacity: 0.3;
}

@media screen and (min-width: 768px) {
  .footer a {
    color: #777;
    transition: color 0.3s ease-in;
  }

  .footer a:hover {
    color: #fff;
  }

  .footer__sections {
    grid-template-columns: repeat(auto-fit, minmax(10rem, 1fr));
  }

  .footer__section .list {
    margin: 0;
  }

  .footer .collapsible__chevron-container {
    display: none;
  }

  .footer .collapsible__content {
    opacity: 1;
    max-height: 100%;
  }

  .footer__brand {
    order: -1;
  }

  .footer__section {
    border: 0;
  }

  .footer__copyright {
    font-size: 1.5rem;
  }

  .footer__brand {
    margin-top: 1rem;
  }

  .footer__heading {
    font-size: 1.6rem;
  }
}
```

### **Putting It All Together**

Put all code block one by one and fix layout issues. Fix them in isolation so that there is only one element in this component. You can create playground.html for this.

### **Animations: AOS Animation**

[Search on Google: Animate on Scroll(AOS)](https://www.google.com/search?q=aos+animation)

```jsx
// Step 1
<link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />

// Step 2
<script src="https://unpkg.com/aos@next/dist/aos.js"></script>
<script>
  AOS.init();
</script>

// Step 3: Use | Place it in any html tag
<header class="block__header hero__content" data-aos="fade-right">
```

### **Search Engine Optimization**

[og: for Open Graph](https://ogp.me)

```jsx
<meta name="description" content="Build Your website just for $100" />
<meta property="og:title" content="Understanding Open Graph Properties" />
<meta property="og:description" content="Build Your website just for $100" />
<meta property="og:type" content="website" />
<meta property="og:image" content="https://example.com/image.jpg" />
<meta property="og:url" content="https://edeves.com" />
<title>Subroto Biswas - Grow your business just for $100</title>
```

### **HTML and CSS Validation**

[HTML Validator](https://validator.w3.org/)<br>
[CSS Validator](https://jigsaw.w3.org/css-validator)

### **Building for Production**

Before deploy need to prepere for production. This is why we need build tool

- Combine CSS and JS files
- Minify JS/CSS files (Remove all spaces and comments)
- Optimize images

**Build Tools**

- Webpack (Popular one, but need a lot of configuration)
- Rollup
- Parcel (Blazing Fast, zero configuration)

**Parcel Use**<br>
Step 1

```bash
npm init -y
```

Step 2: devDependencies

```bash
npm i -D parcel-bundler
```

Step 3: Install golabally

```bash
npm i -g parcel-bundler
```

```bash
parcel index.html
```

Open Website: http://localhost:1234 <br>

**Build Project**

```bash
parcel build index.html
```

If error create file .htmlnanorc (root directory) and put

```js
{
    "minifySvg": false
}
```

### **Production**

1. netlify.com
2. Build command: "parcel build index.html"
3. Publish directory: "dist"

NB: You can change site name <br>

Change anything and push to github. You are good to go.

### **Measuring the Site's Performance**

[pagespeed.web.dev](https://pagespeed.web.dev) <br />
Follow all lighthouse suggestion.

- @import "./normalize.css": Parcel combine into one
- Chrome Store Lighthouse: If provide same suggestion. But Purcel minify and combine asset that is not possible during development in lighthouse
