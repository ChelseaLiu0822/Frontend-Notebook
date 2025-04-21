# ❓ 21 Interview Questions

## 1 Difference Between `src` and `href`

Both `src` and `href` are used to reference external resources, but they serve different purposes:

* **`src` (source)**: Refers to a resource that is embedded in the current tag's position. For example, when using a `<script>` tag with a `src` attribute, the browser will download and apply the script into the document. When the browser encounters a tag using `src`, it pauses other downloads and processing until the resource is fully loaded, compiled, and executed. This is why JavaScript files are often placed at the bottom of the page.
* **`href` (hypertext reference)**: Refers to a hyperlinked resource, creating a relationship between the current document and the external file. When the browser detects a file referenced by `href`, it downloads the file in parallel without stopping the current document’s parsing. This is commonly used in `<a>` and `<link>` tags.

## 2 Understanding Semantic HTML

Semantic HTML refers to choosing the appropriate HTML tags based on the structured meaning of the content (content semantics), using the correct tags to do the correct job (code semantics).

**Benefits of Semantic HTML:**

* **Better for machines**: Text with semantic meaning is more expressive and suitable for web crawlers, aiding SEO. Screen readers can also generate document outlines automatically.
* **Better for developers**: Semantic tags improve readability and clarify page structure, making development and collaboration easier.

**Common Semantic Tags:**

```html
<header></header>   <!-- Header -->
<nav></nav>         <!-- Navigation bar -->
<section></section> <!-- Section block -->
<main></main>       <!-- Main content -->
<article></article> <!-- Article -->
<aside></aside>     <!-- Sidebar -->
<footer></footer>   <!-- Footer -->
```

## 3 What is HTML?

HTML (HyperText Markup Language) is a markup language used to describe web pages. It uses markup tags to describe text, images, and other content elements and their relationships. HTML documents are plain text files that are readable by both humans and machines. HTML is not a programming language; it is a markup language.

## 4. Difference Between `defer` and `async` in `<script>`

If neither `defer` nor `async` is used, the browser will immediately download and execute the script. It does not wait for subsequent document elements to load — execution begins as soon as the script is encountered, blocking further document parsing.

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

**Key Differences:**

* **Execution Order**:
  * `async`: Multiple scripts may execute in any order, as soon as they are downloaded.
  * `defer`: Multiple scripts are guaranteed to execute in order after parsing.
* **Blocking Behavior**:
  * `async`: Does not wait for HTML parsing; script loads and runs as soon as possible.
  * `defer`: Loads in parallel but waits until HTML is fully parsed before running (triggers before `DOMContentLoaded`).

## 5. What is the Function of Doctype?

The `<!DOCTYPE>` declaration is a standard Generalized Markup Language (SGML) document type declaration used in HTML5. It tells the browser (or parser) what type of document definition to use when parsing the page — whether it’s HTML or XHTML. Different rendering modes affect how the browser interprets CSS or even JavaScript. The `DOCTYPE` must be declared on the first line of the HTML document.

**Rendering Modes (accessed via `document.compatMode`):**

* `CSS1Compat`: **Standards Mode (Strict Mode)** — The browser uses W3C standards to render the page.
* `BackCompat`: **Quirks Mode (Compatibility Mode)** — The browser uses a backward-compatible mode to support older pages.

```html
<!DOCTYPE html>
```

## 6. Commonly Used `<meta>` Tags

The `<meta>` tag is used to define metadata about an HTML document. It is commonly used with the `name` and `content` attributes, and in some cases `http-equiv`.

**Examples:**

1. **Character Encoding**

```html
<meta charset="UTF-8">
```

2. **Keywords**

```html
<meta name="keywords" content="keyword1, keyword2">
```

3. **Description**

```html
<meta name="description" content="This is a sample description.">
```

4. **Refresh / Redirect**

```html
<meta http-equiv="refresh" content="0;url=https://example.com">
```

