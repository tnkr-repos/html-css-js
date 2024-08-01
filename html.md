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