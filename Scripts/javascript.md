[Back to main page](../README.md#frontend-coding-standards-and-best-practices)

## Table of Contents
- [Node Modules](../Node/node-modules.md#node-modules)
- [HTML](../HTML/html.md#html)
- [Styles (CSS/SCSS)](../Styles/styles.md#styles-cssscss)
- [JavaScript/TypeScript](#javascripttypescript)
    - [JavaScript](#javascript)
        - [Consider placing JavaScript scripts at the bottom](#consider-placing-javascript-scripts-at-the-bottom)
        - [Whitespacing and formatting](#whitespacing-and-formatting)
            - [Always use braces](#always-use-braces)
            - [Same line braces](#same-line-braces)
            - [Character spacing](#character-spacing)
            - [Use 4 spaces indentation](#use-4-spaces-indentation)
            - [Always use semicolon](#always-use-semicolon)
            - [Always use comparison](#always-use-comparison)
                - [Exception](#exception)
            - [Avoid comparing to true and false](#avoid-comparing-to-true-and-false)
        - [Variables](#variables)
            - [Camel case variables](#camel-case-variables)
            - [Boolean variables](#boolean-variables)
        - [Use ternary `if` statement whenever possible and easy to read](#use-ternary-if-statement-whenever-possible-and-easy-to-read)
        - [Avoid polluting the global namespace](#avoid-polluting-the-global-namespace)
        - [Check existance of variables, arrays and objects](#check-existance-of-variables-arrays-and-objects)
    - [TypeScript specific standards](#typescript-specific-standards)
        - [Whitespacing and formatting](#whitespacing-and-formatting-1)
            - [Include a single space after colon and before and after equal](#include-a-single-space-after-colon-and-before-and-after-equal)
            - [Always define strict type when declaring variables](#always-define-strict-type-when-declaring-variables)
            - [Include a single space before and after curly brakets when importing](#include-a-single-space-before-and-after-curly-brakets-when-importing)
            - [Use single quotes in typescript files](#use-single-quotes-in-typescript-files)
            - [Include blank line separator between imports and the rest of the code](#include-blank-line-separator-between-imports-and-the-rest-of-the-code)
- [General best practices](../Generals/generals.md#general-best-practices)


---



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
