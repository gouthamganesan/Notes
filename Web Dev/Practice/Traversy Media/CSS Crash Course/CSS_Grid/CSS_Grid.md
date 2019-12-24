# CSS Grid

- Flexbox is a one dimensional layout for columns or rows and Grid is a two dimensional layout for columns and rows.
- To setup a grid on a selected element (using the selector) use the property `display: grid;`. Then after that we can setup the columns using the `grid-template-column: 70% 30%` representing the distribution of columns in the display.
  - Setting this column will make it follow for all the rows i.e. all the rows have a 70-30 ratio.
  - For example, in the [index.html](index.html) file the `.wrapper` class contains 4 div elements and the `div` elements continue to position in the 70-30 rule. Adding more `div` elements will do the same.
- The `grid-gap` or `grid-column-gap`, `grid-row-gap` property contains a length value which determines how much gap there should be between the grid elements or columns, rows respectively.
- In setting up the grid with `grid-template-columns` instead of % it is recommended to use `fr` unit which stands for fraction. This will divide the screen into the number of fractions specified and allot the number of fractions specified for each section.
  - For example, if the fraction value is `grid-template-column: 1fr 2fr 1fr` then the screen is divided into 4 (1+2+1) fractions and it can contain 3 sections. The first one occupies the first fraction and the second one occupies the middle two fractions and the last one occupies the last fraction.
  - The `grid-template-column` also takes any other length value like pixel and such. But the most recommended is the fractions. Especially when we use percentages, we will run into issue when using padding, margin and while nesting elements.
  - Instead of `grid-template-column: 1fr 1fr 1fr` we can also use `grid-template-column: repeat(3, 1fr)` which does the same thing.
  - `repeat(3, x)` -> `x x x`, i.e. x can contain more than one value, like `1fr 2fr`. So `repeat(3, 1fr 2fr)` gives `1fr 2fr`, 3 times.
- `grid-auto-rows` sets the heights of an element.
  - This when set to a length unit just as is, it sets a fixed height.
  - Using, `minmax(100px, auto)` lets the height to be minimum 100px and maximum to the needed height. This prevents the elements/contents from overflowing from the container.
- Nesting grids/sub grids
  - Make another div container inside a container and use `display` as grid in the CSS. This allows us to make grids within a grid element.
- The `justify-items` property is used to align the element inside their grid element. There are values, like, `stretch` (default), `start`, `center` and `end`. More [here](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items).
- Just like `justify-items`, we also have `align-items` and also has the same values. But the difference is that, the justify is used to position the elements, horizontally in the grid element while the align property is used to align the element vertically in the grid element.
- The `justify-items` and `align-items` are used to modify the whole grid elements at once. There are individual grid elements inside the grid and those can be modified using the `justify-self` and `align-self` properties.
- **Positioning elements in CSS Grid**

  - Once the grid is setup with the `display` and the `grid-template` then we can position the elements however we want using the `grid-column` and `grid-row` property. For example,

  ```css
  .box4 {
    grid-column: 1;
    grid-row: 2/4;
  }
  ```

  - In the above example, the value `1` will set the element in the position 1 with respect to column. And the value `2/4` will span the element from position 2 to 4 with respect to rows.
  - Read more about the grid in CSS in [MDN Docs](https://developer.mozilla.org/en-US/docs/Glossary/Grid)
