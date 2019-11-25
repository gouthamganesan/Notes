# Applied Visual Design

* Visual Design in web development is a broad topic. It combines typography, color theory, graphics, animation, and page layout to help deliver a site's message.

## Points to note

* Text make up a very big part of the web. So it is important to present them properly. We can use the `text-align` property to align the text properly on the web page.
* You can use the `width` and `height` property to set the respective of any element.
* Using the `<strong>` HTML tag and enclosing elements is similar to applying a `font-weight: bold;` property to an element. Both are read by the browser the same and the text is rendered Bold.
* Like wise, `<u>` tag and `text-decoration: underline;` does the same. Both underlines the text.
  * Since anchor tags too have the same underlined format, use them both carefully as they might confuse.
* The `em` (emphasis) HTML tag and `font-style: italic;` italicizes the text.
* The `s` tag and `text-decoration: line-through;` property strikes-through the text.
* `<hr>` self-closing tag is used to add a horizontal line across the width of its containing element.
  * This can be used to represent change in topic or separation of groups.
* Like `hex` and `rgb()` there is color representation format called `rgba()` which is similar to `rgb()` but where `a` refers to the alpha/opacity level which ranges from `1` which is fully opaque to `0` which is fully transparent.
* It is important to have differentiating `font-size` for the users to understand the hierarchy of the content.
* `box-shadow` element applies one or more shadows to an element.
  * The property takes values for `offset-x`, `offset-y`, `blur-radius`, `spread-radius` and `color` in that order. (The `blur-radius` and `spread-radius` values are optional)
  * For example, ```box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);```. This will create multiple shadows with some blur, at mostly transparent black colors.
    * If only 2 values are given then they are taken as offset-x and offset-y.
    * Third value is interpreted as blur-radius.
    * Fourth value is interpreted as spread-radius.
    * Add the `inset` keyword to change the default drop shadow to one inside the frame.
    * Add the color value to give a color to the shadow.
* We have a `opacity` property to change the opacity of the said element. It can have values from 0 to 1 (from fully transparent to fully opaque).
* `text-transform` property changes the appearance of the text without having to change the content of the HTML manually.
  * It can have keywords like, `lowercase`, `uppercase`, `capitalize` (first letter capital), `initial` (use the default value), `inherit` (use the `text-transform` value of the parent element) and `none` (use the original text).
* The `font-size` property can be used to change the size of the font and `font-weight` property shows how thick or thin characters are in a section of text. These properties can be applied to any element that contains text.
* `line-height` property is used to change the height of each line in a block of text.
* There are different 'states' to an element. `pseudo-classes` can be used to select a particular state of an element and style that state.
  * For example, the `hover` pseudo call of anchor can be used to give CSS rules for/when the element is hovered.
  
  ```html
  <style>
    a {
        color: black;
    }
    a:hover {
        color: blue;
    }
  </style>
  <a href="http://freecatphotoapp.com/" target="_blank">CatPhotoApp</a>
  ```

  * In the above example, the anchor element when hovered will turn to the set value blue. Otherwise it would be in the set value black.
* [CSS box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model#content-area): All the HTML elements are considered as a box.
* There are two types of element layout
  * Block-level items - These will automatically start on a new line (think headings, paragraphs and div).
  * Inline items - They sit within the surrounding content (like images or spans).
  * The default layout of elements in this way is called the *normal flow* of a document. But CSS offers a property to override it.
  * When the `position` of an element is set to `relative`, we can specify how the element should be moved relative to its current position. It pairs with **offset** properties `left` or `right` and `top` or `bottom`. These properties can have a length value that specifies how far the element should be from its original placement.
    * For example, `top: 15px;` offsets the element `15px` below its default placement.
    * Changing an element's position to relative does not remove it from the normal flow - other elements behave as if the element is in its default position. And because of this behavior overlapping can happen, if we are not careful.
    * We are offsetting an element away from a given spot, which moves the element away from the referred side.

![CSS Offset properties](https://cdn-media-1.freecodecamp.org/imgr/eWWi3gZ.gif)

* The next option for the CSS `position` property is `absolute`, which locks the element in place relative to its parent container. Unlike the `relative` position, this removes the element from the normal flow of the document, so surrounding items ignore it. The CSS offset properties (top or bottom and left or right) are used to adjust the position.
  * One nuance with absolute positioning is that it will be locked relative to its closest positioned ancestor. If you forget to add a position rule to the parent item, (this is typically done using `position: relative;`), the browser will keep looking up the chain and ultimately default to the body tag.
  * Like `relative` this would also result in overlapping if not the elements are placed correctly.
* Similar to the other layout scheme there is `fixed` position, which is a type of absolute positioning that fixes the element relative to the browser window.
  * This takes it out of the normal flow of the element like other position types and requires layout adjustments to correctly place other surrounding elements in place.
  * This is used with the offset properties of CSS like, `top`, `bottom` and others to fix the position.
  * The key difference between the `fixed` and `absolute` is that the element with fixed position would not move when the user scrolls.
  * These are mostly used for navbar elements and headers which needs to be fixed in their place.
* `float` property
  * Floating elements are removed from the normal flow of a document and pushed to either the `left` or `right` of their containing parent element.
  * This will be particularly helpful to divide the webpage into columns and have the content and the sidebar placed on them, side by side.
* When we set `position` with `absolute | relative | fixed | sticky` the element is removed from the normal flow of the document but the surrounding elements are unaware of that change and continue to stay in the same position. So because of this there will be overlapping of elements.
  * So when the elements are overlapped, the element that comes later in the HTML markup will be placed on top of the other element.
  * `z-index` property will let us customize which element comes at top of the other. It takes an integer value which specified which element comes on top of which with the higher value. So higher the value, higher it would be.
* We can center a block element horizontally by many ways. One of them is to use, `margin` with a value `auto`.
  * This works for images too, which are by default inline elements. But we can change that to a block element by using the `display: block;` property.
* Colors that are opposite in the color wheel will produce vibrant color patterns.
  * Secondary colors are the ones that are the result of combining two primary colors. For example, magenta is made with red and blue. But this complements the third primary color (which is not involved in its creation). In our case, magenta is complement to green.
  * Tertiary colors are the result of combining a primary color with a secondary one.
  * Split-complementary scheme is one of the methods of combining and choosing colors for the web page.
    * This scheme starts with a base color, then pairs it with the two component that are adjacent to its complement. The three colors provide strong visual contrast in design but are more subtle than using two complementary colors.
