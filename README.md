# CSS Guide
 
 Detailed guide about CSS (all basics for CSS) + templates.

 The code examples in the guide can be found in the listed folders.

-----------------------------------------------------------------------------------------

## Contents
1. Introduction to CSS
    - 1.1. History of CSS 
    - 1.2. Principle of CSS application

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