5. **Viewport (for mobile adaptation)**

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
```

* `width`: viewport width (e.g., number or `device-width`)
* `height`: viewport height
* `initial-scale`: initial zoom level
* `maximum-scale`: max zoom level
* `minimum-scale`: min zoom level
* `user-scalable`: whether user can zoom (`yes`/`no`)

6. **Search Engine Robots Directive**

```html
<meta name="robots" content="index,follow">
```

* `all`: Index page and follow links
* `none`: Do not index page or follow links
* `index`: Index the page
* `follow`: Follow links
* `noindex`: Do not index the page
* `nofollow`: Do not follow the links

## 7 What Are the Key Updates in HTML5?

### **7.1 Semantic Tags**

* `<header>`: Defines the header of a document.
* `<nav>`: Defines navigation links.
* `<footer>`: Defines the footer of a document or section.
* `<article>`: Defines self-contained article content.
* `<section>`: Defines a section within a document.
* `<aside>`: Defines content aside from the main content (e.g., sidebars).

### **7.2 Media Tags**

**(1) `<audio>` – Embeds audio**

```html
<audio src="" controls autoplay loop="true"></audio>
```

Attributes:

* `controls`: Shows audio control panel
* `autoplay`: Automatically starts playback
* `loop="true"`: Loops playback continuously

**(2) `<video>` – Embeds video**

```html
<video src="" poster="imgs/aa.jpg" controls></video>
```

Attributes:

* `poster`: Shows an image before the video is played or fully loaded
* `controls`: Displays playback controls
* `width`, `height`: Set video dimensions

**(3) `<source>` – Specifies video/audio source formats**

To support multiple formats across browsers:

```html
<video controls>
  <source src="aa.flv" type="video/flv">
  <source src="aa.mp4" type="video/mp4">
</video>
```

### **7.3 Form Enhancements**

**New Input Types:**

* `email`: Validates email address format
* `url`: Validates URLs
* `number`: Only accepts numbers; includes up/down arrows, supports `min`, `max`, `value`
* `search`: Provides a clear “X” icon for clearing input
* `range`: Select a range, supports `min`, `max`, `value`
* `color`: Provides a color picker
* `time`: Time picker (HH:MM:SS)
* `date`: Date picker (YYYY-MM-DD)
* `datetime`: Date & time (only supported in Safari)
* `datetime-local`: Date and time input control
* `week`: Week picker
* `month`: Month picker

**Form Attributes:**

* `placeholder`: Hint text
* `autofocus`: Automatically focuses on this input
* `autocomplete="on|off"`: Enables browser auto-fill (requires form submission & `name`)
* `required`: Field must be filled before submitting
* `pattern`: Custom regex validation (e.g. `pattern="^(+86)?\d{10}$"` for phone numbers)
* `multiple`: Allows multiple selections (e.g. for email or file)
* `form`: Associates input with a specific form by ID

**Form Events:**

* `oninput`: Triggered when the input’s value changes
* `oninvalid`: Triggered when form validation fails

### **7.4 Progress and Meter Tags**

*   `<progress>`: Displays task progress\
    Example:

    ```html
    <progress value="30" max="100"></progress>
    ```

    _Note: Not supported in IE/Safari._
*   `<meter>`: Displays a scalar measurement (e.g., disk usage)\
    Example:

    ```html
    <meter value="0.6" min="0" max="1" low="0.3" high="0.8"></meter>
    ```

    _Note: Not supported in IE/Safari._

Value logic: `min < low < high < ma`

### **7.5 DOM Query Methods**

* `document.querySelector()` – Selects the first matching element (tag/class/id)
* `document.querySelectorAll()` – Selects all matching elements

```js
document.querySelector('div');        // by tag
document.querySelector('.className'); // by class
document.querySelector('#id');        // by ID
```

### **7.6 Web Storage**

HTML5 introduces client-side storage APIs:

* `localStorage`: Stores data without expiration
* `sessionStorage`: Stores data per session (clears when tab closes)

### **7.7 Other Features**

**Drag and Drop**

Enable an element to be draggable:

```html
<img draggable="true" />
```

**Canvas API**

A drawable area in HTML that can be used to render shapes, text, and images:

```html
<canvas id="myCanvas" width="200" height="100"></canvas>
```

**SVG (Scalable Vector Graphics)**

Uses XML to define graphics. SVGs remain sharp when scaled and are ideal for responsive designs.

**Geolocation API**

Used to detect a user's location via GPS or IP.

### **Summary**

**New Features Introduced in HTML5:**

* Semantic tags: `nav`, `header`, `footer`, `aside`, `section`, `article`
* Media: `audio`, `video`
* Storage: `localStorage`, `sessionStorage`
* Canvas, Geolocation, WebSocket
* New input attributes: `placeholder`, `autocomplete`, `autofocus`, `required`
* History API: `go()`, `forward()`, `back()`, `pushState()`

**Deprecated Elements:**

* Purely visual: `basefont`, `big`, `center`, `font`, `s`, `strike`, `tt`, `u`
* Accessibility-breaking: `frame`, `frameset`, `noframes`

## **8 What is the function of the `srcset` attribute in the `<img>` tag?**

In responsive web design, it's common to display different images depending on the screen's pixel density. This is where the `srcset` attribute in the `<img>` tag becomes useful. The `srcset` attribute allows the browser to automatically load different images depending on the screen's resolution. Here's a basic example:

```html
<img src="image-128.png" srcset="image-256.png 2x" />
```

With this code, the browser loads `image-128.png` for screens with 1x pixel density, and `image-256.png` for 2x displays.

However, if you had to provide separate images for each screen density—such as 1x, 2x, 3x, and 4x—it would result in loading many image files, slowing down the page. To address this, the updated `srcset` standard uses a different approach:

```html
<img src="image-128.png"
     srcset="image-128.png 128w, image-256.png 256w, image-512.png 512w"
     sizes="(max-width: 360px) 340px, 128px" />
