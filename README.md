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
    - 2.1 The simple selectors of CSS

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


## 2.1 The simple selectors of CSS

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

