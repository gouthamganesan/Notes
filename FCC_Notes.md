# Chapter 1: Basic HTML and HTML5
1. Most HTML elements have an opening `<h1>` and closing tags `</h1>`
2. There are 6 different levels of subheadings as in, h1, h2, h3...
3. `p` is for paragraph. `<p>I'm a p tag</p>`
4. Lorum ipsum has been used as a placeholder for many centuries and it will be highly useful in web dev too.
5. `<!-- Comment -->`
6. Some of the HTML tags include, `main`, `header`, `footer`, `nav`, `video`, `article` and `section`.
7. `main` tag helps search engines and other developers to find the main content of the page.
8. **`img` tag**
   1. `<img src="https://www.your-image-source.com/your-image.jpg">`
   2. The `src` attribute points to specific image's URL.
   3. The `img` tag is self-closing
   4. All `img` tags must have `alt` attribute, which displays an alternate text if the image could not render.
      1. In case of images that are purely for decorative purpose, using an empty `alt` attribute is the best practice.
9. `<a href="url">Text to hyperlink</a>` (anchor tag) is used to hyperlink the text inside the tag.
   1.  The `href` attribute where we will give the link to hyperlink.
   2.  The anchors can also be used to create internal links to jump to different sections of the web page,
       1.  To do that, first we must assign those elements to which the link to refer to with an `id` attribute.
       2.  Then use that `id` given in the `href` attribute of the `a` tag with a `#` prefix. For example,
            ```html
            <a href="#contacts-header">Contacts</a>
            ...
            <h2 id="contacts-header">Contacts</h2>>
            ```
   3.  The `target="_blank"` attribute to the anchor tag is used to open the link in a new tab.
   4.  The anchor element (tag) can be nested within other text elements. For example, 
      ```html
      <p>Click here to view more <a href="http://freecatphotoapp.com" target="_blank">cat photos</a>.</p>
      ```
   5. Adding an anchor tag with `href="#"` will create dead links. Dead links are used when,
      1. You don't know where the link will be pointing to at that point of time.
      2. You want to change the link dynamically with JS.
   6. Anchor elements can nest images too! so that when the image will point to the specified URL.
      1. You can include as many elements as you want in the anchor tag.
10. Unordered list is indicated by `<ul>` and ordered list are indicated by `<ol>`. Inside the list elements are added with `<li>`. For example,
    ```html
    <ol>
          <li>Item 1</li>
          <li>Item 2</li>   
    </ol>
    ```
11.  Input elements are used to get input data from a webpage. This can be achieved using, the `input` tag. For example, `<input type="text" placeholder="Enter some text">`
   1. There are many types of input that can be obtained from the user. The same is specified by the `text` attribute.
   2. `input` tags are self closing.
   3. `placeholder` attribute holds the text that should be shown before the user enters anything in the input field.
12.  Form elements can be used to submit data to a server using the `form` element. For example,
    ```html
    <form action="/url-where-you-want-the-data-to-be-submitted">
      <input type="text" placeholder="Username" required>
    </form>
    ```
13.  Buttons can be added to add to the interaction using the `button` tag.
    1.  Just like `input` tag, this also has a `type` attribute to specify the type of button that is.
    2.  The text that is to be used on the button is specified inside the `button` tag as in, `<button type="submit">Submit</button>`.
    3.  It is not a self closing tag and requires a closing tag, with the text that is to be displayed surrounded by both of the tags.
14. Adding a `required` attribute in the input element will make the entry as mandatory and would not allow the user to submit the form until the user provides that input.
15. Radio buttons are a type of input which should be associated inside a `<label>` tag. 
    1.  All related radio buttons should have the same value for the `name` attribute. Otherwise they will multi-selectable, like a set of check box. Associating all the related radio buttons with a same `name` tag will make it a group to select only one amo ng them.