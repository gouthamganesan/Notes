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