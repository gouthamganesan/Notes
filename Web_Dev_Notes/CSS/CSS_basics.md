# Introduction to Basic CSS

* Cascading Style Sheet (CSS) tells the browser how to display the text and other content you write in HTML.
* CSS is case sensitive so be careful with your capitalizations. It has been adopted by all major browsers and allows to control,
  * color
  * fonts
  * positioning
  * spacing
  * sizing
  * decorations
  * transitions
* There are three ways to add CSS to the web page.
  1. Adding inline `style` attribute to the HTML elements itself.
  2. Adding a separate `style` tag with all the required rules in the HTML document.
  3. Writing CSS rules in an external style sheet and referencing the same in the HTML document. (*Most preferred* as they keep the styles separate from the HTML elements, which improves the readability and usability of the code).
     * The idea behind using a separate CSS is that you can use a selector to target an HTML element in the DOM (Document Object Model) and then apply a variety of attributes to that element to change the way it is displayed.
       * [Document Object Model](https://en.wikipedia.org/wiki/Document_Object_Model): *The Document Object Model (DOM) is a cross-platform and language-independent interface that treats an XML or HTML document as a tree structure wherein each node is an object representing a part of the document. The DOM represents a document with a logical tree*.

---

* Each HTML element can have a `style` attribute.
* Properties in CSS are rules that can be changed to change the way the element is displayed. Some of the properties in CSS are, `background`, `color`...There are hundreds of CSS properties that can be used.
* To change the color of a text element (say, a h2 element), `<h2 style="color: blue;">CatPhotoApp</h2>`.
  * It is a good practice to end inline `style` declarations with a `;`.
  * Styling like this, inline styling, is used to style only that particular element.
* Adding a `style` block at the top of the code, like,

    ```html
    <style>
        h2 {
            color: red;
        }
    </style>
    ```

  * This will change the way all the `h2` elements look. Here `h2` is called as a *Selector*, which selects all the specified elements.
* Using a `class` attribute will allow us to name a few element and apply style rules to those particular elements. Classes are reusable styles that can be added to HTML elements.
* To assign an element with a class name, use the `class=class_name` attribute in that element.
* And to use styles for that particular class, use the class_name prefixed with a period, instead of a selector. For example,

    ```html
    <style>
        .blue_text {
            color: blue;
        }
    </style>
    <h2 class="blue_text">Hello, world</h2>
    ```

  * **Note:** The class attribute in the HTML element does not start with a period, and in the `style` element it does.
* The main advantage of using classes is that you can assign the same class to multiple elements to reuse style on all those elements.
* The font size of an element can be adjusted by the `font-size` property. The value can be set in pixels. Like, `font-size: 16px`. Some of the other units the size can be represented are,
  * Absolute-size keywords, `xx-small`, `x-small`, `small`, `medium` `large`, `x-large`, `xx-large`, `xxx-large`. These are based on the user's default font size (which is equalled with `medium`)
  * `<length>` value. There are many font-relative units, such as `em` or `ex` which are relative to parent element's font size, and root-based units like, `rem` in which the font size is relative to the font used by the `<html>` root element.
  * `<percentage>` is relative to the parent element's font size.
  * **Pixels:** Setting the value in pixels, tells the browsers to display the content at the exact pixel height which is specified.
    * Using `px` for setting font size is not recommended for web pages if they are needed to be inclusive. As the browsers will not allow the font size to be changed by the user, users with limited vision might find it difficult to read if the font size is set too small for them.
  * **`em`** The size of an `em` value is dynamic. The size of `em` is relative to its parent's font size. If there is no font size set anywhere on the page, the browser's default value is taken, which is `16px`. So then `1em=16px`. Then the font size is multiplied by the number of ems. If the font size is set to be `20px` in the parent, then `1em=20px` and `2em=40px` and so on.
    * In order to calculate the em equivalent of any pixel value required then,
      * `em = desired element pixel value / parent element font-size in pixels`
    * The em is a very useful unit in CSS, since it automatically adapts its length relative to the font it chooses to render.
    * `em` values  **compounding**. Compounding means, multiple font-sizes being relative in the hierarchy. A inner element is relative to its parent, which is again relative to its own parent element.
  * For more detailed documentation - [MDN Web Docs by Mozilla](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size)
