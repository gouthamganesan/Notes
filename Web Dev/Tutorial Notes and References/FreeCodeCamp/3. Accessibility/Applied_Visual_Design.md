# Applied Visual Design

- Visual Design in web development is a broad topic. It combines typography, color theory, graphics, animation, and page layout to help deliver a site's message.

## Points to note

- Text make up a very big part of the web. So it is important to present them properly. We can use the `text-align` property to align the text properly on the web page.
- You can use the `width` and `height` property to set the respective of any element.
- Using the `<strong>` HTML tag and enclosing elements is similar to applying a `font-weight: bold;` property to an element. Both are read by the browser the same and the text is rendered Bold.
- Like wise, `<u>` tag and `text-decoration: underline;` does the same. Both underlines the text.
  - Since anchor tags too have the same underlined format, use them both carefully as they might confuse.
- The `em` (emphasis) HTML tag and `font-style: italic;` italicizes the text.
- The `s` tag and `text-decoration: line-through;` property strikes-through the text.
- `<hr>` self-closing tag is used to add a horizontal line across the width of its containing element.
  - This can be used to represent change in topic or separation of groups.
- Like `hex` and `rgb()` there is color representation format called `rgba()` which is similar to `rgb()` but where `a` refers to the alpha/opacity level which ranges from `1` which is fully opaque to `0` which is fully transparent.
- It is important to have differentiating `font-size` for the users to understand the hierarchy of the content.
- `box-shadow` element applies one or more shadows to an element.
  - The property takes values for `offset-x`, `offset-y`, `blur-radius`, `spread-radius` and `color` in that order. (The `blur-radius` and `spread-radius` values are optional)
  - For example, `box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);`. This will create multiple shadows with some blur, at mostly transparent black colors.
    - If only 2 values are given then they are taken as offset-x and offset-y.
    - Third value is interpreted as blur-radius.
    - Fourth value is interpreted as spread-radius.
    - Add the `inset` keyword to change the default drop shadow to one inside the frame.
    - Add the color value to give a color to the shadow.
- We have a `opacity` property to change the opacity of the said element. It can have values from 0 to 1 (from fully transparent to fully opaque).
- `text-transform` property changes the appearance of the text without having to change the content of the HTML manually.
  - It can have keywords like, `lowercase`, `uppercase`, `capitalize` (first letter capital), `initial` (use the default value), `inherit` (use the `text-transform` value of the parent element) and `none` (use the original text).
- The `font-size` property can be used to change the size of the font and `font-weight` property shows how thick or thin characters are in a section of text. These properties can be applied to any element that contains text.
- `line-height` property is used to change the height of each line in a block of text.
- There are different 'states' to an element. `pseudo-classes` can be used to select a particular state of an element and style that state.

  - For example, the `hover` pseudo class of anchor can be used to give CSS rules for/when the element is hovered.

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

  - In the above example, the anchor element when hovered will turn to the set value blue. Otherwise it would be in the set value black.

