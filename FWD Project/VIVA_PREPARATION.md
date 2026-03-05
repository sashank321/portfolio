# FWD Portfolio Project — Viva Preparation Guide
**Student:** J Sashank | **Course:** FWD (Front-End Web Development) | **Files:** `portfolio.html`, `portstyle.css`, `projects.html`

---

## TABLE OF CONTENTS
1. [HTML Concepts Explained](#1-html-concepts-explained)
2. [CSS Concepts Explained](#2-css-concepts-explained)
3. [JavaScript Concepts Explained](#3-javascript-concepts-explained)
4. [Line-by-Line Code Walkthrough](#4-line-by-line-code-walkthrough)
5. [Possible Viva Questions & Answers](#5-possible-viva-questions--answers)

---

## 1. HTML CONCEPTS EXPLAINED

### 1.1 `<!DOCTYPE html>`
- Tells the browser this is an **HTML5** document.
- Without this, the browser might render the page in "quirks mode" (old/broken rendering).
- **Must be the very first line** of any HTML file.

### 1.2 `<html lang="en">`
- The root element of the page; everything goes inside it.
- `lang="en"` tells browsers and screen readers the page is in English.

### 1.3 `<head>` Section
Contains **metadata** — information about the page that isn't visible to the user.

| Tag | Purpose | Example in our code |
|-----|---------|-------------------|
| `<meta charset="UTF-8">` | Sets character encoding to support all characters (emojis, accents, etc.) | Line 5 |
| `<meta name="viewport" ...>` | Makes the page responsive on mobile devices | Line 6 |
| `<title>` | Text shown on the browser tab | "J Sashank \| Portfolio" |
| `<link rel="stylesheet">` | Connects an external CSS file | `portstyle.css` |
| `<link href="...googleapis...">` | Loads Google Fonts (Poppins) | Line 8 |

### 1.4 `<body>` Section
Contains everything the user actually **sees** on the page.

### 1.5 Semantic HTML Tags
"Semantic" means the tag name **describes its purpose**:

| Tag | Meaning | Where we use it |
|-----|---------|----------------|
| `<nav>` | Navigation section | The top navbar |
| `<section>` | A thematic grouping of content | About, Education, Skills, etc. |
| `<footer>` | Bottom of the page info | Copyright notice |
| `<h1>` to `<h3>` | Headings (h1 = main, h2 = sub, h3 = smaller) | Page title, section titles, school names |

### 1.6 Generic Container Tags
| Tag | Purpose |
|-----|---------|
| `<div>` | A **block-level** container — used to group elements for styling. Takes full width. |
| `<span>` | An **inline** container — used inside text for styling a small portion. |

### 1.7 Links (`<a>` tag)
```html
<a href="#about">About</a>
<a href="projects.html?skill=HTML" target="_blank">HTML</a>
```
- `href="#about"` — **anchor link**: scrolls to the element with `id="about"` on the same page.
- `href="projects.html?skill=HTML"` — navigates to another page and passes data (`?skill=HTML`) via the **URL query string**.
- `target="_blank"` — opens the link in a **new browser tab**.

### 1.8 Images (`<img>` tag)
```html
<img src="profile.png" alt="Profile Photo" class="hero-avatar">
```
- `src` — the file path of the image.
- `alt` — alternative text shown if the image fails to load; also used by screen readers for accessibility.
- **Self-closing tag** — does not have a `</img>`.

### 1.9 Lists
```html
<ul class="nav-links">
  <li><a href="#about">About</a></li>
</ul>
```
- `<ul>` — **unordered list** (bullet points by default).
- `<li>` — each **list item**.
- We remove default bullets using CSS `list-style: none`.

### 1.10 Buttons
```html
<button class="filter-btn active" data-filter="all">All</button>
```
- `<button>` — a clickable button element.
- `data-filter="all"` — a **custom data attribute** (HTML5 feature) that stores extra information. JavaScript reads this using `dataset.filter`.

### 1.11 The `id` Attribute
```html
<section id="about" class="card">
```
- `id` must be **unique** on the entire page — only one element can have `id="about"`.
- Used for:
  - **Anchor navigation** (`href="#about"` scrolls to it)
  - **JavaScript selection** (`document.getElementById('about')`)

### 1.12 The `class` Attribute
```html
<div class="card">
<div class="edu-item">
```
- `class` can be **reused** on multiple elements.
- Used to apply the **same CSS styles** to multiple elements.
- An element can have **multiple classes**: `class="filter-btn active"`.

### 1.13 HTML Entities
| Entity | Displays As | Why use it? |
|--------|------------|-------------|
| `&copy;` | © | Copyright symbol |
| `&amp;` | & | The `&` character is special in HTML |
| `&rarr;` | → | Right arrow |
| `&nbsp;` | (space) | Non-breaking space — prevents line breaks |

### 1.14 HTML Comments
```html
<!-- NAVBAR -->
<!-- HERO SECTION -->
```
- Not visible on the page.
- Used to organize and document code for developers.

### 1.15 Inline CSS (`style` attribute)
```html
<p class="skills-label" style="margin-top: 20px;">Web Technologies</p>
```
- Applies CSS **directly to one element**.
- Overrides CSS from the stylesheet.
- Should be used sparingly — external CSS is preferred for maintainability.

---

## 2. CSS CONCEPTS EXPLAINED

### 2.1 External CSS & `@import`
```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap');
```
- Loads the **Poppins** font from Google Fonts.
- This is an alternative to using `<link>` in HTML (both work).

### 2.2 Universal Reset (`*` selector)
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
- `*` selects **every element** on the page.
- Removes default browser margins and padding so spacing is consistent.
- `box-sizing: border-box` — makes `width` include padding and border (not just content), which makes layout calculations easier.

### 2.3 CSS Selectors Used

| Selector | Example | Meaning |
|----------|---------|---------|
| Element selector | `body { }` | Targets all `<body>` elements |
| Class selector | `.card { }` | Targets elements with `class="card"` |
| Descendant selector | `.card p { }` | Targets `<p>` inside `.card` |
| Multiple classes | `.filter-btn.active { }` | Targets elements with BOTH classes |
| Element inside class | `.edu-info h3 { }` | Targets `<h3>` inside `.edu-info` |

### 2.4 The Box Model
Every HTML element is a box with these layers (inside → outside):

```
Content → Padding → Border → Margin
```

| Property | What it does | Example |
|----------|-------------|---------|
| `padding: 25px 28px` | Space **inside** the border | 25px top/bottom, 28px left/right |
| `margin: 30px auto` | Space **outside** the border; `auto` centers horizontally | Container centering |
| `border: 1px solid #cccccc` | A visible border around the element | Card borders |
| `border-radius: 8px` | Rounds the corners | Cards, buttons |

**Shorthand:** `padding: 14px 40px` means 14px top/bottom, 40px left/right.

### 2.5 Flexbox Layout
Used to arrange items in a **row or column** with easy alignment.

```css
.navbar {
    display: flex;           /* enables flexbox */
    align-items: center;     /* vertical centering */
    justify-content: space-between;  /* pushes logo and links apart */
}
```

| Property | Values Used | Meaning |
|----------|------------|---------|
| `display: flex` | — | Turns the element into a flex container |
| `flex-direction: column` | — | Stack items vertically (default is row) |
| `align-items: center` | — | Center children on the cross axis |
| `justify-content: space-between` | — | Spread children with space between |
| `flex-wrap: wrap` | — | Allow items to wrap to next line |
| `gap: 20px` | — | Space between flex children |

### 2.6 CSS Grid Layout
Used in `projects.html` for the project card grid:

```css
.proj-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 14px;
}
```

- `display: grid` — turns the element into a grid container.
- `repeat(auto-fill, minmax(200px, 1fr))` — creates as many columns as fit, each at least 200px wide, expanding equally (`1fr`).
- `gap: 14px` — space between grid items.

### 2.7 Positioning
```css
.navbar {
    position: sticky;
    top: 0;
    z-index: 99;
}
```
- `position: sticky` — the navbar **scrolls with the page**, but once it reaches the top, it **sticks** there.
- `top: 0` — sticks at 0px from the top edge.
- `z-index: 99` — ensures the navbar appears **above** other elements (higher number = on top).

### 2.8 Typography Properties

| Property | What it does | Example |
|----------|-------------|---------|
| `font-family: 'Poppins', sans-serif` | Sets the font; falls back to default sans-serif | Body text |
| `font-size: 14px` | Text size in pixels | Paragraphs |
| `font-weight: 600` | Boldness (400=normal, 600=semibold, 700=bold) | Headings |
| `line-height: 1.7` | Space between lines (1.7 = 170% of font size) | Paragraph readability |
| `letter-spacing: 0.05em` | Space between individual letters | Skill labels |
| `text-transform: uppercase` | Forces text to UPPERCASE | "PROGRAMMING LANGUAGES" |
| `text-decoration: none` | Removes underline from links | Navbar links |
| `text-align: center` | Centers text horizontally | Hero section, footer |

### 2.9 Colors
```css
color: #2980b9;           /* text color — hex code */
background-color: #f2f2f2; /* background color */
opacity: 0.9;             /* transparency: 0=invisible, 1=fully visible */
```
- Hex colors: `#RRGGBB` — two digits each for Red, Green, Blue (00–FF).
- `#ffffff` = white, `#000000` = black, `#2980b9` = blue.

### 2.10 `display` Property

| Value | Behavior |
|-------|---------|
| `flex` | Flexbox layout |
| `grid` | Grid layout |
| `inline-block` | Flows inline but can have width/height |
| `none` | Hides the element completely |
| `block` | Takes full width, starts on new line |

### 2.11 Image Styling
```css
.hero-avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;     /* makes it circular */
    object-fit: cover;      /* crops image to fill the box */
    border: 3px solid white;
}
```
- `border-radius: 50%` on a square element makes it a **circle**.
- `object-fit: cover` — scales the image to fill the container, cropping if needed (prevents stretching).
- `object-fit: contain` — scales image to fit entirely inside the container.

### 2.12 `max-width` and Centering
```css
.container {
    max-width: 850px;
    margin: 30px auto;
}
```
- `max-width: 850px` — the container never gets wider than 850px.
- `margin: 30px auto` — 30px top/bottom margin; `auto` left/right margin centers the element horizontally.

### 2.13 `white-space: nowrap`
Prevents text from wrapping to the next line — keeps it on a single line.

### 2.14 `cursor: pointer`
Changes the mouse cursor to a hand icon, indicating the element is clickable.

### 2.15 `width: fit-content`
The element is only as wide as its content (the text inside), instead of stretching full width.

### 2.16 CSS Comments
```css
/* ---------- NAVBAR ---------- */
```
- Used to organize code into sections.

### 2.17 Internal CSS (`<style>` tag)
In `projects.html`, page-specific CSS is written inside `<style>` tags in the `<head>`:
```html
<style>
    .proj-card { ... }
</style>
```
- Applies only to this page.
- The page also links to `portstyle.css` for shared styles (navbar, footer, etc.).

---

## 3. JAVASCRIPT CONCEPTS EXPLAINED

All JavaScript is in `projects.html` inside a `<script>` tag at the bottom of `<body>`.

### 3.1 Variables (`const`)
```js
const params = new URLSearchParams(window.location.search);
const skill = params.get('skill');
```
- `const` — declares a variable that **cannot be reassigned**.
- Used because we don't need to change these values after assigning them.

### 3.2 URL Query Parameters
When we click "HTML" on the portfolio page, it goes to:
```
projects.html?skill=HTML
```
- `?skill=HTML` is the **query string**.
- `window.location.search` returns `"?skill=HTML"`.
- `URLSearchParams` is a built-in JavaScript object that parses query strings.
- `params.get('skill')` returns `"HTML"`.

### 3.3 DOM Manipulation
DOM = **Document Object Model** — the browser's representation of the HTML page as a tree of objects.

| Method | What it does | Example |
|--------|-------------|---------|
| `document.getElementById('page-title')` | Finds ONE element by its `id` | Gets the `<h1 id="page-title">` |
| `document.querySelectorAll('.proj-card')` | Finds ALL elements matching a CSS selector | Gets all project cards |
| `.textContent` | Gets or sets the **text** inside an element | `note.textContent = 'Showing...'` |
| `.style.display` | Changes the CSS `display` property via JS | `card.style.display = 'none'` hides it |
| `document.title` | Changes the browser **tab title** | `document.title = 'HTML Projects'` |

### 3.4 Custom Data Attributes (`data-*`)
HTML:
```html
<div class="proj-card" data-tag="html">
<button class="filter-btn" data-filter="css">
```
JavaScript:
```js
card.dataset.tag    // returns "html"
btn.dataset.filter  // returns "css"
```
- Any attribute starting with `data-` is a **custom data attribute**.
- In JavaScript, access it via `element.dataset.attributeName`.
- `data-tag` → `dataset.tag`, `data-filter` → `dataset.filter`.

### 3.5 `.forEach()` Loop
```js
document.querySelectorAll('.proj-card').forEach(function (card) {
    if (card.dataset.tag !== filter) {
        card.style.display = 'none';
    }
});
```
- `querySelectorAll` returns a **NodeList** (like an array of elements).
- `.forEach()` loops through each element, running the function for each one.
- The `card` parameter represents the current element in each iteration.

### 3.6 Event Listeners
```js
btn.addEventListener('click', function () {
    // this code runs when the button is clicked
});
```
- `addEventListener('click', ...)` — attaches a function that runs when the element is **clicked**.
- `'click'` is the **event type** (others include `'mouseover'`, `'keydown'`, etc.).
- The function inside is called a **callback function**.

### 3.7 `classList` API
```js
btn.classList.remove('active');  // removes the "active" class
btn.classList.add('active');     // adds the "active" class
```
- Changes which CSS classes are applied to an element.
- When `.active` is added, the CSS rule `.filter-btn.active { background-color: #2980b9; color: white; }` takes effect.

### 3.8 `if / else` Logic
```js
if (chosen === 'all' || card.dataset.tag === chosen) {
    card.style.display = '';       // show
} else {
    card.style.display = 'none';   // hide
}
```
- `===` — strict equality (checks both value and type).
- `||` — logical OR (true if either condition is true).
- `!==` — strict inequality.

### 3.9 String Methods
```js
const filter = skill.toLowerCase();
```
- `.toLowerCase()` converts `"HTML"` → `"html"` for case-insensitive comparison.

### 3.10 `this` Keyword
```js
btn.addEventListener('click', function () {
    const chosen = this.dataset.filter;
    this.classList.add('active');
});
```
- Inside an event listener, `this` refers to the **element that was clicked**.

---

## 4. LINE-BY-LINE CODE WALKTHROUGH

### 4.1 portfolio.html — Key Lines

| Lines | What it does |
|-------|-------------|
| 1 | `<!DOCTYPE html>` — declares HTML5 |
| 2 | `<html lang="en">` — root element, English language |
| 5-6 | Meta tags for charset and viewport |
| 7 | `<title>` — browser tab text |
| 8 | Google Fonts `<link>` — loads Poppins font |
| 9 | Links to external stylesheet `portstyle.css` |
| 15-25 | **Navbar** — `<nav>` with a logo `<div>` and `<ul>` list of anchor links |
| 28-36 | **Hero section** — profile image, heading, subtitle, description, CTA button |
| 39-142 | **Main container** — wraps all content cards with `max-width: 850px` |
| 42-49 | **About card** — `<section>` with id for navbar anchor linking |
| 52-72 | **Education card** — three `edu-item` divs, each with school name + details |
| 75-101 | **Skills card** — skill tags (`<span>`) + clickable icon cards (`<a>`) that link to filtered projects |
| 86 | **Inline style** — `style="margin-top: 20px"` adds spacing |
| 88 | **Query string link** — `projects.html?skill=HTML` passes data to JS |
| 104-111 | **Hobbies card** — flex-wrapped hobby items |
| 114-124 | **Projects card** — nested project card with `<span>` tag badge |
| 127-140 | **Contact card** — three contact items |
| 145-147 | **Footer** — copyright using `&copy;` entity |

### 4.2 portstyle.css — Section Summary

| Lines | Section | Key Concepts |
|-------|---------|-------------|
| 1 | `@import` | Google Fonts import |
| 3-7 | Universal reset | `*`, `box-sizing: border-box` |
| 9-13 | Body | `font-family`, background color |
| 17-45 | Navbar | `display: flex`, `position: sticky`, `z-index` |
| 51-99 | Hero | `text-align: center`, `opacity`, `border-radius: 50%` |
| 105-109 | Container | `max-width`, `margin: auto` centering |
| 113-134 | Cards | Box model (`padding`, `border`, `border-radius`, `margin`) |
| 138-162 | Education | Flexbox for layout, `border-bottom` separators |
| 166-214 | Skills | `flex-wrap`, skill tags, icon cards |
| 221-234 | Hobbies | Green-themed color scheme |
| 238-267 | Projects | Nested card styling with tag badges |
| 271-287 | Contact | `flex-direction: column` for vertical list |
| 291-298 | Footer | `text-align: center`, `border-top` separator |

### 4.3 projects.html JS — Execution Flow

**Step 1: Page loads**
```
URL: projects.html?skill=HTML
```

**Step 2: Read URL parameter**
```js
const params = new URLSearchParams(window.location.search);  // parses "?skill=HTML"
const skill = params.get('skill');                            // skill = "HTML"
```

**Step 3: If skill exists, filter the page**
```js
const filter = skill.toLowerCase();                           // filter = "html"
document.title = skill + ' Projects | J Sashank';            // changes tab title
document.getElementById('page-title').textContent = ...       // changes heading text
```

**Step 4: Show filter note, hide non-matching cards**
```js
note.style.display = 'block';                                 // shows the hidden note
card.style.display = 'none';                                  // hides cards where data-tag ≠ filter
```

**Step 5: Highlight the correct filter button**
```js
btn.classList.remove('active');                                // remove active from all
btn.classList.add('active');                                   // add active to matching button
```

**Step 6: Filter buttons click functionality**
```js
btn.addEventListener('click', function () {                   // listen for clicks
    const chosen = this.dataset.filter;                       // get clicked button's data-filter
    // remove active from all buttons, add to clicked one
    // show/hide cards based on chosen filter
});
```

---

## 5. POSSIBLE VIVA QUESTIONS & ANSWERS

### HTML Questions

**Q1: What is `<!DOCTYPE html>`?**
> It declares the document type as HTML5. It tells the browser to render the page using modern HTML5 standards instead of older rendering modes.

**Q2: What is the difference between `<div>` and `<span>`?**
> `<div>` is a **block-level** element — it takes up the full width and starts on a new line. `<span>` is an **inline** element — it only takes as much width as its content and stays in the same line.

**Q3: What does `<meta name="viewport" content="width=device-width, initial-scale=1.0">` do?**
> It makes the page responsive on mobile devices. `width=device-width` sets the page width to the device's screen width. `initial-scale=1.0` sets the default zoom level to 100%.

**Q4: What is the difference between `id` and `class`?**
> `id` is **unique** — only one element can have a specific id. `class` can be **reused** on multiple elements. Use `id` for unique elements (like page sections for navigation), and `class` for styling groups of elements.

**Q5: Why do you use `target="_blank"` in links?**
> It opens the linked page in a **new browser tab**, so the user doesn't leave the current page.

**Q6: What are HTML entities? Give examples.**
> HTML entities are special codes for characters that have a meaning in HTML or can't be typed normally. Examples: `&copy;` = ©, `&amp;` = &, `&nbsp;` = non-breaking space.

**Q7: What is a semantic HTML tag?**
> A semantic tag describes its content's purpose. For example, `<nav>` means navigation, `<footer>` means bottom section, `<section>` means a thematic group. `<div>` is NOT semantic because it doesn't describe what's inside.

**Q8: What is the `alt` attribute in `<img>`?**
> It provides alternative text shown when the image can't be loaded. It also helps screen readers describe the image to visually impaired users (accessibility).

**Q9: What is a query string in a URL?**
> The part after `?` in a URL, like `?skill=HTML`. It passes data to the destination page. Multiple parameters are separated by `&`, e.g., `?skill=HTML&page=1`.

**Q10: What is a custom data attribute?**
> An HTML5 feature where you add `data-*` attributes to store extra data on elements. Example: `data-tag="html"`. JavaScript reads it via `element.dataset.tag`.

---

### CSS Questions

**Q11: What does `* { box-sizing: border-box; }` do?**
> It makes the `width` and `height` of every element include padding and border. Without it, padding and border are added outside the width, making layout calculations harder.

**Q12: Explain the CSS Box Model.**
> Every element is a box with 4 layers: **Content** (the text/image), **Padding** (space inside the border), **Border** (the visible edge), and **Margin** (space outside the border separating it from other elements).

**Q13: What is Flexbox and how does it work?**
> Flexbox is a one-dimensional layout system. You set `display: flex` on a container, then control how children are arranged using `justify-content` (main axis), `align-items` (cross axis), `flex-direction` (row or column), and `gap` (spacing).

**Q14: What is CSS Grid?**
> CSS Grid is a two-dimensional layout system for rows AND columns. `grid-template-columns: repeat(auto-fill, minmax(200px, 1fr))` creates a responsive grid where each column is at least 200px and they share available space equally.

**Q15: What is `position: sticky`?**
> The element scrolls normally until it reaches a specified offset (like `top: 0`), then it sticks in place as the user continues scrolling. We use it for the navbar to always stay visible at the top.

**Q16: What is `z-index`?**
> It controls the stacking order of overlapping elements. Higher `z-index` = element appears on top. Only works on positioned elements (`sticky`, `relative`, `absolute`, `fixed`).

**Q17: How do you center a `<div>` horizontally?**
> Use `margin: 0 auto` (or `margin: 30px auto`) along with a `max-width`. The `auto` value on left and right margins distributes space equally, centering the element.

**Q18: What does `opacity: 0.9` do?**
> It makes the element 90% visible and 10% transparent. `0` = fully transparent, `1` = fully opaque.

**Q19: What is the difference between an external stylesheet, internal CSS, and inline CSS?**
> - **External**: Separate `.css` file linked with `<link>`. Best for reusability.
> - **Internal**: CSS inside `<style>` tags in the `<head>`. Good for page-specific styles.
> - **Inline**: CSS in the `style=""` attribute on an element. Should be used sparingly.

**Q20: What is `object-fit: cover`?**
> It scales an image to fill its container while maintaining aspect ratio. Parts of the image may be cropped. `contain` scales to fit entirely inside without cropping.

**Q21: What does `display: none` do versus `visibility: hidden`?**
> `display: none` **removes** the element from the layout entirely — it takes up no space. `visibility: hidden` hides the element visually but it **still takes up space**.

**Q22: What is `list-style: none`?**
> It removes the default bullet points (•) from `<ul>` lists. We use it on the navbar so the navigation links don't show bullets.

**Q23: What does `flex-wrap: wrap` do?**
> When flex items don't fit in a single row, `flex-wrap: wrap` allows them to move to the **next line** instead of overflowing.

---

### JavaScript Questions

**Q24: What is the DOM?**
> DOM stands for **Document Object Model**. It's the browser's representation of the HTML page as a tree structure of objects. JavaScript uses the DOM to read, modify, add, and delete HTML elements.

**Q25: What is the difference between `getElementById` and `querySelectorAll`?**
> `getElementById` returns a **single element** matching the given `id`. `querySelectorAll` returns a **NodeList** (collection) of ALL elements matching a CSS selector.

**Q26: What is an event listener?**
> A function that waits for a specific event (like a click) to happen on an element, then executes code. Syntax: `element.addEventListener('click', function() { ... })`.

**Q27: What does `.forEach()` do?**
> It loops through each item in an array or NodeList and runs a function for each one. Example: `cards.forEach(function(card) { ... })` runs the function once per card.

**Q28: What is `classList`?**
> It's a JavaScript property that lets you add, remove, or toggle CSS classes on an element. `element.classList.add('active')` adds the class; `element.classList.remove('active')` removes it.

**Q29: What does `this` refer to inside an event listener?**
> Inside an event listener (when using `function()`), `this` refers to the **element that triggered the event** — the element that was clicked, hovered, etc.

**Q30: What is a callback function?**
> A function passed as an argument to another function, to be executed later. In `addEventListener('click', function() { ... })`, the anonymous function is the callback — it's called when the click happens.

**Q31: Explain `const` vs `let` vs `var`.**
> - `const` — cannot be reassigned after declaration. Use when the value won't change.
> - `let` — can be reassigned. Block-scoped (limited to `{}`).
> - `var` — older syntax. Function-scoped. Generally avoided in modern JS.

**Q32: How does the filter functionality work in your projects page?**
> 1. Each project card has a `data-tag` attribute (e.g., `data-tag="html"`).
> 2. When a filter button is clicked, JavaScript reads its `data-filter` value.
> 3. It loops through all cards with `forEach()`.
> 4. If the card's `data-tag` matches the filter, it's shown (`display: ''`).
> 5. If it doesn't match, it's hidden (`display: 'none'`).
> 6. The clicked button gets the `active` class for visual feedback.

**Q33: What is `window.location.search`?**
> It returns the **query string** portion of the current URL, including the `?`. For example, if the URL is `projects.html?skill=HTML`, it returns `"?skill=HTML"`.

**Q34: What is `URLSearchParams`?**
> A built-in JavaScript class that parses URL query strings. `new URLSearchParams("?skill=HTML")` creates an object, and `.get('skill')` returns `"HTML"`.

---

### General / Design Questions

**Q35: Why did you use an external CSS file instead of writing all CSS inline?**
> External CSS is reusable across multiple pages (both `portfolio.html` and `projects.html` share `portstyle.css`). It keeps HTML cleaner, is easier to maintain, and allows consistent styling.

**Q36: What is the purpose of the navbar?**
> It provides navigation links that scroll to different sections of the portfolio using anchor links (`#about`, `#skills`, etc.). It's sticky so users can always access it while scrolling.

**Q37: How do the portfolio and projects pages connect?**
> The skill icon cards on the portfolio have links like `projects.html?skill=HTML`. When clicked, the projects page loads and JavaScript reads the `?skill=HTML` parameter to automatically filter and show only HTML projects.

**Q38: What makes your page responsive?**
> The `<meta name="viewport">` tag, `max-width` on the container, `flex-wrap: wrap` on flex layouts, and `repeat(auto-fill, minmax(200px, 1fr))` on the grid all contribute to the page adapting to different screen sizes.

---

*Good luck with your viva!* 🎯
