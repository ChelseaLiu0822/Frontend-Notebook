# 🧱 Bootstrap 5 Introduction

## What is Bootstrap?

Bootstrap is a **front-end framework** designed to help developers create **responsive web** designs quickly and efficiently. It includes ready-to-use HTML and CSS templates for common UI components such as:

* Forms
* Buttons
* Navigation bars
* Alerts
* Modals
* Tabs

#### Key Features

* **Responsiveness**: Layouts built using Bootstrap automatically adapt to the screen size.
* **Built-in Classes**: Provides predefined classes to speed up development.

## Getting Started with Bootstrap

#### Linking Bootstrap

To use Bootstrap in your project:

1. Link the Bootstrap CSS in the `<head>` section.
2. Link the Bootstrap JavaScript Bundle (includes Popper) before the closing `</body>` tag.

Example:

```html
<!-- Bootstrap CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">

<!-- Bootstrap JS Bundle with Popper -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" crossorigin="anonymous"></script>
```

Refer to: [https://getbootstrap.com/docs/5.0/getting-started/introduction/](https://getbootstrap.com/docs/5.0/getting-started/introduction/)

### Bootstrap Grid System

Bootstrap works on a **12-column grid system**:

* A single row is divided into 12 columns.
* Example: `col-sm-4 col-sm-4 col-sm-4` (4+4+4 = 12)
* You can mix columns: e.g., `col-sm-6 col-sm-6` or `col-sm-3 col-sm-9`

#### Example:

{% embed url="https://codepen.io/ChelseaLiu0822/embed/bNNaNwO?default-tab=html,result" %}

### Responsive Utilities

Bootstrap layouts adjust based on screen size. Grid classes like `col-md-*`, `col-sm-*`, and media queries ensure this adaptability.

### Common Bootstrap Components

{% embed url="https://codepen.io/ChelseaLiu0822/embed/vEEpEeR?default-tab=html,result" %}

### Real-world Example Template Structure

1. **Navbar** with links (Home, About, Services, Contact), Register/Login on the right.
2. **Hero Section** with heading, text, and call-to-action button.
3. **Three Columns Section** with cards/content blocks.
4. **Footer** split into two columns:
   * Left: Copyright
   * Right: Privacy/Terms