```

In this version:

* The `srcset` attribute specifies image sources and their corresponding widths (`w` units), which roughly indicate the image quality or size.
* The `sizes` attribute defines rules for how wide the image should be under specific viewport widths.

The `w` unit helps the browser choose the most appropriate image size. The browser automatically selects the smallest usable image that fits the display requirements.

**Syntax for `sizes`:**

```css
sizes="[media query] [length], [media query] [length], ..."
```

In the example above, the image will be displayed at **128px** by default. If the viewport width exceeds **360px**, it will display at **340px**.

## **9 What are inline elements, block-level elements, and void (empty) elements?**

#### ✅ **Inline Elements:**

Inline elements do **not** start on a new line and only take up as much width as necessary. Common inline elements include:

* `<a>`
* `<b>`
* `<span>`
* `<img>`
* `<input>`
* `<select>`
* `<strong>`

***

#### ✅ **Block-Level Elements:**

Block-level elements **start on a new line** and take up the full width available by default. Common block-level elements include:

* `<div>`
* `<ul>`, `<ol>`, `<li>`
* `<dl>`, `<dt>`, `<dd>`
* `<h1>` to `<h6>`
* `<p>`

***

#### ✅ **Void (Empty) Elements:**

Void elements are HTML elements that **do not have any content and cannot have closing tags**. They're self-closing within the opening tag.

**🔹 Common void elements:**

* `<br>`
* `<hr>`
* `<img>`
* `<input>`
* `<link>`
* `<meta>`

**🔹 Less commonly seen void elements:**

* `<area>`
* `<base>`
* `<col>`
* `<colgroup>` _(when empty)_
* `<command>`
* `<embed>`
* `<keygen>` _(deprecated)_
* `<param>`
* `<source>`
* `<track>`
* `<wbr>` (word break opportunity)

These void elements are automatically closed by the browser, so no closing tag like `</img>` or `</input>` is needed.

## **10 What is a Web Worker?**

In an HTML page, when a script is being executed, the browser may become **unresponsive**—especially during **complex or time-consuming operations**. This happens because JavaScript runs on the **main thread**, which is also responsible for rendering and user interactions.

A **Web Worker** solves this problem by allowing JavaScript to run **in the background**—in a separate thread, **independent of the main UI thread**. This means it won’t block the UI or interrupt user interactions.

Web Workers **communicate with the main thread** using the `postMessage()` method, and the main thread receives the response using the `onmessage` event handler.

***

#### ✅ Key Features of Web Workers:

* Run JavaScript code in background threads
* Operate independently of the DOM
* Communicate with the main thread using messages
* Ideal for heavy computations (e.g., image processing, large loops, data parsing)

***

#### 🛠️ How to Create a Web Worker

**Step 1: Check for browser support**

```javascript
if (window.Worker) {
  // Browser supports Web Workers
}
```

**Step 2: Create a Web Worker file**

Example: `worker.js`

```javascript
// worker.js
onmessage = function(e) {
  console.log('Worker received:', e.data);
  const result = e.data * 2;
  postMessage(result);
};
```

**Step 3: Create and use the Web Worker in your main script**

```javascript
// main.js
const worker = new Worker('worker.js');

// Send data to worker
worker.postMessage(10);