- [CSS box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model#content-area): All the HTML elements are considered as a box.
- There are two types of element layout
  - Block-level items - These will automatically start on a new line (think headings, paragraphs and div).
  - Inline items - They sit within the surrounding content (like images or spans).
  - The default layout of elements in this way is called the _normal flow_ of a document. But CSS offers a property to override it.
  - When the `position` of an element is set to `relative`, we can specify how the element should be moved relative to its current position. It pairs with **offset** properties `left` or `right` and `top` or `bottom`. These properties can have a length value that specifies how far the element should be from its original placement.
    - For example, `top: 15px;` offsets the element `15px` below its default placement.
    - Changing an element's position to relative does not remove it from the normal flow - other elements behave as if the element is in its default position. And because of this behavior overlapping can happen, if we are not careful.
    - We are offsetting an element away from a given spot, which moves the element away from the referred side.

![CSS Offset properties](https://cdn-media-1.freecodecamp.org/imgr/eWWi3gZ.gif)

- The next option for the CSS `position` property is `absolute`, which locks the element in place relative to its parent container. Unlike the `relative` position, this removes the element from the normal flow of the document, so surrounding items ignore it. The CSS offset properties (top or bottom and left or right) are used to adjust the position.
  - One nuance with absolute positioning is that it will be locked relative to its closest positioned ancestor. If you forget to add a position rule to the parent item, (this is typically done using `position: relative;`), the browser will keep looking up the chain and ultimately default to the body tag.
  - Like `relative` this would also result in overlapping if not the elements are placed correctly.
- Similar to the other layout scheme there is `fixed` position, which is a type of absolute positioning that fixes the element relative to the browser window.
  - This takes it out of the normal flow of the element like other position types and requires layout adjustments to correctly place other surrounding elements in place.
  - This is used with the offset properties of CSS like, `top`, `bottom` and others to fix the position.
  - The key difference between the `fixed` and `absolute` is that the element with fixed position would not move when the user scrolls.
  - These are mostly used for navbar elements and headers which needs to be fixed in their place.
- `float` property
  - Floating elements are removed from the normal flow of a document and pushed to either the `left` or `right` of their containing parent element.
  - This will be particularly helpful to divide the webpage into columns and have the content and the sidebar placed on them, side by side.
- When we set `position` with `absolute | relative | fixed | sticky` the element is removed from the normal flow of the document but the surrounding elements are unaware of that change and continue to stay in the same position. So because of this there will be overlapping of elements.
  - So when the elements are overlapped, the element that comes later in the HTML markup will be placed on top of the other element.
  - `z-index` property will let us customize which element comes at top of the other. It takes an integer value which specified which element comes on top of which with the higher value. So higher the value, higher it would be.
- We can center a block element horizontally by many ways. One of them is to use, `margin` with a value `auto`.
  - This works for images too, which are by default inline elements. But we can change that to a block element by using the `display: block;` property.
- Colors that are opposite in the color wheel will produce vibrant color patterns.
  - Secondary colors are the ones that are the result of combining two primary colors. For example, magenta is made with red and blue. But this complements the third primary color (which is not involved in its creation). In our case, magenta is complement to green.
  - Tertiary colors are the result of combining a primary color with a secondary one.
  - Split-complementary scheme is one of the methods of combining and choosing colors for the web page.
    - This scheme starts with a base color, then pairs it with the two component that are adjacent to its complement. The three colors provide strong visual contrast in design but are more subtle than using two complementary colors.
- CSS has a `hsl()` property that will allow us to configure the hue, saturation and the lightness of a color.
  - Hue is what people generally think of as 'color'. If you picture a spectrum of colors starting with red on the left, moving through green in the middle, and blue on right, the hue is where a color fits along this line. In `hsl()`, hue uses a color wheel concept instead of the spectrum, where the angle of the color on the circle is given as a value between 0 and 360.
  - Saturation is the amount of gray in a color. A fully saturated color has no gray in it, and a minimally saturated color is almost completely gray. This is given as a percentage with 100% being fully saturated.
  - Lightness is the amount of white or black in a color. A percentage is given ranging from 0% (black) to 100% (white), where 50% is the normal color.
- Applying the color on CSS elements are not just limited to a solid color. We can also add linear gradient using the `background` property's `linear-gradient()` function. The general syntax is, `background: linear-gradient(gradient-direction, color 1, color 2, color 3,...)`.
  - There is also a `repeating-linear-gradient()` function which is very similar to `linear-gradient()` with the major difference that it repeats the specified gradient pattern.
    - The common syntax is that, `repeating-linear-gradient(angle, color stop 1, color stop 2...)`
    - Where color stops contains a color and a `<length>` value, which says, blend to the next color on this `<length>`.
- The background property also supports the `url()` function in order to link to an image of the chosen texture or pattern.
  - Having a subtle texture or pattern as background adds beauty to the web page. But make sure to be subtle about it as it shouldn't take away the audience from the foreground.
- The scale of an element can be changed using the `scale()` function of the `transform` property. For example, `p { transform: scale(1.5); }` scales the paragraph elements to 1.5 times it size.
  - This will be particularly useful to make a difference when we scale an element on a hover.
  - `p:hover { transform: scale(2.1); }` will scale when the user hovers over it.
- The `transform` property can also be used to 'skew' a particular element by the `skew()` function. There are also, `skewX()` and `skewY()` functions for X and Y skewing.
  - For example, `transform: skewX(45deg);` skews the particular element in the X plane by 45 degrees.
- The `border-radius` property will allow us to control the corner radius of the element. Setting it to `50%` will make a square a circle.
- The `transform: rotate(-45deg)` rotates the element.
- There are also pseudo elements, that are used to target a particular part of the targeted element.
  - For example, there are `before` and `after` pseudo elements, which is used to do changes to the targeted element.
    - This doesn't mean to target the 'element' after the targeted element, but to put/do some changes after or before the targeted element.
    - And also, to use these elements the property `content: ''` should be used. This content should contain an image or a text to put before or after an element. For example, this content property can be used to put an arrow mark after every anchor element. 
    - These are inline by default. This can be used by elements that should have something immediately before or after the selected element, like "Hot topic" and such.
  - Remember, `selector:pseudo-class` and `selector::pseudo-element`.
  - To put it in an easy to remember way, a pseudo element, as the name suggests is an element that is imaginarily associated with the targeted element. You can apply styles as if it is a real element.
- **Animation:** The animation properties control how the animation should behave and the `@keyframes` rule controls what happens during that animation.

  - There is an `animation-name` property that sets the name for an animation which is later used by the `@keyframes` to tell CSS which rules go with which animations.
  - `animation-duration` sets the length of time for the animation.
  - `@keyframes` is how to specify what exactly happens within the animation over the duration.

    - In the `@keyframes` property we can specify the changes to the property frame by frame using the percentage.
    - For example, 0% means at the start and 100% means at the end. And we can fill the ones in the middle.
    - We can specify the properties at each stage and the animation will be carried out for the specified duration.

    ```css
    #anim {
      animation-name: colorful;
      animation-duration: 3s;
    }

    @keyframes colorful {
      0% {
        background-color: blue;
      }
      100% {
        background-color: yellow;
      }
    }
    ```

  - We can also use CSS animation to change the hover state of a button.

    ```css
        <style>
        img:hover {
            animation-name: width;
            animation-duration: 500ms;
        }

        @keyframes width {
            100% {
            width: 40px;
            }
        }
        </style>

        <img src="https://bit.ly/smallgooglelogo" alt="Google's Logo"
    ```

  - Adding the above animation for the button, just for itself would not complete it. After the 500ms, the button returns to its original color.
  - This can be done by setting the `animation-fill-mode` property to `forwards`. `animation-fill-mode` specifies the styling that should be applied to the element when the animation completes. Read more on this [here](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode)
  - `animation-iteration-count` property specifies how many times the animation should repeat. Setting it to infinite will run it continuously. Set the animation to complete a loop so that when it runs continuously it will look natural.
  - Use the `opacity` property to make fading out/in animation.
  - The `animation-duration`, `@keyframe` rule value can be modified to change the rate of animation.
  - The `animation-timing-function` property controls how quickly an animated element changes over the duration of the animation. If the animation is a car moving from point A to point B in a given time (your `animation-duration`), the `animation-timing-function` says how the car accelerates and decelerates over the course of the drive.
  - There are predefined keywords for the popular styles. The default one is `ease` which is slow-quick-slow. There is `ease-out` which is quick-slow and also `ease-in` which is the opposite.
    - There is also `linear` which moves in the same speed throughout the animation.
  - Even finer controls of how the animation plays out is given by Bezier Curves.
    - Imagine a graph with the x axis set to the time during animation and the y axis as the speed of animation.
    - The graph controls the speed of the animation during the timing.
    - There are four points p0, p1, p2 and p3. The points p0 (origin, (0,0)) and p3(1,1) are already set. We should specify the p1 and p2 points and that determines the speed of the animation at that particular time.
    - The co-ordinates for p1 and p2 are given by, `animation-timing-function: cubic-bezier(x1, y1, x2, y2)`.
    - For example, the values, `0.25, 0.25, 0.75, 0.75` is the equivalent of `linear` as it gives a straight line on the curve. 
