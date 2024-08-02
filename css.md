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