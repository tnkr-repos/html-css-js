# ANYTHING ELSE WILL BE ADDED ON A NEED TO KNOW BASIS

- Entry point of every website is `index.html` and it should be present in each
website
  - To create different webpages keep creating and linking HTML documents

- HTML - HyperText Markup Language
- Used to structure and describe the content of a webpage
- It consists of elements that describe different types of content
- [Elements vs Tags](./images/elements-vs-tags.png)
- `DOCTYPE` is to denote the browser that this document is an HTML document, and
`html` tells the browser to use the HTML5 specification to render this document,
instead of their default behavior of using different rendering modes which might
cause incompatibility errors
- Attributes are pieces of data that are used to describe an element
- HTML ignores whitespaces (even multiple spaces added in content)

## HTML ENTITIES

- Used to represent special characters on a webpage that cannot be typed
directly in an HTML document
- General format - `&<code>;`

## HTML ELEMENT

- Referred to as the `root` element and all code is written inside of this
- Has exactly 2 children - `<head>` and `<body>`

## HEAD ELEMENT

- For content not visible to us on the browser window (such as `meta` elements,
`link` to CSS files and favicons, and `title` of browser tab)

## BODY ELEMENT

- For content that is visible on the browser and browser tabs (most content)

## META TAGS

- Inside the `head` element
```html
<meta http-equiv="Content-Type" content="text/html;charset=UTF-8" />
<meta name="viewport" content="width=device-width,initial-scale=1.0" />
<meta name="description" content="Description of Website" />
<meta name="keywords" content="Key, Words, For, SEO" />
```

## LINKING FILES

- Use the `link` tag
```html
<link rel="stylesheet" href="<path_to_css_file>" />
<link rel="shortcut icon" href="<path_to_ico_file>" type="image/x-icon" />
```

## HEADINGS

- `h1` through `h6` tags
- Only 1 `h1` element per page

## PARAGRAPHS

- `p` tag
- To insert line break between two blocks of text, close one `p` tag and open
another

## LISTS

- Ordered Lists - `<ol><li></li>...</ol>`
- Unordered lists - `<ul><li></li>...</ul>`

## FORMS

- Form element - `<form action="" method="GET/POST">...</form>`

- Input element types - Can be divided into 4 categories:
  - User Profile Info Data
  ```html
  <input type="text" placeholder="Full Name" />
  <input type="email" placeholder="Email Address" />
  <input type="password" placeholder="Min 6 characters" />
  <input type="file" />
  <input type="url" placeholder="GitHub Link" />
  ```
  
  - Dates
  ```html
  <input type="time" />
  <input type="datetime-local" />
  <input type="date" />
  <input type="month" />
  ```

  - Boxes
  ```html
  <input type="radio" />
  <input type="checkbox" />
  <input type="range" min="" max="" value="" step="" />
  <input type="number" />
  ```

- Form labels - For UX
```html
<form action="" method="GET/POST">
  <!-- Recommended Approach -->
  <label for="name">Name</label>
  <input type="text" name="name" id="name" placeholder="Full Name" />

  <!-- Not Recommended, but works -->
  <label for="email">
    Email ID
    <input type="email" name="email" id="email" placeholder="Email Address" />
  </label>

  <label for="password">Password</label>
  <input type="password" name="password" id="password" placeholder="Minimum 6 Characters" />

  <label for="profile_pic">Profile Picture</label>
  <input type="file" name="profile_pic" id="profile_pic" />

  <label for="social">GitHub Link</label>
  <input type="url" name="social" id="social" placeholder="GitHub Profile Link" />
</form>
```

- For large text (such as feedback comments)
```html
<label for="comments"></label>
<textarea id="comments" name="comments" placeholder="Please provide Feedback" rols="10" cols="30"></textarea>
```

- To change the inline element behavior of `label` and `input` elements, wrap the whole `form` element in a `ul` element, and individual `label-input` pairs inside `li` tags

- Button element
```html
<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button disabled>Disabled Button</button>
```

## SEMANTIC HTML

