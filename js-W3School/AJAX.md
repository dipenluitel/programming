# Introduction
What is AJAX?
AJAX (Asynchronous JavaScript and XML) is a web development technique that allows a web page to send and receive data from a server asynchronously without reloading the entire page. This means that when you interact with a web application (like submitting a form, fetching data, etc.), the page can update parts of itself without a full refresh, leading to a smoother user experience.
1. AJAX = Asynchronous JavaScript And XML.
2. AX is not a programming language.
3. AJAX just uses a combination of:
   a. A browser built-in XMLHttpRequest object (to request data from a web server)
   b. JavaScript and HTML DOM (to display or use the data)

A browser built-in XMLHttpRequest object (to request data from a web server)
JavaScript and HTML DOM (to display or use the data)
Key Features of AJAX:

**Asynchronous:* Allows background data retrieval, so the user can continue to interact with the page while data is being fetched.

**JavaScript:* AJAX is primarily used with JavaScript to make requests to the server.

**XML/JSON:* Originally, AJAX used XML for data exchange, but now JSON is more commonly used due to its simplicity and ease of use with JavaScript.

**Common Use Cases for AJAX:**

**Loading Data:* Fetching data from a server (like user profiles, comments, etc.) without reloading the page.

**Submitting Forms:* Sending form data to the server (like login forms, comments, etc.) without refreshing the page.

**Dynamic Content:* Updating parts of a web page based on user interactions (like a live search feature).

**How AJAX Works**
1. An event occurs in a web page (the page is loaded, a button is clicked)
2. An XMLHttpRequest object is created by JavaScript
3. The XMLHttpRequest object sends a request to a web server
4. The server processes the request
5. The server sends a response back to the web page
6. The response is read by JavaScript
7. Proper action (like page update) is performed by JavaScript

**Modern Browsers (Fetch API)**
Modern Browsers can use Fetch API instead of the XMLHttpRequest Object.
The Fetch API interface allows web browser to make HTTP requests to web servers.
If you use the XMLHttpRequest Object, Fetch can do the same in a simpler way.

# AJAX - The XMLHttpRequest Object
The keystone of AJAX is the XMLHttpRequest object.
1. Create an XMLHttpRequest object
2. Define a callback function
3. Open the XMLHttpRequest object
4. Send a Request to a server

**Create an XMLHttpRequest Object**
All modern browsers (Chrome, Firefox, IE, Edge, Safari, Opera) have a built-in XMLHttpRequest object.
Syntax for creating an XMLHttpRequest object:
**variable = new XMLHttpRequest();*

**Define a Callback Function**
A callback function is a function passed as a parameter to another function.
In this case, the callback function should contain the code to execute when the response is ready.
**xhttp.onload = function() {
  // What to do when the response is ready
}*

**Send a Request**
To send a request to a server, you can use the open() and send() methods of the XMLHttpRequest object:
**xhttp.open("GET", "ajax_info.txt");
xhttp.send();*

Example<br />
<code>// Create an XMLHttpRequest object
const xhttp = new XMLHttpRequest();

// Define a callback function
xhttp.onload = function() {
  // Here you can use the Data
}

// Send a request
xhttp.open("GET", "ajax_info.txt");
xhttp.send();</code>

**XMLHttpRequest Object Methods**
1. new XMLHttpRequest()	Creates a new XMLHttpRequest object
2. abort()	Cancels the current request
3. getAllResponseHeaders()	Returns header information
4. getResponseHeader()	Returns specific header information
5. open(method, url, async, user, psw)	Specifies the request
      a. method: the request type GET or POST
      b. url: the file location
      c. async: true (asynchronous) or false (synchronous)
      d. user: optional user name
      e. psw: optional password
6. send()	Sends the request to the server
7. Used for GET requests
8. send(string)	Sends the request to the server.
9. Used for POST requests
0. setRequestHeader()	Adds a label/value pair to the header to be sent

**XMLHttpRequest Object Properties**
1. onload	Defines a function to be called when the request is received (loaded)
2. onreadystatechange	Defines a function to be called when the readyState property changes
3. readyState	Holds the status of the XMLHttpRequest.
      0: request not initialized
      1: server connection established
      2: request received
      3: processing request
      4: request finished and response is ready
4. responseText	Returns the response data as a string
5. responseXML	Returns the response data as XML data
6. status	Returns the status-number of a request
      1. 200: "OK"
      2. 403: "Forbidden"
      3. 404: "Not Found"
7. statusText	Returns the status-text (e.g. "OK" or "Not Found")

**The onreadystatechange Property**
1. onreadystatechange	Defines a function to be called when the readyState property changes
2. readyState	Holds the status of the XMLHttpRequest.
      0: request not initialized
      1: server connection established
      2: request received
      3: processing request
      4: request finished and response is ready
3. status	200: "OK"
          403: "Forbidden"
          404: "Page not found"
