[Back to main page](../README.md#frontend-coding-standards-and-best-practices)

## Table of Contents
- [Node Modules](../Node/node-modules.md#node-modules)
- [HTML](../HTML/html.md#html)
- [Styles (CSS/SCSS)](../Styles/styles.md#styles-cssscss)
- [JavaScript/TypeScript](../Scripts/javascript.md#javascripttypescript)
- [General best practices](#general-best-practices)
    - [Always test projects cross-browser and (possibly) cross-devices when developing](#always-test-projects-cross-browser-and-possibly-cross-devices-when-developing)
    - [Use comments when needed](#Use-comments-when-needed)


---



# GENERAL BEST PRACTICES

### ALWAYS TEST PROJECTS CROSS-BROWSER AND (POSSIBLY) CROSS-DEVICES WHEN DEVELOPING

Cross-browser issues are a major problem for front-end developers, especially due to *Internet Explorer* and *Safari*. It is a good practice to test our code against all the browsers supported once the development is finished and (possibly) test it with different devices. In this last case, the Chrome browser is helpful in testing different mobile renderings and engines.



### USE COMMENTS WHEN NEEDED

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
