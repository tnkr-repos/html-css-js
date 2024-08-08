- CSS - Cascading Style Sheets
- Used to format the content (properties such as font, spacing, layout, etc.)
- [CSS Rules](./images/css-rules.png)
- How can CSS be written:
    - Inline - Inside the HTML element using the `style` attribute (Don't use)
    ```html
    <h1 style="color: blue">Hello World</h1>
    ```
    - Internal - Inside the `style` element in the `head` element of HTML file.
    This provides better separation of concerns, but can be a problem if there
    is a lot of CSS
    ```html
    <head>
        <style>
            h1 {
                color: blue;
            }
        </style>
    </head>
    ```
    - External - Writing CSS rules inside another css file, and link the file to
    the HTML document to be styled
    ```html
    <head>
        <link rel="stylesheet" href="<path_of_css_file>" />
    </head>
    ```
    ```css
    h1 {
        color: blue;
    }
    ```
- Styling has to be done for `li` elements, and not `ol` or `ul`
    - To remove bullets use `list-style: none;` declaration
- Combining selectors:
    - List selectors - Add multiple selectors separated by comma (`h1, h2 {}`)
    - Descendant selector - Selector a particular child tag inside a parent tag
    (`footer p {}` selects all `p` in `footer`). But this encodes our HTML
    structure into our CSS selectors, and this will be difficult to maintain in
    future if HTML structure changes. Use `id` or `class` selectors instead
- Element selector - Using the element tag
- ID/CLASS selector - Add `id/class` attribute to an HTML element select using
that. The difference between them is that we can't reuse `id` values on the same
HTML document, but we can do so with `class` attribute values (for values with
multiple words use dashes and not underscores as per convention). Although in
the real world we never work with ids, its always classes for future proofing

## TYPOGRAPHY

- `font-family: system-ui, sans-serif` - Ideal for website (to remove the small
edges on letters and use system font instead of loading a custom font)
- `font-style: italic` - To italisize the letters
- `text-transform: uppercase/capitalise` - To change the case
- `font-size: 26px` - Set size of font
- `text-align: left/right/center/justify-all` - Text alignment
- `line-height: 1.5` - Recommended for normal font sizes (spacing between lines
will be 1.5 times that of the font-size)
- `font-weight: bold/100/200/.../900` - For boldness of font

## COLORS

- [RGB Model in CSS](./images/rgb_model.png)
- [Color Representation in CSS](./images/rgb_notation.png)
- Grey is formed when all colors have equal values (#000 - black; #fff - white;
#444 - dark grey for fonts; $b7b7b7b - light grey for backgrounds)
- `color` - Defines text color
- `background-color` - Defines color of page

## PSEUDO CLASSES

- `:first-child`, `:last-child`, `:nth-child(odd/even)` - Dealing with HTML
structure
- They don't work great when we mix multiple elements inside a parent element,
but work great when all the child elements are the same (like in a `ul` or `ol`)

## BOX MODEL

- Everything is a box on the web
- Box Model applies to everything on the web. It consists of:
    - Content - Width and height of an element
    - Padding - Adds space inside of an element
    - Border - 
    - Margin - creates extra space around an element which pushes away the other elements away
- To view an element's box model in Dev Tools - Select the element using the `Element Selector` tool and go to the `Computed` tab
```html
<div class="box">
    Hello World
</div>
```
```css
.box {
    font-size: 2rem;
    background-color: pink;

    /* BOX MODEL */
    display: block; 
    height: 100px;
    width: 300px;

    /* padding-top -> padding-right -> padding-bottom -> padding-left */
    padding: 32px;
    padding: 32px 100px;
    padding: 32px 100px 64px;
    padding: 32px 100px 32px 64px;

    /* size style color */
    border: 5px solid black;
    /* border-top; border-bottom; border-right; border-left */

    /* margin-top -> margin-right -> margin-bottom -> margin-left */
    margin: 20px;
    margin: 20px 40px;
    margin: 20px 40px 20px;
    margin: 30px 30px 30px 30px;
}
```
- If you select an element in Dev Tools and go to the `Styles` panel, you will get the `user agent stylesheet` showing the default styles applied by the browser
- Under normal circumstances, `border` and `padding` are inside the block element, and when calculating the net effective `height` and `width` ofthe element, we need to add them up. This is tedious, so use `box-sizing: border-box` (normally it is `box-sizing: content-box`)
```css
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

## CSS RESET

## INFINITE SCROLL ANIMATION (MARQUEE) USING CSS ONLY

- Concept:
    - Bunch of `div` are positioned `absolute` so that they move out of the flow of the page
    - Then we place them to the right outside of their container, and animate them to move to the left. This would move all the `div` elements together towards the left and we would be able to see only 1 `div` (the topmost one) moving from right to left
    - Loop them so that the scrolling keeps happening infinitely
    - Add different delays for each so that they all start moving towards the left at different times, but move at the same rate, thus giving an illusion that they are all scrolling one after the other
    - Add gradients at the edges to get the complete effect
```html
<body>
    <div class="wrapper">
        <div class="item item-1"></div>
        <div class="item item-2"></div>
        <div class="item item-3"></div>
        <div class="item item-4"></div>
        <div class="item item-5"></div>
        <div class="item item-6"></div>
        <div class="item item-7"></div>
        <div class="item item-8"></div>
    </div>
</body>
```
```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
.wrapper {
    border: 1px solid black;
    width: 90vw;
    max-width: 2000px;
    margin: auto;
    position: relative;
    height: 100px;
    margin-top: 5rem;
    overflow: hidden;
}
.item {
    width: 200px;
    height: 100px;
    background-color: red;
    border-radius: 10px;
    position: absolute;
    left: 100%;
    animation-name: scrollleft;
    animation-duration: 30s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
}

@keyframes scrollleft {
    to {
    left: -200px;
    }
}

.item-1 {
    animation-delay: calc(30s / 8 * (8 - 1) * -1);
}
.item-2 {
    animation-delay: calc(30s / 8 * (8 - 2) * -1);
}
.item-3 {
    animation-delay: calc(30s / 8 * (8 - 3) * -1);
}
.item-4 {
    animation-delay: calc(30s / 8 * (8 - 4) * -1);
}
.item-5 {
    animation-delay: calc(30s / 8 * (8 - 5) * -1);
}
.item-6 {
    animation-delay: calc(30s / 8 * (8 - 6) * -1);
}
.item-7 {
    animation-delay: calc(30s / 8 * (8 - 7) * -1);
}
.item-8 {
    animation-delay: calc(30s / 8 * (8 - 8) * -1);
}
```

## CONTAINER QUERIES

- Allow responsiveness depending upon the size of the container (and not that of the entire viewport)
- This allows us to use the same component in different sections of the page with different layouts (depending on the container size) -> If we use media queries then the same styling to apply to both components, and thus to achieve different styling we would need different components. [For Example](./images/container_queries.png)
```html
<div class="container">
    <div class="card"></div>
    <div class="card"></div>
    <div class="card"></div>
</div>
```
```css
.container {
    /* container-type: size for different styling depending on height and width of the container both taken into account; inline-size is just for container width */
    container-type: inline-size;
    /* any container name */
    container-name: card-container;
}

/* similar to media query syntax -> difference being the name included between the @container and parentheses */
/* can use min-width (for mobile-first) or max-width (for larger screens first) */
@container card-container (min-width: 800px) {
    /* the styling for the components */
    .card {...}
}
```

## POSITIONING

- If you simply place element in HTML, they will move other elements around it

- Use CSS Positioning to insert elements into pages without altering the position of other elements

- `top, right, bottom, left` properties are unlocked when the `position` attribute is assigned a value

- `position: absolute`
    - The element gets removed from the document. No space is created for them, and other elements are placed as if the element with absolute positioning never existed
    - The `top, right, bottom, left` attributes are calculated from the page. If you want them to be calculated based on the element's container, the container should have `position` attribute (any value will work except `static` which is the default `position` value)
    - If you want the popped-out element to stack underneath the normal page, use `z-index: -1`
    - If you are placing element using the `top, right, bottom, left` attributes and a horizontal scroll-bar is appearing, just add `overflow-x: hidden` to the `body` element
- `position: relative`
    - The element remains in the normal flow of the document, but has access to `top, right, bottom, left` properties as well as `z-index`
- `position: fixed`
    - The element is removed from the normal flow of the document just like `absolute`
    - The difference with `absolute`


## CSS GRID

- `display: none` - To remove something completely from the webpage (other elements will shift as if the hidden element was never even created)
- Grids have Grid Containers and Grid items
- `display: grid`
- `grid-template-columns: <width_value1> <width_value2> ... <width_valuen>` - Define as many width values as you want, and n number of columns will be created as per the specified widths. As many rows will be created as per requirement to accomodate the items
- If we define a `height` or `width` for a cell, the whole row or column will adjust to accomodate the cell. We say that the grid items stretch to fill
- We can manually set the row's height to allow the grid items to stretch to the specified height (unless the grid item already has a height defined to it) - `grid-template-rows: <height_value1> <height_value2> ... <height_valuen>`
- To give space between items, `margin` won't work. Use `gap` (or `column-gap` and `row-gap`) - `gap: 30px`
- Putting `grid-template-columns: 1fr 1fr 1fr` will create 3 columns with equal width, and they will change at the same rate. If we put `grid-template-columns: 1fr 1fr auto` then the 3rd column will take only the space necessary for its content, and the remaining space will be divided equally between the 1st and 2nd columns
- We can do the same with explicit rows as well (the rows which are created and for which we explicitly define the height - any row created due to residual items is called implicity row). The height of a row (and thus the `fr` unit) will be determined by the tallest item in the row
- To get grid items to span multiple cells we can use `grid-column: <start_column_no> <end_column_no>` (we can use either the positive column number or the negative column number). If we don't want to do the math, just use the start column number followed by the `span` word (`grid-column: <start_column_no> span <number_of_columns>`). Same can be done to `grid-row` to span across rows

## COMPONENTS AND LAYOUT PATTERNS

- 