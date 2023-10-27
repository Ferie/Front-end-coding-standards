[Back to main page](../README.md#frontend-coding-standards-and-best-practices)

## Table of Contents
- [Node Modules](../Node/node-modules.md#node-modules)
- [HTML](../HTML/html.md#html)
- [Styles (CSS/SCSS)](#styles-cssscss)
    - [CSS](#css)
        - [Use CSS reset or Normalize CSS](#use-css-reset-or-normalize-css)
        - [Never use inline styles](#never-use-inline-styles)
        - [Modularize styles for reuse](#modularize-styles-for-reuse)
        - [Class names](#class-names)
            - [State classes](#state-classes)
        - [Use multiple stylesheets, but be aware of them expanding beyond control](#use-multiple-stylesheets-but-be-aware-of-them-expanding-beyond-control)
        - [Organize CSS with comments](#organize-css-with-comments)
        - [Never use large fixed width elements](#never-use-large-fixed-width-elements)
        - [Never let content rely on a particular viewport width](#never-let-content-rely-on-a-particular-viewport-width)
        - [Whitespacing and formatting](#whitespacing-and-formatting)
            - [Proper spacing between properties](#proper-spacing-between-properties)
            - [One selector per line](#one-selector-per-line)
            - [Blank line between rulesets](#blank-line-between-rulesets)
            - [Same line opening braces](#same-line-opening-braces)
            - [Same column closing braces as the first character of the ruleset](#same-column-closing-braces-as-the-first-character-of-the-ruleset)
            - [Indenting child elements](#indenting-child-elements)
            - [End all declarations with a semicolon](#end-all-declarations-with-a-semicolon)
            - [Use double quotes in style files](#use-double-quotes-in-style-files)
            - [Double quote attribute values](#double-quote-attribute-values)
            - [Avoid units on zero values](#avoid-units-on-zero-values)
            - [Grouping vendor prefixes](#grouping-vendor-prefixes)
            - [Properties order](#properties-order)
                - [Exception](#exception)
            - [Long comma separated property values](#long-comma-separated-property-values)
        - [Keep the natural flow](#keep-the-natural-flow)
        - [Typography](#typography)
            - [Font Size](#font-size)
            - [Pixels vs `em`s vs. `rem`s for typography](#pixels-vs-ems-vs-rems-for-typography)
            - [Font adjustment](#font-adjustment)
        - [Inheritance](#inheritance)
        - [Use shorthand](#use-shorthand)
            - [Exceptions](#exceptions)
        - [Never ever use `!important`](#never-ever-use-important)
        - [Selectors](#selectors)
            - [Minimize selectors tightly coupled to the DOM elements](#minimize-selectors-tightly-coupled-to-the-dom-elements)
            - [Minimize selector accesses to the DOM](#minimize-selector-accesses-to-the-dom)
        - [Positioning](#positioning)
        - [Colours](#colours)
        - [Media queries](#media-queries)
            - [Responsive layouts](#responsive-layouts)
            - [Approach](#approach)
            - [Placing Media Queries](#placing-media-queries)
    - [Sass/SCSS specific standards](#sassscss-specific-standards)
        - [Extensions and inclusions at the top of the ruleset](#extensions-and-inclusions-at-the-top-of-the-ruleset)
        - [Operators](#operators)
- [JavaScript/TypeScript](../Scripts/javascript.md#javascripttypescript)
- [General best practices](../Generals/generals.md#general-best-practices)


---



# STYLES (CSS/SCSS)

## CSS

### USE CSS RESET OR NORMALIZE CSS

- CSS reset _removes all built-in browser styling to all elements_ so that they have no particular style and you can define your own.
- Normalize CSS aims to make _built-in browser styling consistent_ across browsers.



### NEVER USE INLINE STYLES

When creating the markup, do not use inline styling because it would be very hard to override them when needed and any desired changes to styles have to be made in the HTML. Consequently, these styles cannot be reused, and the consistency of the styles will likely suffer.

Instead of these styles we can use:
- external style sheets,
- classes to target elements that contain the styles.



### MODULARIZE STYLES FOR REUSE

CSS is built to allow styles to be reused, specifically with the use of classes. For this reason, styles assigned to a class should be modular and available to share across elements as necessary.



### CLASS NAMES

- Keep classes lowercase and use dashes or underscores as per [BEM](http://getbem.com/) methodology (do not use _camelCase_ nor _CapitalCase_).
- Think about using the [ABEM](https://css-tricks.com/abem-useful-adaptation-bem/) strategy related to the modifiers (if necessary) to shorten the html.
- Avoid excessive and arbitrary shorthand notation: `.btn` is useful for buttons, but `.b` doesn't mean anything.
- Keep classes as short and succinct as possible.
- Use meaningful names; use structural or purposeful names over presentational.
- Prefix classes based on the closest block or parent or base class as per [BEM](http://getbem.com/) methodology.

It is also useful to apply many of those rules when defining _Sass_/_Less_ variable names.



#### STATE CLASSES

Use the `.is-*` prefix for state classes that are shared between CSS/SCSS and JavaScript to denote a temporary styling application.

Example:

```HTML
<div class="accordion-tab is-active" data-accordion="true">
    ...
</div>
```



### USE MULTIPLE STYLESHEETS, BUT BE AWARE OF THEM EXPANDING BEYOND CONTROL

Depending on the complexity of the design and the size of the website, sometimes it is easier to make smaller, multiple stylesheets (or partials in Sass/SCSS/Less) instead of a giant one. Having multiple files/partials, improve the maintainability developers can easily maintain 

_Note_: if we are working with a JavaScript framework, this is really helpful because (usually) it can load only the styles that are needed for the components used in the current view, instead of loading one giant CSS file that contains styles that are used elsewhere in the website/application).



### ORGANIZE CSS WITH COMMENTS

Let's keep our styles organized in logical groups and provide a comment noting what the following styles pertain to. [Learn more about comments in the General section of this guide](../Generals/generals.md#use-comments-when-needed).



### NEVER USE LARGE FIXED WIDTH ELEMENTS

Adjust the content to fit within the width of the viewport. For example, if an image is displayed at a width wider than the viewport it can cause the viewport to scroll horizontally: use instead `width: 100%` that keeps the image at the maximum size of the parent.



### NEVER LET CONTENT RELY ON A PARTICULAR VIEWPORT WIDTH

Since screen dimensions and width in CSS pixels vary widely between devices, **content should not rely on a particular viewport** width to render well. For example:

```CSS
/* Don't do this */
body {
    width: 1024px;
}

/* Do this instead */
body {
    max-width: 1024px;
}
```

This means also that we should not rely on the element's fixed sizes to stack other elements alongside the first one: whenever possible use percentages for widths and heights or use Flexbox.



### WHITESPACING AND FORMATTING

#### PROPER SPACING BETWEEN PROPERTIES

- Include a single space before the opening brace of a ruleset.
- Include a single space after the colon and semicolon of a property.
- Include a single space after each comma in comma-separated property or function values.
- Prefer one property per line (_in this case, no space after the semicolon_).

```SCSS
/* Don't do this */
.selector{display:none;background:rgba(2,0,36,.5);color:#000} 

/* Do this */
.selector { display: none; background: rgba(2, 0, 36, .5); color: #000; } 

/* This is even better - for the sake of readability */
.selector {
    display: none;
    background: rgba(2, 0, 36, .5);
    color: #000;
}
```



#### ONE SELECTOR PER LINE

```SCSS
/* Don't do this */
.selector-one, .selector-two, .selector-three {
    display: none;
    background: #f00;
    color: #000;
}

/* Do this instead */
.selector-one,
.selector-two,
.selector-three {
    display: none;
    background: #f00;
    color: #000;
}
```



#### BLANK LINE BETWEEN RULESETS

```SCSS
/* Don't do this */
.selector-one {
    display: none;
    background: #f00;
    color: #000;
}
.selector-two,
.selector-three {
    display: block;
    background: #0f0;
    color: #00f;
}

/* Do this instead */
.selector-one {
    display: none;
    background: #f00;
    color: #000;
}

.selector-two,
.selector-three {
    display: block;
    background: #0f0;
    color: #00f;
}
```
```SCSS
/* Don't do this */
.selector {
    display: none;
    background: #f00;
    color: #000;
    &__child {
        display: block;
        background: #0f0;
        color: #00f;
    }
}

/* Do this instead */
.selector {
    display: none;
    background: #f00;
    color: #000;

    &__child {
        display: block;
        background: #0f0;
        color: #00f;
    }
}
```



#### SAME LINE OPENING BRACES

```SCSS
/* Don't do this */
.selector
{
    display: none;
    background: #f00;
    color: #000;
}

/* Do this instead */
.selector {
    display: none;
    background: #f00;
    color: #000;
}
```



#### SAME COLUMN CLOSING BRACES AS THE FIRST CHARACTER OF THE RULESET

```SCSS
/* Don't do this */
.selector {
    display: none;
    background: #f00;
    color: #000; }

/* Do this instead */
.selector {
    display: none;
    background: #f00;
    color: #000;
}
```



#### INDENTING CHILD ELEMENTS

Use 4 spaces on each indentation.

```SCSS
.selector {
    display: none;
    background: #f00;
    color: #000;

    &__child {
        text-decoration: none;
    }

    span {
        font-weight: bold;
    }
}
```



#### END ALL DECLARATIONS WITH A SEMICOLON

The last declarations semicolon is optional, but your code is more error prone without it.

```SCSS
/* Don't do this */
.selector {
    color: red
}

/* Do this instead */
.selector {
    color: red;
}
```



#### USE DOUBLE QUOTES IN STYLE FILES

```SCSS
/* Don't do this */
.selector {
    content: '';
}

/* Do this instead */
.selector {
    content: "";
}
```



#### DOUBLE QUOTE ATTRIBUTE VALUES

```SCSS
/* Don't do this */
input[type=checkbox] {
    color: red;
}

/* Do this instead */
input[type="checkbox"] {
    color: red;
}
```

[Further reading about the reason behind this choice](https://mathiasbynens.be/notes/unquoted-attribute-values#css).



#### AVOID UNITS ON ZERO VALUES

One way to easily cut down on the amount of CSS we write is to remove the unit from any zero value: a zero will always be a zero.

```SCSS
/* Don't do this */
.selector { 
    margin: 0px;
    padding: 0rem;
}

/* Do this instead */
.selector { 
    margin: 0;
    padding: 0;
}
```



#### GROUPING VENDOR PREFIXES

_DO NOT use all the major prefixes on every single CSS3 property_.

It appears that many generic mixins are just putting everything with the prefixes: something like `-o-border-radius` has never existed and never needs to go into your CSS. Consult [CanIUse](https://caniuse.com/) if you have doubts about a property.

If you have to use them, insert them before the standard property.

```SCSS
.selector-1 {
    -webkit-transition: all 4s ease; /* Android, Chrome, iOS, Edge */
    -moz-transition: all 4s ease; /* FireFox */
    -ms-transition: all 4s ease; /* Internet Explorer */
    -o-transition: all 4s ease; /* Opera */
    transition: all 4s ease; /* Modern browsers */
}

.selector-2 {
    background-image: -webkit-linear-gradient(#a1d3b0, #f6f1d3);
    background-image: -moz-linear-gradient(#a1d3b0, #f6f1d3);
    background-image: -ms-linear-gradient(#a1d3b0, #f6f1d3);
    background-image: -o-linear-gradient(#a1d3b0, #f6f1d3);
    background-image: linear-gradient(#a1d3b0, #f6f1d3);
    -ms-filter: "progid:DXImageTransform.Microsoft.Gradient(startColorStr='#a1d3b0', endColorStr='#f6f1d3', GradientType=0)"; /* linear gradient for IE8+ */
    filter: progid:DXImageTransform.Microsoft.Gradient(startColorStr='#a1d3b0', endColorStr='#f6f1d3', GradientType=0); /* linear gradient for IE7- */
}
```



#### PROPERTIES ORDER

For the sake of readability, I structure all the properties in alphabetical order with the exception of the ones that are ruling the position of the element (`float`, `position`, `top`, `left`, `right`, `bottom`) and the visibility (`display`) at the top of the declaration.

Example:

```SCSS
.selector { 
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: block;
    background-color: #ff0000;
    border: 1px solid #00ff00;
    color: #0103fe;
    font-size: 1.2rem;
    height: auto;
    line-height: 1.4;
    margin: 0 auto;
    padding: .5rem 1rem;
    max-width: 10rem;
    z-index: 1;
}
```

Positioning rules come first because they can remove an element from the normal flow of the document and override box model related styles.


##### EXCEPTION

All extensions and inclusions that are coming from Sass features, should be placed at the top of the declarations, even before the positioning properties, like in the following example:

```SCSS
.selector { 
    @extend .extendedClass;
    @include transition(0.3s, ease-all)
    display: block;
    background-color: #ff0000; 
    border: 1px solid #00ff00;
    color: #0000ff;
    height: 2rem;
    width: 100%;
}
```

[More on this further below](#extensions-and-inclusions-at-the-top-of-the-ruleset).



#### LONG COMMA-SEPARATED PROPERTY VALUES

Those properties (such as collections of gradients or shadows) can be arranged across multiple lines in an effort to improve readability and produce more useful diffs (when checked in).

```SCSS
.selector {
    background-image: linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow: 1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```



### KEEP THE NATURAL FLOW

Do not change the default behaviour of an element whenever possible.

Keep elements in the natural document flow as much as possible.

```SCSS
/* Don't do this */
div {
    display: block; /* it is redundant */
    color: red
}

/* Do this instead */
div {
    color: red;
}
```

Similarly, do not bring an element off the flow if you can avoid it.

```SCSS
/* Don't do this */
.selector {
    position: absolute;
    right: 0;
    width: 100px;
}

/* Do this instead */
.selector {
    margin-left: auto;
    width: 100px;
}
```



### TYPOGRAPHY

#### FONT SIZE

Avoid setting a default font-size on the `html` or `body` selectors. Browsers have a default size of `16px` that we can use as a baseline.

We can control _font-size proportion_ with relative sizing units `rem` or `em`.

If you need to, use a percentage unit on the `:root` or `html` selector's `font-size` property.

For example, in case of `20px` default project's font size, use:

```CSS
html {
    font-size: 125%; // (125/100) * 16px = 20px
}
```

the project's root font size would then be `20px`, therefore, `1.5rem` would be `30px`.



#### PIXELS vs EMs vs. REMs FOR TYPOGRAPHY

Use `rem`s or `em`s over `px`s for font sizes: as recommended in the previous point, these units are scalable and therefore, they offer users the control over the size of the text. [More about this here](https://www.24a11y.com/2019/pixels-vs-relative-units-in-css-why-its-still-a-big-deal/).

Additionally, a unitless `line-height` is preferred because it does not inherit a percentage value of its parent element, but instead is based on a multiplier of the `font-size`.

```SCSS
/* Don't do this */
.selector { 
    font-size: 16px;
    line-height: 24px;
}

/* Do this instead */
.selector { 
    font-size: 1rem;
    line-height: 1.5;
}
```

Read more about when and how we should use `em`s or `rem`s [here](https://zellwk.com/blog/rem-vs-em/).



#### FONT ADJUSTMENT

To help prevent adjustments of font sizes after iOS device orientation changes, use `text-size-adjust: 100%` in the `body` tag so it will be inherited by its children.

```CSS
body {
    -webkit-text-size-adjust: 100%;
    text-size-adjust: 100%;
}
```

[More about `text-size-adjust` in the MDN documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/text-size-adjust)

Notice that modern Safari versions are no more using the `user-scalable` trick in the meta tag `viewport`, while in older versions this is still effective. [Read more about this in this StackOverflow question](https://stackoverflow.com/questions/2710764/preserve-html-font-size-when-iphone-orientation-changes-from-portrait-to-landsca)



### INHERITANCE

Don't duplicate style declarations that can be inherited.

```SCSS
/* Don't do this */
.parent-selector {
    text-shadow: 0 1px 0 #000;
}

.child-selector {
    text-shadow: 0 1px 0 #000;
}

/* Just do this */
.parent-selector {
    text-shadow: 0 1px 0 #000;
}
```

More on [CSS Inheritance on MDN web docs](https://developer.mozilla.org/en-US/docs/Web/CSS/inheritance) and in [this StackOverflow answer](https://stackoverflow.com/a/5612360/2275011) that has a complete list of properties that can be inherited.



### USE SHORTHAND

One feature of CSS is the ability to use shorthand properties and values. Using that allows us to quickly set and identify styles (`margin`, `padding`, `border`, `animation`, `flex`, etc).

```SCSS
/* Don't do this */
.selector {
    padding-top: 1rem;
    padding-left: 2rem;
    padding-right: 2rem;
    padding-bottom: 1rem;
}

/* Do this */
.selector {
    padding: 1rem 2rem 1rem 2rem;
}

/* This is even better */
.selector {
    padding: 1rem 2rem;
}
```

On the contrary, when we are only setting just one value, shorthand alternatives should not be used because it will be hard to identify immediately which CSS attribute is being applied.

```SCSS
/* Don't do this */
.selector {
    border: red;
    background: center;
    margin: 1rem 0 0 0;
}

/* Do this instead */
.selector {
    border-color: red;
    background-position: center;
    margin-top: 1rem;
}
```

More on shorthand properties on the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties).


#### EXCEPTIONS

There are few exceptions to that standard: those are particularly related to the `font` and `background` properties.

In both these cases, it is not always easy to read the shorthand rule and/or understand immediately what the single rule in the shorthand is related to (i.e. `background-position` and `background-size`).

Furthermore, the shorthanded property could become quite long losing readability and breaking the IDE's 80 columns rule.

In those cases, I prefer to use the complete and full property.

```CSS
/* Don't do this */
.selector {
    background: url('../images/branding/logo.png') 10rem 2rem center 100% no-repeat;
}

/* Do this instead */
.selector {
    background-image: url('../images/branding/logo.png');
    background-size: 10rem 2rem;
    background-position: center 100%;
    background-repeat: no-repeat;
}

/* Notice that `background-position` and `background-repeat` are already shorthand properties themselves */
```
```CSS
/* Don't do this */
.selector {
    font: italic small-caps 800 1rem/1.5 "Segoe UI", Verdana, Arial, Helvetica, sans-serif;
}

/* Do this instead */
.selector {
    font-family: "Segoe UI", Verdana, Arial, Helvetica, sans-serif;
    font-size: 1rem;
    font-style: italic;
    font-variant: small-caps;
    font-weight: 800;
    line-height: 1.5;
}
```



### NEVER EVER USE `!IMPORTANT`

**Never ever use `!important`**. That’s it!

There is always another way, check the specificity of the rules and eventually amend them.

Avoiding the use of this attribute is the first step to keep a pretty good level of maintainability.

Side note: the _only rare case_ when there is the necessity to override a third party stylesheet, which we do not have access or permission to edit, _is the only exception_ where this property can be admitted.



### SELECTORS

#### MINIMIZE SELECTORS TIGHTLY COUPLED TO THE DOM ELEMENTS

Consider adding a class to the HTML elements you want to match, especially when your selector exceeds 3 structural pseudo-classes, descendant or sibling combinators.

```SCSS
/* Don't do this */
div p a {
    color: orange;
    text-decoration: none;
}

/* Do this instead */
.paragraph__link {
    color: orange;
    text-decoration: none;
}
```



#### MINIMIZE SELECTOR ACCESSES TO THE DOM

Consider using structural pseudo-classes, descendant or sibling combinators when you realize there are multiple accesses to the DOM when writing a CSS rule.

```SCSS
/* Don't do this */
.article .paragraph .paragraph__link { /* 3 accesses to the DOM to find the elements */
    color: orange;
    text-decoration: none;
}

/* Do this instead */
.article > .paragraph > .paragraph__link { /* 1 access to the DOM to find the elements */
    color: orange;
    text-decoration: none;
}
```



### POSITIONING

- `float` rules are great for pulling elements out of the DOM and forcing them hard up against a left or a right edge.
- The `position` rule is always relative to the nearest positioned parent element. `position: absolute;` pulls elements out of their normal flow. To position absolutely an element relatively to the parent, the parent element needs to be styled `position: relative;` so all child elements will draw from the top, right, bottom and left of this parent container.



### COLOURS

- Lowercase all hex values, for example `#fff`. Lowercase letters are much easier to discern when scanning a document as they tend to have more unique shapes.
- Use shorthand hex values where available, for example `#fff` instead of `#ffffff`.



### MEDIA QUERIES

#### RESPONSIVE LAYOUTS

Use CSS media queries to apply different styling for small and large screens.



#### APPROACH

Use [mobile-first approach](https://www.freecodecamp.org/news/taking-the-right-approach-to-responsive-web-design/).



#### PLACING MEDIA QUERIES

Place media queries as close to their relevant rulesets, whenever possible. Do not bundle them all in a separate stylesheet or at the end of the file. Doing so only makes it easier for developers to miss them in the future.



## SASS/SCSS SPECIFIC STANDARDS

### EXTENSIONS AND INCLUSIONS AT THE TOP OF THE RULESET

All extensions and inclusions should be placed at the top of the declarations because they may have rule(s) that can be specifically overwritten by the ruleset that is extending or including them.

- Always place `@extend` statements on the first lines of a declaration block.
- Where possible, group `@include` statements at the top of a declaration block, after any `@extend` statements.

```SCSS
.selector { 
    @extend .extendedClass;
    @include box-sizing(border-box);
    @include clearfix();
    @include transition(0.3s, ease-all)
    display: block;
    background-color: #ff0000;
    border: 1px solid #00ff00;
    color: #0000ff;
    height: 2rem;
    width: 100%;
}
```



### OPERATORS

Wrap all math operations in parentheses with a single space between values, variables, and operators.

```SCSS
/* Don't do this */
.selector {
    margin: 10px 0 $variable*2 10px;
}

/* Do this instead */
.selector {
    margin: 10px 0 ($variable * 2) 10px;
}
```
