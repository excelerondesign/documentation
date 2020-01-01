---
id: style-guide-html
title: HTML Guide
---
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
