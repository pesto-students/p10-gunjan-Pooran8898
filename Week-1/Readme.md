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

