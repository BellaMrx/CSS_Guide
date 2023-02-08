# CSS Guide
 
 Detailed guide about CSS (all basics for CSS) + templates.

 The code examples in the guide can be found in the listed folders.

-----------------------------------------------------------------------------------------

## Contents
1. Introduction to CSS
    - 1.1. History of CSS 
    - 1.2. Principle of CSS application
    - 1.3. Embedding CSS into HTML
    - 1.4. Analyze CSS in the web browser
2. The CSS selectors
    - 2.1. The simple selectors of CSS
    - 2.2. Combinators
3. Inheritance and the cascade 
    - 3.1 The principle of inheritance in CSS
    - 3.2. Understanding the control system of the cascade
    - 3.3. Pass values to CSS properties
4. The box model of CSS 
    - 4.1. The classic box model
    - 4.2. The newer alternative box model of CSS
    - 4.3. Design boxes


--------------------------------------------------------------------------------------------

# 1. Introduction to CSS
 The main task of CSS (stylesheets) is the presentation when creating web pages. CSS is used to create rules on how the content of an HTML element should be displayed. CSS supports the separation of structure and design of a document. 
 - HTML defines the semantics of the content
 - CSS defines the presentation of the content

From this point on, knowledge of HTML should be available. If there is no knowledge of HTML yet: [HTML Guide](https://github.com/BellaMrx/HTML_Guide) - Detailed guide about HTML5 (all basics for HTML) + templates


## 1.1. History of CSS
 The inventors of CSS are Hakon Wium Lie and Bert Bos. CSS Level 1 Recommendation was published in 1996, the version was mainly about the design of Wch Fonts and Color.
 The next version, CSS Level 2, was published in 1998. Since there were many inconsistencies, because different web browsers do not implement many things correctly, this version was revised in 2002. It took until 2011 for CSS 2.1.to be released. In this version, the positioning of elements was included.
 The third version of CSS, has been in the works since 2000, there was no longer a single specification used, but the various features were with CSS3 aufgeilt into modules. Each module adds new capabilities and extends CSS 2.1, keeping everything backward compatible.
 Today, CSS no longer has a version number and consists of numerous modules. CSS3 is actually just a term for the modules added after 2.1.. However, the individual modules still have version numbers. 

 An overview of all modules in progress, can be found at [W3C:CSS current work](https://www.w3.org/Style/CSS/current-work.en.html).
 All other modules can be found at [W3C:CSS Snapshot 2022](http://w3.org/TR/CSS/).


## 1.2. Principle of CSS application
 In CSS, rules for the individual HTML elements determine the appearance. It is not important at this point to understand what is written in *style.css*.
 
 example --> *1_Introduction/Part_1/index.html*

   ```
    <header>
        <h1>My CSS blog</h1>
        <p>A blog with tips about CSS ...</p>
    </header>
    <nav>
        <p> 
            <a href="#">Blog</a> | <a href="#">Tips</a> |
            <a href="#">About me</a> | <a href="#">Legal notice</a>
        </p>
    </nav>
    <main>
    <article>
        <h2>CSS Tips</h2>
        <p>Daily articles about CSS and all things related to web design and development...</p>
        <h3>More tips</h3>
        <ul>
            <li><a href="#">Hover effects</a></li>
            <li><a href="#">Center a div</a></li>
        </ul>
    </article>
    </main>
    <footer>
        <hr>
        <p> 
            <a href="#">Contact</a> | <a href="#">FAQ</a> |
            <a href="#">About me</a> | <a href="#">Legal notice</a>
        </p>
    </footer>
   ```

  example --> *1_Introduction/Part_1/style.css*

   ```
    body { 
     margin:0px; 
    }

    h1 { 
     font-family: "Verdana", "Geneva";
     font-size: 200%;
     text-align: center;
    }

    h2 { 
     font-family: "Verdana", "Geneva";
     background: #dd95cd;
     padding: 10px;
	 text-align: center;
    }

    h3 { 
     font-family: "Verdana", "Geneva"; 
     margin-left: 20px;
    }

    header { 
     background: #dd95cd;
     padding: 2px;
     text-align:center;
    }

    nav, footer { text-align: center;  }

    p { font-family: "Verdana", "Geneva"; }

    li { font-family: "Verdana", "Geneva"; }

    article p { margin: 20px; }

    article ul { margin: 20px; }

    hr { color: #dd95cd;}
   ```
  ![Preview](1_Introduction/Images/Preview_1_1.png)


### Structure of a CSS rule
 A CSS rule is defined with a selector and the declarations it contains. Selectors are an essential building block of CSS, of which there are many different types.
 - **Selector**: Specifies the HTML element to which the CSS rule should be applied. It is possible to apply a rule to multiple HTML elements.

   ```
    h1, h2, h3, p { color: red;}
   ```
 This specifies that the font color is red, but only for the HTML elements h1, h2, h3 and p.

 - **Declaration**: Declarations are used to format the selected HTML elements. The declaration consists of two parts, the *property* and a *value*.

 ![Preview](1_Introduction/Images/CSSstatement.PNG)


### The declaration of a selector
 The declaration inside the braces consists of at least one property and one value. E.g. with `font-family` the font is selected, with color the font color. The order of the statements can be arbitrary.

 - **Property**: This specifies the CSS property (e.g. color, font, alignment) to be changed for the HTML element selected with the selector. CSS has many properties. More about that later.
 - **Value**: This specifies the value for the CSS property used. This value depends on the property used, e.g. if the property is `color`, the value of a color (e.g. red) can be specified.

   ```
    h1 { 
     font-family: "Arial";
     color: red;
     text-align: center;
    }
   ```


### Use comments for CSS code
 If a lot of CSS code is used, comments should be applied in the code to be able to understand what it is later.
 A comment in the CSS is displayed like this:

   ```
    /* creates a circle */
    .circle { 
     height: 50px; 
     width: 50px;
     border-radius: 50px;
    }

    /* ----------------- */
    /* header and footer */
    /* ----------------- */
    ...
   ```


## 1.3. Embedding CSS into HTML
There are three ways to include CSS in an HTML document:
- **inline style**: The CSS code is applied directly to the HTML element. 
- **internal style sheet**: The style statements are collected in the header of the HTML document.
- **external style sheet**: The CSS code is created in a CSS file and linked to the HTML document.

**inline style**
- This method is not very advantageous, because the HTML document becomes quickly confusing, and each change must be made individually, which is very time-consuming. However, if only a single property is to be changed that only applies to this element, then this method can be used for testing or demonstration purposes.

 example --> *1_Introduction/Part_2/index.html*

   ```
    <h2 style="font-family: Verdana; background: blue; padding: 2px; text-align: center;">CSS Tips</h2>
    <p style="font-family: Verdana;">Daily articles about CSS and all things related to web design and development...</p>
    <h3 style="font-family: Verdana; margin-left: 20px;">More tips</h3>
   ```

**internal style sheet**
- With this method, the CSS instructions are specified in the header of the HTML document between `<style> ... </style>` are specified. These apply to the gaze HTML document. For learning CSS it is advantageous, because you have everything in one file. But if a style is applied to multiple web pages and changed later, each page must be changed individually.
 
 example --> *1_Introduction/Part_3/index.html*

   ```
    <head>
        <title>My CSS blog</title>
        <meta charset="UTF-8" />
        <style>
            body {
                margin: 0px;
            }
        
            h1 {
                font-family: "Verdana", "Geneva";
                font-size: 200%;
                text-align: center;
            }
        
            h2 {
            font-family: "Verdana", "Geneva";
            background: #add8e6;
            padding: 2px;
            text-align: center;
            }      
        </style>
    </head>
   ```

**external style sheet**
- This method is best suited for large web pages. HTML and CSS are saved in separate files. This is the only way to ensure that the layout is consistent for each page of a large web project. The CSS file is included in the link element in the header.
 
 example --> *1_Introduction/Part_4/index.html*

   ```
    <head>
        <title>My CSS blog</title>
        <meta charset="UTF-8" />
        <link rel="stylesheet" href="style.css" />
    </head>

    <body>
        <header>
            <h1>My CSS blog</h1>
            <p>A blog with tips about CSS ...</p>
        </header>
        <nav>
            <p>
                <a href="#">Blog</a> | <a href="#">Tips</a> |
                <a href="#">About me</a> | <a href="#">Legal notice</a>
            </p>
        </nav>
        <main>
            <article>
                <h2>CSS Tips</h2>
                <p>
                Daily articles about CSS and all things related to web design and development...
                </p>
                <h3>More tips</h3>
                <ul>
                    <li><a href="#">Hover effects</a></li>
                    <li><a href="#">Center a div</a></li>
                </ul>
            </article>
        </main>
        <footer>
            <hr />
            <p>
                <a href="#">Contact</a> | <a href="#">FAQ</a> |
                <a href="#">About me</a> | <a href="#">Legal notice</a>
            </p>
        </footer>
    </body>
   ```
 
 example --> *1_Introduction/Part_4/style.css*

   ```
    h1 { 
        font-family: "Verdana", "Geneva";
        font-size: 200%;
        text-align: center;
    }

    h2 { 
        font-family: "Verdana", "Geneva";
        background: #add8e6;
        padding: 10px;
	    text-align: center;
    }

    h3 { 
        font-family: "Verdana", "Geneva"; 
        margin-left: 20px;
    }

    header { 
        background: #add8e6;
        padding: 2px;
        text-align:center;
    }

    nav, footer {
        text-align: center;  
    }

    p { 
        font-family: "Verdana", "Geneva"; 
    }

    li { 
        font-family: "Verdana", "Geneva"; 
    }

    article p { 
        margin: 20px; 
    }

    article ul { 
        margin: 20px; 
    }
   ```

Several methods can be used at the same time, e.g. an internal and external stylesheet. Here the rule noted last gets the preference.

 example --> *1_Introduction/Part_5/index.html*

   ```
    <head>
        <title>CSS Conflicts</title>
        <meta charset="UTF-8" />
        <link rel="stylesheet" href="style.css" />
        <style>
            p {
                text-align: center;
            }
        </style>
    </head>

    <body>
        <h1>A headline</h1>
        <p style="text-align: left">First paragraph text ...</p>
        <p>Second paragraph text ...</p>
    </body>
   ```
 
 example --> *1_Introduction/Part_5/style.css*

   ```
    p { 
        text-align:right; 
        color: grey; 
    }
   ```

Using the global title attribute, alternative stylessheets can be set up within the link or style element. This can be useful during team development to compare different styles. Or for different color schemes e.g. light and dark mode.

  example --> *1_Introduction/Part_6*

 ![Preview](1_Introduction/Images/LightDarkMode.png)


### Include style statements from an external CSS file with @import
The `@import` rule is noted in the HTML document header between `<style> ... </style>`. In practice, this example makes little sense, but should illustrate the use of the @import -rule. It is important that the `@import` rule is noted at the beginning, before which no CSS statement may stand.

 example --> *1_Introduction/Part_7/index.html*

   ```
    <head>
        <title>My CSS blog</title>
        <meta charset="UTF-8">
        <style>
        @import url("style.css");
        </style>
    </head>
   ```


### Media-specific stylesheets for specific output devices
If a stylesheet is to be specified for a particular output medium, this can be done with the media attribute in the link element.

This example demonstrates how to create a media-specific stylesheet for the screen and another for the printer:

 example --> *1_Introduction/Part_8/index.html*

   ```
    <head>
        <title>My CSS blog</title>
        <meta charset="UTF-8">
        <!-- <link rel="stylesheet" type="text/css" media="screen" href="style.css">
        <link rel="stylesheet" type="text/css" media="print" href="print.css"> -->
        <style>
            @import url("style.css") screen;
            @import url("print.css") print;
        </style>
    </head>
   ```

If the output device is a screen (`media="screen"`), the HTML document is formatted with *style.css*. If the output device is a printer (`media="print"`), the document is formatted with *print.css*.

| attribute      | explanation                    |
| -------------- | ------------------------------ |
|`media="all"`   | all output devices             |
|`media="print"` | printer                        |
|`media="screen"`| screen-oriented output devices |

There are other media types or device classes such as `aural, braille, embossed, handheld, projection, speech, tty, tv` these are considered obsolete since Media Queries Level 4, so their use is discouraged.


### Media-specific stylesheets with CSS
Media-specific stylesheets (media queries) play a major role in responsive web design. Responsive web design is standard today because web pages are viewed first not only on the computer but predominantly on the smartphone. For media-specific stylesheets, logical operators have been introduced (`and`,`not`), which can be used to perform queries about various media properties, such as the usable screen width or screen orientation.

   ```
    <link rel="stylesheet" media="screen and (min-width: 1080px)" href="style1080.css">
   ```
If the media has a screen and it is at least 1080 pixels wide, the CSS file *style1080.css* is included in the HTML document. 

There are other such media properties like `min-width`. More about that later.


## 1.4. Analyze CSS in the web browser
A good learning and help tool are the development tools provided by each web browser.

 ![Preview](1_Introduction/Images/BrowserAnalyze.PNG)

Here it is possible to examine a styled HTML element. When an element is selected e.g. header. The CSS instructions are displayed, which can then be changed there for testing purposes. This is only visual, the file remains untouched.

-------------------------------------------------------------------------------------

# 2. The CSS selectors
CSS offers many different selectors, which are divided into:
- **Simple selectors**: these include the type selector, the universal selector (*), the class selector(.class), the ID selector (#id), the attribute selector, and several pseudo-classes.
- **Combinators**: Combinators are two selectors concatenated with a > character (E > F; child selector), the plus sign (E + F; neighbor selector), a tilde character (E ~ F; sibling selector), or a space (E F; descendant selector).

If you want to know which selectors are implemented in the web browser and which ones can be used, you can do it here [CSS- Selector- Test ](http://css4-selectors.com/browser-selector-test/).


## 2.1. The simple selectors of CSS

### Type selector
Such a type selector, also called HTML element selector, addresses the HTML elements directly with the element name.

 example --> *2_CSS_Selectors/Part_1/index.html*

   ```
    <head>
        <title>Type selectors</title>
        <meta charset="UTF-8" />
        <link rel="stylesheet" href="styles/style.css" />
    </head>
    <body>
        <header>Header</header>
        <nav>Navigation</nav>
        <main>
            <h1>Type selectors</h1>
            <p>
                Such a type selector addresses the <abbr>HTML</abbr> elements directly with the element name.
            </p>
            <p>
                This rule is applied to all elements of the same type in the HTML document. It is irrelevant where in the HTML document these elements are written, to which class they belong or which identifier they have.
            </p>
        </main>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_1/styles/style.css*

   ```
    /* black frame, centered text, 5 pixel distance from top */
    header, nav, footer { 
        text-align:center;
        border: 1px solid black;
        margin-top: 5px;
    }

    /* gray text */
    h1, abbr { 
        color: gray; 
    }

    /* gray dotted frame */
    p { 
        border: 1px dotted gray; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_1.png)


### Class selector
In an HTML document there is usually more than just, for example, a `<p>` element, so that individual paragraphs can also be designed differently, classes are very useful. It is possible to assign a class to each element. A class is assigned with the global HTML attribute *class*. In CSS the class is marked with a *dot* e.g. `.note {...}`.
    
index.html
   ```
    <p class="note">A paragraph text</p>
   ```
style.css
   ```
    .note {
        color:red;
    }
   ```

It is also possible to use several classes at once.
    
 example --> *2_CSS_Selectors/Part_2/index.html*
   ```
    <body>
        <header class="head_foot">Header</header>
        <nav class="bigfont">Navigation</nav>
        <main>
            <h1>Class selector</h1>
            <p>The p element without a class</p>
            <p class="note">The p element with the class <code>note</code></p>
            <p class="note warning">
                The p element with the classes <code>note</code> and <code>warning</code>
            </p>
            <p class="warning">The p element with the class <code>warning</code>.</p>
            <p class="note bigfont">
                The p element with the classes <code>note</code> and <code>bigfont</code>
            </p>
        </main>
        <footer class="head_foot">Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_2/styles/style.css*
   ```
    /* black frame, centered text, 5 pixel distance from top */
    header, nav, footer { 
        text-align:center;
        border: 1px solid black;
        margin-top: 5px;
        padding: 5px;
        font-family: Verdana, Arial;
    }

    /* gray text */
    h1, abbr {
        color: gray;
        font-family: Verdana, Arial;
    }

    /* font family for p elements */
    p { 
        font-family: Verdana, Arial; 
    }

    /* style for a hint */
    .note {
        margin-left: 50px;
        border-left: 10px solid green;
        padding-left: 5px;
    }

    /* style for a note as a warning */
    .warning {
        border-left: 10px solid red;
        border-top: 2px solid red;
        border-right: 10px solid red;
        border-bottom: 2px solid red;
        text-align: center;
    }

    /* font size to 140%, background color to gray */
    .headfoot {
        font-size: 140%;
        background: #f5f5f5;
    }

    /* font size to 130%  */
    .bigfont { 
        font-size: 130%; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_2.PNG)


### ID selector
An ID is assigned with the HTML attribute `id`. IDs are always unique elements in an HTML document, i.e. they may only be assigned to one element in the HTML document. Since an ID occurs only once, the id is usually preferred for div elements. In CSS the id is marked with a *#* e.g. `#main {...}`

 example --> *2_CSS_Selectors/Part_3/index.html*
   ```
    <body>
        <div id="header">Header</div>
        <div id="nav">Navigation</div>
        <div id="main">
            <h1>Class selector</h1>
            <p>The p element without a class.</p>
            <p class="note">The p element with the class <code>note</code>.</p>
            <p class="note warning">
                The p element with the classes <code>note warning</code>.
            </p>
            <p class="warning">The p element with the class <code>warning</code>.</p>
            <p class="note bigfont">
                The p element with the classes <code>note bigfont</code>.
            </p>
        </div>
        <div id="footer">Footer</div>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_3/styles/style.css*
   ```
    /* black frame, centered text, 5 pixel distance from top */
    #header, #nav, #footer { 
        text-align:center;
        border: 1px solid black;
        margin-top: 5px;
        padding: 5px;
        font-family: Verdana, Arial;
    }

    /* Font size to 140%, background color to gray */
    #header, #footer {
        font-size: 140%;
        background: #f5f5f5;
    }

    #main { 
        margin: 20px; 
    }

    /* grey text */
    h1, abbr {
        color: gray;
        font-family: Verdana, Arial;
    }

    /* font family for p elements */
    p { 
        font-family: Verdana, Arial; 
    }

    /* paragraph text for a note */
    .note {
        margin-left: 50px;
        border-left: 10px solid green;
        padding-left: 5px;
    }

    /* paragraph text for a note as a warning */
    .warning {
        border-left: 10px solid red;
        border-top: 2px solid red;
        border-right: 10px solid red;
        border-bottom: 2px solid red;
        text-align: center;
    }   

    /* font size to 130% */
    .bigfont { 
        font-size: 130%; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_3.PNG)


In practice, class selectors should be preferred for specific properties or groups such as notes, warnings, error messages. The ID selector should be used to note individual or unique areas of a web page. 
Meaningful class names and ID names should be assigned. A meaningful name should describe the function and not the formatting (e.g. `.redBorder` = bad name, `.warning` = good name). Only upper and lower case letters, numbers, hyphens and underscores may be used for the name of the selector. The name must also not start with a digit.


### Universal selector
The universal selector is used to select all HTML elements in the HTML document. The universal selector is marked with the asterisk `*`.

 example --> *2_CSS_Selectors/Part_4/index.html*
   ```
    <body>
        <header>Header</header>
        <nav>Navigation</nav>
        <main>
            <h1>Universal selector</h1>
            <p>A single paragraph text</p>
            <p>A second paragraph text</p>
        </main>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_4/styles/style.css*
   ```
    /* black frame for all elements */

    * {
        margin: 5px;
        padding: 3px;
        border: 1px dotted black;
        text-align: center;
    }

    /* thicker border around the main element */
    /* main { border: 2px solid black; } */
    /* Thicker border around all HTML elements inside the main element */
    /* main * { border: 2px solid black; } */
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_4.PNG)


### Attribute selector
The attribute selector is used to select HTML elements according to their HTML attributes. This is the possibility to check the presence of an attribute.

 example --> *2_CSS_Selectors/Part_5/index.html*
   ```
    <h1>Attribute selector</h1>
    <p>
      Here you can find my GitHub profile
        <a href="https://github.com/BellaMrx" title="BellaMrx GitHub Profile">BellaMrx</a>
    </p>
    <p title="A paragraph with title">
      This paragraph also has a title attribute.
    </p>
   ```

 example --> *2_CSS_Selectors/Part_5/styles/style.css*
   ```
    a[title] {
        text-decoration: none;
        color: gray;
        font-weight: bold;
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_5.PNG)


### Attribute selector for attributes with a specific attribute value
There are 3 possibilities:
- `[attributname=attributevalue]`
- `[attributname~=attributevalue]`
- `[attributname|=attributevalue]`

 example --> *2_CSS_Selectors/Part_6/index.html*
   ```
    <body>
        <h1>[title=deprecated]</h1>
        <p>
        The HTML element <code title="deprecated">center</code> was declared deprecated in HTML5 and should be implemented by a CSS solution such as
        <code>text-align: center;</code>.
        </p>
        <h1>[title~=CSS-Guide]</h1>
        <ul>
            <li>
                <a href="https://github.com/BellaMrx/CSS_Guide" title="GitHub Website BellaMrx CSS-Guide">CSS-Guide</a>
            </li>
        </ul>
        <h1>[hreflang|=en]</h1>
        <ul>
            <li>
                <a href="https://www.w3schools.com/css/css_attribute_selectors.asp" hreflang="en">W3Schools</a>
            </li>
        </ul>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_6/styles/style.css*
   ```
    /* Styling for all HTML elements where title
    has the attribute value deprecated */
    [title=deprecated] {
         color: red;
        text-decoration: line-through;
    }

    /* Styling HTML elements where title contains the word
    attribute value contains the word "CSS-Guide". */
    [title~=CSS-Guide] { 
        font-weight: bold; 
    }

    /* Styling HTML elements where hreflang
    begins with the attribute value en, followed by a hyphen */
    [hreflang|=en] { 
        font-weight: bold; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_6.PNG)


### CSS pseudo-classes
CSS pseudo-classes are selectors for specific properties.
- Pseudo-classes for visited and non-visited hyperlinks

 example --> *2_CSS_Selectors/Part_7/index.html*
   ```
    <body>
        <h1>:link and :visited</h1>
        <ul>
            <li><a href="https://www.google.com/">Google</a></li>
            <li><a href="https://www.w3schools.com/">w3school</a></li>
            <li><a href="https://www.freecodecamp.org/">freeCodeCamp</a></li>
        </ul>
        <article class="articlestyle">
            <h2>:any-link</h2>
            <p>A simple <a href="https://github.com/BellaMrx">link</a>.</p>
        </article>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_7/styles/style.css*
   ```
    a:link { 
        color: red; 
    }
    a:visited { 
        color: green; 
    }
    .articlestyle a:any-link { 
        color: grey; 
    }
    /* Chrome and Opera */
    .articlestyle a:-webkit-any-link { 
        color: grey; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_7.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_7_B.PNG)


- Pseudo classes for user interactions with mouse and keyboard

 example --> *2_CSS_Selectors/Part_8/index.html*
   ```
    <body>
        <h1>:hover and :focus</h1>
        <ul>
            <li><a href="https://www.google.com/">Google</a></li>
            <li><a href="https://www.w3schools.com/">w3school</a></li>
            <li><a href="https://www.freecodecamp.org/">freeCodeCamp</a></li>
        </ul>
        <h2>:focus</h2>
        <form>
            Your name:
            <input type="text" name="name" id="name" placeholder="Your name" />
        </form>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_8/styles/style.css*
   ```
    input { 
        background-color: lightgray; 
    }
    input:focus { 
        background-color: white; 
    }
    input:hover { 
        box-shadow: 0 0 3px blue;  
    } 
    input:placeholder-shown {
        color: white;
    }
    li { 
        background-color: lightgray; 
    }
    li:hover { 
        background-color: snow; 
    }
    li:active { 
        background-color: gray; 
    }
    a:link { 
        text-decoration: none; color: blue; 
    }
    a:hover { 
        font-weight: bold; 
    }
    a:active { 
        color: red; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_8.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_8_B.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_8_C.PNG)


- Pseudo class for reference targets

 example --> *2_CSS_Selectors/Part_9/index.html*
   ```
    <body>
        <h1>:target</h1>
        <ul>
            <li><a href="#target01">Target nr. 1</a></li>
            <li><a href="#target02">Target nr. 2</a></li>
            <li><a href="#target03">Target nr. 3</a></li>
            <li><a href="#fade_in">Show hint</a></li>
        </ul>
        <div id="fade_in">Important notice!!!</div>
        <h2 id="target01">Target nr. 1</h2>
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor.
        </p>
        <h2><a id="target02">Target nr. 2</a></h2>
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor.
        </p>
        <p id="target03">
            Target nr. 3: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor.
        </p>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_9/styles/style.css*
   ```
    :target { 
        background: lightgrey; 
    }
    div#fade_in { 
        display: none; 
    }
    div#fade_in:target { 
        display: block; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_9.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_9_B.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_9_C.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_9_D.PNG)
 ![Preview](2_CSS_Selectors/Images/Preview_2_9_E.PNG)


### CSS structure pseudo-classes
Structure pseudo-classes can be used to select elements based on their position in the document structure.

- CSS structure pseudo-classes with `:root` and `:empty`

 example --> *2_CSS_Selectors/Part_10/index.html*
   ```
    <body>
        <h1>:root and :empty</h1>
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor.
        </p>
        <p></p>
        <h2>:empty on table</h2>
        <table>
            <tbody>
                <tr>
                    <td>Value</td>
                    <td></td>
                </tr>
                <tr>
                    <td></td>
                    <td>Value</td>
                </tr>
                <tr>
                    <td></td>
                    <td></td>
                </tr>
            </tbody>
        </table>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_10/styles/style.css*
   ```
    :root { 
        color: lightgrey; 
    }

    :empty { 
        background-color: yellow; padding: 10px; 
    }

    td:empty { 
        background-color: green; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_10.PNG)


- Structure pseudo-classes for child elements

 example --> *2_CSS_Selectors/Part_11/index.html*
   ```
    <body>
        <h1>:first-child in body</h1>
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor.
        </p>
        <h2>:first-child and :last-child on table</h2>
        <table>
            <tbody>
                <tr>
                    <td>:first-child in tr</td>
                    <td>Text only</td>
                    <td>:last-child in tr</td>
                </tr>
                <tr>
                    <td>:first-child in tr</td>
                    <td>Text only</td>
                    <td>:last-child in tr</td>
                </tr>
            </tbody>
        </table>
        <ul>
            <li>This is selected by :first-child in ul.</li>
            <li>This is not selected.</li>
            <li>This is not selected.</li>
            <li>This is selected by :last-child in ul.</li>
        </ul>
        <p>This one is selected by :last-child of body.</p>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_11/styles/style.css*
   ```
    * { 
        background-color: white; 
    }

    body { 
        padding: 5px; 
    }

    :first-child { 
        border: 2px solid black;  
    }

    :last-child { 
        border: 2px dotted gray; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_11.png)


 example --> *2_CSS_Selectors/Part_12/index.html*
   ```
    <body>
        <h1>:nth-child on table</h1>
        <table>
            <tbody>
                <tr>
                    <td>Line1.1</td>
                    <td>Line1.2</td>
                </tr>
                <tr>
                    <td>Line2.1</td>
                    <td>Line2.2</td>
                </tr>
                <tr>
                    <td>Line3.1</td>
                    <td>Line3.2</td>
                </tr>
                <tr>
                    <td>Line4.1</td>
                    <td>Line4.2</td>
                </tr>
            </tbody>
        </table>
        <h1>:nth-last-child on list</h1>
        <ul>
            <li>Entry 1</li>
            <li>Entry 2</li>
            <li>Entry 3</li>
            <li>Entry 4</li>
        </ul>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_12/styles/style.css*
   ```
    tr:nth-child(odd) { 
        background: lightgray; 
    }

    tr:nth-child(even) { 
        background: grey; 
    }

    li:nth-last-child(odd) { 
        color: blue; 
    }

    li:nth-last-child(even) { 
        color: lightgray; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_12.PNG)


- Structure pseudo-classes for certain child elements

 example --> *2_CSS_Selectors/Part_13/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Article 1</h1>
            <p>Text for article</p>
        </article>
        <article>
            <h1>Article 2</h1>
            <p>Text for article</p>
        </article>
        <article>
            <h1>Article 3</h1>
            <p>Text for article</p>
        </article>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_13/styles/style.css*
   ```
    article:first-of-type { 
        border: 2px solid black; 
    }

    article:last-of-type { 
        border: 2px dotted gray; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_13.png)


 example --> *2_CSS_Selectors/Part_14/index.html*
   ```
    <body>
        <h1>:only-of-type</h1>
        <p><em>Bear</em>! Who is this <em>Bear</em>?</p>
        <p>Attention! <em>Bear</em> could be behind <strong>you</strong>!</p>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_14/styles/style.css*
   ```
    em:only-of-type { 
        font-weight: bold; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_14.PNG)


- Pseudo elements, the selectors for elements that do not exist

 example --> *2_CSS_Selectors/Part_15/index.html*
   ```
    <body>
        <h1>:first-letter and :first-line</h1>
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis,
            sem. Nulla consequat massa quis enim.
        </p>
        <h1>:before and :after</h1>
        <table>
            <tbody>
                <tr>
                    <td>from A to B</td>
                    <td class="time">55</td>
                </tr>
                <tr>
                    <td>from A to C</td>
                    <td class="time">35</td>
                </tr>
                <tr>
                    <td>from B to C</td>
                    <td class="time">20</td>
                </tr>
            </tbody>
        </table>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_15/styles/style.css*
   ```
    p::first-line { 
        font-weight: bold; 
    }

    p::first-letter{ 
        font-size: xx-large; float: left; 
    }

    h1::-moz-selection { 
        background-color: orange; color:red; 
    }

    td.time::before { 
        content: "approx. "; 
    }

    td.time::after { 
        content: " Minutes";    
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_15.png)


## 2.2. Combinators
A combiner is a character between two selectors that concatenates these selectors. The first selector forms the condition and the second selector forms the target to be selected if the condition is true.

| Combinator | Designation                 | Meaning                                             |
| ---------- | --------------------------- | --------------------------------------------------- |
| E,F        | descendant combinator       | F is selected if it is a descendant of an E element |
| E > F      | child combinator            | F is selected only if it is a direct descendant of an E element |
| E + F      | adjacent sibling combinator | F is only selected if it occurs directly after E (in the same parent element) |
| E ~ F      | general sibling combinator  | F is selected only if occurs after E (in the same parent element) |

- Descendant selector (E, F)

 example --> *2_CSS_Selectors/Part_16/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Descendant combiner (E1 E2)</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>
                    <p>A paragraph text in the list item</p>
                </li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_16/styles/style.css*
   ```
    article p { 
        background: lightblue; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_16.png)


- Child selector (E1 > E2)

 example --> *2_CSS_Selectors/Part_17/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Child Combinator (E1 &gt; E2)</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>
                    <p>A paragraph text in the list item</p>
                </li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_17/styles/style.css*
   ```
    article > p { 
        background: lightblue; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_17.png)


- Neighbor selector (E1 + E2)

 example --> *2_CSS_Selectors/Part_18/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Direct adjacent combiner (E1 + E2)</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>
                    <p>A paragraph text in the list item</p>
                </li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_18/styles/style.css*
   ```
    article + p { 
        background: lightblue; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_18.png)


- Sibling selector (E1 ~ E2)

 example --> *2_CSS_Selectors/Part_19/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Indirect adjacent combiner (E1 ~ E2)</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>
                    <p>A paragraph text in the list item</p>
                </li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *2_CSS_Selectors/Part_19/styles/style.css*
   ```
    article ~ p { 
        background: lightblue; 
    }
   ```

 ![Preview](2_CSS_Selectors/Images/Preview_2_19.png)


 ----------------------------------------------------------------------

# 3. Inheritance and the cascade 

## 3.1 The principle of inheritance in CSS
An important principle in CSS is inheritance. Only this makes it possible to define different CSS properties such as colors, font and font size once in a central place instead of having to repeat them all the time.
The various HTML elements have ancestors and descendants (parent and child elements). Because of these relationships, the subsequent child elements inherit many style properties from the higher-level parent elements. 

 example --> *3_Inheritance_Cascade/Part_1/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Inheritance</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```
The body element here contains a header, article, two p and a footer element as direct descendants. This makes the body element the parent element of all these elements. Direct descendants of the article element are the h1, p, and ul elements. These direct descendants of article are the indirect descendants of the body element. Starting from the body element, the set CSS properties are inherited from element to element.

 example --> *3_Inheritance_Cascade/Part_1/styles/style.css*
   ```
    body {
        background: gray;
        font-family: Arial, Verdana;
        color: white;
    }

    article {
        background: lightblue;
        color: black;
    }
   ```
If, as in this example with the article selector, a new inheritable CSS property is assigned to an element, such as the text color here, the element specified with the selector (here article) and its descendants no longer inherit the CSS property of the parent element. In that case, the CSS properties declared in the selector to the descendants of an article element now become a black text color. The font-family of the body selector, on the other hand, was not declared in the article type selector, so the font-family declared in the body selector (here Arial) is still passed on to article and its descendants. background is not passed on to the descendants by the article selector, but is transparent, since that is the default value in CSS.

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_1.png)

