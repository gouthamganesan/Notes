# Flexbox

## Basics

- Placing a CSS property `display: flex;` on an element allows you to use other flex properties to build a responsive page.
- Adding the above said `display: flex` property turns the element into a flex container. i.e. any children of that element can be aligned into rows and columns. You can do this by setting the `flex-direction` property to the parent item and set it to `row` or `column`. There are also `row-reverse` and `column-reverse`.
- There will be cases where the flex containers won't be filled with elements equally. There is a `justify-content` property to correct this. But there is some terminology involved.
  - [Here is an image that shows how the elements are laid out (as a row) and what the axis are for them](https://www.w3.org/TR/css-flexbox-1/images/flex-direction-terms.svg)
  - For the flex elements that are laid as `row` then the horizontal line which cross through the elements is called the main axis. Similarly for elements that are laid as `column` the vertical line is the main axis.
  - There are several options on how to place the flex elements along the main axis. `justify-content: center;` is one of the common one.
    - There are also,
      - `flex-start` - the default one. All the elements are pushed against the main start.
      - `flex-end` - All the elements are pushed against the main end.
      - `space-between` - The first and last are pushed against the main start and end respectively and the rest are evenly spread.
      - `space-around` - Similar to the `space-between` but, the first and last are not pushed to the edge. The space is evenly distributed on all elements with half space on either end.
      - `space-evenly` - Distributes the elements evenly along the container with full space on the edges.
- Similar to `justify-content` which takes care of alignment of elements along the main axis, there is another axis called cross axis (which is the opposite of main axis) and there is a property `align-items` to align the elements along the cross axis inside the container.
  - `flex-start`: aligns items to the start of the flex container. For rows, this aligns items to the top of the container. For columns, this aligns items to the left of the container.
  - `flex-end`: aligns items to the end of the flex container. For rows, this aligns items to the bottom of the container. For columns, this aligns items to the right of the container.
  - `center`: align items to the center. For rows, this vertically aligns items (equal space above and below the items). For columns, this horizontally aligns them (equal space to the left and right of the items).
  - `stretch`: stretch the items to fill the flex container. For example, rows items are stretched to fill the flex container top-to-bottom. This is the default value if no align-items value is specified.
  - `baseline`: align items to their baselines. Baseline is a text concept, think of it as the line that the letters sit on.
- Usually a flex container will fit all flex items together. But using `flex-wrap` if the size is larger then the extra of the item will be wrapped on a new row (or column).
  - `nowrap` - Which is the default option.
  - `wrap` - Wraps items from left-to-right if they are in a row, or top-to-bottom if they are in a column.
  - `wrap-reverse` - Wraps items from right-to-left if they are in a row, or bottom-to-top if they are in a column.
