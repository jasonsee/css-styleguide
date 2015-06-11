# CSS Style Guide


As the portfolio of client work expands, it is essential that a team of front-end developers create consistant CSS. This document defines formatting and style rules for CSS. The goal is aimed at improving collaboration, code quality, and enabling supporting infrastructure across projects.

## General Formatting Rules

* Avoid the use IDs. There is no point to using IDs in CSS. It takes 256 classes to override one ID. Make several classes out of the reusable parts of the ID.
* Use one level of indentation for each declaration.
* Always start with a CSS reset. [HTML5 Boilerplate](https://html5boilerplate.com) is the preferred starting point for projects.
* Use uppercase hex values only for color `#1F0541`, exception might be rgba for opacity.
* Never use `!important` in CSS. If you are, you’re doing it wrong.
* Omit 0 values unless required. If the value of the width or height is 0, do not specify units. Not this: `padding: 0 px;`
* Use a leading 0 for decimal values. Ex: `opacity: 0.6`;
* Shorthand CSS will allow you to speed up the writing process, cut down on clutter in your stylesheets and will allow you to find things much easier. Ex: `.box {margin: 10px 20px }`
* Each selector should be on its own line ending with either a comma for a list or opening curly bracket. Nested selectors should be on one line. The closing brace should be flush left, using the same level of indentation as the opening selector.
* If you are attempting to fix an issue, attempt to remove code before adding more.
* Magic Numbers are unlucky. These are numbers that are used as quick fixes on a one-off basis. Example: `.box { margin-top: 37px }`.
 
Correct:
```
.selector-1,
 .selector-2,
 .selector-3 {
     background: #fff;
     color: #000;
 }
 
 .asset-selector ul li a {
      background: #000;
 }
 ```
Incorrect: 
```
.selector-1, .selector-2, .selector-3 {background: #fff; color: #000;}
``` 
 
## Table of Contents

The WAT team encourages the style guide of Scalable and Modular Architecture for CSS (SMACSS) when creating a Table of Contents. Read more about Jonathan Snook’s SMACSS and the catagorizing of CSS rules.
1.  Base
2.  Layout (positional)
3.  Modules
4.  Theme
 
``` 
/* Example Table of Contents:
 
 1.0 - CSS Reset
 2.0 - Structural Elements
         2.1 - Left column
         2.2 - Right column
         2.3 - Search
 3.0 - Form Elements
         3.1 - Amount
         3.2 - User Email
         3.3 - Address
         3.4 - Form Errors
         3.5 - Success
 4.0 - Advertisements
 5.0 - Footer
 
 */
 ```
 
 
## Class Naming

Naming is hard, but very important. It’s a crucial part of the process of developing a maintainable code base, and ensuring that you have a relatively scalable interface between your HTML and CSS.
It is always preferable to name classes by the nature of what it is rather than by what it looks like. For instance, a class name of big-blue-text for a special note on a page is quite meaningless if it has been changed to have a small red text color.
Instead of presentational or cryptic names, always class names that reflect the purpose of the element in question, or that are otherwise generic. Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change.
Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as “helpers.”
Using functional or generic names reduces the probability of unnecessary document or template changes.
•   Use lowercase and separate words with hyphens when naming selectors. Avoid camelcase and underscores.
•   Use human readable selectors that describe what element(s) they style.
•   Avoid quotes on attribute selector values.
•   Avoid type selectors. Wrong: div.selector. This limits the reusability and is more work for the browser.
•   Avoid action or verb-related class names
 
Correct: 
```
.comment-form {
     margin: 1em 0;
 }
 
 input[type=text] {
     line-height: 1.1;
 }
 ```
Incorrect: 
```
/* Avoid camelcase. */
 .commentForm {
     margin: 0;
 }
 
 /* Avoid underscores. */
 .comment_form {
     margin: 0;
 }
 
 /* Avoid type selectors. */
 div#comment_form {
     margin: 0;
 }
 
 /* What is a c1-xr?! Use a better name. */
 .c1-xr {
     margin: 0;
 }
 
 /* Should be [type=text] */
 input[type="text"] {
     line-height: 110% /* Also doubly incorrect */
 }
 ```
 
## Whitespace

Always be consistent with use of whitespace. Use whitespace to improve readabililty.
* Never mix spaces and tabs for indentation.
* Use tabs set to four spaces.
* Put a space after : in property declarations.
* Put spaces before { in rule declarations.
 
## Ems vs. Px

Use ems for font-size, because it preserves vertical rhythm. Additionally, unit-less line-height is preferred because it does not inherit a percentage value of its parent element, but instead is based on a multiplier of the font-size.

##Commenting

Well commented code is extremely important. Use comments to explain code: What does it cover, what purpose does it serve, why is respective solution used or preferred? Take time to describe components, how they work, their limitations, and the way they are constructed. Don’t leave others in the team guessing as to the purpose of uncommon or non-obvious code. http://www.stack.nl/~dimitri/doxygen/docblocks.html
* Use /*  */ for comment blocks (instead of //).
* Place comments on a new line above their subject.
* Avoid end of line comments.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Use “sentence case” and consistent text indentation.
 
Example: 
```
/* MAIN SECTION HEADING - ALL CAPS */
 
 
 /* 2.2.1 Global Typography - Subsection headings */
 
 
 /* Long description first sentence starts here and continues
 * on this line for a while finally concluding here at the
 * end of this paragraph.
 *
 * The long description is ideal for more detailed
 * explanations and documentation. It can include example
 * HTML, URLs, or any other information that is deemed necessary
 * or useful.
 */
 
 /* TODO: This is a todo summary on one line that describes the gist.
 *   If needed, additional comment for the TODO can start on a
 *   second line and wraps at 80 characters and following lines
 *   are indented by 2 spaces.
 */
 
 /* Basic comment */
 ```
 
## Property Order
1. Preprocessor variables
2. display
3. position
4. color
5. font
6. background & border
7. border-radius & text-shadow
8. any other visual elements and vendor prefixes
 
Example: 
```
.selector {
     /* Preprocessor variables */
     @box-size(20px);
     @graident(@main_blue, 2px);
 
     /* Display & Box Model */
     display: inline-block;
     overflow: hidden;
     box-sizing: border-box;
     width: 100px;
     height: 100px;
     padding: 10px;
     margin: 10px;
 
     /* Positioning */
     position: absolute;
     z-index: 10;
     top: 0;
     right: 0;
 
     /* Color */
     background: #000;
     color: #fff
 
     /* Text */
     font-family: sans-serif;
     font-size: 16px;
     line-height: 1.4;
     text-align: right;
 
     /* Background */
     background-image: url(/static/img/icon/bullet.png);
     border: 10px solid #333;
 
     /* Radius */
     border-radius: 2px 2px 0px 0px;
     text-shadow: 1px 1px #333;
 
     /* Other & Vendor Prefixes */
     cursor: pointer;
     -webkit-box-shadow: inset 0 0 1px 1px #eee;
     -moz-box-shadow: inset 0 0 1px 1px #eee;
     box-shadow: inset 0 0 1px 1px #eee;
 
 }
 ```
 
## Media Queries

Media queries allow us to gracefully degrade the DOM for different screen sizes. If you are adding any, be sure to test above and below the break-point you are targeting.
* It is generally advisable to keep media queries grouped by media at the bottom of the section.
* Rule sets for media queries should be indented one level in.
 
Example:
```
@media all and (-webkit-min-device-pixel-ratio: 2),
     all and (min-device-width: 641px) {
         .selector {
                 background: url('/static/img/placeholder.png') #fff no-repeat center center;
                 background-size: 33px;
         }
     }
```
