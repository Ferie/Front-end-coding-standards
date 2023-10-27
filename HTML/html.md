[Back to main page](../README.md#frontend-coding-standards-and-best-practices)

## Table of Contents
- [Node Modules](../Node/node-modules.md#node-modules)
- [HTML](#html)
    - [Validation](#validation)
    - [Declare a Doctype](#declare-a-doctype)
    - [Declare the language of the page](#declare-the-language-of-the-page)
    - [Titles](#titles)
    - [Meta Descriptions](#meta-descriptions)
    - [Viewport](#viewport)
    - [Use semantic HTML 5 tags](#use-semantic-html-5-tags)
    - [Close the tags](#close-the-tags)
    - [Use lowercase in your tags](#use-lowercase)
    - [Character encoding](#character-encoding)
    - [Use conditional comments](#use-conditional-comments)
    - [Use practical `id` and `class` names and values](#use-practical-id-and-class-names-and-values)
    - [Images need `alt` attributes](#images-need-alt-attributes)
    - [Use tables for tabular data only](#use-tables-for-tabular-data-only)
    - [Include external CSS inside the `<head>` tag](#include-external-css-inside-the-head-tag)
    - [Avoid to specify the type of imported CSS and JavaScript files](#avoid-to-specify-the-type-of-imported-css-and-javascript-files)
    - [Separate content from style](#separate-content-from-style)
    - [Keep the syntax organized](#keep-the-syntax-organized)
    - [Reduce markup](#reduce-markup)
    - [Whitespacing and formatting](#whitespacing-and-formatting)
        - [Indent tags that are very long](#indent-tags-that-are-very-long)
        - [Attributes order](#attributes-order)
        - [Always use double quotes in HTML files](#always-use-double-quotes-in-html-files)
- [Styles (CSS/SCSS)](../Styles/styles.md#styles-cssscss)
- [JavaScript/TypeScript](../Scripts/javascript.md#javascripttypescript)
- [General best practices](../Generals/generals.md#general-best-practices)


---



# HTML

### VALIDATION

A concerted effort should be made to ensure that all HTML and CSS validate. Markup should be semantic, readable, well-formatted and well-formed and contain all required attributes. Elements should occur within the proper context of the DOCTYPE.

- [W3C HTML Markup Validator](http://validator.w3.org/)
- [W3C CSS Validator](http://jigsaw.w3.org/css-validator)



### DECLARE A DOCTYPE

The DOCTYPE declaration should be in the first line of any HTML file. Actually, it activates the standard mode in all browser. It is recommended that you use the HTML doctype when using HTML 5:

```HTML
<!DOCTYPE html>
```



### DECLARE THE LANGUAGE OF THE PAGE

Always add a `lang` attribute to the `html` tag to set the default language of your page.

```HTML
<html lang="en">
```

Browsers and other applications can use information about the language of content to deliver to users the most appropriate information, or to present information to users in the most appropriate way. The more content is tagged and tagged correctly, the more useful and pervasive such applications will become.



### TITLES

Titles should contain descriptive information that concisely describes the current page. In case of nested pages, information in the title tag should be ordered from most specific to least specific. A standard delimiter such as `–` or `|` should be employed to indicate distinct content levels, for example:

```HTML
<title>About us - Our mission and values | The Most Wonderful Company</title>
```



### META DESCRIPTIONS

A quality `meta description` can help when talking about SEO and indexing the web pages on the search engines. Ideally, all pages include a unique `meta description` that is a concise, human-readable description of that page’s contents.

_**Do not duplicate meta descriptions from other pages.**_

Customised meta descriptions can appear in search engine result pages. For example, _Google_ will sometimes replace custom meta descriptions with on-page content if they feel it is of more value to the end user. If no meta description exists, it usually create its own from on-page content. [More about titles and meta tags on _Google Developers_](https://developers.google.com/search/docs/advanced/appearance/good-titles-snippets).



### VIEWPORT

The viewport is the user's visible area of a web page. The viewport varies with the device, for this reason, it is smaller on a mobile phone than on a computer screen. HTML5 introduced a method to let web designers take control over the viewport, through the `<meta>` tag. We should include the `meta` tag `viewport` in all our web pages:

```HTML
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
```

- `width=device-width` sets the width of the page to follow the screen-width of the device (which will vary depending on the device);
- `initial-scale=1` sets the initial zoom level when the page is first loaded by the browser and ensures smartphones retain the same zoom level during orientation change (from portrait to landscape and viceversa).
- `viewport-fit=cover` ensures that smartphones that use "[safe areas](https://developer.apple.com/design/human-interface-guidelines/ios/visual-design/adaptivity-and-layout/)" are able to [adapt the content accordingly](https://stackoverflow.com/questions/56243315/handle-the-safe-area-in-chrome-browser-on-the-iphone-x-family).



### USE SEMANTIC HTML 5 TAGS

To improve the experience of users that are using readers and other tools to read a website, the best practice is to use the tags provided by HTML 5 so that clearly describe their meaning in a human and machine readable way.

```HTML
<!-- Don't do this -->
<div id="main">
    <div class="article">
        <div class="header">
            <h1>Blog post</h1>
            <p>Published: <span>21st Feb, 2015</span></p>
        </div>
        <p>
            Paragraph of this wonderful article.
        </p>
    </div>
</div>

<!-- Do this instead -->
<main>
    <article>
        <header>
            <h1>Blog post</h1>
            <p>Published: <time datetime="2015-02-21">21st Feb, 2015</time></p>
        </header>
        <p>
            Paragraph of this wonderful article.
        </p>
    </article>
</main>
```



### CLOSE THE TAGS

Leaving some tags open is simply a bad practice.

**Only self-closing tags are valid**. In HTML 5, normal HTML tags can never have self-closing tags.

```HTML
<!-- Don't do this - Wrong but accepted in HTML 5 -->
<br />
<input />
<img />
<meta />
<link />
<hr />

<!-- Do this instead - Correct use in HTML 5 -->
<br>
<input>
<img>
<link>
<meta>
<hr>
```



### USE LOWERCASE

It is a good practice to keep markup lower-case. The capitalizing markup will work and will probably not affect how your web pages are rendered, but it does affect code readability.

We should keep it simple.



### CHARACTER ENCODING

Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document (generally UTF-8).

```HTML
<meta charset="utf-8">
```



### USE CONDITIONAL COMMENTS

Sometimes some clients want to target specific versions of *Internet Explorer*, other than using well known IE hacks, we can use the conditional comment like the one shown below to target IE9 and lower versions.

```HTML
<link href="style.css" rel="stylesheet">
<!--[if lte IE 9]>
    <link href="ie.css" rel="stylesheet" type="text/css">
<![endif]-->
```



### USE PRACTICAL `id` AND `class` NAMES AND VALUES

We should only give elements an `id` attribute if they are unique. Classes can be applied to multiple elements that share the same style properties.

It is always preferable to name something `id` or `class`, by the nature of what it is rather than by what it looks like.

Ids and class names should be all lowercase.



#### SPECIFICITY

To avoid CSS specificity issues, `id`s should be used sparingly, examples are: in-page bookmarks, anchors, form `label` tags, JavaScript's hooks, etc.



### IMAGES NEED `alt` ATTRIBUTES

The `img` tag requires alt text to both validate and meet accessibility guidelines. The text in the `alt` attribute should be descriptive of what the image shows, or is trying to achieve, unless of course the image is not critical.

If an image is purely decorative (it provides no content value other than visual flair to the page) then a `background-image` is appropriate. 



### USE TABLES FOR TABULAR DATA ONLY

The `table` tag should only be used for the presentation of tabular data such as pricing or feature charts.

The only exception is when composing HTML email, in which a table is almost the only thing supported by soul crushing email clients.



### INCLUDE EXTERNAL CSS INSIDE THE `head` TAG

Style sheets can be placed anywhere but the HTML specification recommends that they be placed within the document `head` tag. The primary benefit is that pages will load faster.



### AVOID TO SPECIFY THE TYPE OF IMPORTED CSS AND JAVASCRIPT FILES

Per HTML 5 spec, typically there is no need to specify a `type` when including CSS and JavaScript files as `text/css` and `text/javascript` are their respective defaults.

```HTML
<!-- External CSS file -->
<link href="styles.css" rel="stylesheet">

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript script -->
<script src="app.js"></script>
```



### SEPARATE CONTENT FROM STYLE

Avoid using inline styles within HTML. Doing so creates pages that take longer to load, are difficult to maintain, and cause headaches for designers and developers. [More on this here](./Styles/styles.md#never-use-inline-styles)



### KEEP THE SYNTAX ORGANIZED

When pages grow, managing HTML can be hard. There are some quick rules that can help us to keep our syntax clean and organized. These include the following:

- Indent nested elements (I use and prefer 4 spaces)..
- Use blank lines to space between blocks of related elements.
- Omit the values on Boolean attributes

For example:

```HTML
<form action="/action_page.php" method="get">
    <fieldset>
        <label>Select an option</label>
        <select>
            <option value="1" selected>Option 1</option>
            <option value="2">Option 2</option>
            <option value="3">Option 3</option>
        </select>
    
        <label>Default choice</label>
        <input type="checkbox" value="1" checked>
    
        <button type="submit" disabled>Submit</button>
    </fieldset>
</form>
```



### REDUCE MARKUP

Whenever possible, avoid superfluous parent elements when writing HTML: merging attributes and tags can help readability and improve the code.

Many times this requires iteration and refactoring, but produces less HTML.

```HTML
<!-- Don't do this -->
<span class="avatar">
  <img src="images/dog.jpg">
</span>

<!-- Do this instead -->
<img src="images/dog.jpg" class="avatar">
```



### WHITESPACING AND FORMATTING

#### INDENT TAGS THAT ARE VERY LONG

For the sake or readability

```HTML
<!-- Don't do this -->
<input type="text" placeholder="Enter input" name="inputName"
    id="input-id" class="input-class" data-attribute="attribute-1"
    data-attribute-option="attribute-option">

<!-- Do this instead -->
<input
    type="text"
    name="inputName"
    class="input-class"
    id="input-id"
    placeholder="Enter input"
    aria-label="Enter input"
    data-attribute="attribute-1"
    data-attribute-option="attribute-option"
>
```



#### ATTRIBUTES ORDER

HTML attributes should come in this particular order for easier reading the code:
- `src`, `for`, `type`, `href`, `rel`
- `name`
- `class`
- `id`
- `placeholder`
- `title`, `alt`, `value`
- `checked`, `disabled`
- `role`, `aria-*`
- `data-*`

Examples:

```HTML
<a href="/home" class="link" data-toggle="modal">
    Home page
</a>

<input type="text" name="username" class="form-control">

<img src="images/dog.jpg" class="image" alt="My dog running in the garden">
```

As far as Identifiable information is concerned, classes make for great reusable components, so they come before `id`s.



#### ALWAYS USE DOUBLE QUOTES IN HTML FILES

```HTML
<!-- Don't do this -->
<input type='text' name='inputName' class='input-class'>

<!-- Do this instead -->
<input type="text" name="inputName" class="input-class">
```
