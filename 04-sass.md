- What is SASS?

  - CSS Preprocessor

- Why use Sass?

  - To overcome the messy nature that CSS can introduce in a large-scale
    project

- Why is it called a CSS Preprocessor?

  - We write Sass in .scss files and this is then converted into CSS code by a
    Sass Compiler. Since the browser only understand CSS, it only sees the the
    compiler CSS files, and not the Sass files that we had written

- What are the main features of Sass?

  - Variables
  - Nesting to nest selectors inside of one another allowing us to write less
    code
  - Operators for mathematical calculations (inside of CSS directly)
  - Partials and imports to write CSS in different files and import them all
    into a single file
  - Mixins to write reusable piece of CSS code
  - Functions (similar to mixins) but they produce a value that can be reused
  - Extends to make different selectors inherit declarations that are common
    to all of them
  - Control directives (for writing complex code using conditions and loops) -
    Not really used in the real-world; rather for building CSS frameworks

- How is Sass written?

  - It can be written in two formats - .sass and .scss files
  - .scss files look more like regular CSS with curly braces to denote rules
    and semicolons (preferable - Sassy CSS)
  - .sass files use indentation and no semicolons are separators between rules
    which make it harder to convert CSS project into Sass

- How are variables declared?

  - `$<variable_name>: <value>`
  - variables can be used for any value that might need tweaking in future

- How are variables used

  - `<property_name>: $<variable_name>`

- Why is nesting done?
  - To prevent having to use lengthy selectors for targeting an element
  - Use `&` to get to the current nesting level, and add on the further
    selectors

```html
<nav>
  <ul class="navigation">
    <li>
      <a href="#">About Us</a>
    </li>
    <li>
      <a href="#">Pricing</a>
    </li>
    <li>
      <a href="#">Contact</a>
    </li>
  </ul>
  <div class="buttons">
    <a class="btn-main" href="#">Sign Up</a>
    <a class="btn-hot" href="#">Get a Quote</a>
  </div>
</nav>
```

```scss
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

$color-primary: yellow;
$color-secondary: orange;
$color-tertiary: pink;

$color-text-dark: black;
$color-text-light: #eee;

$width-buttons: 150px;

@mixin style-link-text($color) {
  text-decoration: none;
  text-transform: uppercase;
  color: $color;
}

@function divide($a, $b) {
  @return $a / $b;
}

nav {
  margin: divide(60, 2) * 1px;
  background-color: $color-primary;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navigation {
  list-style: none;

  li {
    margin: 20px;
    display: inline-block;

    &:first-child {
      margin-left: 0;
    }

    a {
      @include style-link-text($color-text-dark);
    }
  }
}

.btn-main:link,
.btn-hot:link {
  display: inline-block;
  padding: 10px;
  text-align: center;
  border-radius: 100px;
  width: $width-buttons;
  @include style-link-text(yellow);
}

.btn-main {
  &:link {
    background-color: $color-secondary;
  }

  &:hover {
    background-color: darken($color-secondary, 15%);
  }
}

.btn-hot {
  &:link {
    background-color: $color-secondary;
  }

  &:hover {
    background-color: lighten($color-secondary, 15%);
  }
}
```

- What are `darken()` and `lighten()` in-built functions?

  - Use to change a certain color with a certain percentage value
  - The compiled CSS will contain the hex value of the final output color
    obtained by this operation

- What is a mixin?
  - Its analogous to a variable, but instead of referring to a particular
    value, it references a entire piece of code
  - So it can be thought of as macros in programming languages
  - They can also accept arguments. These need to be provided at the time of
    calling these mixins, and then the mixin can make use of that value inside
    of its code

```scss
@mixin <mixin_name> {
  // scss code
}
@mixin <mixin_name>($<variable_name>) {
  // scss code
}
<any_selection > {
  @include <mixin_name>; // this line will be replaced by code in mixin
  @include <mixin_name>($<variable_name/value>);
}
```

- What is a function?
  - Just like in programming languages, functions can be used to abstract
    away certain complex calculations
  - They too can accept arguments, and return certain value as an outcome of
    certain operations it performs on those arguments

```scss
@function <function_name>($<varuable1>, $<variable2>, ...) {
  // certain operations
  @return <value>;
}

<any_selection > {
  // To get output and convert it into pixels
  <property_name>: <function_name>(<argument1>, <argument2>...) * 1px;
}
```

- What is extends in Sass?
  - Do abide by DRY principles, instead of copying sections of code to certain
    selections (as in the case of mixins), we can copy the selectors themselves
    to where the code is defined. This way we don't have to use the same
    selector more than once
  - These should only be used when there are related components (for eg. if
    two links are styled as buttons in the navbar, then we can use extends as
    they are related to each other - but don't use the same extends for all
    the links in the website that are styled as buttons)
