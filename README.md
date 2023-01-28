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


