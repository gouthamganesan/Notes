# Grid

## Basics

- The `display: grid` property sets all the elements inside an element in grid.
- The `grid-template-columns: 50px 50px;` property allows to configure the columns in the grid. The number of values for this property represents the number of columns and the value itself represent the size of that particular column.
- Defining only the above (column) sets the row automatically. To define that explicitly, we can use the, `grid-template-rows` in the same way as above.
- There are units like, `em`, `%` and `fr` to set the size of the grid relative.
  - The `fr` units deals with only free space (so gaps and such won't come here), unlike the `%`, which calculates from the actual size.
- `grid-column-gap` property is used to allocate gap between the grid columns. Setting a value to this, will set a gap between all the columns in the grid.
- Just as similar to `grid-column-gap` there is `grid-row-gap` that helps in setting the gap between the rows.
- The `grid-gap` is a shorthand for `grid-row-gap` and `grid-column-gap` that take either one or two values. NOTE: If only one value is present, it is taken for both the property.
- All the above are addressed to the grid itself and this is the first property that addresses a particular grid item. `grid-column`. This property is used to mark the start and end of an item in the grid.
  - The imaginary lines that separate the elements and make the grid are called lines. These lines start with 1 and count upwards. So there are 4 vertical and 4 horizontal lines in a 3 x 3 grid.
  - The property `grid-column: 1 / 3;` makes the element start from the 1st grid column line and end on the 3rd grid column line, i.e. the element will span for 2 columns (the first and the second)
- Just like `grid-column`, there is also a `grid-row` which can be used to specify where the element occupies.
- NOTE: Each of the box is called as a __cell__.
- Inside each cell the contents can be aligned using the `justify-self` property. By default the value is set to `stretch`. But there are other values like, `start`, `center` and `end`, which aligns the content at the left, center and the right of the cell.
- Likewise, we can align the item vertically using the `align-self`, just like you do with `justify-self`.
- Unlike the above properties, `justify-self` and `align-self`, the `justify-items` and `align-items` can take the same values and does the same function as the former but does it for all the items in the container.
- We can create a template of the grid using the `grid-template-areas` on the grid container and assign that 'area' to an item using the `grid-area` property. For example,
  ```css
  .container {
    display: grid;
    grid-template-areas:
      "header header header"
      "advert content content"
      "footer footer footer";
  }

  .grid_item1 {
    grid-area: content;
  }
  ```
  - This will create a 3 x 3 grid inside the container and then divide the 3 x 3 grid into 4 parts namely header (1st row), advert (1 cell), content (2 cells) and footer (3rd row).
  - And the `grid_item1` is assigned on the area `content`.
- The `grid-area` property can also be used without the `grid-template-areas` property as in,
  ```css
  grid-area: 1/1/2/4;
  ```
  - The syntax is that, `grid-area: the horizontal starting line / the vertical starting line / the horizontal ending line / the vertical ending line;`
  - So element in the above example covers the cells in the first column and span downward 3 rows.
- We can use the `repeat` function to avoid repetitions. For example, to create a 100 rows with 10px height you need not type `grid-template-rows: 10px 10px...` a 100 types. `grid-template-rows: repeat(100, 10px)` does the same job.
  - The `repeat()` function can be used extensively. `grid-template-columns: repeat(2, 1fr 50px) 20px;` is equal to `grid-template-columns: 1fr 50px 1fr 50px 20px;`.
- There is another builtin function called `minmax` that can be used with `grid-template-rows` and `grid-template-columns` to limit the size of the rows and columns when the grid size changes. 
  - For example, `grid-template-columns: 100px minmax(50px, 200px);` creates two columns. One with 100px width and another with minimum width of 50px and a maximum width of 200px.
  - NOTE: This can also be used in conjunction with `range()` function.
- The `range()` function comes with a `auto-fill` value, which automatically fills the number of values (repeated) needed as per the size of the container. When the size of the container is increased the items are stretched until there is more space for one more (repeated) item. For example, `repeat(auto-fill, minmax(60px, 1fr))`. When the container size increases, it keeps inserting 60px columns and it keeps stretching until there is space for another 60px column.
- There is also another value that can be used with `range()` function called `auto-fit`. The only difference between, `auto-fit` and `auto-fill` is that, even after the container size exceeds the total size of the items in it combined, it keeps adding more empty rows/columns. But `auto-fit` collapses these empty rows/columns and resizes the items to fit the container.
- We can use media query to make the page more responsive in CSS Grid.
- You can create a grid within another grid. Just use the `display: grid;` and `grid-template-columns` property on a grid item and that item is a grid on its own, which can have sub grids.
