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
