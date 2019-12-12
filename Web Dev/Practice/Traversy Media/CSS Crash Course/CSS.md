# CSS crash course

[Link to Youtube Video](https://www.youtube.com/watch?v=yfoY53QXEnI)

* There are many ways to do the same thing. So everyone's CSS is different.
* There are techs like Sass and Less which helps to extend CSS.
* There are 3 main ways of adding CSS to HTML.
  * Inline CSS: Horrible practice.
  * Internal CSS: Using `<style>` tags within a single document. Better than the above Inline method, but still bad. Limits to using the CSS only on that file.
  * External CSS: Linking an external `.css` file. This separates the presentation from the style which is the best practice and also allows the CSS to be reused on a variety of files (just linking the file to the HTML will do).
* To link an external CSS file in a HTML file use the `link` tag as in, `<link rel="stylesheet" href="path_to_css">`. This will link that `css` to the `html` file.
* CSS Selectors.<br>
  <a href="Screenshot 2019-12-06 at 6.52.08 AM.png" target="_blank">
    <img src="Screenshot 2019-12-06 at 6.52.08 AM.png" width=600>
  </a>
<br>

* Web safe fonts are those that are already available in the browsers and need not require any importing of "Web fonts".<br>
  <a href="Screenshot 2019-12-06 at 7.02.33 AM.png" target="_blank">
    <img src="Screenshot 2019-12-06 at 7.02.33 AM.png" width=600>
  </a>
<br>


* IDs should be unique and classes can be reused.
* Using length values like % is encouraged for responsive design, instead of pixels.
* Box model in CSS:
  * There are 4 things mainly.
    1. Content
    2. Padding
    3. Border
    4. Margin
  * Content is our element. It can be a div, a, h1 or anything. Content is the actual object we are specifying there.
  * Border is the area that surrounds the element. It is the outer most edge of that element. Border area comprises of the element and the padding.
  * Margin is the space outside of that border.<br>
  <a href="Screenshot 2019-12-07 at 3.20.55 PM.png" target="_blank">
    <img src="Screenshot 2019-12-07 at 3.20.55 PM.png" width=400>
  </a>
  <br>
  * For all shorthands that deals with 4 directions the order is -> Top, Right, Bottom, Left.
  * For just giving 2 values (Top = Bottom and Right = Left) -> Top, Right.
  * For all values equal -> Value
* Using just an `*` as a selector will set the properties to everything.
* Using containers inside containers might come in handly and might be tricky.
  * For example, at [32:58](https://youtu.be/yfoY53QXEnI?t=1978), he refreshed and the content stayed in the middle. But mine didn't. It went to the left. I checked with the dev tools, and found that the already mentioned `margin: auto;` property got overridden by the newly said `margin` values. This happened only for me and not for him because, while assigning the classes to the `div` he used a `div` inside a `div` (Container inside a container) and assigned the classes individually. What I thought was that only for the purpose of assigning classes we can use the same `div` and added both the classes in the same `div` element. So when both the classes are assigned to the same `div` element and had same properties said again, the most recent value got accepted and the `auto` got overridden. Using a container inside a container will prevent this. This can further be enhanced to having multiple containers inside a container. Kinda like a group of groups in figma.

```css
.box-1 h1 {
    
}
```

* The above is used to target a selector inside a selector. The above will be applicable for `h1` inside the `box-1` class and not the other `h1`s. This will be applicable for all kinds of selectors.
* Here while putting a unnumbered list, we put the class in the `div` that surrounds the `ul`. But the class can be assigned directly to the `ul` itself. In CSS, we can do the same thing in many different ways and with practice we can find our way of doing things.
* The `border-radius` property is used to give rounded corners.
* Links have different states (hover and such).
* `border-bottom` and all those other properties that refer the position or side of the properties also are a shorthand for all the styles like size, style and color. Eg. `border-bottom: dotted 1px #333`
* The `link-style-image` can also be used to use an image as a bullet. 
  * PS: Remember to change the size of the image to the actual needed size or you might get surprised.
  * If the file is not found then the default bullet is used.
* Padding for `li` only affects the actual content, i.e. not the bullets. To apply for the bullets too apply for the `ul` element.
* To change an element from inline to block level, use the CSS property, `display: block;`

```css
.my-form input[type="text"]{
    padding: 8px;
    width: 100%;
}
```

* The above selector chooses the `input` tags inside the `.my-form` class, but only those whose `type="text"`

```css
.my-form input[type="text"], .my-form textarea{
    padding: 8px;
    width: 100%;
}
```

* We can also target multiple selectors using the `,` as separator as shown above.
* The states (like hover and such) can be applied to almost all elements.
* The property `float: left;` will let the element float and making it align side by side.
  * When you float an element, be sure to give width as that will make the elements align side by side.
  * And when you use width and use the exact available area for the elements alone then there won't be any for the paddings and the borders.
  * So `box-sizing: border-box;` will tell the browser that the width that you have mentioned is not the the content inside the box but the box itself. So that the paddings and borders are included in the box.
  * The `box-sizing` property can have only two values. `content-box` and `border-box`. Learn more at [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)
  * Flexbox takes care of this very nicely.
  * When you float a set of elements the elements that comes next are messed up on position. For that you have to `clear` the element for float. Using the property `clear: both;` will set it right. The clear CSS property sets whether an element must be moved below (cleared) floating elements that precede it. Learn more at [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/clear).
    * Clearing the float is more important. Floating an element will make it an out-of-flow element. Therefore it won't affect the surrounding elements as an in-flow element would. Read more about it in [Stackoverflow](https://stackoverflow.com/questions/2062258/floating-elements-within-a-div-floats-outside-of-div-why).
    * This `clear` property is applied to an empty `div` after the floating elements. Kinda like a break.
* **Positioning**
  * Static
    * It is the default of all. This just renders the position in order like in the document flow.
  * Relative
    * The elements are positioned relative to the normal flow. It falls naturally but we can add properties like top, left, right and bottom to position the element relative to the original position.
  * Absolute
    * This will allow us to target where ever we want to position the element inside a relative element.
    * This is mostly used to place an element at some absolute position with respect to another element. If another element is not mentioned, then default body element will be its reference point.
    * Changing this really helpful to build games that has to do with CSS.
  * Fixed
    * It will always be in the same position irrespective of the scroll position and where ever we are in the page.
    * This can be used to place social media links and scroll to top and so on.
  * Initial
    * Sets the property to its default value.
  * Inherit
    * This will inherit the property of its parent element.
* A background image can be used by the `background-image` property and setting the image to the file using the `url(../file_path)`.
  * There are various `background` properties like, size, position, repeat (which says that the picture will be tiled to repeat or not) and so on.
* **Pseudo classes**
  * Let us say we have a `ul` list and multiple `li` inside it.

```html
<ul class="my-list">
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
  <li>List Item</li>
</ul>
```

* These are most used in scenarios where these are dynamically generated.
* We can target a CSS property inside the `ul` to a specific `li` without having to manually name an id or a class to it. These are called pseudo classes.

```css
.my-list li:first-child {
    background: red;
}

.my-list li:last-child {
    background: blue;
}

.my-list li:nth-child(5) {
    background: yellow;
}

.my-list li:nth-child(even) {
    background: grey;
}
```

* There are many more ways you can target a pseudo class. Have to learn more on it.
* To make an element responsive to the browser size (wrt height) we can use the `min-height` property. Learn more about it.