// Receive result from worker
worker.onmessage = function(e) {
  console.log('Main thread received:', e.data); // Output: 20
};
```

***

#### 🔒 Notes:

* Web Workers **cannot access the DOM** or `window`, `document`, `alert`, etc.
* They **can use** `setTimeout`, `setInterval`, `XMLHttpRequest` (in most browsers), `fetch`, and import other scripts via `importScripts()`
* Suitable for CPU-intensive tasks to keep the UI smooth and responsive

## **11 How to use HTML5 offline storage and what is its working principle?**

**Offline storage** allows users to **access a website or application without an internet connection**. When the internet connection is restored, it **automatically updates the cached files** on the user's device.

***

#### ✅ **Working Principle**

HTML5 offline storage is based on a **cache manifest file** (with the `.appcache` extension). It's not a data storage technology (like `localStorage` or `IndexedDB`), but rather a **caching mechanism**. Resources listed in this manifest file are cached by the browser and used when the device is offline—similar in behavior to cookies.

When a user accesses a page with an associated `.appcache` file, the browser **caches the specified resources**, and when the network is unavailable, it **loads the page using those cached resources**.

***

#### 🛠️ **How to Use HTML5 Offline Storage**

**1. Create a manifest file with the same name as your HTML page, and link it in the HTML:**

```html
<html lang="en" manifest="index.manifest">
```

**2. Write resources into the `.manifest` file, like this:**

```plaintext
CACHE MANIFEST
# v0.11

CACHE:
js/app.js
css/style.css

NETWORK:
resource/logo.png

FALLBACK:
/ /offline.html
```

**🔍 Manifest Sections Explained:**

* **CACHE:**\
  Lists resources that should be stored for offline use.\
  &#xNAN;_&#x4E;ote:_ The HTML file referencing the manifest is automatically cached and doesn't need to be listed.
* **NETWORK:**\
  Lists resources that must always be accessed online. These will **not** be available offline.\
  If a resource is listed in both `CACHE` and `NETWORK`, it will still be cached—**CACHE takes priority**.
* **FALLBACK:**\
  Specifies fallback pages if a resource can’t be loaded.\
  In the above example, if any resource in the root path fails, `offline.html` will be served instead.

***

#### ⚙️ **Managing the Cache**

Use `window.applicationCache` in JavaScript to handle offline cache events and updates when offline.

***

#### 🔄 **How to Update the Cache**

1. **Change something in the manifest file** (like the version number comment).
2. **Update the cache via JavaScript** using methods like `applicationCache.update()`.
3. **Clear the browser cache manually**.

***

#### ⚠️ **Caveats and Notes**

* Different browsers have **different storage size limits** (commonly around 5MB per domain).
* If **any resource** in the manifest **fails to download**, the entire cache update will fail, and the browser will continue to use the **old cached version**.
* The HTML page and the manifest file must be **on the same origin (domain)**.
* Resources listed in the `FALLBACK` section must also be from the **same origin** as the manifest.
* Once a file is cached, any request using its **absolute path** will serve the **cached version**.
* Even **pages without the `manifest` attribute** will use cached resources if those resources have already been cached.
* Any **change to the manifest file** triggers a **resource update**.

***

#### 📌 Note:

**AppCache is deprecated** and has been replaced by more robust options like:

* **Service Workers** (recommended)
* **Cache API** For modern web apps, use **Service Workers** instead for better flexibility and control.&#x20;

## **12 How does the browser manage and load HTML5 offline storage resources?**

When **online**, if the browser detects a `manifest` attribute in the HTML `<head>`, it will request the specified manifest file.

* **On the first visit**, the browser will download and cache the resources listed in the manifest file for offline use.
* **On subsequent visits**, if the resources are already cached, the browser will load the page using the **cached resources**.
  * Meanwhile, it will **compare the current manifest file with the previously saved version**.
    * If the manifest **has not changed**, the browser does **nothing**.
    * If the manifest **has changed**, the browser will **re-download** the listed resources and update the offline cache.

When **offline**, the browser directly loads the page using the **previously cached resources**.

This mechanism ensures that:

* Users can still access the website even without an internet connection.
* Cached resources are only updated when the manifest file changes, optimizing performance and minimizing unnecessary downloads.

## **13 What are the differences between `title` and `h1`, `b` and `strong`, `i` and `em`?**

#### ✅ `title` vs `h1`:

* **`<title>`**:
  * Appears in the **browser tab** or **window title**.
  * Describes the **entire page**.
  * Not visible within the main content of the webpage.
  * Has **no hierarchical structure** or semantic emphasis on the page content.
* **`<h1>`**:
  * Represents a **top-level heading** in the page content.
  * Visible to the user and used to structure content **hierarchically**.
  * Plays an important role in **SEO** and helps search engines understand the structure and main topics of the page.

***

#### ✅ `b` vs `strong`:

* **`<b>`**:
  * Renders text in **bold**, but has **no semantic meaning**.
  * Used purely for **visual styling**.
* **`<strong>`**:
  * Also renders text in **bold**, but **adds semantic emphasis**.
  * Indicates that the content is of **strong importance**.
  * Search engines and screen readers give it more weight compared to `<b>`.

***

#### ✅ `i` vs `em`:

* **`<i>`**:
  * Renders text in **italic** style.
  * Like `<b>`, it is **stylistic** only and has **no semantic meaning**.
* **`<em>`**:
  * Also renders text in **italic**, but **adds semantic emphasis**.
  * Used to **emphasize** a word or phrase in context (like stressing it in speech).
  * Can affect how assistive technologies (like screen readers) interpret and announce the text.

## **14 What are the advantages and disadvantages of `<iframe>`?**

The `<iframe>` element creates an **inline frame** that embeds another HTML document within the current page.

***

#### ✅ **Advantages of `<iframe>`:**

1. **Loads slow content independently**\
   Useful for embedding elements like **advertisements** or widgets that may take longer to load, without blocking the rest of the page.
2. **Allows scripts to download in parallel**\
   Scripts inside the iframe can be loaded **concurrently**, improving performance in certain cases.
3. **Enables cross-subdomain communication**\
   With proper settings (e.g., `postMessage`), iframes can be used to **safely exchange messages** between different subdomains.

***

#### ❌ **Disadvantages of `<iframe>`:**

1. **Delays the main page's `onload` event**\
   The browser waits for all iframes to load before triggering the `onload` event of the main page, which can affect user experience.
2. **Limited SEO visibility**\
   Some **search engines cannot index** content inside an iframe, reducing the discoverability of embedded content.
3. **Can clutter and complicate page structure**\
   Each iframe creates a separate document context, which can lead to **many nested pages**, making them harder to manage and debug.

## **15 What is the purpose of the `<label>` tag and how is it used?**

The `<label>` tag is used to **define a label for a form control**. When a user clicks on the label, the browser **automatically focuses** on the associated form input, improving accessibility and usability.

***

#### ✅ **Purpose of `<label>`:**

* Enhances **user experience** by expanding the clickable area for form inputs
* Improves **accessibility**, especially for screen readers
* Clearly defines the relationship between **text descriptions** and **form controls**

***

#### 🛠️ **Two ways to use `<label>`:**

**Method 1: Using the `for` attribute**

{% embed url="https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_label_for" fullWidth="false" %}
click to see the example
{% endembed %}

```html
  <input type="radio" id="html" name="fav_language" value="HTML">
  <label for="html">HTML</label><br>
