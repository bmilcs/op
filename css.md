# CSS

**CSS** is a Stylesheet language that changes how HTML documents are styled. It affects font styles, colors, layout and responsive features.

## Basic Syntax

- CSS is made up of rules
  - Selector
  - Semi-colon
  - List of declarations
    - Property:Value pair

```css
/* selector */
div.bold-text {
  font-weight: 700;
  /* property: value; */
}
```

## Selector

- Refer to HTML elements to which the CSS rules apply
  - What's being selected for each rule

### Universal Selector

```css
/* styles.css */
* {
  color: purple;
}
```

### Type Selector

- Selects elements of the given **element type**

```html
<!-- index.html -->
<div>Please agree to our terms of service.</div>
```

```css
/* styles.css */
div {
  color: white;
}
```

### Class Selector

- Selects elements with the given **class**
- Classes are **attributes** you place on an HTML element

```html
<!-- index.html -->
<div class="alert-text">
  Welcome to the machine.
</div
```

```css
/* styles.css */
.alert-text {
  color: red;
}
```

### ID Selector

- Similar to class selectors
- Select elements with a given ID
- Use a hashtag followed by case sensitive ID
- **Common pitfall**: overusing ID. Classes will suffice most of the time and ID's should be use **sparingly (if at all)**
- Used when specificity is needed or having links redirect to a section on the current page
- Elements can have only **ONE ID** & **NO WHITESPACE**

```html
<!-- index.html -->
<div id="title">Welcome to the machine.</div
```

```css
/* styles.css */
#title {
  background-color: white;
}
```

### Grouping Selectors

- Used with multiple groups of elements that share style declarations

```css
.read,
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

### Chaining Selectors

- Used to apply styles to a specific combo of selectors
- Must contain all selectors in order for rules to apply
- No space between selectors
- Can't chain multiple `type` selectors (ie: div, p, h1)
  - Because that would give you `divph1`

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
/* elements that contain both classes */
.subsection.header {
  color: red;
}
/* can mix classes and id's*/
.subsection#preview {
  color: blue;
}
```

### Descendant Combinator

