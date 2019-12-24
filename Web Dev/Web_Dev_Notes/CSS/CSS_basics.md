# Introduction to Basic CSS

For detailed explanation about a specific property refer, [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/CSS).

## Basics of CSS

- Cascading Style Sheet (CSS) tells the browser how to display the text and other content you write in HTML.
- CSS is case sensitive so be careful with your capitalizations. It has been adopted by all major browsers and allows to control,
  - color
  - fonts
  - positioning
  - spacing
  - sizing
  - decorations
  - transitions
- There are three ways to add CSS to the web page.
  1. Adding inline `style` attribute to the HTML elements itself.
  2. Adding a separate `style` tag with all the required rules in the HTML document.
  3. Writing CSS rules in an external style sheet and referencing the same in the HTML document. (_Most preferred_ as they keep the styles separate from the HTML elements, which improves the readability and usability of the code).
     - The idea behind using a separate CSS is that you can use a selector to target an HTML element in the DOM (Document Object Model) and then apply a variety of attributes to that element to change the way it is displayed.
       - [Document Object Model](https://en.wikipedia.org/wiki/Document_Object_Model): _The Document Object Model (DOM) is a cross-platform and language-independent interface that treats an XML or HTML document as a tree structure wherein each node is an object representing a part of the document. The DOM represents a document with a logical tree_.

### Ways of styling and Property declarations

- Each HTML element can have a `style` attribute.
- Properties in CSS are rules that can be changed to change the way the element is displayed. Some of the properties in CSS are, `background`, `color`...There are hundreds of CSS properties that can be used.
- To change the color of a text element (say, a h2 element), `<h2 style="color: blue;">CatPhotoApp</h2>`.
  - It is a good practice to end inline `style` declarations with a `;`.
  - Styling like this, inline styling, is used to style only that particular element.
- Adding a `style` block at the top of the code, like,

  ```html
  <style>
    h2 {
      color: red;
    }
  </style>
  ```

  - This will change the way all the `h2` elements look. Here `h2` is called as a _Selector_, which selects all the specified elements.

- Using a `class` attribute will allow us to name a few element and apply style rules to those particular elements. Classes are reusable styles that can be added to HTML elements.
- To assign an element with a class name, use the `class=class_name` attribute in that element.
- And to use styles for that particular class, use the class_name prefixed with a period, instead of a selector. For example,

  ```html
  <style>
    .blue_text {
      color: blue;
    }
  </style>
  <h2 class="blue_text">Hello, world</h2>
  ```

  - **Note:** The class attribute in the HTML element does not start with a period, and in the `style` element it does.

- The main advantage of using classes is that you can assign the same class to multiple elements to reuse style on all those elements.

## Properties

### font

- The font size of an element can be adjusted by the `font-size` property. The value can be set in pixels. Like, `font-size: 16px`. Some of the other units the size can be represented are,
  - Absolute-size keywords, `xx-small`, `x-small`, `small`, `medium` `large`, `x-large`, `xx-large`, `xxx-large`. These are based on the user's default font size (which is equalled with `medium`)
  - `<length>` value. There are many font-relative units, such as `em` or `ex` which are relative to parent element's font size, and root-based units like, `rem` in which the font size is relative to the font used by the `<html>` root element.
  - `<percentage>` is relative to the parent element's font size.
  - **Pixels:** Setting the value in pixels, tells the browsers to display the content at the exact pixel height which is specified.
    - Using `px` for setting font size is not recommended for web pages if they are needed to be inclusive. As the browsers will not allow the font size to be changed by the user, users with limited vision might find it difficult to read if the font size is set too small for them.
  - **`em`** The size of an `em` value is dynamic. The size of `em` is relative to its parent's font size. If there is no font size set anywhere on the page, the browser's default value is taken, which is `16px`. So then `1em=16px`. Then the font size is multiplied by the number of ems. If the font size is set to be `20px` in the parent, then `1em=20px` and `2em=40px` and so on.
    - In order to calculate the em equivalent of any pixel value required then,
      - `em = desired element pixel value / parent element font-size in pixels`
    - The em is a very useful unit in CSS, since it automatically adapts its length relative to the font it chooses to render.
    - `em` values **compounding**. Compounding means, multiple font-sizes being relative in the hierarchy. A inner element is relative to its parent, which is again relative to its own parent element.
  - For more detailed documentation - [MDN Web Docs by Mozilla](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size)
- The font family of an element can be using the `font-family` property.

  ```html
  <style>
    p {
      font-family: "Source Code Pro", monospace;
    }
  </style>
  ```

  - The fonts that we give in the `font-family` property is used in the same order we give, when the previous font is not available. So make sure to give a fall back font value if the first one seems ambiguous.
  - And also, if the font name contains space then they should be enclosed by double quotes as shown.
  - Font names are case sensitive.
  - We can also use custom web fonts on our website. [Google fonts](https://fonts.google.com/) is a free web library to use.
  - These web fonts can be used in the web site just by referencing the font's URL in the CSS.
  - To import a google font you can copy the font(s) URL from the Google font library and then paste it in your HTML before using it, like `<link href="font-URL" rel="stylesheet" type="text/css">`
  - Now the font can be used in the CSS as shown in the example.
  - Generic fonts like `monospace`, `serif` and `sans-serif` are not case sensitive as they are CSS keywords. They are used so that if the give font is not available then they can be degraded to this value.

### Sizing of elements

- Just like fonts other elements, images in this case, can be resized to a specified px value. This can be done using the `width` keyword.
  - By default it sets the width of the content area, but if `box-sizing` is set to `border-box` it sets the width of the border area.
  - `width` can also have values like, `em` and percentage `%` and also keyword values like, `max-content`, `min-content`, `available` etc.
- There are border properties like, `border-width`, `border-style` and `border-color` to surround a HTML element with a border. For example,

  ```html
  <style>
    .thin-red-border {
      border-color: red;
      border-width: 5px;
      border-style: solid;
    }
  </style>
  ```

  - There are many properties for customizing borders ([Refer here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Backgrounds_and_Borders) for more) like, `border-radius`.

- **NOTE:** For applying more than one class to a HTML element separate them with space as in, `<img class="class1 class2">`
- When there are more number of classes assigned to a same HTML element, it is considered as in, list down all the properties set in all the assigned classes and apply them. So giving a property in one class or the other depends on the class usage, like how the class is going to be reused for other components.
- There are background properties like, `background-color`. These properties when set to HTML elements will allow the element and all the other elements inside it to have that color unless overridden.
- In addition to `class` each HTML element can have an `id` attribute as a `Selector`. This will be particularly helpful to identify elements to modify them with JS.
  - It is best practice to have the `id` of an element to be unique from others.
- While styling, `id` attribute can also be used as style name (instead of element tags like `h2` and class names by `.class-name`) by using the `#` sign as in, `#id-name { properties; }`.
  - Although the `id` are not reusable so should be applied to only one element.
  - Styling with `id` has more specificity (precedence/importance) so, when both `class` and `id` are used for styling, the style with the `id` is taken.
- All HTML elements are essentially rectangles. Three important properties control the space that surrounds each HTML elements: `padding`, `margin` and `border`. They can be assigned a `px` value.
  - `padding` is the amount of space between the element's content and its `border`.
  - `margin` controls the amount of space between the element's `border` and surrounding elements.
    - If there are two elements (top and bottom) the largest `margin` will be the space between them.
    - If you set an element `margin` to a negative value, the element will grow larger.
  - Just like properties like, `border-radius`, `padding` and `margin` is also shorthand for, `-top`, `-right`, `-bottom` and `-left` properties. This is known as 'Clockwise notation' and can be implemented as, `padding: 10px 20px 10px 20px;` for top, right, bottom, and left respectively.
  - **TIP:** For more details on how these properties affect the HTML elements look into the 'Styles' tab of 'developer tools'.
- In addition to `class` and `id` selectors we have spoke about earlier, we can also specify, `[attr=value] { properties; }` and this will apply the said properties to all the elements which has the `attr`'s value as `value`. For detailed explanation on all the available types of attribute selectors, [click here](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors).

  ```html
  <style>
    [type="radio"] {
      margin: 20px 0px 20px 0px;
    }
  </style>
  ```

- There are two types of units in CSS.
  - **Absolute**, like, `px` which we have been using so far. There are also other absolute units including, `mm` and `in` for millimeter and inches. These absolute values amount to the actual distance on the screen (though might differ slightly due to resolution of screens).
  - **Relative**, like, `em` and `rem` which are relative to another `<length>` value. `em` for example is relative to the `font-size` of the element in topic. If the `font-size` itself is set in `em` then it is based on the `font-size` of the parent element.

## Inheritance and variables

- Every HTML page has a body element which is at the top of the hierarchy for inheritance.
- All the elements inside another element, will inherit the style of the parent element.
- For example, if we give properties to the `body` element then all the elements in the page will inherit from the `body` element.
- If we manually style an element which inherits styles from a parent, then the manual values override the inherited one.
- For example,

  ```html
  <style>
    body {
      background-color: black;
      font-family: monospace;
      color: green;
    }
    .pink-text {
      color: pink;
    }
  </style>
  <h1 class="pink-text">Hello World!</h1>
  ```

- Here the `h1` element inherits the `background-color`, `font-family` and the `color` property from the `body` selector's style.
- But the `h1` is also styled by the `pink-text` class which has a `color` property. So the `color` property inherited from the `body` element will be overridden here.
- If we declare another style after `pink-text`, say, `blue-text` with `color: blue` and add the same class to the `h1` the `pink-text` will be overrode by the `blue-text`.
  - Although the order in which the classes are listed in the element doesn't matter, what matters is the order of styles declaration and since `blue-text` is declared after the `pink-text`, the `blue-text` has higher precedence.
  - This proves that browsers read CSS from top to bottom and the lowest one takes higher precedence.
- There are other ways to override CSS, using the `id` attribute. If we give an element an `id` attribute (remember `id` attributes should be unique for each element) and use the `id` to style the component as in `#id-value` then this takes more precedence than the class declarations.
  - `id` declarations override class declarations, regardless of where they are declared (well on top or lower on the bottom in the style element or CSS)
- Just like the `id` declarations overrode class declarations, inline styling overrides `id` declarations.
- Sometimes it is needed to defy the natural CSS hierarchy and enforce a style over its overriding components. This can be done by using the `!important` keyword along with the property declaration. For example, `color: red !important;` makes this particular component the un-override-able and use the property value declared here for styling.
- We can also represent colors using [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal). In CSS we use 6 hexadecimal digits to represent colors, two each for Red, Green and Blue. For example, `#000000` is black and also the lowest possible value.
- 6 digits gives us the possibilities of over 16 million colors. We can use shortened value using only 3 digits, where one value corresponds to RGB. This reduces the total number of possibilities to 4000.
- We can also represent colors using RGB values like, `rgb(0, 255, 255)`, where the values represent r, g and b (brightness of each colors) respectively and can take values from 0 to 255. The number of colors `RGB` and hexadecimal gives are the same.
- We can use CSS variables to change multiple values at once. To create a CSS variable use a variable name with `--` prefix and its value after a `:`, like, `--variable-name: value`.
- To refer to the variable after declaring it, use can use the `var` keyword like in, `var(--variable-name)`.
- We can attach a fallback value while using the variable in a place by, `var(--variable-name, fallback-value)` this way, if there is no declaration or an invalid value in the declaration the property will have a fallback value. **Note** This is just for the said purpose and not for increasing browser compatibility.
- The declaration of the variable and its scope are mostly handled by the natural CSS inheritance. For non-trivial projects it is a good practice to declare the variables in the `:root` (_pseudo_) class selector and use it as needed in the document. We can also declare them in `body` tag's style thus making it available for all the other tags.
- Declaring a variable in the `:root` selector will set the value for that variable for the whole page. You can override the value of that variable inside another area, by declaring another value.
- **_Questions_**: How are classes inherited? How are classes/values overridden? What makes a class a subclass of another?
- It is important to provide browser fallbacks. For example, if there is some problem with our properties the browser should have something to fallback to. Otherwise it will fallback to the browser default values, which is simply not ideal.
- To provide browser fallbacks, declare a fallback value which is widely available which immediately BEFORE your declaration. Like in the below

```html
<style>
  :root {
    --red-color: red;
  }
  .red-box {
    background: red;
    <!--This is read first by the browser and executed -->
        background: var(--red-color);
    <!--This is read second. If this is not available then ... -->
        <!-- it will stay with the above value or else this value will be used -->
        <!-- This happens because of the precedence order. -->
        <!-- Properties which are declared latest has more precedence than the ones that are declared before -->
        height: 200px;
    width: 200px;
  }
</style>
<div class="red-box"></div>
```

- Using media queries to change the value of a variable.
- _Media queries are useful when you want to modify your site or app depending on a device's general type (such as print vs. screen) or specific characteristics and parameters (such as screen resolution or browser viewport width)._<sup>[[1]](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)</sup>
- For instance if the screen is smaller then we have to make adjustments to our absolute values. This can be done by,

```html
<style>
  @media (max-width: 350px) {
    :root {
      --penguin-size: 200px;
    }
  }
</style>
```
