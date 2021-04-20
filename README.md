# Frontend coding standards and best practices

I want to produce a clean, semantic, cross-browser and well supported code. All of these, with maintainability as one of the first priorities.

In this front-end style guide there are some best practices and standards I am following when coding.

_Note_: in this documents, sometimes I use "I" to refer specifically to what I use (or prefer to use), while some other times I use "We" to highlight a common best practice.

## Table of Contents
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
        - [Avoid to specify the type of imported CSS and JavaScript files](./HTML/html.md#avoid-to-specify-the-type-of-imported-css-and-javascript-files)
        - [Separate content from styles](./HTML/html.md#separate-content-from-style)
        - [Keep the syntax organized](./HTML/html.md#keep-the-syntax-organized)
        - [Reduce markup](./HTML/html.md#reduce-markup)
        - [Whitespacing and formatting](./HTML/html.md#whitespacing-and-formatting)
            - [Indent tags that are very long](./HTML/html.md#indent-tags-that-are-very-long)
            - [Always use double quotes in HTML files](./HTML/html.md#always-use-double-quotes-in-html-files)
            - [Attributes order](./HTML/html.md#attributes-order)
- [Styles (CSS/SCSS)](./Styles/styles.md#styles-cssscss)
    - [CSS](./Styles/styles.md#css)
        - [Use CSS reset or Normalize CSS](./Styles/styles.md#use-css-reset-or-normalize-css)
        - [Never use inline styles](./Styles/styles.md#never-use-inline-styles)
        - [Modularize styles for reuse](./Styles/styles.md#modularize-styles-for-reuse)
        - [Class names](./Styles/styles.md#class-names)
            - [State classes](./Styles/styles.md#state-classes)
        - [Use multiple stylesheets, but be aware of them expanding beyond control](./Styles/styles.md#use-multiple-stylesheets-but-be-aware-of-them-expanding-beyond-control)
        - [Organize CSS with comments](./Styles/styles.md#organize-css-with-comments)
        - [Never use large fixed width elements](./Styles/styles.md#never-use-large-fixed-width-elements)
        - [Never let content rely on a particular viewport width](./Styles/styles.md#never-let-content-rely-on-a-particular-viewport-width)
        - [Whitespacing and formatting](./Styles/styles.md#whitespacing-and-formatting)
            - [Proper spacing between properties](./Styles/styles.md#proper-spacing-between-properties)
            - [One selector per line](./Styles/styles.md#one-selector-per-line)
            - [Blank line between rulesets](./Styles/styles.md#blank-line-between-rulesets)
            - [Same line opening braces](./Styles/styles.md#same-line-opening-braces)
            - [Same column closing braces as the first character of the ruleset](./Styles/styles.md#same-column-closing-braces-as-the-first-character-of-the-ruleset)
            - [Indenting child elements](./Styles/styles.md#indenting-child-elements)
            - [End all declarations with a semicolon](./Styles/styles.md#end-all-declarations-with-a-semicolon)
            - [Use double quotes in style files](./Styles/styles.md#use-double-quotes-in-style-files)
            - [Double quote attribute values](./Styles/styles.md#double-quote-attribute-values)
            - [Avoid units on zero values](./Styles/styles.md#avoid-units-on-zero-values)
            - [Grouping vendor prefixes](./Styles/styles.md#grouping-vendor-prefixes)
            - [Properties order](./Styles/styles.md#properties-order)
                - [Exception](./Styles/styles.md#exception)
            - [Long comma separated property values](./Styles/styles.md#long-comma-separated-property-values)
        - [Keep the natural flow](./Styles/styles.md#keep-the-natural-flow)
        - [Typography](./Styles/styles.md#typography)
            - [Font Size](./Styles/styles.md#font-size)
            - [Pixels vs `em`s vs. `rem`s for typography](./Styles/styles.md#pixels-vs-ems-vs-rems-for-typography)
            - [Font adjustment](./Styles/styles.md#font-adjustment)
        - [Inheritance](./Styles/styles.md#inheritance)
        - [Use shorthand](./Styles/styles.md#use-shorthand)
            - [Exceptions](./Styles/styles.md#exceptions)
        - [Never ever use `!important`](./Styles/styles.md#never-ever-use-important)
        - [Selectors](./Styles/styles.md#selectors)
            - [Minimize selectors tightly coupled to the DOM elements](./Styles/styles.md#minimize-selectors-tightly-coupled-to-the-dom-elements)
            - [Minimize selector accesses to the DOM](./Styles/styles.md#minimize-selector-accesses-to-the-dom)
        - [Positioning](./Styles/styles.md#positioning)
        - [Colours](./Styles/styles.md#colours)
        - [Media queries](./Styles/styles.md#media-queries)
            - [Responsive layouts](./Styles/styles.md#responsive-layouts)
            - [Approach](./Styles/styles.md#approach)
            - [Placing Media Queries](./Styles/styles.md#placing-media-queries)
    - [Sass/SCSS specific standards](./Styles/styles.md#sassscss-specific-standards)
        - [Extensions and inclusions at the top of the ruleset](./Styles/styles.md#extensions-and-inclusions-at-the-top-of-the-ruleset)
        - [Operators](./Styles/styles.md#operators)
- [JavaScript/TypeScript](./Scripts/javascript.md#javascripttypescript)
    - [JavaScript](./Scripts/javascript.md#javascript)
        - [Consider placing JavaScript scripts at the bottom](./Scripts/javascript.md#consider-placing-javascript-scripts-at-the-bottom)
        - [Whitespacing and formatting](./Scripts/javascript.md#whitespacing-and-formatting)
            - [Always use braces](./Scripts/javascript.md#always-use-braces)
            - [Same line braces](./Scripts/javascript.md#same-line-braces)
            - [Character spacing](./Scripts/javascript.md#character-spacing)
            - [Use 4 spaces indentation](./Scripts/javascript.md#use-4-spaces-indentation)
            - [Always use semicolon](./Scripts/javascript.md#always-use-semicolon)
            - [Always use comparison](./Scripts/javascript.md#always-use-comparison)
                - [Exception](./Scripts/javascript.md#exception)
            - [Avoid comparing to true and false](./Scripts/javascript.md#avoid-comparing-to-true-and-false)
        - [Variables](./Scripts/javascript.md#variables)
            - [Camel case variables](./Scripts/javascript.md#camel-case-variables)
            - [Boolean variables](./Scripts/javascript.md#boolean-variables)
        - [Use ternary `if` statement whenever possible and easy to read](./Scripts/javascript.md#use-ternary-if-statement-whenever-possible-and-easy-to-read)
        - [Avoid polluting the global namespace](./Scripts/javascript.md#avoid-polluting-the-global-namespace)
        - [Check existance of variables, arrays and objects](./Scripts/javascript.md#check-existance-of-variables-arrays-and-objects)
    - [TypeScript specific standards](./Scripts/javascript.md#typescript-specific-standards)
        - [Whitespacing and formatting](./Scripts/javascript.md#whitespacing-and-formatting-1)
            - [Include a single space after colon and before and after equal](./Scripts/javascript.md#include-a-single-space-after-colon-and-before-and-after-equal)
            - [Always define strict type when declaring variables](./Scripts/javascript.md#always-define-strict-type-when-declaring-variables)
            - [Include a single space before and after curly brakets when importing](./Scripts/javascript.md#include-a-single-space-before-and-after-curly-brakets-when-importing)
            - [Use single quotes in typescript files](./Scripts/javascript.md#use-single-quotes-in-typescript-files)
            - [Include blank line separator between imports and the rest of the code](./Scripts/javascript.md#include-blank-line-separator-between-imports-and-the-rest-of-the-code)
- [General best practices](./Generals/generals.md#general-best-practices)
    - [Always test projects cross-browser and (possibly) cross-devices when developing](./Generals/generals.md#always-test-projects-cross-browser-and-possibly-cross-devices-when-developing)
    - [Use comments when needed](./Generals/generals.md#use-comments-when-needed)