If no specific value has been assigned to a CSS property, then the web browser uses the default value set for it when it inherits.
If these inheritances did not exist, a CSS rule would have to be explicitly created for each element. Inheritance can help write an efficient and well-organized stylesheet. For example, it is often sufficient to specify the font and other CSS properties early in the body element.

### Caution when using relative properties
Inheriting relative units such as font size with percentages or em can result in surprising changes, because some web browsers reapply this value for each element if the font size is also defined with percentages or em for further elements. Because it is not the value defined in the stylesheet that is passed on, but the value calculated by the web browser.

### Not everything is inherited
Not all CSS properties are passed on to the descendants. Especially CSS properties like `margin`, `padding`, `border` or `width` would not make much sense.
The following are not inherited: `background`, `border`, `width`, `height`, `padding`, `margin`, `position`, `top`, `right`, `bottom`, `left`, `float`, `clear`

### Force inheritance with `inherit` 
Some CSS properties are not inherited, but it is possible to force that with `inherit`.

 example --> *3_Inheritance_Cascade/Part_2/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Inheritance</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_2/styles/style.css*
   ```
    body {
        font-family: Arial, Verdana;
        color: white;
        background: gray;
    }

    article {
        border: 4px dotted black;
        background: lightblue;
        color: black;
    }

    p {
        border: inherit;
        background: lightgray;
    }
   ```

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_2.png)

