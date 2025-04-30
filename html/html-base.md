# 🧱 HTML base

## 1 What is HTML

It is used to create webpage or layout.

features:

* latest version is html5
* not a case sensitive language
* extension .html or .htm
*   everything is on tags, every tag should be closed

    ```html
    <hr></hr>//<hr />
    ```

## 2 Structure of a HTML

```html
<!Doctype html>//indicate that this is a html 5 document
<html>
<head></head>//we defined meta, title, styles, js script
<body></body>//everything in this section will be rendered in browser.
</html>
```

## 3 `<head>` Section

`<head>` is used to define the head of the document, which is a container for all header elements. The elements in the header can refer to scripts, indicate to the browser where to find style sheets, provide meta-information, and so on.

The header of a document describes a variety of attributes and information about the document, including the title of the document, its location on the Web, and its relationship to other documents. Most of the data contained in the head of a document is not actually displayed to the reader as content.

The following tags can be used in the head section:

* base
* link
* **meta**
* **title**: This defines the title of the document, which is <mark style="background-color:yellow;">**the only required element**</mark> in the head section.
* **style**
* **script**

### 3.1 \<meta> Tag Details

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="High-quality custom software development">
<meta name="keywords" content="software, development, web design">
<meta name="author" content="John Doe">
```

#### Purpose of `<meta>` Tags:

| Attribute     | Description                                                              |
| ------------- | ------------------------------------------------------------------------ |
| `charset`     | Character encoding. Usually set to UTF-8                                 |
| `viewport`    | Used for **responsive design**; ensures layout fits on all device widths |
| `description` | Short summary shown in search engines under the link                     |
| `keywords`    | Search terms for SEO                                                     |
| `author`      | Author of the document                                                   |

💡 _Meta tags help with SEO (Search Engine Optimization) and are mainly used by digital marketers._

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### 3.2 \<title> Tag

Appears on the browser tab

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```html
<title>My First HTML Page</title>
```

Example use:

* Helps users identify tabs
* Plays a role in SEO ranking

## 4 \<body> Section

### 4.1 🔠 Text Tags & Structure

```html
<h1>Heading 1</h1> <!-- largest -->
<h6>Heading 6</h6> <!-- smallest -->

<p>This is a paragraph.</p>
<br> <!-- line break -->
<hr> <!-- horizontal line -->

<b>Bold</b> <i>Italic</i>
<sup>2</sup> <sub>2</sub>
```

<figure><img src="../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

* Superscript (`<sup>`) for expressions like 22
* Subscript (`<sub>`) for H2O

### 4.2 🖼️ Inserting Images

```html
<img src="path-to-image.jpg" alt="Description">
```

* `src`: Source of the image (local or URL)
* `alt`: Alternative text (for accessibility, or shown if the image fails to load)

🔸 Tip: Use [Lorem Picsum](https://picsum.photos/) for placeholder images.

Internal image example:

```html
<img src="./images/photo.jpg" alt="Team Photo">
```

### 4.3 📋 Lists

#### Ordered List (Numbered)

```html
<ol type="A" start="3">
  <li>Apple</li>
  <li>Banana</li>
</ol>
```

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Types: `1` (default), `A`, `a`, `I`, `i`\
`start`: Starting number/letter

#### Unordered List (Bulleted)

```html
<ul type="square">
  <li>React</li>
  <li>Angular</li>
</ul>
```

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Types: `disc` (default), `circle`, `square`

#### Nested List&#x20;

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

```html
<ol type="I">
  <li>Courses
    <ul>
      <li>React</li>
      <li>Node</li>
      <li>Angular</li>
    </ul>
  </li>
  <li>Duration
    <ul>
      <li>1 Month</li>
      <li>2 Months</li>
    </ul>
  </li>
</ol>
```

### 4.4 ✏️ Special Characters

```html
&copy; 2024 All rights reserved.
```

Outputs: © 2024 All rights reserved.

Other examples:

* `&lt;` → `<`
* `&gt;` → `>`
* `&amp;` → `&`

### 4.5 Hyperlink `<a>`

The `<a>` tag defines a hyperlink, which is used to link from one page to another.

The most important attribute of the `<a>` element is the `href` attribute, which indicates the link's destination.

By default, links will appear as follows in all browsers:

* An unvisited link is underlined and blue
* A visited link is underlined and purple
* An active link is underlined and red

[https://www.w3schools.com/tags/tag\_a.asp](https://www.w3schools.com/tags/tag_a.asp)

### 4.6 Tables

{% embed url="https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_table_test" %}

The `<table>` tag defines an HTML table.

An HTML table consists of one `<table>` element and one or more [\<tr>](https://www.w3schools.com/tags/tag_tr.asp), [\<th>](https://www.w3schools.com/tags/tag_th.asp), and [\<td>](https://www.w3schools.com/tags/tag_td.asp) elements.

The \<tr> element defines a table row, the \<th> element defines a table header, and the \<td> element defines a table cell.

An HTML table may also include [\<caption>](https://www.w3schools.com/tags/tag_caption.asp), [\<colgroup>](https://www.w3schools.com/tags/tag_colgroup.asp), [\<thead>](https://www.w3schools.com/tags/tag_thead.asp), [\<tfoot>](https://www.w3schools.com/tags/tag_tfoot.asp), and [\<tbody>](https://www.w3schools.com/tags/tag_tbody.asp) elements.

```html
<table border="5" cellpadding="15" cellspacing="30">
  <tr>
    <th>Month</th>
    <th>Savings</th>
  </tr>
  <tr>
    <td>January</td>
    <td>$100</td>
  </tr>
  <tr>
    <td>February</td>
    <td>$80</td>
  </tr>
