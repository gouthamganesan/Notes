# HTML5

## Basics
* Most HTML elements have an opening `<tag_name>` and closing tags `</tag_name>`.
* There are 6 different levels of subheadings as in, `<h1>`, `<h2>`, `<h3>`...
* `p` is for paragraph. For example, `<p>I'm a p tag</p>`
* `Lorum ipsum` has been used as a placeholder for many centuries and it will be highly useful in web dev too.
* `<!-- Comment -->`. That'll do.
* Some of the HTML tags include, `main`, `header`, `footer`, `nav`, `video`, `article` and `section`.
* `main` tag helps search engines and other developers to find the main content of the page.
  * There should be only one `main` tag in a document.
  * The content inside the main tag should be the one that is unique to that particular page and they should not be the ones that are duplicated. Some of the examples of contents that are common to more than one web pages are header, footer, sidebar nav, etc.

## `img` tag
`<img src="https://www.your-image-source.com/your-image.jpg">` is used to display images in our page.
* The `src` attribute points to specific image's URL.
* The `img` tag is self-closing.
* All `img` tags must have `alt` attribute, which displays an alternate text if the image could not render.
  * In case of images that are purely for decorative purpose, use an empty `alt` attribute.

## Anchoring!
`<a href="url">Text to hyperlink</a>` (anchor tag) is used to hyperlink the text inside the tag.
   * The `href` attribute is where we will give the link to hyperlink.
   * The anchors can also be used to create internal links to jump to different sections of the web page.
     * To do that, first we must assign those elements to which the link to refer to with an `id` attribute.
     * Then use that `id` given in the `href` attribute of the `a` tag with a `#` prefix. For example,
         ```html
         <a href="#contacts-header">Contacts</a>
         ...
         <h2 id="contacts-header">Contacts</h2>>
         ```
   * The `target="_blank"` attribute to the anchor tag is used to open the link in a new tab.
   * The anchor element (tag) can be nested within other text elements. For example, 
      ```html
      <p>Click here to view more <a href="http://freecatphotoapp.com" target="_blank">cat photos</a>.</p>
      ```
   * Adding an anchor tag with `href="#"` will create dead links. Dead links are used when,
     * You don't know where the link will be pointing to at that point of time. 
     * You want to change the link dynamically with JS.
   * Anchor elements can nest images too! so that the image will point to the specified URL.
     * You can include as many elements as you want in the anchor tag.

## Lists
* Unordered list is indicated by `<ul>` tag and ordered list are indicated by `<ol>` tag. 
* The list elements are added with `<li>` tag. For example,
    ```html
    <ul>
       <li>Item 1</li>
       <li>Item 2</li>
    </ul>
    <ol>
       <li>Step 1</li>
       <li>Step 2</li>
    </ol>
    ```

## Forms - Getting inputs from the users

### Basic Input tag
* Input elements are used to get input data from the user through the webpage. This can be achieved using, the `input` tag. For example, `<input type="text" placeholder="Enter some text">`
  * There are many types of input that can be obtained from the user. The type of the input is specified by the `type` attribute.
  * `input` tags are self closing.
  * `placeholder` attribute holds the text that should be shown before the user enters anything in the input field.

### Form tag
* Form elements, represented as `form`, can be used to submit data to a server. For example,
   ```html
   <form action="/url-where-you-want-the-data-to-be-submitted">
      <input type="text" placeholder="Username" required>
   </form>
   ```
   **NOTE:** You can specify the `required` keyword as an attribute to make that input field mandatory. So until the user enters a value for that field, the user would not be permitted to submit the form.

### Buttons
* Buttons can be added using the `button` tag.
  * Just like `input` tag, this also has a `type` attribute to specify the type of button that is.
  * The text that is to be used on the button is wrapped between the `button` tag as in, `<button type="submit">Submit</button>`.
  * It is not a self closing tag and requires a closing tag, with the text that is to be displayed surrounded by both of the tags.

#### Radio buttons
* Radio buttons are a type of input which should be associated inside a `<label>` tag. 
  * By wrapping an `input` element (radio) inside of a `label` element it will automatically associate the radio button input with the element surrounding it. The text that comes after the `input` tag is the text element that is associated to the radio button.
  * All related radio buttons should have the same value for the `name` attribute. Otherwise they will multi-selectable, like checkboxes. Associating all the related radio buttons with a same `name` tag will make it a group to select only one among them.
  * Always set a `for` attribute on the `label` tag which matches the value of `id` attribute of the `input` child element in it, to created a linked relationship. For example,
      ```html
      <label for="indoor">
         <input id="indoor" type="radio" name="indoor-outdoor">Indoor
      </label>
      ```

#### Checkboxes
* For questions where more than one answer is needed Checkboxes are used. 
* To use checkboxes give the `type` attribute as `checkbox` for `input` tag.
  * Just like the radio buttons, each of the checkbox should be nested within its own `label` element by wrapping the `input` element inside the `label`.
  * All the checkbox inputs should have the same `name` attribute, it they are related.
  * Just like radio buttons, use `for` in `label` and `id` in the `input` with a same name (identifier) to create a link between the two.
     ```html
     <label for="loving"><input id="loving" type="checkbox" value="loving" name="personality">Loving</label>
     ```

#### `value` attribute 
* The radio or checkbox need an identifiable `value` attribute which will be sent along with the `name` attribute when the form is submitted.
  * Each of the `radio` or `checkbox` input element should have a unique `value` attribute to identify the selected option.
  * When the form is submitted, the value is transferred as `<name>=<value_of_selected>`. For example, `personality=loving` if the label 'Loving' is selected.
    * If the `value` attribute is not present, then the default value that is transmitted is `on`, which is not very helpful.

#### Default selected input using `checked` attribute
* Mentioning the `checked` attribute will make that particular `radio` or `checkbox` selected by default.
  ```html
  <label for="loving"><input id="loving" type="checkbox" value="loving" name="personality" checked>
  ```

## The `div` tag
* The `div` tag means division element, which is a non-self-enclosing one.
* It will be used as a container for other elements.
   ```html
   <div>
      <!---
      Enter the elements that should be contained here
      --->
   </div>
   ```

## Structure of a HTML document
* We should tell the browser which HTML version to use using the `<!DOCTYPE html>` tag. Here, `html` tells the browser to use **HTML5** which is the latest version and most of the browsers support HTML5. 
* Just after the DOCTYPE is declared, you should open a `<html>` tag that will enclose all the contents of the page. 
  * It will be closed at the end of the page.
* To add more structure to the web page, you can use the, `head` and `body` tags to wrap around all the meta data that informs about the page (which is recognised by the search engines) and the actual content that the users sees, respectively.
  * Meta elements such as, `link`, `meta`, `title`, `style` typically go into the `head` tag.