- Allow you to combine multiple selectors by their relationship between them
- There are [**4** types of combinators](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#combinators) in total
- Represented by single space between selectors
- Matches the **last selector only**
  - If they also have an ancestor (parent, grandparent, etc.) that matches the previous selector
- `.ancestor .child` would select the class `child` if it has the ancestor with the class `ancestor`
  - If it is **nested** inside of ancestor

```html
<!-- index.html -->
<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"></div>
<!-- D -->
```

In this example, **BOTH B & C** would be selected.

```css
/* styles.css */
.ancestor .contents {
  /* some declarations */
}
```

# Properties

## Color Values

- **Common keywords** (Predefined, Cross-browser)
  - ie: `red`, `coral`, `transparent`
  - [Full List of Pre-defined Colors](https://www.w3schools.com/colors/colors_names.asp)

```css
#p1 {
  background-color: red;
} /* red */
#p2 {
  background-color: transparent;
} /* transparent */
```

- **HEX values**
  - ie: `#ff0000` (red)
  - Specified with `#RRGGBB`
    - `RR`: Red values
    - `GG`: Green values
    - `BB`: Blue values
  - Range: `00` (lowest) to `FF` (highest)

```css
#p1 {
  background-color: #ff0000;
} /* red */
#p2 {
  background-color: #00ff00;
} /* green */
#p3 {
  background-color: #0000ff;
} /* blue */
```

- **HEX values with transparency**
  - ie: `#ff000080`
  - Transparency: Add 2 digitals between `00` & `FF`

```css
#p1a {
  background-color: #ff000080;
} /* red transparency */
#p2a {
  background-color: #00ff0080;
} /* green transparency */
#p3a {
  background-color: #0000ff80;
} /* blue transparency */
```

- **RGB values**
  - ie: `rgb(red, green, blue)`
  - `rgb()` is a _function_
  - Intensity of each value: 0 (lowest) to 255 (highest)

```css
#p1 {
  background-color: rgb(255, 0, 0);
} /* red */
#p2 {
  background-color: rgb(0, 255, 0);
} /* green */
#p3 {
  background-color: rgb(0, 0, 255);
} /* blue */
```

- **RGBA values**
  - ie: `rgba(red, green, blue, alpha)`
  - RGB colors with an **_alpha channel_**
    - Specifies opacity of the object
    - Alpha: 0.0 (fully transparent) to 1.0 (opaque)

```css
#p1 {
  background-color: rgba(255, 0, 0, 0.3);
} /* red with opacity */
#p2 {
  background-color: rgba(0, 255, 0, 0.3);
} /* green with opacity */
#p3 {
  background-color: rgba(0, 0, 255, 0.3);
} /* blue with opacity */
```

- **HSL values**
  - ie: `hsl(hue, saturation, lightness)`
  - Cylindrical-coordinate representation of colors
  - `hsl()` is a function
  - **Hue**: Color Wheel `0` - `360`
    - Red: `0` or `360`
    - Green: `120`
    - Blue: `240`
  - **Saturation**: Percentage value
    - Shade of gray: `0%`
    - Full color: `100%`
  - **Lightness**: Percentage value
    - Black: `0%`
    - White: `100%`

```css
#p1 {
  background-color: hsl(120, 100%, 50%);
} /* green */
#p2 {
  background-color: hsl(120, 100%, 75%);
} /* light green */
#p3 {
  background-color: hsl(120, 100%, 25%);
} /* dark green */
#p4 {
  background-color: hsl(120, 60%, 70%);
} /* pastel green */
```

- **HSLA values**
  - ie: `hsla(hue, saturation, lightness, alpha)`
  - Alpha parameter: `0.0` - `1.0`
    - Fully transparent: `0.0`
    - Fully Opaque: `1.0`

```css
#p1 {
  background-color: hsla(120, 100%, 50%, 0.3);
} /* green with opacity */
#p2 {
  background-color: hsla(120, 100%, 75%, 0.3);
} /* light green with opacity */
#p3 {
  background-color: hsla(120, 100%, 25%, 0.3);
} /* dark green with opacity */
#p4 {
  background-color: hsla(120, 60%, 70%, 0.3);
} /* pastel green with opacity */
```

### Color & Background Color

- **Color** property: text color
- **Background-Color** property: background color of an element

```css
p {
  /* hex example: */
  color: #1100ff;
  /* rgb example: */
  color: rgb(100, 0, 127);
  /* hsl example: */
  color: hsl(15, 82%, 56%);
}
```

## Typography Basics & Text Align

### Font Family

- `font-family` can be single value, or comma-separated list for fonts
- Falls into 1 of 2 categories:
  - Font Family Name: `Times New Roman`
  - Generic Family Name:
    - `sans-serif` have clean lines, modern, minimal
      - ie: Arial, Verdana, Helvetica
    - `serif` are formal, elegant, have small stroke at edge of each char
      - ie: Times New Roman, Georgia, Garamond
    - `monospace` have fixed width, mechanical look
      - ie: Courier New, Lucida Console, Monaco
    - `cursive` imitate human handwriting
      - ie: Brush Script MT, Lucida Handwriting
    - `fantasy` are decorative, playful
      - ie: Copperplate, Papyrus
- If browser can't find 1st font in list, it will use the next one
- **Best Practice:** Include list of values, starting with top preference, and ending with least preferred

```css
font-family: "Times New Roman", sans-serif;
font-family: "Times New Roman", Times, serif;
font-family: Arial, Helvetica, sans-serif;
font-family: "Lucida Console", "Courier New", monospace;
```

### Custom Font Family

- `@font-face` is used for loading custom fonts in browser & present it to site
- Must appear **before other styling properties**
- Requires 2 properties:
  - `font-family` font name
  - `src` URL to download the font

```css
@font-face {
  font-family: fontname;
  src: url(https://fonts.gstatic.com/s/lato/v16/S6u_w4BMUTPHjxsI5wq_Gwftx9897g.woff2);
  font-weight: italic;
}
```

- Alternative: **Linking fonts** in the `<head>`

```html
<head>
  <link
    href="https://fonts.googleapis.com/css?family=Gayathri&display=swap"
    rel="stylesheet"
  />
</head>
```

- Alternative: **Importing fonts** using `@import` to css

```css
@import url("https://fonts.googleapis.com/css?family=Gayathri&display=swap");
```

- [Google Fonts API](https://developers.google.com/fonts/docs/getting_started)

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Inter" />
```

### Font Size

- `font-size` should contain NO whitespace

```css
font-size: 22px;
```

### Font Weight

- `font-weight` affects boldness of text
- Values can be:
  - the word `bold` or a value between `1` - `1000`
  - **Typically** in increments of `100` up to `900`, depending on the font: `200`, `300`, `400`
  - `bold` word equivalent: `700`

```css
font-weight: 700;
```

### Text Align

- `text-align` aligns text horizontally within an element
- Common keywords:
  - `center`, `right`, `left`

```css
text-align: center;
```

### Image Height & Width

- Default `<img>` size = actual image's `height` & `width`
- `auto` value will automatically adjust size of an image without causing it to lose its proportions

```css
img {
  height: auto;
  width: 500px;
}
```

- If the above image had a height of `500px` and width of `1000px`
- `auto` would downsize the `height` to `250px`
- **Best Practices**
  - **ALWAYS** include _both_ height & width for _ALL_ images
  - Reserves space on the page & will appear blank until image loads
  - If `height` & `width` are not included & the image takes longer to load than the rest of the page, the **image will not take up any space on page at first**
  - Will suddenly cause a drastic shift of the other page contents once loaded

## [The Cascade of CSS](https://wattenberger.com/blog/css-cascade)

- Sometimes rules conflict with one another
- CSS does what we tell it to do
- Unexpected behavior can occur due to:
  - _Default styles_ vary from browser to browser
    - ie: Large gaps between elements, button styles, etc. can appear on it's "own"
  - Not understanding `the cascade` or how a `property` works
- **The CSS Cascade is the way our browsers resolve competing CSS declarations.**
  1. **Importance**
     1. **_transition_** - active transitions are #1
     2. `!important` - reserve for overriding 3rd party libraries
     3. **_animation_** - active animation
     4. **_normal_** - bulk of rules
  2. **Origin**, where rules are defined
     1. **_website_**: in your control as web developer
     2. **_user_**
     3. **_browser_**: each browser has its own set of default styles
  3. **[Specificity](#specificity)**
  4. **Position**, rule order

## Specificity

- If two or more CSS rules that point to the same element, the selector with the **highest specificity** value will "win", and its style declaration will be applied to that HTML element.
  - Creates a score or ranking system
- **More specific** CSS declarations > **less specific** CSS declarations
- Specificity only matters when elements have _multiple, conflicting declarations_ (a tie breaker):
- Hierarchy
  1. **Inline** `<h1 style="color: white">`
  2. **Layers** unlayered > layered `@layers one, two;`
  3. **ID** selectors `#navbar`
  4. **Class** `.class`, **Attribute Selectors** `[href]` or `[checked]`, **Pseudo Selectors** `:hover` or `:first-of-type`
  5. **Type** or **Pseudo-eEement** selectors `h1` or `:before`

```html
<div class="main">
  <div class="list subsection"></div>
</div>
```

> **Multiple** classes > **Single** class

```css
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 -- MORE SPECIFIC */
.main .list {
  color: red;
}
```

---

```html
<div class="main">
  <div class="list" id="subsection"></div>
</div>
```

> **ID** selector > **Multiple Class** selectors

```css
/* rule 1 -- MORE SPECIFIC */
#subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```

> **1 ID** & **2 Class** Selectors > **1 ID** & **1 Class** Selector

```css
/* rule 1 */
#subsection .list {
  background-color: yellow;
  color: blue;
}

/* rule 2 -- MORE SPECIFIC */
#subsection .main .list {
  color: red;
}
```

**Chaining Selector** (_no space_) & **Descendant Combinator** (_empty space_) **DO NOT AFFECT specificity**

```css
/* rule 1 -- SPECIFICITY EQUAL TO rule 2 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 -- SPECIFICITY EQUAL TO rule 1 */
.class .second-class {
  font-size: 24px;
}
```

**Universal selector** `*` and **Combinators** `+`, `~`, `>`, ` ` (_empty space_) **DO NOT ADD specificity**

```css
/* rule 1 -- NO SPECIFICITY */
* {
  color: black;
}

/* rule 2 -- MORE SPECIFIC (Type selector) */
h1 {
  color: orange;
}
```

## Inheritance

- CSS Properties, when applied to an element, are inherited by the element's **descendants**
  - Even if we don't explicitly write a rule for it
- **Typography** based properties **ARE USUALLY** inherited
- Most **OTHER** properties **AREN'T** inherited

**Exception**: Directly targeting an element > inheritance

```html
<!-- index.html -->
<div id="parent">
  <div class="child"></div>
</div>
/* styles.css */
```

```css
/* Inherited */
#parent {
  color: red;
}

/* Directly targeted -- TAKES PRECEDENCE */
.child {
  color: blue;
}
```

## Rule Order

- Final factor in a tie-breaker
- If multiple conflicting rules target an element
  - The _last_ defined rule is the winner

```html
<div class="alert warning"></div>
```

```css
.alert {
  color: red;
}

/* defined last, takes precedence */
.warning {
  color: yellow;
}
```

## Adding CSS to HTML

### External CSS

- Most common method
- Create a separate file for CSS
- Link to inside HTML's `<head>` tag with the `<link>` element
  - ie: `<link rel="stylesheet" href="styles.css">`
  - `href` is the location of the CSS file
  - `rel` specifics relationship between HTML & linked file
- Pros of external css:
  - HTML & CSS are separate, smaller HTML, cleaner look
  - Edit CSS in only 1 place, _handy for multiple pages that share similar styles_

```html
<!-- index.html -->
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

```css
/* styles.css */

/* declaration block */
div {
  /* selector */
  /* declarations */
  color: white;
  /* color: property */
  /* white: value */
  background-color: black;
}

/* declaration block */
p {
  /* selector */
  /* declarations */
  color: red;
  /* color: property */
  /* white: value */
}
```

## Internal CSS (Embedded)

- Add CSS within HTML doc itself
- Place all rules inside `<style>` tags, within the `<head>` of the HTML file
  - No longer require `<link>` tag
- Useful for adding _unique styles_ to a _single page_
- Causes HTML files to be larger

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>
  ...
</body>
```

## Inline CSS

- Add CSS tags directly to HTML elements
- Added with the `style=` attribute
- Used when you need a `unique` style for a `single` element
- **NOT recommended**:
  - Gets messy quickly, bloated
  - If you want to share styles among elements, it requires a lot of _copy_ and _pasting_
  - Inline CSS **_overrides_** all other methods, causing unexpected results

## Inspecting HTML & CSS

- Inspecting & Debugging HTML/CSS is criticial to frontend development
- **Chrome Dev Tools** is used to see detailed info & assists in finding/fixing problems in code

### The Inspector

- To access the inspector in Google Chrome
  - `Right Click` on element & click `Inspect Element`
  - `CTRL+SHIFT+C` to Inspect Elements on hover
  - `F12`
  - `CTRL+SHIFT+I` to open the last panel you had open
  - `Arrow Keys` to go up/down and expand elements in DOM
  - `Right Click` on element within DOM and `Scroll into view` to hop to it's location on the page
  - `H` hides currently selected node
  - `Delete` deletes currently selected node
- HTML: Initial page contents
- DOM: current page contents

#### Inspecting Elements (the DOM)

- Blue top left arrow icon: inspect any element on hover
- Elements: HTML
- Styles: CSS Rules
  - ~~Strikethrough~~ - overwritten style

#### Testing Styles

- [Styles pane allows you to directly edit in your browser](https://developer.chrome.com/docs/devtools/css)
  - Add new rules
  - Edit existing rules
- Changes apply in real-time
- Does NOT affect source code
- **Extremely useful** for testing out various attributes & values without having to reload page over and over

#### [Overview of Chrome DevTools](https://developer.chrome.com/docs/devtools/overview/)

- `CTRL+F` Find things in DevTools

##### Device Mode

- Simulate mobile devices

##### Elements panel

- View & change DOM & CSS

##### Console

- View messages & run JavaScript from the Console
- `CTRL+SHIFT+J`

##### Sources Panel

- Debug JavaScript
- Persist changes made in DevTools across page reloads
- Save & run snippets of JavaScript
- Save changes you make in DevTools to disk

##### Network Panel

- View & debug network activity

##### Performance Panel

- Find ways to improve load & runtime performance

##### Memory Panel

- Fix memory problems
- JavaScript CPU Profiler

##### Application Panel

- Inspect all resources that are loaded
  - IndexedDB or Web SQL databases
  - Local & Session Storage
  - Cookies
  - Application Cache
  - Images
  - Fonts
  - Stylesheets

##### Security Panel

- Debug
  - Mixed content issues
  - Certificate problems, etc.

#### [CSS Overview](https://www.freecodecamp.org/news/how-to-use-css-overview-in-chrome-developer-tools/)

- `CTRL+SHIFT+I`, click 3 dot icons > `More tools` > `CSS Overview`
- Click `Capture Overview`
- Menu Options
  - Overview Summary
    - Number of Elements used
    - Selector types
    - Number of inline style elements
    - Number of external stylesheets
  - Colors
    - Each color is clickable
    - Shows which elements use each color
  - Font Info
    - `font-size`, `line-height`, `font-weight`, `font-family`
    - Where they're used
  - Unused declarations
    - Styles that don't affect the web page
  - Media Queries
    - Various widths & screen resolutions used in creating the page
    - ie: `screen` and `(max width:736px)`

## The Box Model

- Most important CSS skills: **positioning** & **layout**
- JavaScript is meaningless if you can't stick elements on the page where you need them
- Every single thing on page is a **rectangular box**
- Boxes can have other boxes in them and can sit next to one another

```css
/* To test the box model: */
* {
  border: 2px solid red;
}
```

> Parts of a box
>
> ![Parts of a box](img/box-parts.png)

- Manipulating boxes & space between them:
  - `border`, space between margin & padding
  - `padding`, space between edge of box & content
    - inside the border
    - includes `background-color`
  - `margin`, space between box & any other boxes next to it
    - **collapse** between two elements
    - highest `margin` value wins
    - outside of the border
    - not affected by `background-color`
  - `height`, `width` size of inner element
- ["True" height of an element](https://www.youtube.com/watch?v=rIO5326FgPE), add all values:
  - `padding` top & bottom
  - `border` top & bottom
  - `height`
- `box-sizing: border-box;`
  - Almost always added to CSS
  - Makes stylizing easier
  - Added to universal selector (`* { }`)
  - Ensures `height` and `width` are obeyed

> Standard CSS Box Model
>
> ![Box Model](./img/standard-box-model.png)

> Border-Box in CSS

![Border-Box](./img/border-box.png)

### Box Types

In CSS, there are two types of boxes. The type refers to how the box behaves in terms of _page flow_ and _in relation_ to other boxes.

- **Block**
  - `display: block`
  - Appear stacked atop each other
  - Each new element creates a new line
  - Fills available _inline_ space of the parent element and _grows_ along the _block_ dimension to accommodate its content
  - **Centering** a block: `margin: auto`
- **Inline**
  - Sizes according to its content
  - Sits inside _content_ of _block-level elements_
  - Do not start a new line
  - Appear _in line_ with with elements they are placed beside
  - ie: `<a>`
  - Generally, don't add extra padding/margin on inline elements
  - **Inline-block** elements
    - Behave like inline elements
    - Have block-style padding & margin
    - Useful, but `flexbox` is better for lining up boxes

Boxes then have an **inner** and **outer** display type.

#### Outer Display Type

- `block` outer display types:

  - Break onto a **new line**
  - Width & Height are respected
  - Other elements will be **pushed away** using padding, margin, border
  - Box extends in _inline_ direction to fill space available in container
    - Become as wide as it's container, 100% of the space
  - ie: `<h1>` and `<p>` use `block` by default

- `inline` outer display types:
  - Will NOT break onto a **new line**
  - Width & Height are NOT applied
  - **Vertical** padding, margins, border WILL apply
    - WON'T push other inline boxes away from the box
  - **Horizontal** padding, margins, borders WILL apply
    - WILL push other inline boxes away from the box
  - ie: `<a>`, `<span>`, `<em>`, `<strong>`

#### Inner Display Type

Inner display types dictate how elements **inside that box** are laid out.

- Default: Elements _inside_ a box are laid out in:
  - **normal flow**
  - Behave as `block` or `inline`
- Change inner display type with `display: flex;`
  - Still uses _outer_ display type `block`
  - _Inner_ display type `flex`

### DIV's & Spans

- DON'T give meaning to their content
- Generic boxes that can do anything
- Used to _hook_ elements
  - Give `id` or `class` to them for CSS styling
  - Grouping related elements under one parent element to _correctly position them_ on the page

#### DIV

- Block-level element by default
- Used as a container to group other elements
- Divs allow us to _divide_ pages into blocks and apply styles to those blocks

#### Span

- Inline-level element by default
- Group text content and inline HTML elements for styling
- Should only be used when no other _semantic_ HTML element is appropriate

### Normal Flow

- Default layout of elements in the Box Model
- Block-level elements
  - `<address><article><aside><blockquote><canvas><dd><div><dl><dt><fieldset><figcaption><figure><footer><form><h1>-<h6><header><hr><li><main><nav><noscript><ol><p><pre><section><table><tfoot><ul><video>`
- Inline-level elements
  - `<a><abbr><acronym><b><bdo><big><br><button><cite><code><dfn><em><i><img><input><kbd><label><map><object><output><q><samp><script><select><small><span><strong><sub><sup><textarea><time><tt><var>`

## [Flex Box](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)

- Flexbox is a way to arrange items into _rows_ and _columns_
- Based on simple rules you can define
- Fill available area w/ _equal width_

```html
<div class="flex-container">
  <div class="one"></div>
  <div class="two"></div>
  <div class="three"></div>
</div>
```

```css
.flex-container {
  display: flex;
  /*
  flex-direction: row
  > start from edge of main axis
  > does not grow on main dimension, but can shrink
  >
  /*
}

/* this selector selects all divs inside of .flex-container */
.flex-container div {
  background: peachpuff;
  border: 4px solid brown;
  height: 100px;
  flex: 1;
}
```

#### Flex Containers & Flex Items

- Flexbox is a **toolbox** of properties to put things where you need them
- Any element can be a **BOTH** a flex **container** & flex **item**
- **Flex Containers**: `display:flex`
- **Flex items**: `flex: 1`
- Creating/nesting multiple flex containers and items is the primary way we will be building up complex layouts

```html

```

```css
/* flex containers */
.container {
  display: flex;
  display: inline-flexinline;
}
```

![Flexbox 1](./img/flexbox-1.png)

![Flexbox 1](./img/flexbox-2.png)

#### Flex Shorthand

- `flex` declaration: **shorthand** for **3 properties**
  - shorthand: CSS properties that allow you to set values of multiple **other** properties simultaneously
- `flex: flex-grow, flex-shrink, flex-basis;`
- `flex: 0, 1, 0%;`

##### Flex-Grow

- `flex: flex-grow, *, *`
- Single number
- Flex-item's **Growth Factor**
  - `flex: 1;` To all DIV's = grow the same amount
  - `flex: 2;` To 1 DIV = 2x the size as `flex: 1;`

##### Flex-Shrink

- Similar to `flex-grow`
- Flex-item's **Shrink Factor**
- **Only applied** if size of ALL flex items is **larger** than their parent
- Default: `flex-shrink: 1;`
  - ie: all items shrink evenly
- If 3 DIV's had `width: 100px;` and their container was _smaller_ than `300px`, the DIV's would have to shrink to fit
- **NO Shrink**: `flex-shrink: 0;`
- **Faster Shrink**: `flex-shrink: 2(+);`

> `flex-grow` and `flex-shrink` do NOT necessarily obey width rules (ie: `250px`)
>
> > if parent is big enough, they grow to fill it
> >
> > > if parent is too small, they shrink to fit

##### Flex-Basis

- Sets initial size of a flex item
- Grow/shrinking starts from this baseline
- Default shorthand value: `0%`
  - ie: `flex: 1` is equal to `flex: 1 1 0%;`
- If you want to **only** adjust an item's flex-grow
- Default value of `flex-basis` is `auto` UNLESS you specify `flex: 1;`
  - `flex-basis: auto;` checks for a **width declaration**
- `flex: auto;` is equal to `flex: 1 1 auto;` (check for width)
- `flex: 1;` is equal to `flex: 1 1 0%` (ignore width)

#### Flex in Practice

```css
/* grow evenly */
flex: 1;
/* prevent shrinking */
flex-shrink: 0;
```

#### Flex Axes

- Flexbox can work _horizontally_ or _vertically_
  - Rows or Columns
- Default: horizontal (row)
  - Alternative: vertical (column)
    - ie: `css .flex-container { flex-direction: column; }`

```css
/* default setting */
flex-direction: row;
flex-direction: row-reverse; /* right to left */
/* columns/vertical flexbox */
flex-direction: column;
flex-direction: column-reverse; /* down to up */
```

- When `flex-direction: column;` is used, `flex-basis` refers to `height`

### Alignment

- To space objects out within a container, you would add `justify-content: space-between;`

```css
.container {
  display: flex;
  justify-content: space-between;
}
```

![Center](./img/justify-content-space-between.png)

- To center objects within a container, you would add:
  - X-axis (horizontally): `justify-content: center;`
  - Y-axis (vertically): `align-items: center;`

```css
.container {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

![Center](./img/justify-content-center.png)

- `gap` adds space between flex items

![Gap](./img/gap.png)

- Multi-line flex **containers**

```css
/* default */
flex-wrap: nowrap;
/* move to item to next line */
flex-wrap: wrap;`
```

![flex-wrap](./img/flex-wrap.png)

#### Flex Flow Shorthand

- Combine flex direction & wrap into one line

```css
flex-flow: flex-direction, flex-wrap;
/* example */
flex-flow: row wrap;
```
