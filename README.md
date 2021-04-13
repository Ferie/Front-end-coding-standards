# Frontend coding standards and best practices

I want to produce a clean, semantic, cross-browser and well supported code. All of these, with maintainability as one of the first priorities.

In this front-end style guide there are some best practices and standards I am following when coding.

_Note_: in this documents, sometimes I use "I" to refer specifically to what I use (or prefer to use), while some other times I use "We" to highlight a common best practice.

## Table of Content
- [Node Modules](./Node/node-modules.md#node-modules)
- [HTML](./HTML/html.md#html)
    - [HTML](./HTML/html.md#html)
        - [Validation](./HTML/html.md#validation)
        - [Declare a Doctype](./HTML/html.md#declare-a-doctype)
        - [Declare the language of the page](./HTML/html.md#declare-the-language-of-the-page)
        - [Titles](./HTML/html.md#titles)
        - [Meta Descriptions](./HTML/html.md#meta-descriptions)
        - [Viewport](./HTML/html.md#viewport)
        - [Use semantic HTML 5 tags](./HTML/html.md#use-semantic-html-5-tags)
        - [Close your tags](./HTML/html.md#close-tags)
        - [Use lowercase in your tags](./HTML/html.md#use-lowercase)
        - [Character encoding](./HTML/html.md#character-encoding)
        - [Use conditional comments](./HTML/html.md#use-conditional-comments)
        - [Use practical `id` and `class` names and values](./HTML/html.md#use-practical-id-and-class-names-and-values)
        - [Images need `alt` attributes](./HTML/html.md#images-need-alt-attributes)
        - [Use tables for tabular data only](./HTML/html.md#use-tables-for-tabular-data-only)
        - [Include external CSS inside the `<head>` tag](./HTML/html.md#include-external-css-inside-the-head-tag)
        - [Including CSS and JavaScript](./HTML/html.md#including-css-and-javascript)
        - [Keep the syntax organized](./HTML/html.md#keep-the-syntax-organized)
        - [Reduce markup](./HTML/html.md#reduce-markup)
        - [Whitespacing and formatting](./HTML/html.md#whitespacing-and-formatting)
            - [Indent tags that are very long](./HTML/html.md#indent-tags-that-are-very-long)
            - [Always use double quotes in HTML files](./HTML/html.md#always-use-double-quotes-in-html-files)
            - [Attributes order](./HTML/html.md#attributes-order)
- [Styles (CSS/SCSS)](./Styles/styles.md#styles-cssscss)
    - [CSS](#css)
        - [Use a CSS reset](#use-a-css-reset)
        - [Never use inline styles](#never-use-inline-styles)
        - [Organize CSS with comments](#organize-css-with-comments)
        - [Whitespacing and formatting](#whitespacing-and-formatting-1)
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
        - [Inheritance](#inheritance)
        - [Pixels vs `em`s vs. `rem`s for typography](#pixels-vs-ems-vs-rems-for-typography)
        - [Use shorthand](#use-shorthand)
        - [Never ever use `!important`](#never-ever-use-important)
        - [Selectors](#selectors)
            - [Minimize selectors tightly coupled to the DOM elements](#minimize-selectors-tightly-coupled-to-the-dom-elements)
            - [Minimize selector accesses to the DOM](#minimize-selector-accesses-to-the-dom)
        - [Class names](#class-names)
            - [State classes](#state-classes)
        - [Modularize styles for reuse](#modularize-styles-for-reuse)
        - [Use multiple stylesheets, but be aware of them expanding beyond control](#use-multiple-stylesheets-but-be-aware-of-them-expanding-beyond-control)
        - [Positioning](#positioning)
        - [Colours](#colours)
        - [Media query placement](#media-query-placement)
    - [Sass specific standards](#sass-specific-standards)
        - [Extensions and inclusions at the top of the ruleset](#extensions-and-inclusions-at-the-top-of-the-ruleset)
        - [Operators](#operators)
- [JavaScript/TypeScript](./Scripts/javascript.md#javascripttypescript)
    - [JavaScript](#javascript)
        - [Consider placing JavaScript scripts at the bottom](#consider-placing-javascript-scripts-at-the-bottom)
        - [Whitespacing and formatting](#whitespacing-and-formatting-2)
            - [Always use braces](#always-use-braces)
            - [Same line braces](#same-line-braces)
            - [Character spacing](#character-spacing)
            - [Use 4 spaces indentation](#use-4-spaces-indentation)
            - [Always use semicolon](#always-use-semicolon)
            - [Always use comparison](#always-use-comparison)
                - [Exception](#exception-1)
            - [Avoid comparing to true and false](#avoid-comparing-to-true-and-false)
        - [Variables](#variables)
            - [Camel case variables](#camel-case-variables)
            - [Boolean variables](#boolean-variables)
        - [Use ternary `if` statement whenever possible and easy to read](#use-ternary-if-statement-whenever-possible-and-easy-to-read)
        - [Avoid polluting the global namespace](#avoid-polluting-the-global-namespace)
        - [Check existance of variables, arrays and objects](#check-existance-of-variables-arrays-and-objects)
    - [TypeScript specific standards](#typescript-specific-standards)
        - [Whitespacing and formatting](#whitespacing-and-formatting-3)
            - [Include a single space after colon and before and after equal](#include-a-single-space-after-colon-and-before-and-after-equal)
            - [Always define strict type when declaring variables](#always-define-strict-type-when-declaring-variables)
            - [Include a single space before and after curly brakets when importing](#include-a-single-space-before-and-after-curly-brakets-when-importing)
            - [Use single quotes in typescript files](#use-single-quotes-in-typescript-files)
            - [Include blank line separator between imports and the rest of the code](#include-blank-line-separator-between-imports-and-the-rest-of-the-code)
- [General best practices](./Generals/generals.md#general-best-practices)
    - [Checking in cross browser and possibly cross devices while developing](#checking-in-cross-browser-and-possibly-cross-devices-while-developing)
    - [Comments](#comments)

---



# STYLES (CSS/SCSS)

## CSS

### USE A CSS RESET

CSS reset will ensure that all elements have no particular style so you can define your own.

### NEVER USE INLINE STYLES

When creating the markup, do not use inline styling because it would be very hard to override these styles in case you need to.

### ORGANIZE CSS WITH COMMENTS

Let’s keep our styles organized in logical groups and provide a comment noting what the following styles pertain to. See more at the comment paragraph of this guide.

### WHITESPACING AND FORMATTING

#### PROPER SPACING BETWEEN PROPERTIES

- Include a single space before the opening brace of a ruleset.
- Include a single space after the colon and semicolon of a property.
- Include a single space after each comma in comma-separated property or function values.
- Prefer one property per line (in this case, no space after the semicolon).
```SCSS
/* Don't do this */
.selector{display:none;background:rgba(2,0,36,.5);color:#000000} 

/* Do this */
.selector { display: none; background: rgba(2, 0, 36, .5); color: #000000; } 

/* This is even better - for the sake of readability */
.selector {
    display: none;
    background: rgba(2, 0, 36, .5);
    color: #000000;
}
```

#### ONE SELECTOR PER LINE

```SCSS
/* Don't do this */
.selector-one, .selector-two, .selector-three {
    display: none;
    background: #ff0000;
    color: #000000;
}

/* Do this instead */
.selector-one,
.selector-two,
.selector-three {
    display: none;
    background: #ff0000;
    color: #000000;
}
```

#### BLANK LINE BETWEEN RULESETS

```SCSS
/* Don't do this */
.selector-one {
    display: none;
    background: #ff0000;
    color: #000000;
}
.selector-two,
.selector-three {
    display: block;
    background: #00ff00;
    color: #0000ff;
}

/* Do this instead */
.selector-one {
    display: none;
    background: #ff0000;
    color: #000000;
}

.selector-two,
.selector-three {
    display: block;
    background: #00ff00;
    color: #0000ff;
}
```
```SCSS
/* Don't do this */
.selector {
    display: none;
    background: #ff0000;
    color: #000000;
    &__child {
        display: block;
        background: #00ff00;
        color: #0000ff;
    }
}

/* Do this instead */
.selector {
    display: none;
    background: #ff0000;
    color: #000000;

    &__child {
        display: block;
        background: #00ff00;
        color: #0000ff;
    }
}
```

#### SAME LINE OPENING BRACES

```SCSS
/* Don't do this */
.selector
{
    display: none;
    background: #ff0000;
    color: #000000;
}

/* Do this instead */
.selector {
    display: none;
    background: #ff0000;
    color: #000000;
}
```

#### SAME COLUMN CLOSING BRACES AS THE FIRST CHARACTER OF THE RULESET

```SCSS
/* Don't do this */
.selector {
    display: none;
    background: #ff0000;
    color: #000000; }

/* Do this instead */
.selector {
    display: none;
    background: #ff0000;
    color: #000000;
}
```

#### INDENTING CHILD ELEMENTS

Use 4 spaces on each indentation.
```SCSS
.selector {
    display: none;
    background: #ff0000;
    color: #000000;

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

One way to easily cut down on the amount of CSS we write is to remove the unit from any zero value. A zero will always be a zero.
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

_DO NOT use all the major prefixes on every CSS3 property_.

It appears that many generic mixins are just putting everything with the prefixes: something like `-o-border-radius` has never existed and never needs to go into your CSS. Consult [CanIUse](https://caniuse.com/) if you have doubts about a property.

If you have to use them, insert them before the standard property.
```SCSS
.selector { 
    -webkit-transition: all 4s ease; /* Android, Chrome, iOS */
    -moz-transition: all 4s ease; /* FireFox */
    -ms-transition: all 4s ease; /* Internet Explorer */
    -o-transition: all 4s ease; /* Opera */
    transition: all 4s ease; /* Modern browsers */
}
```

#### PROPERTIES ORDER

There is no real standard on how to order the properties inside a CSS rule, but for the sake of readability we should structure them in alphabetical order with the exception of the ones that are ruling the position of the element (`float`, `position`, `top`, `left`, `right`, `bottom`) and the visibility (`display`) at the top of the declaration and the ones that are ruling the dimensions (`max-height`, `max-width`, `height` and `width`) at the bottom where `width` should be (considering alphabetical order).

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
    color: #0000ff;
    font-size: 1rem;
    line-height: 1;
    margin: 0 auto;
    padding: .5rem 1rem;
    max-width: 10rem;
    height: auto;
    z-index: 10;
}
```

Positioning comes first because it can remove an element from the normal flow of the document and override box model related styles.

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

More on this further below.

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

Do not change the default behaviour of an element if you can avoid it. Keep elements in the natural document flow as much as you can. For example, removing the white-space below an image shouldn't make you change its default display.
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

### INHERITANCE

Don't duplicate style declarations that can be inherited.
```SCSS
/* Don't do this */
.parent-selector {
    text-shadow: 0 1px 0 #fff;
}

.child-selector {
    text-shadow: 0 1px 0 #fff;
}

/* Just do this */
.parent-selector {
    text-shadow: 0 1px 0 #fff;
}
```

### PIXELS vs EMs vs. REMs FOR TYPOGRAPHY

Use REMs with a pixel fallback for `font-size`, because it offers absolute control over text.

Additionally, a unitless `line-height` is preferred because it does not inherit a percentage value of its parent element, but instead is based on a multiplier of the `font-size`.
```SCSS
/* Don't do this */
.selector { 
    font-size: 16px;
    line-height: 32px;
}

/* Do this instead */
.selector { 
    font-size: 1rem;
    line-height: 1;
}
```

### USE SHORTHAND

One feature of CSS is the ability to use shorthand properties and values. Using that allows us to quickly set and identify styles.
```SCSS
/* Don't do this */
.selector {
    padding-top: 1px;
    padding-left: 2px;
    padding-right: 2px;
    padding-bottom: 1px;
}

/* Do this */
.selector {
    padding: 1px 2px 1px 2px;
}

/* This is even better */
.selector {
    padding: 1px 2px;
}
```

But when we’re only setting one value, shorthand alternatives should not be used, because it will be hard to identify which CSS attribute is being applied.
```SCSS
/* Don't do this */
.selector {
    background: center;
}

/* Do this instead */
.selector {
    background-position: center;
}
```

### NEVER EVER USE `!IMPORTANT`

**Never ever use `!important`**. That’s it!

There is always another way, check the specificity of your rules and eventually amend them.

Avoiding the use of this attribute, will keep a pretty good level of maintainability.

Note: the ***extremely rare case*** where this can be admitted, is when there is the necessity to override a third party stylesheet which you do not have access or permission to edit.

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

### CLASS NAMES

- Keep classes lowercase and use dashes or underscores as per BEM methodology (do not use camelCase nor *CapitalCase*).
- Avoid excessive and arbitrary shorthand notation. `.btn` is useful for buttons, but `.b` doesn't mean anything.
- Keep classes as short and succinct as possible.
- Use meaningful names; use structural or purposeful names over presentational.
- Prefix classes based on the closest parent or base class.

It is also useful to apply many of those rules when creating Sass and/or Less variable names.

#### STATE CLASSES

Use the `.is-*` prefix for state classes that are shared between CSS/SCSS and JavaScript to denote a temporary styling application.

Example:
```HTML
<div class="accordion-tab is-active" data-accordion="true">
    ...
</div>
```

### MODULARIZE STYLES FOR REUSE

CSS is built to allow styles to be reused, specifically with the use of classes. For this reason, styles assigned to a class should be modular and available to share across elements as necessary.

### USE MULTIPLE STYLESHEETS, BUT BE AWARE OF THEM EXPANDING BEYOND CONTROL

Depending on the complexity of the design and the size of the site, sometimes it’s easier to make smaller, multiple stylesheets instead of a giant one.

### POSITIONING

- `float` rules are great for pulling elements out of the DOM and forcing them hard up against a left or a right edge.
- The `position` rule is always relative to the nearest positioned parent element. `position: absolute;` pulls elements out of their normal flow. To position absolutely an element relatively to the parent, the parent element needs to be styled `position: relative;` so all child elements will draw from the top, right, bottom and left of this parent container.

### COLOURS

- Lowercase all hex values, for example `#fff`. Lowercase letters are much easier to discern when scanning a document as they tend to have more unique shapes.
- Use shorthand hex values where available, for example `#fff` instead of `#ffffff`.

### MEDIA QUERY PLACEMENT

Place media queries as close to their relevant rulesets, whenever possible. Do not bundle them all in a separate stylesheet or at the end of the file. Doing so only makes it easier for developers to miss them in the future.

## SASS SPECIFIC STANDARDS

### EXTENSIONS AND INCLUSIONS AT THE TOP OF THE RULESET

All extensions and inclusions should be placed at the top of the declarations because they may have rules that can be specifically overwritten by the ruleset.

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

# JAVASCRIPT/TYPESCRIPT

## JAVASCRIPT

### CONSIDER PLACING JAVASCRIPT SCRIPTS AT THE BOTTOM

When loading a script, the browser cannot continue until the entire file has been loaded. If we have JavaScript files in order to add functionality, we should place those files at the bottom, just before the closing body tag. This is a good performance practice and the results are quite noticeable.

### WHITESPACING AND FORMATTING

#### ALWAYS USE BRACES
```TypeScript
// Don't do this
if (blah === "foo")
    bar("foo");

// Do this instead
if (blah === "foo") {
    bar("foo");
}
```

#### SAME LINE BRACES
```TypeScript
// Don't do this
if (blah === "foo")
{
    bar("foo");
}

// Do this instead
if (blah === "foo") {
    bar("foo");
}
```

Main reason for this is simply that is a [JavaScript pitfall](https://stackoverflow.com/questions/3641519/why-do-results-vary-based-on-curly-brace-placement), but also it looks nicer.

#### CHARACTER SPACING

- Use a  single space between values, variables, and operators.
- Use a single space after commas.
```TypeScript
// Don't do this
var x=123;
var baz="Concatenated string"+x;

if(blah==="foo"){
    foo("bar",baz);
}

// Do this instead
var x = 123;
var baz = "Concatenated string" + x;

if (blah === "foo") {
    foo("bar", baz);
}
```

#### USE 4 SPACES INDENTATION
```TypeScript
// Don't do this
if (blah === "foo") {
  foo("bar");
}

// Do this instead
if (blah === "foo") {
    foo("bar");
}
```

#### ALWAYS USE SEMICOLON
```TypeScript
// Don't do this
var foo = true

if (foo) {
    bar()
}

// Do this instead
var foo = true;

if (foo) {
    bar();
}
```

#### ALWAYS USE COMPARISON
```TypeScript
// Don't do this
if (blah == "foo") {
    foo("bar");
}

// Do this instead
if (blah === "foo") {
    foo("bar");
}
```

The use of the `==` equality operator allows frustrating bugs to slip through almost undetected while the use of the strict equality operator `===` does not run type coercion and therefore strictly evaluates the difference between two objects.

##### EXCEPTION

Double equals comparison is allowed when comparing to `null`, because it will detect both `null` or `undefined` properties. [Here a great article about this exception](https://medium.com/javascript-in-plain-english/how-to-check-for-null-in-javascript-dffab64d8ed5#:~:text=One%20way%20to%20check,the%20double%20equality%20%3D%3D%20operator%3A&text=So%2C%20when%20programming%20to%20check,for%20either%20null%20or%20undefined%20.) and [here the MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness).
```TypeScript
var foo = null;

// `foo` is null, but `bar` is undefined as it has not been declared...
if (foo == null && bar == null) {
    // ...still get in here
}
```

#### AVOID COMPARING TO TRUE AND FALSE
```TypeScript
// Don't do this as it's redundant
if (foo === true) {
    blah("foo");
}

if (bar === false) {
    blah("bar");
}

// Do this instead
if (foo) {
    blah("foo");
}

if (!bar) {
    blah("bar");
}
```

### VARIABLES

Use meaningful names when creating a variable: think about how the variable is going to serve your purpose. If the variable is caching a jQuery CSS selector, give it the name of the selector prefixed with `$`.

#### CAMEL CASE VARIABLES

The camel casing (or *camelCasing*) of JavaScript variables is accepted as the standard in most coding environments. The only exception is the use of uppercase to denote constants and underscores to denotate private variables (TypeScript).
```TypeScript
// Don't do this
let MyVar = "blah";

// Do this instead
let myVar = "blah";
```

#### BOOLEAN VARIABLES

Booleans should be easily identifiable by the way they are named. Use prefixes like `is`, `can` or `has` to propose a question.
```TypeScript
// Do this
let isEditing = true;

obj.canEdit = true;

user.hasPermission = true;
```

### USE TERNARY IF STATEMENT WHENEVER POSSIBLE AND EASY TO READ
```TypeScript
// Don't do this
if (foo) {
    blah("foo");
} else {
    blah("bar");
}

// Do this instead
foo ? blah("foo") : blah("bar");
```

### AVOID POLLUTING THE GLOBAL NAMESPACE

The chance of script and variable conflicts is increased, and both the source file and the namespace itself become littered with countless ambiguously named variables.

### CHECK EXISTANCE OF VARIABLES, ARRAYS AND OBJECTS
```TypeScript
if (element) {
    // element exists
} else {
    // element does not exists
}
```

This simple `if` statement is returning `false` for all of the following:
- `undefined`: if the *value, array or object* is not defined;
- `null`: if the *value, array or object* is null;
- `''`: if the *value* is an empty string;
- `0`: if the *value* is number zero;
- `NaN`: if the *value* is not a number;
- `false`: if the *value* is a boolean false.

Please note that the same `if` statement is always returning `true` for all of the following:
- empty arrays `[]` and empty objects `{}`: because they are defined;
- spaced string `'  '`: because it is a valid and defined object.

## TYPESCRIPT SPECIFIC STANDARDS

### WHITESPACING AND FORMATTING

#### INCLUDE A SINGLE SPACE AFTER COLON AND BEFORE AND AFTER EQUAL
```TypeScript
// Don't do this
let str : string = 'This is a definition of a string';
let bool :boolean= false;
let nr:number=123;

// Do this instead
let str: string = 'This is a definition of a string';
let bool: boolean = false;
let nr: number = 123;
```

#### ALWAYS DEFINE STRICT TYPE WHEN DECLARING VARIABLES
```TypeScript
// Don't do this
let str = 'This is a definition of a string';
let bool = false;
let nr = 123;

// Do this instead
let str: string = 'This is a definition of a string';
let bool: boolean = false;
let nr: number = 123;
```

#### INCLUDE A SINGLE SPACE BEFORE AND AFTER CURLY BRAKETS WHEN IMPORTING
```TypeScript
// Don't do this
import {ComponentName} from './path/to/component';

// Do this instead
import { ComponentName } from './path/to/component';
```

#### USE SINGLE QUOTES IN TYPESCRIPT FILES
```TypeScript
// Don't do this
import { ComponentName } from "./path/to/component";

let str: string = "This is a definition of a string";

// Do this instead
import { ComponentName } from './path/to/component';

let str: string = 'This is a definition of a string';
```

#### INCLUDE BLANK LINE SEPARATOR BETWEEN IMPORTS AND THE REST OF THE CODE
```TypeScript
// Don't do this
import { ComponentName } from './path/to/component';
let str: string = 'This is a definition of a string';

// Do this instead
import { ComponentName } from './path/to/component';

let str: string = 'This is a definition of a string';
```

# GENERAL BEST PRACTICES

### CHECKING IN CROSS-BROWSER AND (POSSIBLY) CROSS-DEVICES WHILE DEVELOPING

Cross-browser issues are a major problem for front-end developers, especially due to *Internet Explorer* and *Safari*. It is a good practice to test our code against all the browsers supported once the development is finished and (possibly) test it with different devices. In this last case, the Chrome browser is helpful in testing different mobile renderings and engines.

### COMMENTS

Some parts of a project will never be easy to scan and understand. Consider a complicated regular expression, or a math function calculating angles or switching between degrees and radians. Without the comment above, beginner and intermediate readers will be fairly clueless to the scripts' meaning.

Well commented code is extremely important. Take time to describe components, how they work, their limitations, and the way they are constructed. Don't leave others in the team guessing as to the purpose of uncommon or non-obvious code.

- Each SCSS partial should have a clear comment header to define the role of this section of code.
- Place comments on a new line above their subject.
- Keep line-length to a sensible maximum (e.g. 80 columns).
- Make liberal use of comments to break SCSS code into discrete sections.
- Use "sentence case" comments and consistent text indentation.
- Keep One space between the single line comment and the comment you are writing.

[More on comment structures](https://www.doxygen.nl/manual/docblocks.html).
```JavaScript
/**
 * Multi line comment in JavaScript.
 * This is a multi line comment with the text that describes, in detail, how the
 * below code works, any limitations, and the way it is constructed.
 * This comment is a standard in the JavaScript/TypeScript world.
 */

// Single line comment in JavaScript
```

```SCSS
/***********************************************************************************\
 * Multi line comment in the style files (CSS/SCSS).                               *
 * There is no real standard for multi-line comments in the styling files, you can *
 * find many inspirations outside or simply use this example.                     *
\***********************************************************************************/

/* Single line comment in the style files (CSS/SCSS) */
```

This is another good example of a comment that describes the reason for some rules in the ruleset:
```SCSS
/**
 * Grid container
 *
 * Must only contain `.cell` children.
 *
 * 1. Remove inter-cell whitespace
 * 2. Prevent inline-block cells wrapping
 */

.grid {
    font-size: 0; /* 1 */
    height: 100%;
    white-space: nowrap; /* 2 */
}
```