```

* The `for` attribute's value must **match the `id`** of the associated input element.
* Clicking the label focuses the input with `id="mobile"`.

**Method 2: Wrapping the input inside the label**

```html
<label>Date: <input type="text" /></label>
```

* No need for `id` or `for`; the input is directly wrapped in the label.
* Clicking the text also focuses the input.

## **16 What are the differences between Canvas and SVG?**

#### ✅ **(1) SVG (Scalable Vector Graphics)**

SVG is a language for describing **2D vector graphics** using **XML**. Because it's based on XML, every element in an SVG can be part of the **DOM** and can have **JavaScript event handlers** attached.

**📌 Key Features of SVG:**

* **Resolution-independent**: Maintains quality when scaled.
* **Supports event handling**: You can bind click, hover, etc., to shapes.
* Best suited for **applications with large rendering areas**, like maps (e.g., Google Maps).
* Rendering performance decreases with complexity: Overuse of the DOM can slow things down.
* **Not ideal for real-time gaming** or scenarios that require frequent updates.

***

#### ✅ **(2) Canvas**

Canvas provides a **drawing surface (a bitmap)** where you can use JavaScript to draw 2D graphics pixel by pixel. When an element's position changes, the entire canvas needs to be **redrawn**.

**📌 Key Features of Canvas:**

* **Resolution-dependent**: Image quality may degrade when scaled.
* **Does not support event handling** on individual drawn elements.
* **Weaker text rendering** capabilities.
* Final graphics can be **exported as `.png` or `.jpg`** images.
* Best suited for **image-heavy applications or games**, where many elements are frequently redrawn.

***

#### 🎨 **Bonus – What is a vector graphic?**

A **vector graphic** is an image composed of **objects** defined by mathematical formulas—points, lines, curves, and shapes. Each object has its own properties like color, size, and position, making it ideal for scaling without quality loss.

## **17 What is the purpose of the `<head>` tag, and which tag is required within it?**

The `<head>` tag defines the **head section** of an HTML document. It is a container for metadata elements such as scripts, stylesheets, and general information about the document.

The head section describes attributes and information **about the document**, including its title, location on the web, and its relation to other documents. Most of the content in the `<head>` is **not directly visible** to users.

Common tags within `<head>` include:

* `<base>`
* `<link>`
* `<meta>`
* `<script>`
* `<style>`
* `<title>`

📌 Among these, the **`<title>` tag is mandatory**, as it defines the **title of the document**, which is displayed in the browser tab.

## **18 What is the function of the document declaration (`<!DOCTYPE html>`)? How are strict mode and quirks mode distinguished, and what do they mean?**

**Document declaration** tells the browser **which version of HTML** the page uses, so it can render the page accordingly.

* `<!DOCTYPE html>` is used to trigger **standard mode**, instructing the browser to parse the page using **HTML5 standards**.
* If omitted, the browser may enter **quirks mode**, which is undesirable for modern development.

**📌 Modes:**

* **Strict Mode (Standards Mode)**: Browser parses code according to **W3C standards**.
* **Quirks Mode (Compatibility Mode)**: Browser uses its own legacy rules for parsing, typically to support **older websites**.

**📌 How to distinguish them:**

* A document with a **strict DOCTYPE** (e.g., HTML5's `<!DOCTYPE html>`) will trigger **strict mode**.
* Transitional DOCTYPEs with a URI may still trigger strict mode, but if the **URI is omitted**, **quirks mode** may be used.
* If the **DOCTYPE is missing or malformed**, quirks mode is also used.
* **HTML5 does not use DTDs**, and thus **has no distinction between strict and quirks mode**, aiming for maximum backward compatibility.

✅ **In summary**: Strict mode ensures all browsers follow a unified standard; quirks mode helps legacy websites remain functional.

## **19 What causes browser text encoding issues (garbled text), and how can they be resolved?**

**📌 Causes:**

* The **HTML source code is encoded in GBK**, but the content (e.g., Chinese characters) is **encoded in UTF-8**, or vice versa.
* The HTML page uses **one encoding**, while the **database output uses another**, causing mismatches.
* The browser **fails to auto-detect** the correct encoding.

**📌 Solutions:**

1. **Use an editor** that supports correct encoding when editing HTML files.
2. If HTML is **GBK-encoded** but the database uses **UTF-8**, apply **character encoding conversion** before displaying the data.
3. If the page displays garbled characters in the browser, use the **"Encoding" menu** in the browser to manually select the correct encoding (e.g., UTF-8).

## **20 What is the difference between Progressive Enhancement and Graceful Degradation?**

**✅ Progressive Enhancement:**

* Focuses on **building a basic, functional version** first (targeting older browsers).
* Then **enhances features** for modern browsers.
* Ensures **core functionality** is accessible to everyone.

**✅ Graceful Degradation:**

* Starts by building a **fully-featured version** targeting modern browsers.
* Then **adds compatibility** for older or less capable browsers.
* Assumes older browsers may get a **simplified or fallback experience**.

**📌 Key Differences:**

* **Graceful Degradation** looks **backward**, starting from a full version and reducing complexity.
* **Progressive Enhancement** looks **forward**, starting from the basics and building up.
* Progressive Enhancement focuses on **content-first design**, while Graceful Degradation often emphasizes **feature completeness** from the outset.
* Yahoo adopted Progressive Enhancement in its **Graded Browser Support** strategy.

## **21 Briefly explain the HTML5 Drag and Drop API**

The **HTML5 Drag and Drop API** allows elements to be dragged and dropped within the browser. Here are the main events:

| **Event**   | **Target Element** | **Description**                                         |
| ----------- | ------------------ | ------------------------------------------------------- |
| `dragstart` | Drag source        | Fires when dragging starts.                             |
| `drag`      | Drag source        | Fires repeatedly while dragging.                        |
| `dragenter` | Drop target        | Fires when dragged item enters a drop zone.             |
| `dragover`  | Drop target        | Fires when the item is moved inside a drop zone.        |
| `dragleave` | Drop target        | Fires when the item leaves a drop zone.                 |
| `drop`      | Drop target        | Fires when the item is dropped onto the target.         |
| `dragend`   | Drag source        | Fires when the drag operation ends (success or cancel). |
