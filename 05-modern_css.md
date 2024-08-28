## CSS VARIABLES

- Defined inside the `:root` pseudo class
- Defining variables - `--<variable_name>: <value>;`
- Using variables - `<css_property>: var(--<variable_name>)`

```css
:root {
  --clr-dark: #000;
  --clr-light: #fff;
}

body {
  background-color: var(--clr-dark);
  color: var(--clr-light);
}
```

## ANIMATIONS

- What are the two ways of creating animations in CSS?

  - Transitions
  - Animations

- What are Transitions?

  - Wait until a property change occurs and allows that change to take place
    over time
  - Without a transition any change would take effect immediately
  - Should be used when properties are changed interactively

- What are animations?

  - Animations provide keyframes for more control over the animation
  - Allows us to create a complex animation on a frame-by-frame basis
  - To be used when we don't want to wait for properties to change
    interactively

- How to create transitions?
  - We need a component that has a property that can be changed interactively
  - Not all elements can be transitioned. Only those having states such as
    `hover`, `click`, or defined by JavaScript

```css
.btn:hover {
  transform: translate(0, -10px);
  background-color: green;
  color: orange;
}

.btn {
  transition-property: transform; /* the property that will be changed */
  transition-duration: 0.3s; /* Should be 0.2s to 0.5s */
  transition-timing-function: ease; /* ease-in, ease-in-out (ease) */
  transition-delay: 0.1s; /* Time after which transition will start (0) */
  transition:
    transform 0.3s ease-in 0.2s,
    color 0.1s ease-in-out;
  transition: all 0.3s; /* Change all properties with 0.3s duration */
}
```

    - Each quadruple set can be used in a short-hand separated by commas for
    different properties

- How to create animations?
  - We need an element that we want to animate
  - General format - `@keyframes <name> { from {...} to {...} }`

```css
@keyframes slideInLeft {
  from {
    transform: translate(-300px, 0);
  }
  to {
    tranform: translate(0, 0);
  }
}

@keyframes bounce {
  /* No need to be in order */
  0%,
  50%,
  100% {
    /* Analogous to from */
    transform: translate(0, 0);
  }

  25% {
    tranform: translate(0, -30px);
  }

  /* 50% {
		transform: translate(0, 0);
	} */

  75% {
    transform: translate(0, -15px);
  }

  /* 100% {
		transform: translate(0, 0);
	} */
}

.heading-1 {
  animation-name: slideInLeft; /* Keyframe name */
  animation-duration: 1s;
  animation-timing-function: ease; /* ease-in, ease-out, ease-in-out */
  animation-delay: 1s; /* (0) default */
  animation-iteration-count: infinite; /* (1), 2, ... */
  animation-direction: normal; /* reverse - it goes to->from */
  animation-fill-mode: both;

  animation: slideInLeft 1s ease-in-out infinite both; /* shorthand */
}
```

## MEDIA QUERIES

- We can set `media screen () {}`, `media speech () {}`
- Using breakpoints at the widths where website layout breaks can result in a
  large number of media queries - Prefer to use a mobile-first approach by adding a container class to all
  the sections. This will help in alignment, as well as we can reduce the
  width of the container for predefined screen size widths

```css
.container {
  width: 100%;
  margin: 0 auto;
  padding: 0 0.5rem;
}

/* xs */
@media (min-width: 475px) {
  .container {
    max-width: 475px;
  }
}
/* sm */
@media (min-width: 640px) {
  .container {
    max-width: 640px;
  }
}
/* md */
@media (min-width: 768px) {
  .container {
    max-width: 768px;
  }
}
/* Use other media queries for 1024px, 1280px, 1536px */
```

- Use min-width for mobile-first approach; max-width for desktop-first
  - min-width means the styles will be applied on screen size above breakpoint
  - max-width means the styles will be applied on screen size below breakpoint

```css
@media (max-width: <length_unit>) {
	...
}
```

## CSS UNIT DEEP DIVE

- What are the types of units in CSS?
  - Absolute - provide fixed size to each element they are applied to. For eg.
    `cm`, `mm`, `in`, `px` (only px should be used)
  - Relative - relative to viewport size or font size. For eg. `vh`, `vw`

### PIXEL UNIT

- Output of dimensions is dependent on anchor unit
- Pixel is the anchor unit for displays with different resolutions. So the
  measurement is dependent on the reference pixel. Generally 1px = 1/96 of an inch
- But if we draw a box of 96px x 96px and view it on different displays with
  different resolutions (phones, monitors, TVs) we will get different lengths
- This is because the reference pixel changes depending on the viewing
  distance. Since the viewing distance for each device is different, so the
  reference pixel size is different, and so the px is also of different size. So
  pixel is a measurement of unit that is relative to the expected viewing
  distance of the device being used

### em AND rem UNITS

- Don't use px for font-sizes for accessibility reasons. Use rem for font sizes
  - If we change the default font size in the browser settings, and the font
    sizes in our webpage is set using px instead of rem, then the font will
    not scale with the change in the browser settings
- Use em for paddings, margins and width as this will relative to the element's
  own font-size. So this can be calculated easily. Also when the root font size is
  changed the margin, padding and widths will grow with them and make the layout
  responsive

### VIEWPORT UNITS AND PERCENTAGE

- % is relative to the parent. Use this for components related to layout
- Use vw and vh when you want to size relative to the viewport. This can be used
  in max-width situations

### CH UNIT

- Measures the size of character '0' on your font and set it equal to 1ch
- We can use this to set a max-width on a paragraph to prevent a long text line
  as the maximum line length should be 75 characters