</table>
```

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

```html
<table border="1">
  <tr>
    <th rowspan=4>value</th>
    <th colspan=3>names</th>
  </tr>
  <tr>
    <th>Month</th>
    <th>Savings</th>
  </tr>
  <tr>
    <td>January</td>
    <td>$100</td>
  </tr>
  <tr>
    <td>February</td>
    <td>$80</td>
  </tr>
</table>
```

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

### 4.7 Audio & Video

The `<audio>` tag is used to embed sound content in a document, such as music or other audio streams.

The `<audio>` tag contains one or more [`<source>`](https://www.w3schools.com/tags/tag_source.asp) tags with different audio sources. The browser will choose the first source it supports.

The text between the `<audio>` and `</audio>` tags will only be displayed in browsers that do not support the `<audio>` element.

There are three supported audio formats in HTML: MP3, WAV, and OGG.

Example for audio:

{% embed url="https://www.w3schools.com/tags/tryit.asp?filename=tryhtml5_audio" %}

The `<video>` tag is used to embed video content in a document, such as a movie clip or other video streams.

The `<video>` tag contains one or more [`<source>`](https://www.w3schools.com/tags/tag_source.asp) tags with different video sources. The browser will choose the first source it supports.

The text between the `<video>` and `</video>` tags will only be displayed in browsers that do not support the \<video> element.

There are three supported video formats in HTML: MP4, WebM, and OGG.

example for video:

{% embed url="https://www.w3schools.com/tags/tryit.asp?filename=tryhtml5_video" %}

:question:What if I want a YouTube video or a video from google drive?

use `iframe`

{% embed url="https://codepen.io/ChelseaLiu0822/embed/NPPRXZQ?default-tab=html,result" %}

## 5 Type of Elements

**Block and Inline Elements**

* **Block Elements**:\
  They start on a new line and take up the full width of their container, like `<p>`, `<h1>` to `<h6>`, `<div>`, `<ul>`, etc.\
  They are used to structure the main content of a web page.
* **Inline Elements**:\
  They don't start with a new line and only take up as much width as necessary.\
  Examples: `<a>`, `<span>`, `<label>`, `<img>`, etc.\
  They are used within block-level elements to style or format specific parts of the content.

## 6 HTML5 Semantic Tags

HTML5 introduced several **semantic tags** that give meaning to the structure of web pages. These elements help both developers and browsers (including assistive technologies) understand the content better.

### ✅ Common HTML5 Semantic Tags

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

| Tag            | Description                                                                                    |
| -------------- | ---------------------------------------------------------------------------------------------- |
| `<header>`     | Represents the introductory content or a set of navigational links.                            |
| `<nav>`        | Defines a section containing navigation links.                                                 |
| `<main>`       | Represents the main content of the document (should appear only once per page).                |
| `<section>`    | Represents a standalone section of related content.                                            |
| `<article>`    | Represents a self-contained composition, like a blog post or news article.                     |
| `<aside>`      | Contains content that is tangentially related to the main content (e.g., sidebars, tips, ads). |
| `<footer>`     | Represents the footer of a section or page (usually includes copyright, links).                |
| `<figure>`     | Used to group media content (e.g., images, charts) with a caption.                             |
| `<figcaption>` | Provides a caption or description for the `<figure>` content.                                  |

### 📌 Why Use Semantic Tags?

* 🔍 **Improves Readability**: Makes the structure of your HTML clearer for developers.
* ♿ **Accessibility**: Better support for screen readers and other assistive tools.
* 🎯 **Clear Structure**: Easier to style and maintain.
* 🌐 **SEO Friendly**: Helps search engines better understand and index your content.

### 📘 Example

{% embed url="https://codepen.io/ChelseaLiu0822/embed/vEEXpmW?default-tab=html,result" fullWidth="true" %}

## 7 Form

An HTML form is used to collect user input. The user input is most often sent to a server for processing.

### **7.1 Attributes of `<form>`**

1. `name`

The name of the form. The value must not be the empty string, and must be unique among the `form` elements in the forms collection that it is in, if any.

2. [`method`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form#method)

The [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP) method to submit the form with. The only allowed methods/values are (case insensitive):

* `post`: The [`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/POST) method; form data sent as the [request body](https://developer.mozilla.org/en-US/docs/Web/API/Request/body).
* `get` (default): The [`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/GET); form data appended to the `action` URL with a `?` separator. Use this method when the form [has no side effects](https://developer.mozilla.org/en-US/docs/Glossary/Idempotent).
* `dialog`: When the form is inside a [`<dialog>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog), closes the dialog and causes a `submit` event to be fired on submission, without submitting data or clearing the form.

This value is overridden by [`formmethod`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button#formmethod) attributes on [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button), [`<input type="submit">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/submit), or [`<input type="image">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/image) elements.

{% hint style="info" %}
**Difference between `get` and `post`:**

* `get` is an **insecure method** because it displays form field values in the URL.
* `post` is a **secure method**, sends data to the server in a secure format, and allows sending large amounts of data.
{% endhint %}

3. [`action`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form#action)

The URL that processes the form submission. This value can be overridden by a [`formaction`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button#formaction) attribute on a [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button), [`<input type="submit">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/submit), or [`<input type="image">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/image) element. This attribute is ignored when `method="dialog"` is set.

4. [`enctype`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form#enctype)

If the value of the `method` attribute is `post`, `enctype` is the [MIME type](https://en.wikipedia.org/wiki/Mime_type) of the form submission. Possible values:

* `application/x-www-form-urlencoded`: The default value.
* `multipart/form-data`: Use this if the form contains [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input) elements with `type=file`.
* `text/plain`: Useful for debugging purposes.

This value can be overridden by [`formenctype`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button#formenctype) attributes on [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button), [`<input type="submit">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/submit), or [`<input type="image">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/image) elements.

### ✅ Example 1: method&#x20;

{% embed url="https://codepen.io/ChelseaLiu0822/embed/XJJjZBZ?default-tab=html,result" %}

Try to enter a word and click the button, in the jump-out website, your can tell the differences between post and get through the "url" in that website.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

#### :large\_blue\_diamond:Form Submission Workflow (GET / POST)

1. User fills in form fields
2. Clicks `<input type="submit">` or `<button type="submit">`
3. The browser processes `<form>` attributes:
   * `action`: Specifies where to send the data
   * `method`: Specifies how to send the data (`GET` or `POST`)
   * `enctype`: Specifies the data encoding type (used with `POST` only)
4. Submit event is triggered
   * If not prevented by JavaScript, the browser proceeds with default submission
5. The browser packages the data and submits it
6. The page reloads and navigates to the `action` URL
7. The server responds and renders the new page

#### :large\_blue\_diamond:Dialog Form Workflow (`method="dialog"`)

1. User clicks a button to open the `<dialog>`
2. Inside the `<dialog>`, a form with `method="dialog"` is shown
3. User clicks a button to respond (e.g., Accept or Cancel)
4. Browser performs:
   * Auto-closes the dialog
   * Triggers the `submit` event on the form
   * Sets `dialog.returnValue` based on the clicked button
   * ❌ Does **not** submit data, reload the page, or navigate
5. JavaScript can access the returned value via `dialog.returnValue`

### ✅ Example 2: Overriding Method and Action with `formmethod` / `formaction`

{% embed url="https://codepen.io/ChelseaLiu0822/embed/ZYYpmej?default-tab=html,result" %}

| Elements                           | Effects                               |
| ---------------------------------- | ------------------------------------- |
| `<form method="get" action="...">` | Default way(can be covered by button) |
| `<button formmethod="post">`       | Cover`form`  's method                |
| `<button formaction="...">`        | Cover `form` 's action                |

📌 **Notes**:

* The second button overrides the form’s default `method` and `action`
* Useful for handling multiple submission options

### ✅ Example 3: File Upload Form (`method="post"` with `enctype`)

{% embed url="https://codepen.io/ChelseaLiu0822/embed/OPPRajp?default-tab=html,result" %}

When you select a file and click **Upload**:

* The file is sent to `https://httpbin.org/post`
* The response will show metadata including your file under the `"files"` or `"form"` field in a JSON format
* You won’t see the file itself stored (because it's a test endpoint), but you'll see the request structure

### 7.2 `input` element

To see all types of the input element go [there](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input).

Here is a practice.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://codepen.io/ChelseaLiu0822/embed/WbbGWXP?default-tab=html,result" %}