### Restore the default value of a CSS property with `initial`

 example --> *3_Inheritance_Cascade/Part_3/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Inheritance</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_3/styles/style.css*
   ```
    body {
        font-family: Arial, Verdana;
        color: white;
        background: gray;
    }

    article {
        border: 4px dotted black;
        background: lightblue;
        color: black;
    }

    p {
        border: inherit;
        background: unset;
        color: initial;
    }
   ```

With `color:initial;` the font color of all p elements in the HTML document is reset to the default value of the browser.

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_3.png)


### Force inheritance or restore value with `unset`
The `unset` keyword is a middle ground between `inherit` and `initial`. When the keyword is used for a CSS property, it behaves like `inherit` and inherits the value for the corresponding CSS property of the parent element. If there is no parent element with a set value for that CSS property, `unset` behaves like `initial` and resets a CSS property to the default value provided by the CSS specification.


### Force inherit or restore values for all properties
With the shorthand notation `all`, all CSS properties of the parent element can be inherited with `inherit` or reset to default with `initial`. `unset` can also be used with `all`.

 example --> *3_Inheritance_Cascade/Part_4/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Inheritance</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p class="p_outside">2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_4/styles/style.css*
   ```
    body {
        font-family: Arial, Verdana;
        color: white;
        background: gray;
    }

    article {
        border: 4px dotted black;
        background: lightblue;
        color: black;
    }

    p {
	    border: inherit;
	    background: lightgray;
	    color: unset;
    }

    .p_outside {
        all: initial; 
        display: block;
        margin: 5px;
        color: silver;
    }
   ```

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_4.png)


