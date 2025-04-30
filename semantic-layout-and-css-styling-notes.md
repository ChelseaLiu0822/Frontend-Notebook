# 🔁 Semantic Layout and CSS Styling Notes

{% embed url="https://codepen.io/ChelseaLiu0822/embed/azzEoOE?default-tab=html,result" %}

### 🎨 CSS Styling

#### Content + Sidebar Layout (Flexbox)

```css
#content {
  max-width: 1000px;
  margin: auto;
  display: flex;
  border: none;
}

main {
  width: 60%;
}

aside {
  width: 40%;
}
```



***

### 📱 Responsive Design with Media Queries

#### Small Screens (Mobile View)

```css
@media screen and (max-width: 600px) {
/* when the screen width < 600 px, css is changed like below*/
  #content {
    display: block;
  }
  main, aside {
    width: 100%;
  }
  aside > div {
    background: #aec6cf;
  }
}
```

#### Medium Screens (Tablet View)

```css
@media screen and (max-width: 800px) and (min-width: 601px) {
  main {
    width: 70%;
  }
  aside {
    width: 30%;
  }
  body, section, aside > div {
    background: #c0c0c0;
  }
}
```

***

### ✅ Key Takeaways

* Semantic tags like `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, and `<footer>` make HTML more readable and structured.
* Flexbox (`display: flex`) is used to lay out main and sidebar in one row.
* Media queries (`@media`) enable responsive design.
* Visual polish through border radius, font styling, padding, and hover effects improves user experience.
