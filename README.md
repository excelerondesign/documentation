#### Documentation for Exceleron Designs

##### Previously on Basecamp

To add more:

###### `>` is the prompt for the command line/terminal and is not necessary to add

-   Clone repo to computer
    -   On github they will explain to you how to do it without the command line/terminal
-   Checkout the documentation branch
    -   run `> git checkout documentation` in the command line/terminal
-   Create a new branch for the document you want to add
    -   run `> git branch new-document-name` in the command line/terminal
-   Do necessary git/copy [Github Resources](https://try.github.io/)
-   Test your additions work in a local server
    -   run `npm start` in the command line
    -   For proper file structure, like how to set up a sidebar, check the [Docsify Documentation](https://docsify.js.org/#/quickstart)
-   When ready merge your `new-document-name` branch into `documentation`
    -   ```sh
        > git checkout documentation
        > git merge new-document-name
        ```
-   On Github, create a pull request
-   Pull request will be reviewed and then merged
-   Then we party 🥳
