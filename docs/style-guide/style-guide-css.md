1. Do not restate base styles
    - Example:
    ```css
    /* WRONG */
    h1 {
    	font-size: 4.5rem;
    	line-height: 0.95em;
    	letter-spacing: 0.025px;
    	margin-bottom: 15px;
    	color: #121314;
    }
    h1.title {
    	font-size: 4.5rem;
    	line-height: 0.95em;
    	letter-spacing: 0.025px;
    	color: #121314;
    	margin-bottom: 15px;
    	font-weight: 800;
    	color: #00f;
    }
    /* RIGHT */
    h1 {
    	font-size: 4.5rem;
    	line-height: 0.95em;
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
    - Use element selectors for base styles
    - Use class '.class' selectors for component styles
        - Simplify things by using no more than 3 selectors. Specificty: 30
    - Do not use ID '#id' selectors
    - Do not use !important
        - Only use to override other !important tags.
        - If overriding !important, document it in the code
    - Alternatives include the following
    ```css
    /* 
        This is not specific enough
        specifity: 10*/
    .form-control {
    	...;
    }
    /* 
        Raise the specificity by one
        using an element selector
        specificty: 11
    */
    input.form-control,
    select.form-control,
    textarea.form-control {
    	...;
    }
    ```
    - Identify specificity of rule to be overridden. Check here: [:bat:](http://batificity.com/)
1. Keep code DRY and avoid duplicating styles
    - Identify code that can be merged
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
    - Expand properties that have multiple values
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
1. Use Custom Properties (CSS Variables)
    - Useful for palettes
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
    - Prefer single word variables
        - For two+ word variables, space with '-'
    - Allows for reuseable code and for simple customizations
    ```css
    .row {
    	--nav-height: 150px;
    	height: calc(100% - var(--nav-height));
    	padding-top: calc(var(--nav-height) / 2);
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
    - Don't use short hand
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
