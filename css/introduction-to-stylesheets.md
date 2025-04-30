# 🧱 Introduction to Stylesheets

Stylesheets are used to apply **attractive formatting** to our webpages, enhancing the **look and appearance** of a website.

### Types of Stylesheets

There are **three types** of stylesheets:

#### **1. Inline**

* Defined **directly in HTML elements** using the `style` attribute.
* Example:

```html
<p style="color:green; text-align:center"> This is a styled paragraph. </p>
```

#### **2. Internal (Embedded)**

* Defined **in the `<head>` section** of an HTML document within a `<style>` tag.
* Example:

```html
<head>
  <style>
    h2 {
      color: purple;
      text-align: center;
    }
    p {
      color: green;
      font-size: 20px;
    }
  </style>
</head>
```

#### **3. External (CSS File)**

* Styles are defined in an external `.css` file.
* This file is **linked in the `<head>` section** using the `<link>` tag.
* Example:

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

* Example CSS in `style.css`:

```css
h2 {
  color: purple;
  text-align: center;
}
p {
  color: green;
  font-size: 20px;
}
```

#### Order of Precedence

1. Inline
2. Internal
3. External

***

### CSS Syntax

```css
selector {
  property: value;
}
```

Example:

```css
p {
  color: red;
}
```

This applies red color to all `<p>` elements on the page.

***

### CSS Selectors

#### Element Selector

Targets all elements of a specific type:

```css
h1 {
  color: blue;
}
```

#### ID Selector

* Uses `#` followed by the **ID name** (ID should be unique).

```css
#main {
  background-color: yellow;
}
```

#### Class Selector

* Uses `.` followed by **class name** (can be reused across multiple elements).

```css
.error {
  color: red;
  font-weight: bold;
}
```

#### Universal Selector

* Applies to **all elements**:

```css
* {
  margin: 0;
  padding: 0;
}
```

#### Grouping Selectors

* Apply same style to multiple selectors:

```css
h1, h2, h3 {
  text-align: center;
}
```

***

### Common CSS Properties

**Typography & Layout:**

* `color`, `background`, `font-family`, `font-size`, `text-align`, `text-decoration`

**Box Model:**

* `border`, `margin`, `padding`, `box-sizing`

**Layout Control:**

* `display`, `position`, `float`, `opacity`

**Flex/Grid & Responsive:**

* `flexbox`, `grid`, `media queries`, `transform`, `animation`

***

### Practice

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

{% embed url="https://codepen.io/ChelseaLiu0822/embed/vEEWwzB?default-tab=html,result" %}



