<h1> 1. When a user enters an URL in the browser, how does the browser fetch the desired result ? </h1>
<p> So to explain this i have created a diagram flow on how the browser creates a connection with host server to render the UI or response.</p>

![browser](https://user-images.githubusercontent.com/77038740/224484556-cd5659e8-05c1-42ea-806a-6dffe3466f2a.png)

<h1> 2. What is the main functionality of the browser?</h1>

<p> The main function of a web browser is to fetch and retrieve resources from the server over the internet. They also provide an interface and display content for the user. Most of the common features of an internet browser are a bookmark, history, menu, address bar, title bar, etc.
</p>

<h1>3. High Level Components of a browser</h1>


![components](https://user-images.githubusercontent.com/77038740/224484885-3f8fd35e-bfcf-4644-b628-55a7dc546828.png)

<ul>
   <li>
     <h3>
The User Interface
</h3><p>
The user interface is the space where User interacts with the browser. It includes the address bar, back and next buttons, home button, refresh and stop, bookmark option, etc. Every other part, except the window where requested web page is displayed, comes under it.
</p>
</li>
<li>
<h3> The Browser Engine </h3>
<p> The browser engine works as a bridge between the User interface and the rendering engine. According to the inputs from various user interfaces, it queries and manipulates the rendering engine.
 </p>
</li>
<li>
<h3> The Rendering Engine </h3>
<p> The rendering engine, as the name suggests is responsible for rendering the requested web page on the browser screen. The rendering engine interprets the HTML, XML documents and images that are formatted using CSS and generates the layout that is displayed in the User Interface. However, using plugins or extensions, it can display other types data also. Different browsers user different rendering engines:
* Internet Explorer: Trident
* Firefox & other Mozilla browsers: Gecko
* Chrome & Opera 15+: Blink
* Chrome (iPhone) & Safari: Webkit </p>
</li>
<li>
<h3> Networking </h3>
<p>
Component of the browser which retrieves the URLs using the common internet protocols of HTTP or FTP. The networking component handles all aspects of Internet communication and security. The network component may implement a cache of retrieved documents in order to reduce network traffic.</p>
</li>
<li>
<h3> JavaScript Interpreter </h3>
<p> It is the component of the browser which interprets and executes the javascript code embedded in a website. The interpreted results are sent to the rendering engine for display. If the script is external then first the resource is fetched from the network. Parser keeps on hold until the script is executed.
 </p>
</li>
<li>
<h3>
UI Backend
</h3>
<p>
UI backend is used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. It underneath uses operating system user interface methods.
</p>
</li>
<li>
<h3> Data Persistence/Storage </h3>
<p>
This is a persistence layer. Browsers support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem. It is a small database created on the local drive of the computer where the browser is installed. It manages user data such as cache, cookies, bookmarks and preferences.
</p>
</li>
</ul>

<h1>4. Rendering engine and its use. </h1>
<p>Rendering engine is one of the browser component which interprets HTML and other resources linked to it and present a webpage on the screen.
To render a webpage rendering engine go through a set of steps.
</p>
<p>DOM → CSSOM → Render tree → Layout → Paint</p>

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="styles.css">
    <title>Dive deep into rendering engine</title>
</head>
<body>
    <div class="container">
        <h1>Rendering engine process</h1>
        <ul>
            <li>DOM</li>
            <li>CSSOM</li>
            <li>Render Tree</li>
            <li>Layout</li>
            <li>Paint</li>
        </ul>
    </div>  
</body>
</html>
```
<h3>DOM</h3>
<p> The rendering engine will receive a HTML file from the network (server) or a local disk in the form of bytes. Then it converts these bytes into characters based on specified encoding of the file i.e utf-8</p>
<p>
After character conversion, Each strings of characters translated into distinct tokens using the HTML5 standards specified by the W3C.
</p>
<p>
In the next step, These tokens get converted into node objects with their properties and rules. Each HTML tag is an individual node object.
</p>
<p>
The rendering engine construct a tree kind of structure using the node objects. The output tree is nothing but a DOM
</p>

![dom](https://user-images.githubusercontent.com/77038740/224486398-eb7fcf9c-856f-4021-84b8-0ce2fcb18722.png)

<h3> CSSOM (CSS Object Model)</h3>
<p> While HTML is getting parsed if rendering engine encounter the styles in any of these forms(external, embed, inline) it will parse and construct a tree like structure same as DOM tree and this tree is called CSSOM tree.</p>
<p> Here also rendering engine will go through the below steps to create a CSSOM tree like how it does while constructing a DOM tree.</p>
<p> Bytes → Characters → Tokens → Nodes → CSSOM</p>

```
body {
    font-family: sans-serif;
    color: #fff;
}
.container {
    background: cornflowerblue;
    padding: 20px;
}
h1 {
    font-size: 40px;
    margin-bottom: 30px;
}
ul {
    padding: 0;
    text-align: center;
    font-size: 24px;
}
li {
    list-style-type: none;
    margin: 25px 0;
    padding: 10px;
    border: 3px solid #fff;
}

```

![CSSOM](https://user-images.githubusercontent.com/77038740/224486714-31b0ba5b-456f-4cdf-bb50-0dbeae228a21.png)


<h3 id="renderTree"> Render Tree </h3>
<p>
Rendering engine will combine the DOM and CSSOM trees and form a render tree. Render tree will capture only the visible nodes from both the trees and it will ignore the nodes which are not going to be rendered on the screen like script, meta, title tags and the nodes hidden through CSS (nodes which are having display: none; property). For each visible node it will find the matching CSSOM rules and apply them.</p>

![Render](https://user-images.githubusercontent.com/77038740/224486837-d313a418-ec6e-4dca-a47e-aa38445cb717.png)

<h3 id="layout">Layout</h3>
<p>
In this phase, The rendering engine start traversing the render tree at the root and calculate each visible element’s exact size and the position where it should get printed on the page. This process is called layout since the rendering engine is calculating the layout information of each node. This process is also called reflow because the element size or position might change on events like scroll, resizing the window or on DOM manipulation
</p>

<h3 id="paint"> Paint </h3>
<p>
Until now rendering engine has calculated visible elements style, size and position. Now the rendering engine is ready to place the elements on the screen. In this phase each node of the render tree converted to actual pixels on the screen. This phase is called paint because rendering engine taking outputs from the previous phases and printing elements on the user screen.
</p>

<h1>5. Parsers </h1>
<p> Parsing means analyzing and converting a program into an internal format that a runtime environment can actually run </p>
<p>
In other words, parsing means taking the code we write as text (HTML, CSS) and transform it into something that the browser can work with. The parsing will be done by the browser engine
</p>
<p>
The browser engine is a core component of every major browser and it's main role is to combine structure (HTML) and style (CSS) so it can draw the web page on our screens. It is also responsible to find out which pieces of code are interactive. We should not think about it like a separate piece of software but as being part of a bigger sofware (in our case, the browser).
There are many browser engines in the wild but the majority of the browsers use one of these three actively developed full engines:
</p>
<p> Gecko  (Mozilla Firefox)</p>
<p> WebKit  (Safari)</p>
<p> Blink, part of Chromium </p>
<h3>Tokenization</h3>
<p>
It is the lexical analysis and it converts some input into tokens (basic components of source code). Imagine we would take an English text and break it down into words, where the words would be the tokens.
</p>

![tokenization](https://user-images.githubusercontent.com/77038740/224487540-a64cc582-3741-4177-bdf1-0c64d26457af.png)

<h1>6. Script Processors</h1>
<p> The script processor executes Javascript code to process an event. The processor uses a pure Go implementation of ECMAScript 5.1 and has no external dependencies. This can be useful in situations where one of the other processors doesn't provide the functionality you need to filter events.
 </p>

<h1>Tree construction</h1>
<h3>
<a href="#renderTree">
Click Here
</a>
</h3>
<h1>Layout</h1>
<h3>
<a href="#layout">
Click Here
</a>
</h3>
<h1>Paint</h1>
<h3>
<a href="#paint">
Click Here
</a>
</h3>