4. statusText	Returns the status-text (e.g. "OK" or "Not Found")
<code>
function loadDoc() {
  const xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML =
      this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt");
  xhttp.send();
}
</code>

# AJAX - XMLHttpRequest
The XMLHttpRequest object is used to request data from a server.

**Send a Request To a Server**
To send a request to a server, we use the open() and send() methods of the XMLHttpRequest object:
 <code>
xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();
</code>

** The url - A File On a Server**
The url parameter of the open() method, is an address to a file on a server:
<code>
xhttp.open("GET", "ajax_test.asp", true);
</code>

**Asynchronous - True or False?**
Server requests should be sent asynchronously.The async parameter of the open() method should be set to true:
<code>
xhttp.open("GET", "ajax_test.asp", true);
By sending asynchronously, the JavaScript does not have to wait for the server response, but can instead:
</code>
1. execute other scripts while waiting for server response
2. deal with the response after the response is ready

**GET Requests**
A simple GET request:
<code>
xhttp.open("GET", "demo_get.asp");
xhttp.send();
</code>

**POST Requests**
A simple POST request:
<code>
xhttp.open("POST", "demo_post.asp");
xhttp.send();
</code>

**Synchronous Request**
To execute a synchronous request, change the third parameter in the open() method to false:
<code>
xhttp.open("GET", "ajax_info.txt", false);
Sometimes async = false are used for quick testing. You will also find synchronous requests in older JavaScript code.
</code>

#AJAX - Server Response
Server Response Properties are
responseText, get the response data as a string.
responseXML, get the response data as XML data.

**The responseText Property**
The responseText property returns the server response as a JavaScript string, and you can use it accordingly:
<code>
document.getElementById("demo").innerHTML = xhttp.responseText;
</code>

**The responseXML Property**
The XMLHttpRequest object has an in-built XML parser.
The responseXML property returns the server response as an XML DOM object.
Using this property you can parse the response as an XML DOM object:
<code>
const xmlDoc = xhttp.responseXML;
const x = xmlDoc.getElementsByTagName("ARTIST");

let txt = "";
for (let i = 0; i < x.length; i++) {
  txt += x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("demo").innerHTML = txt;

xhttp.open("GET", "cd_catalog.xml");
xhttp.send();
</code>

**Server Response Methods**
getResponseHeader(), Returns specific header information from the server resource
getAllResponseHeaders(), Returns all the header information from the server resource

**The getAllResponseHeaders() Method**
The getAllResponseHeaders() method returns all header information from the server response.
<code>
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {
    document.getElementById("demo").innerHTML =
    this.getAllResponseHeaders();
}
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
</code>

**The getResponseHeader() Method**
The getResponseHeader() method returns specific header information from the server response.
<code>
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {
document.getElementById("demo").innerHTML =
this.getResponseHeader("Last-Modified");
}

#AJAX XML Example
AJAX can be used for interactive communication with an XML file.

Example
<code>
function loadDoc() {
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {myFunction(this);}
xhttp.open("GET", "cd_catalog.xml");
xhttp.send();
}
function myFunction(xml) {
const xmlDoc = xml.responseXML;
const x = xmlDoc.getElementsByTagName("CD");
let table="<tr><th>Artist</th><th>Title</th></tr>";
for (let i = 0; i <x.length; i++) {
table += "<tr><td>" +
x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
"</td><td>" +
x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
"</td></tr>";
}
document.getElementById("demo").innerHTML = table;
}
</code>


#XML Applications
**Display XML Data in an HTML Table**
This example loops through each <CD> element, and displays the values of the <ARTIST> and the <TITLE> elements in an HTML table:

Example
table id="demo">/table

<script>
function loadXMLDoc() {
  const xhttp = new XMLHttpRequest();
  xhttp.onload = function() {
    const xmlDoc = xhttp.responseXML;
    const cd = xmlDoc.getElementsByTagName("CD");
    myFunction(cd);
  }
  xhttp.open("GET", "cd_catalog.xml");
  xhttp.send();
}

function myFunction(cd) {
  let table="<tr><th>Artist</th><th>Title</th></tr>";
  for (let i = 0; i < cd.length; i++) {
    table += "<tr><td>" +
    cd[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    cd[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
</script>

**Display XML Data in an HTML Table**
This example loops through each CD element, and displays the values of the ARTIST and the TITLE elements in an HTML table:

Example
table id="demo"> /table

<script>
function loadXMLDoc() {
  const xhttp = new XMLHttpRequest();
  xhttp.onload = function() {
    const xmlDoc = xhttp.responseXML;
    const cd = xmlDoc.getElementsByTagName("CD");
    myFunction(cd);
  }
  xhttp.open("GET", "cd_catalog.xml");
  xhttp.send();
}

function myFunction(cd) {
  let table="<tr><th>Artist</th><th>Title</th></tr>";
  for (let i = 0; i < cd.length; i++) {
    table += "<tr><td>" +
    cd[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    cd[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
</script>
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
</code>


