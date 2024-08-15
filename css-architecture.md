- Component Driven Design
    - Break our page into reusable components 
    - They are joined by layout of the page to form the interface
    - They should be completely reusable, even across projects
    - They should be independent of their parent so that they can be used
    anywhere on the page

- How should you name your classes in HTML and CSS?
    - Use the BEM (Block Element Modifier) naming convention
    - Block - standalone component that is meaningful on its own
    - Element - part of a Block that has no meaning of its own
    - We can get away with using only classes which are never nested, thus using
    very low specificity selectors
    - Modifier - a flag we can put on a Block or Element in order to make it
    different from regular Blocks or Elements (a different version)
![BEM Naming Convention](./images/bem.png)

- How to structure your CSS?
    - 7 different folders for partial Sass files
        - base - basic product definition
        - components - one file for each component
        - layouts - where we define the overall layout of the project
        - pages - styles of specific pages of the project
        - themes - for different visual themes
        - abstracts - code which doesn't output any CSS (variables or mixins)
        - vendors - all third party CSS goes
    - 1 main Sass file to import all other files into a compiled CSS stylesheet