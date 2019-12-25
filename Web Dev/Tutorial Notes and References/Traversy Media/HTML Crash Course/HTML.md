# HTML5

---

- **NOT** a programming language.
  - Just a markup language for creating webpages/documents.
- They are the building block of the web.
- Home page should always be named, `index.html`. That is the default workflow.
- **Tag syntax**
  - `<tagname attributename="attributevalue">content</tagname>`
- There is a very structure to a HTML document.<br>
  <a href="./htmlcheatsheet/Screenshot&#32;2019-11-26&#32;at&#32;9.42.23&#32;PM.png" target="_blank">
  <img src="./htmlcheatsheet/Screenshot&#32;2019-11-26&#32;at&#32;9.42.23&#32;PM.png" width=600>
  Tutorial Notes and References/Traversy Media/HTML Crash Course/htmlcheatsheet/Screenshot 2019-11-26 at 9.42.23 PM.png
  </a>
  <br>
  <!-- ![Structure of HTML document](Screenshot&#32;2019-11-26&#32;at&#32;9.42.23&#32;PM.png) -->
- Declaration should always be the first in a HTML document. (Doctype).
  - `<!DOCTYPE html>`
- Then after that `<html>` will enclose the whole document.
- `<head>` contains information that are not displayed on the web page but contains data like metadata which can be used for SEO and stuff.
  - `<title>` tag contains the title which is display in the tab name.
- `<body>` tag contains the things that are rendered in the web page.
- `<p>` is a block level element. This is because it has a display block.
- The default browser styling is `user agent stylesheet` which can be seen in the developer options.
- Tags can be
  1. Inline elements
     - Only takes the space that is needed and does not start with a new line.
     - Examples: `<span>`, `<img>`, `<a>`
  2. Block elements
     - Starts on a new line and takes full width available.
     - Examples: `<div>`, `<h1>` - `<h6>`, `<p>`, `<form>`
- `<strong>` (inline tag) conveys that the text that this contains is by default **bold**ed.
- `<em>` is for emphasis (similar to `<strong>`)
- For `<li>` elements there is a default padding (`40px`).
  - List elements are usually the ones on the nav bar.
- `<table>` is used to create tables in HTML.

  - Inside the `<table></table>` there are `<thead>` and `<tbody>` which says table heading and table body content respectively.
  - Inside the `<thead>`, the whole heading row should be enclosed within `<tr>` and each table heading should be enclosed between `<th>`.
  - Likewise inside the `<tbody>` each row should be enclosed within `<tr>` and each table data should be enclosed between, `<td>`.

  ```html
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Age</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Goutham</td>
        <td>gouthamganesan98@gmail.com</td>
        <td>21</td>
      </tr>
      <tr>
        <td>Saravana</td>
        <td>saravanak98@gmail.com</td>
        <td>21</td>
      </tr>
    </tbody>
  </table>
  ```

  - Tables were previously used to create layouts, like sidebar, main area and another sidebar. But not now.

- **Form**
  - With HTML we can get the look of the form. But without any other programming language it is not gonna be functional.
  - Attribute `action="something.php` which will submit the form to that mentioned page.
  - Attribute `method="POST"`. This means we are giving `POST` request to the server. POST requests are usually used to add data to a database and stuff like that. It is pretty secure as opposed to `GET` as the data gets filled in, on the URL.
  - In HTML5 we have a input type `email` which will take care of basic email validation.
  - Instead of `<input>` we can also use `<textarea></textarea>` which will give a big textarea for input.
  - We can give a list of options to "select" from (Drop down/Select list) using the `<select>` and `<option>` tags.
    - The `<option>` tag is usually associated with a value tag.
  - There are also other `<input>` types called, `number` and `date`.
  - There is both `value` and `placeholder` attribute to all the `input` elements.
    - The `value` attribute specifies the value it should contain by default. To change it the user should manually erase the value and enter their own value.
    - The `placeholder` attribute specifies the placeholder which is greyed out and disappears when the user clicks on the field.
  - There is a `type` called, `submit` which can be used to submit the form.
    - For example, `<input type="submit" name="submit" value="Submit">`.
    - Here the value is the actual text of the button.
  - There is also a `<button>Button Name</button>` which can be clicked. We can make it dynamic using a programming language.
- Images can be rendered using the self-closing `<img src="image path" alt="Contains the alternate text which is useful in places where the images can't be shown" width=300 height=auto>` tag.
- Quotations can be used in the webpage to cite something that is said from some other page (web page).
  - `<blockquote cite="https://somesite.com">Quote that is to be said</blockquote>`
  - The `cite` is not displayed in the web page but will be useful for other developers to know where this comes from.
- `<abbr title="World Wide Web">WWW</abbr>` is used to abbreviate text. This text will be underlined and the value in the `title` will be shown on hovering.
- There is also a `<cite>Cite content</cite>` tag which can be used to tell the browser that this is cited. The content in the `cite` tag will be shown in italic.
- HTML5 Semantic tags.<br>
  <a href="./htmlcheatsheet/Screenshot 2019-11-27 at 8.46.25 AM.png">
  <img src="./htmlcheatsheet/Screenshot 2019-11-27 at 8.46.25 AM.png" target="_blank" width=300>
  </a>

- Refer the `blog.html` for more understanding of Semantic tags.
- The `<head>` tag can contain `meta` tags which are used by search engines to searches and rank your web page.
  - `<meta name="what the meta tag is about" content="the actual meta data">`
  - These are not displayed in the web page but will be used by the search engines.

---

Continues at [CSS Crash Course](<../CSS Crash Course/CSS.md>)
