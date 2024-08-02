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

- Use the correct element for the job
- Why?
  - Search Engine Optimisation - Search engines use web crawlers, and if the page is not semantic, it won't be able to understand the contents of the webpage, thus ranking it low
  - Accessibility - Visually impaired users take the help of screen readers to access the web. If the HTML is not semantic, then screen readers won't be able to do their job properly
  - Maintainability - Reading and modifying the code becomes tough
- Semantic sectioning refers to grouping content together. General format of website:
  - Header section (containing a navigation section)
  - Hero image
  - A main content section
  - Article section
  - Aside sections
  - Footer section
- To group content together:
  - `div` - Generic container which is non-semantic and has no effect on the content or layout
  - `header` - Introductory information of a page or `section`. It displays the title of the website, maybe a logo, and always a navigation
  - `nav` - Used when grouping a list of links. It represents the menu of a page or `section`
  - `main` - For the main content of the page. Everything except the `header` and `footer` goes inside the `main` element. Should be only 1 per page
  - `article` - Self-contained independent and reusable group of content meant to exist independently of the page on its own
  - `section` - Used to group together nearby content, and represents a standalone section of page but lacks a bit of semantic meaning, so it is used inside an `article` element
  - `footer` - Positioned at the bottom of the page representing the ending of the body. If contains contact information, social links, and some navigation similar to a header menu