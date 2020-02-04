# Applied Accessibility Challenges

- Making the web as accessible as possible for everyone is an implied goal for every website. The main concepts covered are,
  - have well-organized code that uses appropriate markup
  - ensure text alternatives exist for non-text and visual content
  - create an easily-navigated page that's keyboard-friendly

## Tips for building an accessible website

- Add `alt` text for all images (`img` tags)
  - At some places the images are just used for decoration or the image is already conveyed using the captions. In those cases, the alternate text might seem redundant. So just leave the `alt` attribute as empty so that the helper tools like screen readers won't be showing a broken image link which is to indicate that there is no missed out information.
- Screen readers summaries the webpage using the tags used in the webpage. So we should use, appropriate headings to navigate the user accordingly.
  - There should be always one `h1` tag, which is the overall idea of the page.
  - There should be a continuous flow, h1 -> h2 -> h3 and so on. Just because one looks better on the webpage, we shouldn't use inappropriate tags.
  - We can use CSS to make the sections look the way we want.
- Tags like `main`, `section`, `header`, `footer`, `article` and `nav` are nothing but decorated `div`. But using them appropriately will give the tag semantic meaning that will be helpful in many ways.
  - For example, the `main` tag should be used only to include the main content of that page (the central topic) of that particular page. There should be only one `main` tag per page. Assistive technologies like "Jump to main content" use this `main` tag to avail those features.
  - `article` tag is used to wrap independent and self-contained entries like, blog entries, form posts or news articles.
  - `section` is used to group related content. For example, if book is an article then each chapter is a `section`.
  - If there is no relationship between groups of content, then use the `div` element.

    ```html
    <div> - groups content
    <section> - groups related content
    <article> - groups independent, self-contained content
    ```

  - Assistive technologies rely on these thoughtfully used tags to better help the needy people.
  - `header` tag which is different from `head` tag is used inside `body` tag, to contain introductory content, or information that is available at the top of multiple pages or contains links for parent tags (in contrast to the `head` element outside of the `body` to contain page title, meta information and etc.)
  - The `nav` element is another HTML5 item with the embedded landmark feature for easy screen reader navigation. This tag is meant to wrap around the main navigation links in your page.
  - If there are repeated site links at the bottom of the page, it isn't necessary to markup those with a `nav` tag as well. Using a `footer` is sufficient.
  - Similar to `header` and `nav`, the `footer` element has a built-in landmark feature that allows assistive devices to quickly navigate to it. It's primarily used to contain copyright information or links to related documents that usually sit at the bottom of a page.
- Sound accessibility is also a thing. Including an `audio` using the same tag should also make it accessible to people with hearing disabilities. There should be appropriately linked transcription or text that surround the audio should  convey the message.
  - The `audio` also has a `controls` boolean attribute that displays the audio with the default media controls like play, pause and such.

  ```html
  <audio id="meowClip" controls>
    <source src="audio/meow.mp3" type="audio/mpeg" />
    <source src="audio/meow.ogg" type="audio/ogg" />
  </audio>
  ```

  - Since the `controls` attribute is a boolean one, just its presence will turn the settings on.
- There is a `figure` tag (that goes along with the `figcaption` tag), that is used to wrap an image with its caption to represent the conclusion.

  ```html
  <figure>
    <img src="img source" alt="some alternate text">
    <br>
    <figcaption>
      Some caption that is to be displayed under the image, as a conclusion.
    </figcaption>
  </figure>
  ```

- The `label` tag wraps the text for a specific form control item, usually the name or label for a choice. This will make the form more readable.
  - `for` attribute explicitly ties the label with the form control item (radio button and such). The value of the `for` in `label` must match the `id` attribute of the form control.
  
  ```html
  <form>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
  </form>
  ```

- The radio button come as a group where the user must choose one. The `fieldset` tag surrounds the entire group of radio buttons and show that these are a set (in which only one can be selected).
  - The `fieldset` tag often uses a `legend` tag to provide a description for the grouping, which is read by the screen readers fo reach choice in the `fieldset` element.
  - When choice are self-explanatory, (like a gender selection), using a `label` with `for` attribute for each radio button is sufficient. This goes in conjunction with the `name` attribute that is used in the options to tie all of them as a set. Which means, the browser does not allow to select more than one option that has the same attribute.
  - Using `fieldset` and `legend` also adds cool default CSS styles.
- Similar to `text` and `submit` `type`s of `input`s, there is a `type` of `input` called `date` which gives a date picker for easier selection. This will appear on supported browsers and on unsupported devices, it will show as a `text` type input.
- Whenever a date/time is being addressed in the web page, for helping the screen readers, there is a way to tell the date/time in a standardized format. This will be used for the screen readers to show the general date and time whatever maybe the version of date and time that is displayed on the web page.
  - For example,

  ```html
  <p>Master Camper Cat officiated the cage match between Goro and Scorpion <time datetime="2013-02-13">last Wednesday</time>, which ended in a draw.</p>
  ```

  - The `time` tag goes alone with the `datetime` attribute which specifies the date/time in the generalized syntax.
- All these time we were using HTML to restrict data only for Screen Reader access. We can also use CSS to place the data somewhere else off the visual area so that the browsers won't notice that (since the browser views the content as a chart and the screen readers view them as a table) but the screen readers will.
  - So to hide a content from the normal browser's view and view them only on screen readers, set the following properties to the element (through a class ofcourse)

  ```css
  .sr-only {
    position: absolute;
    left: -10000px;
    width: 1px;
    height: 1px;
    top: auto;
    overflow: hidden;
  }
  ```

  - Setting the `display: none;` or `visibility: hidden;` won't do the trick as these will hide the element for everyone including the screen reader users.
  - Zero values for `width` and `height` removes the element from the flow of the document and thus the screen readers will ignore it.
  - The above specified properties, places the element in the far side and hides it without `overflow`ing.
- WCAG recommend at least 4.5 to 1 contrast ratio for normal text to be readable. So always check online if your selected color palate matches with the WCAG recommended ratio.
- While experimenting with color for satisfying the WCAG ratio, setting the `hsl()` will be more helpful as they represent hue, saturation, lightness. And the colors can be adjusted by adding tint to the light color (increasing the lightness) and adding black to the dark color (decreasing the lightness). This is contrast check ratio.
- There are many forms of color blindness from not being able to see a color at all to reduced sensitivity to a color. While conveying important information, using close colors makes it hard for the colorblind user to distinguish the content from. Some online tools represent how the selected colors appear for different types of blindness.
- Screen readers can also be used to choose to hear only the links available in the page. And when this happens just having text like, click here, or read more and stuff won't be much informative. So inside the `<a>` give meaningful descriptive content.
- The `accesskey` attribute can be used to get the browser automatically select the intended element by using the key. This will be helpful for the keyboard only user to navigate around the web-page.
  - Use the `accesskey` attribute in the required element (mostly interactive elements like links, buttons, forms and such) with the value like, `accesskey="b"`. Here `b` activates that particular element.
- The `tabindex="0"` attribute will give the attached element the keyboard focus while tapping and navigating the website through tab key. Certain elements like inputs, forms, links automatically receive keyboard focus.
  - To override the normal tab flow of the HTML source, we can use positive values from 1 to n to specify the order of the tab focus elements. After all this is done (when nth elements has come) the element with tabfocus value 0 is taken up and focused on. Be careful while using this as this might confuse the users who thinks the tabfocus starts from the start of the page. This is highly useful in places where the CSS will be used to change the position of the element.
