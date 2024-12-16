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

Do variation on this component using CSS

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

## Create a components folder and keep all markup of individual component

### **Badges**

Block Element Modifier (BEM): CSS class naming convention.
ie. "badge badge--primary"

- Block(badge): A "block" is a reusable UI element such as a button, card, or badge.
- Modifier (badge--primary): A variant or state of the block (or element).
  NB: "badge badge-primary" single hipen also works but it is not the **convension**

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
