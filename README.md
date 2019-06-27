# Frontend Styleguide

## Table of Contents

- [Intro](#intro)
- [HTML5](#html5)
    - [Markup Languages](#markup-languages)
    - [Semantics](#semantics)
    - [Language features](#language-features)
    - [Language styleguide](#language-styleguide)
    - [Techniques](#techniques)
- [Style](#style)
    - [Semantics](#semantics)
    - [CSS](#css)
        - [Specificity](#specificity)
        - [BEM](#bem)
        - [SMACSS](#smacss)
        - [Language features](#language-features-1)
    - [SCSS](#scss)
        - [Compile SCSS](#compile-scss)
        - [Language features](#language-features-2)
        - [Writing SASS with BEM](#writing-sass-with-bem)
        - [Pattern Library](#pattern-library)
        - [Styles in Angular](#styles-in-angular)
- [Javascript/TypeScript](#javascript)
    - [Basics](#basics)
    - Advanced
    - OOJS
- JSON
- Markdown



- Angular 1.x
    - TDD
    - Modularity
    - Naming conventions
- General
    - Modularity
    - DRY principles
    - Documentation
    - Performance
    - Pattern Library


- Tools
    - Chrome Developer Tools
    - Linting & testing
- Workflow
    - Grunt/Gulp
    - Git
    - Merging
    - Branching
    - Deploying
    - Using UAT
    - Ticket lifecycle
- Design
    - Responsive
    - Mobile
    - Accessibility
    - Usability
    - Consistency
- Working with others
    - Establishing requirements
    - Giving estimates
    - Interfacing with PMs/stakeholders
    - Communication
    - Collaborating with other developers
    - Pushing back

## Intro

These are general code formatting rules that I am applying to my projects.

Those are intended as best practice to be used for Styles all the languages that a Front End Developer is using: styles (CSS, SCSS, etc.), HTML, JavaScript's and TypeScript's files, JSON's file, Markdown, etc.

## HTML5

Is a markup language that stands for HyperText Markup Language: the most updated version is 5.

### Markup Languages

A markup language is a system for annotating a document in a way that is syntactically distinguishable from the text.

### Semantics

Naming conventions is one of the most important aspect of writing maintainable code. There are two main approaches: the **semantic** approach and the **non-semantic** approach.
```HTML
<!-- non semantic -->
<div class="red pull-left pb3">
<div class="grid row">
<div class="col-xs-4">

<!-- semantic -->
<div class="basket">
<div class="product">
<div class="search-results">
```

For the sake of the readability, prefer the [semantic approach](https://maintainablecss.com/chapters/semantics/).

Also, using a semantic approach it is easier to build a responsive website and to find an element inside the code.

In addition, read [MDNs HTML5 semantics articles](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5#SemantIcs).

In general you want your markup to be:
- meaningful;
- minimal as possible to convey your information;
- easy to read and understand;
- not hundreds of divs, use the appropriate tags for each element.

### Language Features

- Be aware of the [HTML attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes), and use them correctly
- Be aware of the [HTML5 elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) available to you and use them appropriately (mostly keeping in my [semantics](#semantics), but also browser support).

### Language styleguide

**HTML 5**:
- Add the doctype before the initial `html` at the top of the page: `<!DOCTYPE html>`
- Do not use `/>` at the end of self closing elements (no more required with HTML5).
- Group elements of the same type in the `<head>` (all the `link`s, `script`s, `meta`s, etc.).
- Try to put the third party libraries just before the end of the `body`.

### Techniques

[MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML) is a good resource. It's all worth reading, but some of the more important articles are:
- How to write [forms](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms_in_HTML)
- [Obsolete HTML development practices](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Obsolete_things_to_avoid)
- The difference between [inline](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements) and [block-level](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements) elements
- The [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/)
- [Optimization](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Tips_for_authoring_fast-loading_HTML_pages)

## Style

Style markup language pages enable the separation of presentation and content, including layout, colors, and fonts.

This separation can improve content accessibility, provide more flexibility and control in the specification of presentation characteristics, enable multiple web pages to share the formatting, and reduce complexity and repetition in the structural content.

This is the list of markup languages that can be styled by CSS:
- HyperText Markup Language (HTML)
- Extensible HyperText Markup Language (XHTML)
- Extensible Markup Language (XML)
- Scalable Vector Graphic (SVG)
- XML User Interface Language (XUL)

The followings are general styleguide rules that I usually apply while coding.

### Semantics

As said before, using a semantic approach is easier to build a responsive website and we all know how much this is important today.

Semantic classes don't convey their styles, but that's fine, that's what CSS is for. Semantic classes mean something to HTML, CSS, Javascript and automated functional tests.

### CSS

**[Cascading style sheets](https://www.w3.org/standards/webdesign/htmlcss)** are used to format the layout of Web pages. They can be used to define element's styles of Web pages. For a developer is easier to create a uniform look across several pages instead of defining the style of each element within a page's HTML

Commonly used styles need to be defined only once in a CSS document. Then they can be used by any page that references the CSS file. Plus, CSS makes it easy to change styles throughout a website at once.

#### Specificity

Very important: read the [MDN article](https://developer.mozilla.org/en/docs/Web/CSS/Specificity) about specificity.

The following naming conventions could help you avoid running into confusing specificity issues. I usually use either one or the other.

#### BEM

**[BEM (Block Element Modifier)](http://getbem.com/)** is a methodology that helps you to create reusable components and code sharing in front-end development. It is a good technique for writing CSS. This also affects the way developers think about and write HTML classes, take that into account when writing markup.

The basic idea is to reduce [specificity](#specificity) and class name clashes, and increase code reusability, maintainability, and modularity.

**Some resources**

- Some [simple BEM examples](https://css-tricks.com/bem-101/)
- [A bit more in-depth article](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) with some good examples
- [Another brief article, with good resources section](http://getbem.com/introduction/)
- [In depth article](https://medium.com/objects-in-space/objects-in-space-f6f404727#.xr4i3ogfq) on creating a BEM style module in [SCSS](#scss), with added examples of states

#### SMACSS

**[SMACSS (Scalable and Modular Architecture for CSS)](http://smacss.com/)**, pronounced "smacks", is more a style guide than rigid framework. Is a way to examine your design process and as a way to fit those rigid frameworks into a flexible thought process. It is an attempt to document a consistent approach to site development when using CSS.

#### Language Features

- [The different CSS keywords](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#Keyword_index) - obviously nobody will memorize all of these, but the most commonly used ones should be.
- [At-rule statements](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule).
- CSS Selectors, including attribute selectors, pseudo-elements, and pseudo-classes  - [[List](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#Selectors)] - [[Article](https://developer.mozilla.org/en/docs/Web/Guide/CSS/Getting_started/Selectors)].
- How to use [media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries).
- CSS Concepts like the [box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model) and how [inheritance](https://developer.mozilla.org/en-US/docs/Web/CSS/inheritance) works.
- How to use [flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes): it helps to create a very good layouts (watch out for older IE browsers).
- Another helpful, but [relatively new](https://caniuse.com/#feat=css-grid), feature is [grid](https://developer.mozilla.org/en-US/docs/Web/CSS/grid) (check the retrocompatibility especially older IE and Edge until version 15).

### SCSS

*CSS preprocessors* make it easy to automate repetitive tasks, reduce the number of errors and code bloat, create reusable code snippets, and ensure backward compatibility.

**[Syntactically Awesome Style Sheets](http://sass-lang.com/)**, is a scripting languages that extend the default capabilities of CSS. They enable developers to use logic in their CSS code, such as variables, nesting, inheritance, mixins, functions, and mathematical operations.

SASS require *[Ruby](https://www.ruby-lang.org/it/)* to be installed on the machine, to work properly.

#### Compile SCSS

I usually compile SCSS files using [gulp-sass](https://www.npmjs.com/package/gulp-sass) that is a very light-weight wrapper which uses [Libsass](https://github.com/sass/libsass) compiler.

It might have some slight differences compared to the original Ruby Sass compiler, but it is faster, and easier to configure in a [Gulp](https://gulpjs.com/) file combined with other tasks. Have a look at the [Sass compatibility comparison](http://sass-compatibility.github.io/).

Usually, projects I am working on, that need compilation, have a watch task set up to continuously compile sass files as they are modified.

#### Language Features

- [Variables](http://sass-lang.com/guide#topic-2): these should be housed in a _variables.scss file, if they are to be used across the site, or at the top of the module you're writing, if they are to be used only for that module.
- [Nesting](http://sass-lang.com/guide#topic-3): it is tempting at first to write your sass to mimic your markup structure, but please do not do this. Your compiled CSS will be brittle, and break when your page structure changes, and it will lead to unintended specificity. Try to write your sass as shallow as possible. Using BEM can help with this.
- [Partials](http://sass-lang.com/guide#topic-4): these should follow the naming convention for sass and the filename should start with an underscore. Most of the sass partials you will write will be ui components. They should be fairly small, and just contain the one ui component, or ui component type that you are writing styles for. They might also be helpers, or mixins, or a variables partial.  

    They are imported into your main sass stylesheet, and ideally they are the only thing in your main sass stylesheet.
    i.e: `sass/ui/_buttons.scss` would be imported into `sass/main.scss` by typing `@import "ui/buttons";`
- [Mixins & Extends](http://sass-lang.com/guide#topic-6): this is where Sass becomes very powerful. Mixins and Extends allow you to write very reusable, concise code. Take advantage of them when possible.  
- [More advanced features](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#control_directives__expressions): `@if`, `@each`, etc empower developer life. Instead of writing something like
    ```CSS
    .class-1 {}

    .class-2 {}

    ...

    .class-9 {}
    ```
    we can write  
    ```SCSS
    @for $i from 1 through 9 {
        .class-#{$i} {}
    }
    ```

- [Maps](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#maps) and [Map Functions](http://sass-lang.com/documentation/Sass/Script/Functions.html#map-functions): very useful, especially when combined with loops and mixins. They allow you to do something like this:
    ```SCSS
    $buttons: (
        'primary': 'blue',
        'secondary': 'green',
        'disabled': 'grey'
    );

    @each $button-type, $color, in ($buttons) {
        .button--#{$button-type} {
            background-color: $color;
        }
    }
    ```

#### Writing SASS with BEM

Sass makes it very easy to write in BEM style. You can easily write something like this:

**SCSS**
```SCSS
.button {
    color: $blue;

    &--disabled {
        color: $grey;
    }

    &__icon {
        right: 10px;
    }
}
```

**CSS output**
```CSS
.button {
    color: #007fae;
}

.button--disabled {
    color: #424242;
}

.button__icon {
    right: 10px;
}
```

**HTML usage**
```HTML
<a class="button"></a>
<a class="button button--disabled"></a>
<a class="button button__icon"></a>
<a class="button button__icon button--disabled"></a>
```

This will generate nice BEM style classes with minimal sass code. Don't be afraid to break out of the current code block if you think your selector chain will become unnecessarily long.

#### BEM States

A useful addition to this is "_states_".

A state describes a dynamic or conditional appearance of an element.

**SCSS** 
```SCSS
.accordion {
    max-height: 0;
    overflow: hidden;

    &.is-active {
        max-height: $accordionHeight;
    }
}
```

This is preferable to a class like `.accordion--is-active` because it makes it clear that it's a class that is dynamic in nature.

Another state type you can use, although it's use case is less common, is `.has-`

**SCSS**
```SCSS
body {
    font-size: 16px;

    // Don't scroll the body when there's a modal open
    &.has-modal {
        max-height: 100vh;
        overflow: hidden;
    }
}
```











### Pattern Library

At Essence we use something called the Pattern Library when writing frontend code. The Pattern Library is a library of general purpose Sass mixins that should be included into your project and used to deliver a **consistent**, **reusable**, and **easy to maintain** user interface.

### Basics

#### How to install the Pattern Library

The pattern library is typically installed as a submodule inside the parent project in a `patterns` subdirectory of your styles folder.

An example `.gitmodules` file is:

```JavaScript
[submodule "src/styles/patterns"]
path = src/styles/patterns
url = git@bitbucket.org:essencedigital/tesco-mobile-pattern-library.git
branch = feature/shop-app
```

Since the Pattern Library currently relies on [Compass Mixins](https://github.com/Igosuki/compass-mixins), you will likely have to run
```bash
npm install
```

after initialising the submodule
#### How to include the Pattern Library into your site
The Pattern Library is designed so that you can easily import the entire library into your project. In your main stylesheet, just write
```SCSS
@import "PATH_TO_PATTERN_LIBRARY/patterns";
```

`_patterns.scss` is a [Sass partial](http://sass-lang.com/guide#topic-4) that contains all the patterns available in the Pattern Library. You shouldn't need to remove any references to an existing pattern since each pattern only gets output into your generated code if used. 

Currently the Pattern Library relies on [Compass Mixins](https://github.com/Igosuki/compass-mixins), but this dependency should be removed since there isn't much utility in the Compass Mixin library any more.

### Creating a pattern
**Steps**
1) First, make sure there isn't an existing pattern that meets your needs. A good rule of thumb is **only add to the Pattern Library if you need to**. For example, if you're making a new component that looks like a panel, make sure you can't use `box-pattern`. Maybe adding a modifier to an existing pattern will suit your needs. 

2) Create a new partial in the Pattern Library folder. Add a reference to this new partial in the main `_patterns.scss` partial. The new partial should be named with a `-partial` suffix, eg `_fancy-element-pattern.scss`.

3) Add a pattern mixin to your new pattern file. the mixin should also have the `-pattern` suffix, eg `@mixin fancy-element-pattern()`. 
If there are variables that are specific to this mixin, keep them at the top of this partial. keep in mind they will pollute the global sass variable namespace, so be careful with this. We have a `_variables.scss` partial included in the pattern library already, so if you have something general, put it in there, unless it's a colour, then put it in the `_colours.scss` colour variable partial.

4) Add the mixin to the selector you want to style _in the main project styles **only**_ never style a selector in the pattern library
     e.g. in `/my-project/styles/pattern-library/_fancy-element-pattern.scss`
     ```SCSS
     // **THIS IS BAD**
	
	.fancy-element {
        @include my-fancy-pattern();
	}
	```

	The above code should go in `/my-project/styles/_fancy-element.scss`

5) Keep in mind that not all code should go in a pattern. Sometimes you will need to write code in both a pattern and your main application.

	```SCSS
	// in "/my-project/styles/_fancy-element.scss"
	.fancy-element {
        @include fancy-element-pattern(); // general, reusable styles for the pattern go in here
        
        // implementation specific styles and overrides go here
        margin: 20px;
        .footer & {
            font-size: 14px;
        }
	}
	```

### Pattern Library Principles
The Pattern Library is designed make development easier for everybody in the long run. Here are some principles to keep in mind while developing.

* **Reusable**
	Code should be reusable and generic enough that it is suitable for all implementations of the pattern. To aid this, consider making certain properties configurable by passing in options as parameters to the pattern mixin. See the following example
	```SCSS
	// regular
	@mixin fancy-element-pattern() {
        color: #f00;
	}
	```
	```SCSS
	// better (configurable color property)
	@mixin fancy-element-pattern($color) {
        color: $color;
	}
	```
	```SCSS
	// Best (configurable with default)
	@mixin fancy-element-pattern($color: #666) {
        color: $color;
	}
	
	@if (saturation($color) != 0% and lightness($color) < 51%) {
        @warn "Only dark grey font colours should be used";
	}
	```
Keep in mind that the pattern library will ideally be used by teams outside of Essence, or for clients other than Tesco, so things like colours, border styles, or selector naming conventions are things that lend themselves to being customisable.

* **Isolated**
	Make sure patterns only affect things inside them. You generally don't want to affect the positioning of an component styled with a pattern on a page, so avoid using things like margin and top/left. Those sorts of styles are better suited to living inside outside the pattern library, and inside your host application.

* **Granular** 
	Sometimes it's unavoidable to create huge patterns, especially for use on components. But if you can, try to create your patterns as small as possible. You can create many mixins and combine them into a larger patterns for ease of use, but then the smaller mixins can be used on their own, or recombined if required.
	
	```SCSS
	// in _headings-pattern.scss
	@mixin heading-pattern($size: 20px) {
		font-size: $size;
		font-weight: bold;
		color: $blue;
	}
	```
	```SCSS
	// in _fancy-element-pattern.scss
	@mixin fancy-element-pattern($headingClass: '__heading') {
		border: 2px solid $border;
		&#{$headingClass} {
			@include heading-pattern(30px)
			border-bottom: $border-width solid $black;
			color: $black;
			padding: $padding;
		}
	}
	```
* **Configurable**
	Ensure that your patterns make use of your base configuration, defined in `_variables.scss`. As is mentioned above, there is a `_colours.scss` where all colours should be defined and referenced from. Avoid adding additional colours to this file if you can, as having many different colours can lead to inconsistency and confusion. If you get a design that contains a colour that isn't in the Pattern Library already, see if you can use a similar colour which is already defined.

### Specific pattern guidance 
* **`_grid-pattern.scss`**
	This is a robust pattern that is used to define a grid system for an entire website. It should probably be included in the base stylesheet, and not in a specific component, that way it's always accessible by templates that need access to it, and it only needs to be loaded once. It is fairly complicated SCSS code to understand, but it's usage should be pretty straightforward. See the following examples. 
	**Note** The grid system is based on 12 columns
	```HTML
	<div class="grid">
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
	</div>
	```
	```HTML
	<div class="grid">
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
		<div class="grid__column grid__column--3">
			// 25% column width
		</div>
		<div class="grid__column grid__column--3">
			// 25% column width
		</div>
	</div>
	```
	
	```HTML
	<div class="grid">
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
		<div class="grid__column grid__column--6 grid__column--omega">
			// 25% column width
			// We need to specify the end of a row if there is multiple lines
		</div>
		<div class="grid__column grid__column--8">
			// 75% column width, on a new row
		</div>
	</div>
	```
	```HTML
	<div class="grid grid--uniform">
		// Two rows of two columns each
		// If we know all the columns are the same width, we can use
		// the .grid--uniform class instead of defining the end of a
		// column and the grid system will handle new rows automatically
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
	</div>
	```
	
	```HTML
	// We can also implement breakpoint specific grid sizes
	// If no grid__column modifiers are present, the grid column size
	// applies to all breakpoints
	//
	// .grid__column--6--tablet will make a column 6/12 columns wide,
	// but only on the "tablet-only" breakpoint (768px - 1024px)
	//
	// .grid__column--12--mobile will make a column full width,
	// but only on the "phone" breakpoint (767px and below)

	<div class="grid">
		<div class="grid__column grid__column--6">
			// 50% column width 
		</div>
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
	</div>
	```
	You can also shift columns to the right by a number of columns like so:
	```HTML
	<div class="grid">
		<div class="grid__column grid__column--4 grid__column--shift-2">
			// 30% column width, shifted right 2 column
		</div>
		<div class="grid__column grid__column--6">
			// 50% column width
		</div>
	</div>
	```
	The grid automatically calculates the column width and there is a fixed (but configurable) width gutter between each columns, but not on the left side of the first column of a row, or the right side of the last column of a row.

* **`_icons-pattern.scss`**
	This is a pattern that definitely needs improvement in the way it's maintained. We have a process of converting a folder of [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) icons to a [WOFF](https://developer.mozilla.org/en-US/docs/Web/Guide/WOFF) webfont file.

	First, check out the [tesco-mobile-shop-tools repo](https://bitbucket.org/essencedigital/tesco-mobile-shop-tools).

	* `$ cd src/IconWebfontBuilder`
	* Run `$ npm install` make sure it that  Grunt is installed
	* The source icon files must be SVG format. Put any new SVG files into `IconWebfontBuilder/source/icons`. Remove any SVG files that are not needed anymore so that the generated font file doesn't become too large.
	* `$ grunt webfont:generate`
	* look in `/IconWebfontBuilder/output`
	* Open `_icons.scss` and copy the `$icons` array into the `_icons-pattern.scss` file in the Pattern Library. You can ignore any other generated code in this file.
	* Locate the `icons.woff` file in the same `/output` directory and convert it to [base64](https://developer.mozilla.org/en-US/docs/Web/API/WindowBase64/Base64_encoding_and_decoding) using a tool of your choice, such as [base64encode.org](https://www.base64encode.org/).
	* take the base64 output and copy it into `_base-icon-pattern.scss`, which is located in the Pattern Library
	* If some of your icons look like they are too wide or tall, you may need to manually adjust them using a tool like [FontForge](http://fontforge.github.io/) ([direct download link page](http://fontforge.github.io/en-US/downloads/mac-dl/)) ([xQuartz dependency](https://www.xquartz.org/))
	* Open up your woff file in FontForge and scroll down a looooong way to near the bottom (past the Chinese, Japanese, and Korean characters, the icons start at F101)
	* Double click on a glyph and edit the icon to be inside the inner square, ignoring the baseline line.
	* re-save your font icon and re-base64 encode it, then put the generated base64 code into `_base-icon-pattern.scss`
	* That's it!
		
	NOTE: Adding an icon will be compiled alphabetically and it can affect the existing icon mapping in the shop project. 
	Therefore ensure the new icon added should be at the bottom of the list. 

* `_element-count.scss`
	This is not a pattern, but a utility that allows you to easily style things depending on how my elements are in an element.

	**Usage**
	```SCSS
	@include el-count( .fancy-element, $NUMBER_OF_ELEMENTS) {
		// If there are 4 sibling elements, .fancy-element will be 25% width
		width: 100% / $NUMBER_OF_ELEMENTS;
	}
	```
* `_colours.scss`
	This is a file which contains all the general colours that you should be using in your application. Occasionally you'll need a colour that won't be used anywhere else; this is not the appropriate place for those kinds of colours.
	For the most part you shouldn't be using colours directly in your styles, but instead referencing a variable. The format for colour name variables should be the colour name, then the first two characters of the hex 

### Styles in Angular

Styles inside an Angular application can be written in either a component stylesheet, or the application stylesheet. There are no hard rules, but generally it's best to write most styles in a component stylesheet, but some things that are used all over the site, can be included in the application stylesheets and be loaded on initialisation, and for the entire time the user is on the site. These things could be styles for the html and body, grid systems, font styles, css resets, etc. 

If you are writing styles in a component, Angular will automatically namespace all your selectors, so that the styles don't 'leak' and affect other components in the application. Despite this, it is still advantageous to adhere to BEM.

### **::ng-deep**

If you need to style a child component, you need to use the [`::ng-deep`](https://angular.io/guide/component-styles#deprecated-deep--and-ng-deep) shadow-piercing descendant combinator. 

### :host
If you need to style the root element on a component, use `:host`
```SCSS
// in fancy-element.component.scss
:host {
	display: block;
	margin: 20px 0;
	.fancy-element {
		@include fancy-element-pattern()
	}
}
```

Notice how the `:host` selector includes the `display` property? That is because you're styling a custom html element, which doesn't have any intrinsic properties.

### Javascript/TypeScript

For our repositories we are using Angular 2+ (currently version 5).

For this reason we are using TypeScript over JavaScript where available.

### Styleguide for names

- Use PascalCase for type names.
- Use PascalCase for enum values.
- Use camelCase for function names.
- Use camelCase for property names and local variables.
- Use whole words in names when possible.
- Do not use "I" as a prefix for interface names.

### Styleguide for Angular components

- Each component must be included in its own folder and should have 4 files:
    - 1 HTML file (the component's view)
    - 1 SCSS file (the component's styles)
    - 1 TS test file (the component's test)
    - 1 TS file (the component's functionalities)
- Each service, guard, directive, pipe must be included in its own folder and should have its own 2 files:
    - 1 TS test file (the service's test)
    - 1 TS file (the service's functionalities)

### Styleguide for Classes

For consistency, do not use classes in the core compiler pipeline. Use function closures instead.

### Styleguide for Comments

- Use [JSDoc style](https://github.com/shri/JSDoc-Style-Guide) comments for functions, interfaces, enums, and classes.
- Use a period at the end of a sentence.
- Use indefinite articles for indefinite entities.
- Definite entities should be named (this is for a variable name, type name, etc..).
- When stating a rule, the subject should be in the singular (e.g. "An external module cannot..." instead of "External modules cannot...").
- Use present tense.
Diagnostics are categorized into general ranges. If adding a new diagnostic message, use the first integral number greater than the last used number in the appropriate range.

### General Angular Styleguide

- Use 4 spaces per indentation.
- Use single quotes.
- Consider arrays as immutable by default after creation.
- Consider objects like Nodes, Symbols, etc. as immutable outside the component that created them. Do not change them.
- Always surround loop and conditional bodies with curly braces. Statements on the same line are allowed to omit braces.
- Open curly braces always go on the same line as whatever necessitates them.
- Parenthesized constructs should have no surrounding whitespace. 
- A single space follows commas, colons, and semicolons in those constructs. For example:
```TypeScript
for (var i = 0, n = str.length; i < 10; i++) { }
if (x < 10) { }
function f(x: number, y: string): void { }
```
- In the HTML files if the elements is exceeding the linted lenght for a single line, and for easier readability, do this:
```HTML
<div
    class="fancy__section another-class"
    [ngClass]="{ 'fancy__section--option': observable$ | async }"
    (event)="callbackFunction()"
>
    <my-component
        class="component__section another-important-class"
        [ngClass]="{ 'component__section--modifier': booleanVar }"
        [firstInput]="firstInputVar"
        [secondInput]="secondInput"
        [thirdInput]="thirdInput"
        (event)="callbackFunction()"
    ></my-component>
</div>
```

### TypeScript Constructs

- For a variety of reasons, we avoid certain constructs, and use some of our own. Among them:
    - Do not use for..in statements; instead, use ts.forEach, ts.forEachKey and ts.forEachValue. Be aware of their slightly different semantics.
    - Try to use ts.forEach, ts.map, and ts.filter instead of loops when it is not strongly inconvenient.
- Use arrow functions over anonymous function expressions.
- Only surround arrow function parameters when necessary. 
    For example, (x) => x + x is wrong but the following are correct:
```TypeScript
x => x + x
(x,y) => x + y
<T>(x: T, y: T) => x === y
```
- Use a single declaration per variable statement (i.e. use var `x = 1; var y = 2;` over `var x = 1, y = 2;`).
- `else` goes on the same line from the closing curly brace.

### Javascript Basics

Make sure you know all of [this section](https://developer.mozilla.org/en-US/Learn/Getting_started_with_the_web/JavaScript_basics#Language_basics_crash_course).  

We write [Object Oriented Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript), so it's important to understand how to write in this style, and how the [prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) works.  

An example of how we structure a OOJS function on the shop site:

```Javascript
Tesco.ToggleTabsAccordion = function (opts) {
    this._init(opts);
};

Tesco.ToggleTabsAccordion.prototype = {
    _setListeners: function () {
        function changeTabState() {
            // Do Stuff
        }
    }
    _init: function (opts) {
        this.opts = opts || {};
    }
}
```
