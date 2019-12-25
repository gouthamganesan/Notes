# Flexbox

## What is Flexbox

* It is also called the flexible box model. A CSS layout mode that provides an easy and clean way to arrange items within a container.
  * In the basic block model, the elements are to be floated to arrange them side by side and needs a lot of mathematical calculations. Flexbox makes this easy by the following points.
    1. NO FLOATS!
    2. Responsive and mobile friendly.
    3. Positioning child elements are much easier.
    4. The margin of the flex container won't affect its content's margins.
    5. Can easily change the order of the elements without having to edit the HTML.
* Some of the main concepts of flexbox.
  * Altering the width and height of the elements inside to best fit the available space inside the flex container.
  * Flexbox is direction-agnostic, i.e. it works well for both, vertical placement (block model) and horizontal placement (inline model).
  * Flexbox is best for small scale layouts while "Grids" are preferred for larger scale ones.
* Introducing the `display: flex` property in the parent container automatically arranges the child elements side by side. The `flex` property is used inside the child elements to essentially tell them how much wide they should be. A number would represent the amount of width (of length) it should have.
* The `order` property allows us to change the order of the elements without having to adjust them in the HTML file. Just look at the flex and specify in what position a particular element should be and the child element would be placed there.
* The `align-items: flex-start;` would align the elements in the flex box at the starting so that the automatic width or height is ignored and only the actual needed length is taken up. By default this is `stretch` and there are other properties like, flex-end and center.
* The `flex-direction` property in the parent flex element specifies the direction in which flex should be laid out. By default the elements are laid out as a row (horizontal). `flex-direction: column` does the job to change it to vertical (column).
* Setting the width of the flex elements (which is by default set to a certain length value) will leave space after the flex elements. To make use of the space after the flex usefully, then we can use the `justify-content: space-between` property to leave space and distribute them equally spaced. There are other values like `space-around`, `space-evenly`, `center` and such.
  * The same also is useful with other values like, `flex-start` and `flex-end`.
* To specify the width in flexbox, use the `flex-basis` property which does the exact same thing, but is a more flexbox way to do things.
* To make the page more responsive for mobile devices, then we can just place a media query which will check for the width and make appropriate changes like remove flex and stack normally or stack in mobile friendly way.
* Wrapping the elements is a way to let the elements be placed according to the size of the screen (without media query). This can be done by, using the `flex-wrap: wrap` property. 