## 3.2. Understanding the control system of the cascade
Cascade means that a document can be formatted not only by one stylesheet, but from a multitude of stylesheets that can come from different sources. This makes it possible for one stylesheet to build on another, saving a lot of work. Due to the multiple ways in which stylesheet statements can be included and combined with each other, conflicts and contradictions can come up. Such a conflict arises when the same CSS property has been assigned different values in several statements. For such cases, there is a rule system that decides which of the conflicting or competing style statements will ultimately be applied to an element.

### The origin of a stylesheet
- **Browser stylesheet**: The default stylesheet of the web browser is used if no CSS formatting is assigned to the HTML document. Each web browser provides basic formatting for this purpose. Each web browser provides its own default setting, so there are usually slight differences.

- **User stylesheet**: Some web browsers offer the user directly or via extensions to include own stylesheet files. When custom stylesheets are included, the corresponding properties of the web browser are overridden.

- **Author stylesheet**: This is the stylesheet you created and referenced or included with the @import rule, which is usually used to override or combine various CSS properties of the browser stylesheet and, if applicable, the user stylesheet.

Of these three sources, the browser stylesheet has the lowest priority. If a user stylesheet (medium priority) is used, the browser stylesheet is overwritten. The author stylesheet has the highest priority and overwrites all others.


