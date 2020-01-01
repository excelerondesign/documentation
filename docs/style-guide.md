---
id: style-guide
title: Code Style Guide
---
> This code style guide is meant to be the ground work for how the development team at Exceleron Designs tackles problems. Any coding should keep this style guide in mind.

#### CSS
1. Do not restate base styles
    * Example:
    ```css
    /* WRONG */
    h1 {
        font-size: 4.5rem;
        line-height: .95em;
        letter-spacing: 0.025px;
        margin-bottom: 15px;
        color: #121314;
    }
    h1.title {
        font-size: 4.5rem;
        line-height: .95em;
        letter-spacing: 0.025px;
        color: #121314;
        margin-bottom: 15px;
        font-weight: 800;
        color: #00f;
    }
    /* RIGHT */
    h1 {
        font-size: 4.5rem;
        line-height: .95em;
        letter-spacing: 0.025px;
        margin-bottom: 15px;
        color: #121314;
    }
    h1.title {
        font-weight: 800;
        color: #00f;
    }
    ```
1. Maintain a low specificity
    * Use element selectors for base styles
    * Use class '.class' selectors for component styles
        * Simplify things by using no more than 3 selectors. Specificty: 30
    * Do not use ID '#id' selectors
    * Do not use !important
        * Only use to override other !important tags.
        * If overriding !important, document it in the code
    * Alternatives include the following
    ```css
    /* 
        This is not specific enough
        specifity: 10*/
    .form-control {
        ...
    }
    /* 
        Raise the specificity by one
        using an element selector
        specificty: 11
    */
    input.form-control,
    select.form-control,
    textarea.form-control {
        ...
    }
    ```
    * Identify specificity of rule to be overridden. Check here: [:bat:](http://batificity.com/)
2. Keep code DRY and avoid duplicating styles
    * Identify code that can be merged
    ```css
    .class {
        color: white;
        font-size: 1rem;
        background-color: blue;
    }
    .class2 {
        color: white;
        font-size: 1rem;
        background-color: blue;
        border-radius: 3px;
    }
    /* Can be combined into */
    .class,
    .class2 {
        color: white;
        font-size: 1rem;
        background-color: blue;
    }
    .class2 {
        border-radius: 3px;
    }
    ```
    * Expand properties that have multiple values
    ```css
    .class {
        border: 1px solid blue;
    }
    .class2 {
        border: 2px solid blue;
    }
    /* Can be combined into */
    .class,
    .class2 {
        border: 1px solid blue;
    }
    .class2 {
        border-width: 2px;
    }
    ```
3. Use Custom Properties (CSS Variables)
    * Useful for palettes
    ```css
    :root {
        --blue: #00f;
        --red: #f00;
        --primary: var(--blue);
        --danger: var(--red);
    }
    h1 {
        color: var(--primary);
    }
    ```
    * Prefer single word variables
        * For two+ word variables, space with '-'
    * Allows for reuseable code and for simple customizations
    ```css
    .row {
        --nav-height: 150px;
        height: calc(100% - var(--nav-height));
        padding-top: calc(var(--nav-height) / 2)
    }
    /*
        Now we can change just the variable without rewriting any of the code above
    */
    @media (min-width: 768px) {
        .row {
            --nav-height: 75px;
        }
    }
    ```
    * Don't use short hand
    ```css
    :root {
        /*
            We can glean that this is blue
            and is possibly a background.
            For someone who has never
            seen/written code in a project
            will not be able to understand
            what this is used for
        */
        --bgp: #00f;
        /* Instead... */
        --background-primary: #00f;
        /*
            Now it is immediately clear
            the purpose of the variable
        */
    }
    ```

#### HTML

1. IDs are written in camelCase
    * IDs are only being used for Javascript, which has a common practice of camelCasing variables
    ```html
    <h1 id="section_title">WRONG</h1>
    <h2 id="section-subtitle">ALSO WRONG</h2>
    <h3 id="sectionTagLine">CORRECT</h3>
    ```
2. Classes should be spaced with hyphens '-'
    * While both CSS and JS use classes, the common practice in CSS is to space with a hyphen, which is not possible in JS.
    ```html
    <h1 class="section_title">WRONG</h1>
    <h2 class="sectionSubtitle">ALSO WRONG</h2>
    <h3 class="section-tag-line">CORRECT</h3>
    ```
3. Defer all script tags
    *  Example:
    ```html
    <!--
        For scripts that must be
        executed in order: add
        the defer attribute
    -->
    <script defer src="./js/index.js"></script>
    
    <!--
        If it does not matter when
        the script is executed:
        add both the async and defer
        attributes
    -->
    <script async defer src="./js/index.js"></script>
    <!--
        All modern browsers support
        defer, but not all support
        async.
    -->
    ```
4. Preload CSS
    * Example:
    ```html
    <!-- Normal Loading -->
    <link rel="stylesheet" href="./css/main.css"/>

    <!-- Preloading -->
    <link rel="preload" as="style" href="./css/main.css" onload="this.onload=null;this.rel='stylesheet';"/>
    ```
    * Preloading is not supported equally in all browsers. Include this polyfill: [:pencil:](https://github.com/filamentgroup/loadCSS/blob/master/src/cssrelpreload.js)
5. Take advantage of instant.page: [:link:](https://instant.page/)
6. Don't use inline CSS or JS
    * ...in productions. It should not be used at all, but it should all be removed to a proper file once moved to production.
7. Don't use reCaptcha
    * Some situations may need it, but instead prefer to use something like weHateCaptchas: [:link:](https://wehatecaptchas.com/)
8. Input name fields should use underscores '_'
    * Example:
    ```html
    <input name="firstName" value="WRONG"/>
    <input name="first-name" value="WRONG"/>
    <input name="first_name" value="CORRECT"/>
    ```

#### Javascript
1. All comments must be multiline `/* ... */`
2. Componentize as much as possible.
    * For example: A form has steps that use an accordion like style. The form will be on multiple pages. This code should be self reliant and used as a component.
3. Code that will be used on every single page will be included in `index.js`
    * Other code that is page specific should be a single resource

#### MODx
1. Cache any TVs or Snippets that can be
    * Some snippets, e.g. FormIt, cannot be cached.
2. Snippet names should be spaced with underscores
    * Exceptions can be made for snippets that perform a small task. E.g. getsvg: gets an svg.
    * Alternatively: processauthform should become process_auth_form
3. Base Template should look like this:
    * Example:
    ```html
    [[$head? &links=`...`]]
        <body>
            [[$header]]
            ...
            [[$footer]]
            [[$footer-js]]
            <!-- Miscellaneous Script Tags -->
        </body>
    </html>
    ```
    * $head example
    ```html
    <!doctype html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>[[*longtitle:default=`[[*pagetitle]]`:append=` | [[++site_name]]`]]</title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            
            <!--
                meta data
            -->

            <!-- stylesheet links -->
            <noscript>
                <!-- 
                    noscript preload link fallbacks
                -->
            </noscript>
            [[+links]]
            <script id="preloadPolyfill">...</script>
        </head>
    ```

##### The point of these rules is...
that they should be seen as a group effort. We should never be afraid to revisit them or adjust them as needed.

###### Exceptions...
Exceptions are bound to happen, but they must be documented. Communication between developers is important.