- Use the correct element for the job (`strong` for important text, `em` for
emphasised text)
- Why?
  - Search Engine Optimisation - Search engines use web crawlers, and if the
  page is not semantic, it won't be able to understand the contents of the
  webpage, thus ranking it low
  - Accessibility - Visually impaired users take the help of screen readers to
  access the web. If the HTML is not semantic, then screen readers won't be able
  to do their job properly
  - Maintainability - Reading and modifying the code becomes tough
- Semantic sectioning refers to grouping content together. They won't change the
layout of the webpage in any way. General format of website:
  - Header section (containing a navigation section)
  - Hero image
  - A main content section
  - Article section
  - Aside sections (doesn't always needs to be a sidebar)
  - Footer section
- To group content together:
  - `div` - Generic container which is non-semantic and has no effect on the
  content or layout
  - `header` - Introductory information of a page or `section`. It displays the
  title of the website, maybe a logo, and always a navigation
  - `nav` - Used when grouping a list of links. It represents the menu of a page
  or `section`
  - `main` - For the main content of the page. Everything except the `header`
  and `footer` goes inside the `main` element. Should be only 1 per page
  - `article` - Self-contained independent and reusable group of content meant
  to exist independently of the page on its own
  - `section` - Used to group together nearby content, and represents a
  standalone section of page but lacks a bit of semantic meaning, so it is used
  inside an `article` element
  - `aside` - Information that complements the information present in the `main`
  section of the page
  - `footer` - Positioned at the bottom of the page representing the ending of
  the body. If contains contact information, social links, and some navigation
  similar to a header menu
  - `menu` - For various actions that can be performed (specifically for web
  applications)

## IMAGES

- Use the `img` tag
- Attributes:
  - `src` - To denote the path
  - `alt` - Description of the image for SEO, accessibility and if the image
  doesn't load then it will be shown on the webpage instead
  - `width` / `height` - To describe the intrinsic size of image
  - `margin` / `padding` - works even though `display: inline` because it is a
  replaced element (works like an `inline-block`)
```html
<img src="<path>" alt="<Description>" width="<width_in_px>"
  height="<height_in_px>" />
```

## VIDEO

- Use the `video` tag
- Attributes
  - `src` - To denote the path (store the video file in `public` directory)
  - `width/height` - To denote size of the video
  - `controls autoplay loop muted` - Boolean attributes (if they are present
  that means true, and if absent that means false)
- Instead of an `alt` attribute, add a `p` tag inside the `video` tag content to
describe in case the video fails to load
```html
<video src="<path>" width="<width_in_px>" height="<height_in_px>" controls
  autoplay loop muted>
  <p>Video Description</p>
</video>
```

## HYPERLINKS

- Pointing outside of our website
  - `<a href="<url>">Display Text</a>`
  - To open link in a new tab use attribute `target="_blank"` and add
  `rel=noopener noreferrer` always alongside `target`
```html
<a href="http://"></a>
<a href="mailto:"></a>
<a href="tel:+"></a>
```

- Pointing inside our website to a different page or section
  - `<a href="<path_of_html_file>">Display text</a>`
  - For `index.html` we can use `<a href="/">Home Page</a>` as `/` refers to the
  `index.html` page always

- For placeholder links (links which don't actually point to any real URL) can
be made by adding `#` in the `href` attribute value - `#` refers to the current
webpage

- Use `title=<x>` attribute to provide information about the hyperlink when
hovering over the link

- To link to different sections of a webpage, add an `id` global attribute to
the element to be linked, and use `<a href="#<id_name>">Some Text</a>`

## RANDOM ELEMENTS

- Horizontal line in webpage - `<hr />`
- Line break in paragraph - `<br />`
- Block level element take up the entire width of the container or viewport,
thus rendering the next element underneath it
- Inline element take up only the width of the content, thus rendering next
element next to it. To make an inline element as block, use the `display`
property in CSS, or enclose the inline element in a block level element (`div`)
- Comments - `<!-- comments -->` (use sparingly only to describe why the code
does as it does)
- Image hyperlinks can be created by enclosing an `img` element inside `a` tags