### Increase the priority of a CSS property with `!important`
If a CSS rule or CSS property is declared multiple times in the same file, the last declared property usually becomes active.

 example --> *3_Inheritance_Cascade/Part_5/index.html*
   ```
    <body>
        <header>Header</header>
        <article class="priority">
            <h1>without !important</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_5/styles/style.css*
   ```
    .priority {
        border: 2px solid red;
    }

    .priority {
        border: 2px dotted green;
    }
   ```

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_5.png)


The CSS keyword `!important` can be used to increase the priority so that the property cannot be overridden by the following specifications.

 example --> *3_Inheritance_Cascade/Part_6/index.html*
   ```
    <body>
        <header>Header</header>
        <article class="priority">
            <h1>with !important</h1>
            <p>1. paragraph text for article</p>
            <ul>
                <li>List item 1</li>
                <li>List item 2</li>
                <li>List item 3</li>
            </ul>
            <p>2. paragraph text for article</p>
        </article>
        <p>1. paragraph text after the article</p>
        <p>2. paragraph text after the article</p>
        <footer>Footer</footer>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_6/styles/style.css*
   ```
    .priority {
        border: 2px solid red !important;
    }

    .priority {
        border: 2px dotted green;
    }
   ```

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_6.png)


### Sorting by weighting of the selectors
This sorting is used when there are equivalent specifications within a stylesheet. Here, a value is calculated for each selector that indicates the weighting of the selector. This value is called specificity. This specificity is expressed as a numerical value, and the higher this numerical value is, the more important the selector is, and it overwrites a competing selector with a lower value.

from highest weight(A) to lowest weight(D):
A = style attributes
B = ID
C = class, pseudo-class, attributes, 
D = pseudo elements

