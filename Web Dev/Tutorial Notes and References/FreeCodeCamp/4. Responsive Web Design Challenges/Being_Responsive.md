# Responsive Design

- Media queries are used to specify different styles to different types of devices. There can be changes in resolution, screen size and processing power.
  - They consist of a media type and if that media type matches the type of devices the document is displayed on, the styles are applied.
  - For example, `@media (max-width: 100px) { /* CSS rules */ }` will apply the styles only when the condition specified here is true, which is, it will be applied for devices with width less than or equal to 100px.
- Making images responsive is easier with CSS.
  - Instead of fixing a width, like, `img { width: 720px; }` we can have,

    ```css
    img {
        max-width: 100%;
        display: block;
        height: auto;
    }
    ```

  - The `max-width` property to `100%` will maintain the image size to below its original width. The `display` property set to `block` will display it in its separate line unlike inline elements. And finally the `height` property set to `auto` will change the height when width is changed to maintain the aspect ratio.
- To adjust the image sizes to different screen sizes, we now use different sizes of images separately. But if the images are not made with Retina displays (high resolution) then the images might look pixelated. To tackle this, set the width and height to half the amount of the original size. This will increase the pixel density.
- Instead of using `em` and `px` to size the text, we can use **viewport** units which are like percentage, relative, but relative to the size of the viewport, unlike percentage which is relative to parent container.
  - **vw** (viewport width): `10vw` would be 10% of the viewport's width.
  - **vh** (viewport height): `3vh` would be 3% of the viewport's height.
  - **vmin** (viewport minimum): `70vmin` would be 70% of the viewport's smaller dimension (height or width).
  - **vmax** (viewport maximum): `100vmax` would be 100% of the viewport's bigger dimension (height or width).