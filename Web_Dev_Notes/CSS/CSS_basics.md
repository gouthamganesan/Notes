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