Universal selectors with `*` get no weighting and behave neutrally, as do combinatorial characters `>`,`+`,`~` and the space between two selectors.

 example --> *3_Inheritance_Cascade/Part_7/index.html*
   ```
    <body>
        <header>Header</header>
        <article>
            <h1>Inheritance</h1>
            <p>1. paragraph text for article</p>
            <ul id="index">
                <li class="aclass">List Item 1</li>
                <li class="aclass">List Item 2</li>
            </ul>
        </article>
        <footer>Footer</footer>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_7/styles/style.css*
   ```
    .aclass { 
        color: green; 
    }

    #index li.aclass { 
        color: orange; 
    }

    li { 
        color: red; 
    }

    li.aclass { 
        color: blue; 
    }

    body article ul li { 
        color: yellow; 
    }

    #index li { 
        color: gray; 
    }
   ```

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_7.png)


### Analyzing the cascade in the browser
Many web browsers offer developer tools that are a great help. There you can easily see which CSS properties were inherited from the web browser (USER AGENT STYLESHEET) and which were inherited from other elements (INHERITED FROM). Crossed out elements were overwritten by another element.

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_8.PNG)


## 3.3. Pass values to CSS properties
Only the most common types will be discussed here. More information about CSS values can be found at [w3](https://www.w3.org/TR/css-values-3/).


### The different units of measurement in CSS
The specifications of numerical values, e.g. font sizes, heights and widths or distances, are noted directly after the value. In CSS, there are many units of measurement that can be used either as relative or absolute specifications. For the number 0, the unit of measurement does not have to be specified.

   ```
    font-size: 14pt;
    margin: 1em;
    width: 100%;
    border: 3px ...;
   ```

The numeric values in CSS can be integers or floating point numbers. The comma is represented by a dot in CSS. e.g. `font-size: 1.2em;`. Some values in CSS do not require units of measurement, e.g. `z-index: 1;` or `opacity: 0.5;`. Negative values can also be used as long as it makes sense e.g. `z-index: -2;` , but negative values cannot be used for length specifications like height or width.

| unit of measurement | CSS name | specification      | description                           |
| ------------------- | -------- | ------------------ |-------------------------------------- |
| pixel               | px       | absolute, relative | The display of pixels depends on the pixel density of the output device. At a high screen resolution, the pixels become smaller, which is why the display appears smaller. Pixels are thus a relative unit of measurement on display devices and an absolute unit of measurement in relation to the content. |
| point               | pt       | absolute           | This is a typographic unit of measure, and 1 point is equal to 1/72 inch e.g. `font-size: 12pt;`  |
| pica                | pc       | absolute           | Pica is a typographic unit of measurement, one pica is 1/6 inch and therefore equals 12 points e.g `font-size: 1pc;` or 12pt |
| centimeter          | cm       | absolute           | A centimeter is the hundredth part of a meter and corresponds to 10 mm e.g. `margin: 1.2cm;` |
| millimeter          | mm       | absolute           | A millimeter is one thousandth of a meter e.g. `padding: 3mm;` |
| inch                | in       | absolute           | 1 inch equals 2.54 cm e.g. `margin-top: 1in;` |
| square width        | em       | relative           | An em stands for the font size of the element. If em is used for the font size itself, then this value refers to the font size of the parent element e.g. `font-size: 1.3em;` |
| x-height            | ex       | relative           | An ex represents the height of the lowercase x of the font used in this element. Again, if ex is used for the font size, then this height refers to the value of x in the parent element. |
| percent             | %        | relative           | The percentage is very flexible. It depends on the CSS property whether this value refers to the element's own size, to that of the parent element, or to a general context. |
| root em             | rem      | relative           | The rem initially behaves in the same way as em, except that the rem value is based on the root element and not on the font size of the respective parent element. In HTML the root element is the body or html element e.g. `font-size: 1.2.rem;` |
| viewport width      | vw       | relative           | 1vw corresponds to 1% or the hundredth part of the width of the display area. Thus, 100vw is equal to the complete width of the display area. This unit of measurement can be used to adjust the font size to the display area of the device or the size of the browser window. |
| viewport height     | vh       | relative           | 1vh corresponds to 1% or the hundredth part of the height of the display area. Therefore, 100vh is equal to the entire height of the display area. This unit of measurement can be used to adjust the font size to the display area of the device or the size of the browser window. |


### Strings and keywords as value for CSS properties
CSS makes a strict distinction between keywords and strings.

Strings are placed between single or double quotes in CSS:
- content: " meter";
- content: '$ ';

The keywords in CSS are not marked separately:
- color: white;
- width: auto;
- display: inline-block;


### Use color in CSS
An important design element in CSS are colors. There are several ways to specify color values in CSS. None of these different color specifications have advantages or disadvantages when displayed on the web page.

#### **use a name as color value**
From the beginning it was possible in CSS to note color values directly with names.

   ```
    section {
        background-color: gray;
        color: blue;
    }
   ```

A list of all color values, can be found at [147Colors](http://www.colors.commutercreative.com/).


#### **Classic hexadecimal notation for the color specification**
This notation is still one of the most commonly used for color values. The specification starts with the character #, followed by the color parts for red, green and blue in a range from 00(for 0) to FF(for 255). The general notation is #RRGGBB.

   ```
    section {
        background-color: #0000FF;      /* blue */
        color: #FFFFFF;     /* white */
    }
   ```

There is also a shorthand notation for hexadecimal values.

   ```
    section {
        background-color: #000000;      /* black */
        color: #FFFFFF;     /* white */
    }
   ```
The same but in shorthand:

   ```
    section {
        background-color: #000;      /* black */
        color: #FFF;     /* white */
    }
   ```


#### **Mix colors yourself with red, green and blue**
An RGB color mixture can be defined with CSS function rgb(red, green, blue). The specifications for red, green and blue can be made either with percentage values (0-100%) or with decimal numbers (0-255).

- decimal numbers

   ```
    section {
        background-color: rgb(0, 0, 255);      /* blue */
        color: rgb(255, 255, 255);      /* white */
    }
   ```

- percent

   ```
    section {
        background-color: rgb(0%, 0%, 100%);      /* blue */
        color: rgb(100%, 100%, 100%);      /* white */
    }
   ```


#### **RBG mix with transparency**
Another function is rgba(), this has been extended by only one value, the alpha value for transparency. This value can be used to specify the transparency of the color. The value 0.0 means complete transparency, and the value 1.0 stands for complete opacity and thus corresponds to the function rgb().
   ```
    section {
        color: rgba(255, 255, 255, 0.3)
    }
   ```

 example --> *3_Inheritance_Cascade/Part_8/index.html*
   ```
    <body>
        <h3>color: rgba(255, 255, 255, 0.5);</h3>
        <p class="p_article_1">Lorem ipsum dolor sit amet, consectetuer adipiscing elit...</p>
        <h3>color: rgb(255, 255, 255);</h3>
        <p class="p_article_2">Lorem ipsum dolor sit amet, consectetuer adipiscing elit...</p>
    </body>
   ```

 example --> *3_Inheritance_Cascade/Part_8/styles/style.css*
   ```
    .p_article_1 { 
        background-image:url('../images/sunsetTree.jpg');
        background-repeat: no-repeat;
        font-weight: bolder;
        width: 450px;
        color: rgba(255, 255, 255, 0.5);    
    } 
 
    .p_article_2 { 
        background-image:url('../images/sunsetTree.jpg');
        background-repeat: no-repeat;
        font-weight: bolder;
        width: 450px;
        color: rgb(255, 255, 255);     
    } 
   ```

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_9.png)


#### **HSL Mix - mix colors with hue, saturation and lightness**
Starting at Level 3, CSS offers an HSL blend of hue, saturation, and lightness. Many web designers find it more intuitive or easier to remember to specify the hue with an integer value from 0 to 360. It's like a color wheel from 0 to 359 degrees, where the value 0 or 360 represents red, 120 represents green, and 240 represents blue.
The values of saturation and lightness are expressed as percentages. The more the value of saturation is reduced from 100% to 0%, the more the hue becomes a gray. The normal brightness, on the other hand, is indicated with the value 50%. A lightness of 100% is white and a lightness of 0% is black.
   ```
    .p_article { 
        background-color: hsl(240, 100%, 50%);      /* blue */
        color: hsl(0, 100%, 100%);      /* white font color */
    } 
   ```

As with the RGB blends, there is still an HSL blend with hsla(hue, saturation, lightness, opacity), where the opacity can be specified as a fourth parameter from 0 (completely transparent) to 1 (no transparency).

If you want to find out which color is used on a page, the browsers offer help.
Firefox for example has a color picker:

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_10.jpg)

 ![Preview](3_Inheritance_Cascade/Images/Preview_3_11.jpg)

Google Chrome offers the extension ColorZilla (which is also available for Firefox). And for Microsft Edge I would use ColorFish Color Picker (if I would use it).

The browsers offer many help options, it is recommended to be familiar with the brwosers.


### Angle measures in CSS
In CSS there are also some angle measures that can be used to define a rotation. If a negative value is used, the rotation is counterclockwise.

| Unit of Measurement | CSS Name | Description |
| ------------------- | -------- | ------------------------------------------------------------- |
| degrees             | deg      | angle in degrees; 360 degrees corresponds to a complete circle e.g. tarnsform: rotate(90deg); |
| Gon                 | grad     | angle in Gon; a complete circle corresponds to 400 Gon. 100 Gon = 90 degree e.g. tarnsform: rotate( 100grad); |
| Radian              | rad      | angle in ground measure; a complete circle corresponds to 2 Pi e.g. tarnsform: rotate(5.5rad); |
| full angle          | turn     | A full angle is a circle rotation (0.25turn corresponds to a 90 degree rotation) e.g. tarnsform: rotate(0.25turn); |


### Shorthand in CSS
- margin: is used for an outer border or distance between the current element and its parent or neighboring element.

   ```
    section { 
        margin: 20px;
    } 
   ```

is the shorthand notation of:
   ```
    section { 
        margin-top: 20px;
        margin-right: 20px;
        margin-bottom: 20px;
        margin-left: 20px;
    } 
   ```

also possible:
   ```
    section { 
        margin: 20px 10px 20px 5px;     /* margin-top, margin-right, margin-bottom, margin-left */
    } 
   ```

The only important thing about this notation is that the order is clockwise (top = 12 o'clock).

If the values of left and right are equal, is also possible:
   ```
    section { 
        margin: 20px 10px 5px;     /* margin-top, margin-right and -left, margin-bottom */
    } 
   ```
By omitting the fourth value (left), the value of right is used, making the left and right spacing 10px. 

This also works with top and bottom:
   ```
    section { 
        margin: 20px 10px;     /* margin-top and -bottom, margin-right and -left */
    } 
   ```

also possible:
   ```
    section { 
        margin: 20px;     /* margin-top, margin-bottom, margin -left */
        margin-right: 0;
    } 
   ```

Besides margin, there are other CSS properties that I will discuss here later.

---------------------------------------------------------------------------------

# 4. The box model of CSS
In CSS, the box model serves as the basis for positioning elements and creating a layout.


## 4.1. The classic box model
The box model includes
- the actual **content** of text and images, which is specified with **width** and **height**
- **padding**, which creates space between the content and the border of an element
- the **border**
- **margin**, this creates space around an element, outside of paddings and borders 

 ![Preview](4_Box_Model/images/BoxModell.png)


### width and height
The actual content area with the space for text and images can be specified with the CSS properties width and height. If no value is specified, the HTML element is as wide and high as the surrounding element.

 example --> *4_Box_Model/Part_1/index.html*
   ```
    <h1>width and height</h1>
    <article class="article_01">
        <h2 class="h_2">Article 1 (width: 300px)</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article_02">
        <h2 class="h_2">Article 2 (width: 600px)</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
   ```

 example --> *4_Box_Model/Part_1/styles/style.css*
   ```
    .article_01 { 
        width: 300px; background: #e7fad7; 
    }

    .article_02 { 
        width: 600px; background: #e7fad7; 
    }

    .h_2 { 
        background: #adfd93; 
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_1.png)


Note that the height specification is only an initial value. If the content of the encompassing element is greater than the specified height, the content will still be displayed and will overflow the box.

 example --> *4_Box_Model/Part_2/index.html*
   ```
    <h1>height</h1>
    <article class="article_01">
        <h2>Headline</h2>
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis,
            sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo.
        </p>
    </article>
   ```

 example --> *4_Box_Model/Part_2/styles/style.css*
   ```
    .article_01 {
        width: 230px;
        height: 215px;
        background-color: #e7fad7;
        border: black 1px solid;
        /* overflow: hidden; */
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_2.png)


If overflowing is to be prevented, this is possible with the CSS property `overflow: hidden;`, with which, however, the oversized content is no longer displayed.

 ![Preview](4_Box_Model/images/Preview_4_2_overflow.png)


In practice, fixed values for width and height are rarely defined. Responsive web design tends to use properties such as `min-width` or `min-height` or `max-height` to allow flexible limits suitable for the device or screen width.


### padding
The CSS property padding alone sets all four sides clockwise, which is the shorthand notation:

   ```
    section { 
        padding: 20px;
    } 
   ```

is the shorthand notation of:
   ```
    section { 
        padding-top: 20px;
        padding-right: 20px;
        padding-bottom: 20px;
        padding-left: 20px;
    } 
   ```

The shorthand notation with padding works the same as with margin.


### border
The border wraps around the inner space (padding) and has its own CSS properties for thickness, line style, and color. Again, as with margin and padding, all four sides can be adjusted separately.

 example --> *4_Box_Model/Part_3/index.html*
   ```
    <h1>border</h1>
    <article class="article01">
        <h2 class="h_2">width: 600px; border: 10px solid sienna;</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article02">
        <h2 class="h_2">width: 600px; border: 10px solid peru; padding: 50px;</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
   ```

 example --> *4_Box_Model/Part_3/styles/style.css*
   ```
    .article01 {
        width: 600px;
        border: 10px solid #56d22d;
        background-color: #e7fad7;
    }

    .article02 {
        width: 600px;
        padding: 50px;
        border: 10px solid #76ea4f;
        background-color: #e7fad7;
    }

    .h_2 { 
        background-color: #adfd93;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_3.png)


### margin
The outer spacing of the box model is called margin. The outer margin has no color, is completely transparent and therefore takes on the background color of the surrounding element. Negative values are also allowed for margin. How these affect margin depends on whether the elements are static, positioned or floated.

 example --> *4_Box_Model/Part_4/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h2>margin: 10px 0px;</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article01">
        <h2>margin: 10px 0px;</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_4/styles/style.css*
   ```
    .article01 {
        width: 600px;
        padding: 5px;
        border: 5px solid #76ea4f;
        background-color: #e7fad7;
        margin: 10px 0px;
    }

    .headfoot {
        width: 600px;
        padding: 5px;
        border: 5px solid #76ea4f;
        background-color: #adfd93;
        text-align: center;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_4.png)


### Collapsing Margins
For the vertical margins of two boxes placed one above the other, the values are not added together, but only the larger of the two margins is used. The smaller value is ignored. Horizontal distances do not collapse. If they touch, they are added together normally.

 ![Preview](4_Box_Model/images/CollapsingMargins.png)

 example --> *4_Box_Model/Part_5/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h2>Article 1</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article01">
        <h2>Article 2</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_5/styles/style.css*
   ```
    .headfoot {
        width: 600px;
        padding: 5px;
        border: 5px solid #adfd93;
        background-color: #e7fad7;
        margin-bottom: 20px;
        text-align: center;
    }

    .article01 {
        width: 600px;
        padding: 5px;
        border: 5px solid #76ea4f;
        background-color: #e7fad7;
        margin: 10px 0px;
    }


    /* h1, h2, p {
        margin-top: 0;
    } */
   ```

 ![Preview](4_Box_Model/images/Preview_4_5.png)

 
The collapsing is intentional and serves to keep the spacing even for texts that consist of multiple paragraphs. It rules:
- If both values are the same, only one is used.
- If the values are different, the larger value is used.


### Calculating the total width and height of a box
It is possible to calculate the total width or total height of a box.

 example --> *4_Box_Model/Part_6/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h2>Article 1</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article01">
        <h2>Article 2</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_6/styles/style.css*
   ```
    .headfoot {
        width: 600px;
        padding: 5px;
        border: 1px solid black;
        background-color: #adfd93;
        margin: 5px 0px;
        text-align: center;
    }

    .article01 {
        width: 600px;
        padding: 15px;
        border: 2px dotted #76ea4f;
        background-color: #e7fad7;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_6.png)


The total width of a box is calculated by adding width, padding-right, padding-left, border-right-width, border-left-width, margin-right and margin-left together.

Calculation for this example:
| CSS Property         | .headfoot | .article  |
| -------------------- | --------- | --------- |
| width      	  	   | 600 Pixel | 600 pixel |
| + padding-right 	   | 5 Pixel   | 15 Pixel  |
| + padding-left  	   | 5 Pixel   | 15 Pixel  |
| + border-right-width | 1 Pixel   | 2 Pixel   |
| + border-left-width  | 1 Pixel   | 2 Pixel   |
| + margin-right 	   | 0 		   | 0 		   |
| + margin-left 	   | 0 		   | 0 		   |
| **total width**      | 612 pixel | 634 pixel |

Thus the difference of the total width is exactly 22 pixels. Here you have to decide for yourself where to add or remove these 22 pixels. 

Example:

 example --> *4_Box_Model/Part_7/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h2>Article 1</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article01">
        <h2>Article 2</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_7/styles/style.css*
   ```
    .headfoot {
        width: 600px;
        padding: 5px;
        border: 1px solid black;
        background-color: #adfd93;
        margin: 5px 0px;
        text-align: center;
    }

    .article01 {
        width: 578px;
        padding: 15px;
        border: 2px dotted #76ea4f;
        background-color: #e7fad7;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_7.png)


## 4.2. The newer alternative box model of CSS
The classic box model can be complicated, since the width specification determines the width of the content area and in the end padding, border and margin must also be taken into account for the total width. As long as the specification is only in pixels, a uniform layout is possible with awkward arithmetic.

It becomes more complicated when different units are used for width, padding, border or margin. The problem was solved by using an inner `<div>` inside the corresponding column for padding, border and margin.

With the alternative box model `border-box`, the width and height are no longer specified only for the content area, but these specifications also sensibly take into account the inner spacing and the frame.

Box model `border-box`
 ![Preview](4_Box_Model/images/BoxModellAlternative.png)



### Use box model `box-sizing`
To use the alternative box model, the CSS property `box-sizing` must be assigned the value `border-box` = `box-sizing: border-box`.

Values that can be used for `box-sizing`:
- `content-box`: This corresponds to the behavior of the classic box model, where the width and height values correspond to the content of the element in the box.
- `border-box`: With this specification the value for width and height corresponds to the value of border-left to border-right or border-top to border-bottom. Changing padding and border does not change the width or height of the element. 
- `inherit`: With this option the value of the parent element is inherited.


Classic box model:

 example --> *4_Box_Model/Part_8/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h2>Article 1</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <article class="article01">
        <h2>Article 2</h2>
        <p>
            Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor.
            <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et
            <ins>magnis</ins> dis parturient montes, nascetur
            <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
        </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_8/styles/style.css*
   ```
    .headfoot {
        width: 70%;
        padding: 5px;
        border: 2px solid black;
        background-color: #adfd93;
        text-align: center;
    }

    .article01 {
        width: 70%;
        padding: 15px;
        border: 1px dotted #76ea4f;
        background-color: #e7fad7;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_8.png)


alternative Box model:

 example --> *4_Box_Model/Part_9/index.html*
   ```
    <header class="headfoot">Header</header>
      <article class="article01">
        <h1>Article 1</h1>
        <p>Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor. <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et <ins>magnis</ins> dis parturient montes, nascetur <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.</p>
      </article>
      <article class="article01">
        <h1>Article 2</h1>
        <p>Lorem <abbr>ipsum</abbr> dolor <em>sit amet</em>, consectetuer adipiscing elit. <strong>Aenean commodo</strong> ligula eget dolor. <a href="#">Aenean massa</a>. Cum sociis natoque penatibus et <ins>magnis</ins> dis parturient montes, nascetur <del>ridiculus</del> mus. Donec quam felis, <mark>ultricies nec</mark>, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.</p>
      </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_9/styles/style.css*
   ```
    * {
        box-sizing: border-box;        
    }

    .headfoot {
        width: 70%;
        padding: 5px;
        border: 2px solid black;
        background-color: #adfd93;
        text-align: center;
    }

    .article01 {
        width: 70%;
        padding: 15px;
        border: 1px dotted #76ea4f;
        background-color: #e7fad7;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_9.png)


The box model with box-sizing can simplify CSS life considerably. Especially if percentages are used for the width and pixel values for padding or border, i.e. different units are mixed. For example, if a column is defined with 30% width, it is with `box-sizing: border-box;` no matter what values and units are used for padding or border, it remains at 30% for the total width of the column.

The interactive box model diagram, can be helpful to understand it better: [angular interactive box-model diagram](https://codepen.io/carolineartz/full/ogVXZj).

#### Analyzing the box model in the browser

The browsers also offer developer tools to analyze and visualize the box model in the browser. There it is also possible to change the values for testing and see how it directly affects the web page.

 ![Preview](4_Box_Model/images/Box-Model-Browser.PNG)


### The box model for inline elements
In HTML, everything consists of rectangular boxes. This also applies to inline elements like `<em>`, `<strong>` and `<a>`. However, it is not possible to specify the height or width for inline elements. Here the content determines the height and width. There are also differences in margin, padding and border for the -top and -bottom versions, these have no effect.


## 4.3. Design boxes
### Add and style a border with the `border` property 
A border can be added for each element, customizing the border color, stroke width and type.

With the shorthand, all four sides can be designed at once:

   ```
    border: 2px solid black;
   ```
this means: 

   ```
    border-color: black;
    border-width: 2px;
    border-style: solid;
   ```

It is possible to specify two, three or four values for border-style or border-color. For example, if :
   ```
    border-color: green red;
   ```

This means that the upper and lower frames are displayed in green and the right and left frames are displayed in red.

or:
   ```
    border-color: green red blue yellow;
   ```

This means the upper frame is green, the left one is red, the lower one is blue and the right one is yellow, (always in clockwise direction starting from the top).

With the properties border-top, border-left, border-bottom and border-right, all four sides can be designed individually.

   ```
    border-top: green 2px dotted;
    border-left: red 4px dashed;
    border-bottom: blue 6px solid;
    border-right: yellow 8px inset;
   ```

or only ones:

   ```
    border-top: green 2px dotted;
   ```
This means that only the upper border is displayed.

Different border styles 
| Value    | Description                         |
| -------- | ----------------------------------- |
| none 	   | Default value. Specifies no border. |
| hidden   | The same as "none", except in border conflict resolution for table elements. |
| dotted   | Specifies a dotted border. |
| dashed   | Specifies a dashed border. |
| solid    | Specifies a solid border. |
| double   | Specifies a double border. |
| groove   | Specifies a 3D grooved border. The effect depends on the border-color value. |
| ridge    | Specifies a 3D ridged border. The effect depends on the border-color value. |
| inset    | Specifies a 3D inset border. The effect depends on the border-color value. |
| outset   | Specifies a 3D outset border. The effect depends on the border-color value. |
| initial  | Sets this property to its default value. |
| inherit  | Inherits this property from its parent element. |

 example --> *4_Box_Model/Part_10/index.html*
   ```
    <body>
        <h1>Different types of border</h1>
        <p class="border01">border: blue 2px solid;</p>
        <p class="border02">
            border: red 1px dashed;<br /> border-left-width: 10px;
        </p>
        <p class="border03">border: green 5px ridge;</p>
        <p class="border04">
            border-top: red 5px dotted;<br /> border-right: blue 5px groove;<br /> border-bottom-style: double;<br /> border-bottom-width: 5px;<br /> border-bottom-color: green;<br /> border-left: orange 5px outset;
        </p>
    </body>
   ```

 example --> *4_Box_Model/Part_10/styles/style.css*
   ```
    * { 
        box-sizing: border-box;
    }

    .border01 {
        border: blue 2px solid;
    }

    .border02 {
        border: red 1px dashed;
        border-left-width: 20px;
    }

    .border03 {
        border: green 5px ridge;
    }

    .border04 {
        border-top: red 5px dotted;
        border-right: blue 5px groove;
        border-bottom-style: double;
        border-bottom-width: 5px;
        border-bottom-color: green;
        border-left: orange 5px outset;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_10.png)


### Create a decorative border with `border-image`
With border-image a graphic can be used as a border. A pixel graphic or an SVG graphic is used for this purpose.

 example --> *4_Box_Model/Part_11/index.html*
   ```
    <body>
        <h1>Decorative border for boxes</h1>
        <p class="border">
            <code>.border {<br />
            &nbsp;width: 500px;<br />
            &nbsp;padding: 10px;<br />
            &nbsp;border: 25px solid transparent;<br />
            &nbsp;border-image:url('../images/myborder.png') 50 50 50 50 round;<br />
            }</code>
        </p>
    </body>
   ```

 example --> *4_Box_Model/Part_11/styles/style.css*
   ```
    .border {
        width: 500px;
        padding: 10px;
        border: 25px solid transparent;
        border-image: url("../images/myborder.png") 50 50 50 50 round;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_11.png)

`border-image` is a summary property of `border-image-source`, `border-image-slice`, `border-image-width` and `border-image-repeat`.


### Set background color with `background-color`
The background color is specified with `background-color`. Only with `background` it is also possible but this is only a summary of CSS properties, so the shorthand.

 example --> *4_Box_Model/Part_12/index.html*
   ```
    <h1>Background color of boxes</h1>
    <p class="border">
        <code>.border {<br />
        &nbsp;background-color: lightblue;<br />
        &nbsp;width: 85%;<br />
        &nbsp;padding: 5px;<br />
        &nbsp;border: darkblue 7px ridge;<br />
      }</code>
    </p>
   ```

 example --> *4_Box_Model/Part_12/styles/style.css*
   ```
    .border {
        background-color: lightgreen;
        width: 85%;
        padding: 5px;
        border: darkgreen 7px ridge;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_12.png)


### Use background graphics
Since background is only a shorthand notation of several CSS properties for the background, the following properties are combined with the shorthand notation:
- `background-color`: background color of the element
- `background-image`: image as background of the element
- `background-position`: position of the background image
- `background-repeat`: repeat background image along the vertical or horizontal axis
- `background-attachment`: Here you can specify whether the background is scrollable or fixed.

Images, logos or graphics should still be added with the HTML element `<img>`. But for decoration or design a background graphic can be added with CSS.

A background graphic can be added with the shorthand `background` or with `background-image`.

 example --> *4_Box_Model/Part_13/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h1>Add background pattern</h1>
        <p>
            <code>.article01 {<br />
          &nbsp;width: 85%;<br />
          &nbsp;background-image: url('../images/pattern.png');<br />
          &nbsp;border-left: grey 1px dotted;<br />
          &nbsp;border-right: grey 1px dotted;<br />
          &nbsp;padding: 10px;<br />
          &nbsp;background-color: #c4c4c4;<br />
          }</code>
      </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_13/styles/style.css*
   ```
    .headfoot {
        width: 85%;
        border: gray 1px dotted;
        padding: 10px;
        background-color: limegreen;
        color: white;
        text-align: center;
    }

    .article01 {
        width: 85%;
        background-image: url("../images/pattern.png");
        border-left: gray 1px dotted;
        border-right: gray 1px dotted;
        padding: 10px;
        background-color: #c4c4c4;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_13.png)

As you can see in this example, the background graphic is overlaid on the background color. The additional specification of a background color is useful (should match the color of the background graphic), if the graphic cannot be loaded.

You can also find the background patterns at [DinPattern](https://dinpattern.com/).


### Repeat background graphic
The background graphic is repeated vertically and horizontally as many times as space is available if no special specifications are made.

This example shows a background image without background-repeat, to the bottom it works fine but to the right it doesn't look optimal.

   ```
    .article01 {
        width: 85%;
        background-image: url("../images/gradient.jpg");

        border-left: gray 1px dotted;
        border-right: gray 1px dotted;
        padding: 10px;
        background-color: #e8f3ea;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_14_A.png)

Tiling of the background image can be restricted to the vertical direction by `background-repeat`, it would also work without but only if the graphic has the appropriate dimensions. For tiling in vertical direction the CSS property `background-repeat` must be assigned the value `repeat-y`.

 example --> *4_Box_Model/Part_14/index.html*
   ```
    <header class="headfoot">Header</header>
    <article class="article01">
        <h1>Add background pattern</h1>
        <p>
            <code>.article01 {<br />
          &nbsp;width: 85%;<br />
          &nbsp;background-image: url('../images/gradient.png');<br />
          &nbsp;<b>background-repeat: repeat-y;</b><br />
          &nbsp;border-left: grey 1px dotted;<br />
          &nbsp;border-right: grey 1px dotted;<br />
          &nbsp;padding: 10px;<br />
          &nbsp;<b>background-color: #e8f3ea;</b><br />
          }</code>
      </p>
    </article>
    <footer class="headfoot">Footer</footer>
   ```

 example --> *4_Box_Model/Part_14/styles/style.css*
   ```
    .headfoot {
        width: 85%;
        border: gray 1px dotted;
        padding: 10px;
        background-color: limegreen;
        color: white;
        text-align: center;
    }

    .article01 {
        width: 85%;
        background-image: url("../images/pattern.png");
        background-repeat: repeat-y;
        border-left: gray 1px dotted;
        border-right: gray 1px dotted;
        padding: 10px;
        background-color: #c4c4c4;
    }
   ```

 ![Preview](4_Box_Model/images/Preview_4_14.png)

In total, there are three ways to tile a background graphic with the CSS background-repeat property:
- `background-repeat: repeat-y;` --> vertical tiling (y-axis)
- `background-repeat: repeat-x;` --> horizontal tiling (x-axis)
- `background-repeat: no-repeat;` --> no tiles at all 