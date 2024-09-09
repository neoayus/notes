# 1) Fundamentals of Web and Basics of XHTML Web Fundamentals: 

## Internet  
The Internet is a vast network of interconnected computers that communicate with each other using a standardized set of protocols. It allows for the exchange of information and resources, enabling various services like email, file transfer, and the World Wide Web.

## World Wide Web
The World Wide Web **(WWW)** is a system of *interlinked hypertext document* and *multimedia content* that can be accessed through the Internet. It allows users to navigate between pages and access a vast array of information using hyperlinks. 

## Web Browsers 
Web browsers are essential tools for accessing the vast resources available on the World Wide Web. It serves as the gateway to the World Wide Web, allowing users to navigate between web pages,
for example: chrome, mozilla firefox. 

## URL 
A **Uniform Resource Locator (URL)** is the address used to access resources on the Internet. It specifies the location of a resource, such as a web page, and the method by which it can be retrieved.
### Structure of URL 
A Typical URL Contains of several Components. 
1. **Protocol:** Specifies the method used to access the resource. Common protocols include:
	`http://` (Hypertext Transfer Protocol)
	`https://` (Secure Hypertext Transfer Protocol)
	
2. **Domain Name:** The human-readable name of the server where the resource is hosted. It often corresponds to the name of a website, like www.example.com.

3. **Port Number:** Specifies the port on the server used to access the resource. It is usually omitted as the default port for HTTP is 80, and for HTTPS, it is 443.

4. Path: Specifies the exact location of the resource on the server. It usually points to a file or directory, like `/path/to/page.`

5. Query String: Contains additional parameters sent to the server. It starts with a ? and includes key-value pairs, such as `?key=value&anotherkey=anothervalue.`

	***EXAMPLE OF THE URL :***  
	**Protocol :** `https`
	**Domain Name :** `www.example.com`
	**Port Number :** `443 (default for HTTPS)`
	**Path :** `/path/to/page`
	**Query String :** `?query=example`
	**Fragment :** `#section`

## Webpage
A **Web Page** is a single document on the World Wide Web that is accessed using a  web browser.   It is typically written in HTML (Hypertext Markup Language) and can include text, images, videos, and other multimedia elements. Web pages are the building blocks of a website and are identified by unique URLs.

## Website
A **Website**  is a collection of  related web pages that are linked together under a common domain name.
Websites are hosted on a web server and are accessed using a web browser. A website can serve various purposes, such as providing information, selling products, or offering interactive services.

## Web Servers
A Web Server is a software application or hardware device that stores, processes, and serves web content to users over the Internet. It handles requests from web browsers and delivers web pages, images, and other resources to the client’s browser.

### Key Functions of Web Server: 
1. **Hosting Web Content:** Stores and manages files such as HTML, CSS, JavaScript, and media. The server provides these files to users when requested.

2. **Processing Requests:** Receives HTTP or HTTPS requests from browsers, processes them, and returns the appropriate responses, including web pages and error messages.

3. **Serving Static and Dynamic Content:**

	+ Static Content: Files that do not change, such as HTML pages and images.
	+ Dynamic Content: Generated on-the-fly based on user interactions or server-side scripts (e.g., PHP, ASP.NET).
	
4. **Handling Multiple Requests:** Capable of managing multiple simultaneous connections from different users.

5. Logging: Records details about requests, errors, and server performance in log files for monitoring and troubleshooting.

## MIME (Multipurpose Internet Mail Extensions)
MIME **(Multipurpose Internet Mail Extensions)** is a standard used to extend the format of email messages and web content beyond plain text, allowing for the inclusion of various types of data such as images, audio, and video. 
**It plays a crucial role in enabling rich content in emails and web applications.** 

### Key Concepts of MIME:
1. **MIME Types:** Also known as media types, MIME types specify the type of content being sent or received. They are used by web browsers and email clients to handle different kinds of data appropriately.

1. Type/Subtype: The MIME type consists of a type and a subtype separated by a slash. For example:
	text/html: Indicates HTML text.
	image/jpeg: Indicates a JPEG image.
	application/json: Indicates JSON data.
2. Content-Type Header: In HTTP requests and responses, the Content-Type header specifies the MIME type of the data being sent. For example:
	+ Content-Type: text/html (for HTML documents)
	+ Content-Type: application/pdf (for PDF files)
	
3. Content-Disposition Header: This header specifies how the content should be displayed or handled by the browser. Common values include:
	+ `inline`:  Display the content within the browser.
	+ `attachment`:  Prompt the user to download the content as a file.
	
4. Multipart Messages: MIME allows for multipart messages, where a single message contains multiple parts, each with its own MIME type. This is commonly used in email to combine text and attachments, or in web forms to upload files.
		Example: A form submission with both text fields and file uploads uses multipart/form-data.
		
5. Encoding: MIME supports various encoding mechanisms to ensure that data is transmitted correctly:

	+ Base64: Encodes binary data as ASCII text, used for embedding images in emails or web content.
	+ Quoted-Printable: Encodes text data in a way that preserves readability and is used for email content.
###  MIME in Web:
HTTP Requests and Responses: MIME types are used in HTTP headers to define the type of data being sent or received. For instance, a web server may send Content-Type: application/json when returning JSON data from an API.
File Uploads: Web forms use MIME types to handle file uploads, ensuring that the correct file type is processed.


## HTTP Protocol and Its Phases
HTTP (Hypertext Transfer Protocol) is the foundational protocol used for **transmitting data on the World Wide Web.** It defines how messages are formatted and transmitted, and how web servers and browsers should respond to various commands. 
HTTP operates as a request-response protocol between a client (usually a web browser) and a server.
### HTTP Methods:
1. GET: Requests data from a specified resource. No body is sent.
2. POST: Submits data to be processed to a specified resource. Includes a request body. 
3. PUT: Updates a current resource with new data. 
4. DELETE: Deletes the specified resource. 
5. HEAD: Similar to GET, but only retrieves the headers, not the body.

### HTTP Status Codes:
+ **2xx Success:** Indicates the request was successfully received, understood, and accepted.
	`200 OK: The request succeeded.`
	
+ **3xx Redirection:** Indicates that further action needs to be taken to complete the request.
	`301 Moved Permanently: The requested resource has been moved to a new URL.`
		
+ **4xx Client Error:** Indicates that the request contains bad syntax or cannot be fulfilled.
	`404 Not Found: The requested resource could not be found.`
		
+ **5xx Server Error:** Indicates that the server failed to fulfill a valid request.
	`500 Internal Server Error: The server encountered an unexpected condition.`

## Phases of HTTP Communication:
HTTP communication typically involves the following phases:

Client Request:

### Request Line: 
+ The client sends a request line to the server that includes the HTTP method (e.g., GET, POST), the URL, and the HTTP version.
+ Headers: The request includes headers that provide additional information about the request, such as Host, User-Agent, Accept, and Content-Type.
+ Body (Optional): For methods like POST and PUT, the request may include a body that contains data to be processed by the server.

### Server Processing:
+ The server receives the request, processes it, and determines the appropriate response. This may involve retrieving a file, querying a database, or executing server-side scripts.
+ The server then prepares the response based on the request.
### Server Response:
+ Status Line: The server sends a status line back to the client, which includes the HTTP version, a status code, and a reason phrase (e.g., HTTP/1.1 200 OK).
+ Headers: The response includes headers that provide additional information about the response, such as Content-Type, Content-Length, and Date.
+ Body: The response body contains the requested resource (e.g., an HTML page, image, or JSON data).

### Connection Close:
After the response is sent, the connection between the client and server is typically closed. However, HTTP/1.1 introduced persistent connections, allowing the connection to be reused for multiple requests/responses between the same client and server.


# 2) Basics of HTML

XHTML **(Extensible Hypertext Markup Language)** is a web markup language that combines the syntax of XML (Extensible Markup Language) with the flexibility of HTML. 

XHTML was developed to improve the accuracy and extensibility of HTML, ensuring that web documents are well-formed and consistently interpreted across different browsers and devices.

## Standard Structure of XHTML 

```
<!DOCTYPE html>
<html>
<head>
    <title>Page Title</title>
</head>
<body>
    <h1>Heading</h1>
    <p>This is a paragraph.</p>
    <img src="image.jpg" alt="Description of Image" />
</body>
</html>
```

### Breakdown of the Structure:

1.  **DOCTYPE Declaration :**  `<!DOCTYPE>` specifies the version of XHTML being used. 
For example, XHTML 1.0 Strict. This ensures that the document is parsed correctly by browsers.

2. **`<html>` Element**: The `<html>` element is the root element of the document and must include the XML namespace declaration.

3.  **`<head>` Section:**  The `<head>` section contains meta-information about the document, such as the title `(<title>)`, character encoding `(<meta>)`, and links to external stylesheets or scripts.

4. **`<body>` Section:** The `<body>` section contains the content of the document, such as headings, paragraphs, images, and other elements.
	All elements must be properly closed, and tag names should be in lowercase.
	
5. ***Tags and Attributes:*** All tags in XHTML must be closed, either with a closing tag (e.g., `</p>`) or self-closed (e.g., `<img />`).***
	Attribute values must be enclosed in double quotes (e.g., alt="Description").
	
## Difference between HTML and XHTML

### 1 ) Syntax Rules:
**HTML:** 
+ HTML is more flexible with its syntax.
+ Tags can be left open (e.g., `<br>`), and attribute values don’t always need to be in quotes.
+ It’s not case-sensitive, so you can use `<html> or <HTML>.`

**XHTML :** 
+ XHTML has stricter rules because it’s based on XML.
+ All tags must be closed (e.g., `<br />`), and attribute values must be in double quotes.
It’s case-sensitive, so all tags and attributes must be in lowercase (e.g., `<html>`).

### 2 ) Error Handling:
**HTML :**
+ Browsers are forgiving with HTML errors and will still try to display the page even if there are mistakes in the code.

**XHTML :**
+ XHTML requires well-formed code, meaning any error can prevent the page from being displayed correctly. It’s less forgiving than HTML.

### Compatibility:
**HTML :** 
+ HTML is widely supported by all browsers, making it a go-to choice for most web developers.

**XHTML :** 
+ XHTML is also widely supported but requires more careful coding to ensure compatibility.

### Media Types:
***HTML :***
+ HTML documents are served with the text/html media type.

**XHTML :**
+ XHTML documents are usually served with the application/xhtml+xml media type, but can also be served as text/html for compatibility.

### Extensibility:
**HTML :**
+ HTML is less extensible because it’s not based on XML.

**XHTML :** 
+ XHTML is extensible, meaning you can combine it with other XML languages and extend it for specific needs.

## Basic Text Markup Elements: Paragraph
In XHTML, a paragraph is defined using the `<p>` tag. 
This tag is essential for grouping together blocks of text that form a complete idea or thought. When you write a paragraph, the content is wrapped inside the `<p>` tag, which automatically adds space before and after the block of text, making it visually separate from other content on the page.

```
	<p>This is a paragraph of text. It can contain multiple sentences.</p> 
```

##  Basic Text Markup Elements
### Heading Tags
Headings are used to define the structure of your content, breaking it into sections and sub-sections. XHTML offers six levels of headings, from `<h1>` to `<h6>`.

The `<h1>` tag represents the main heading, usually the title of the page or the most important section, while `<h6>` is used for the least important subheading.

```
	<h1 THIS THAT SLIME SHIT /> 
	<h6 THIS THAT SLIME SHIT /> 
```
### Break Tag
The `<br />` tag is used to insert a line break within text. Unlike paragraphs, which add space before and after blocks of text, the break tag simply moves the following content to a new line. 

```
	This is the first line.<br />
	This is the second line.
```
### Italic and Bold
To emphasize text, you can use the `<i>` tag for italics and the `<b>` tag for bold. Italics are generally used for subtle emphasis, like highlighting a term or a phrase, while bold is used for stronger emphasis.
```
	<b>This ia a Bold Text.</b> 
	<i>This ia an Italic Text.</i> 
```

### Superscript and Subscript

+ The `<sup>` tag is used to create superscript text, which is text that appears slightly above the normal line, often used for *footnotes* or *mathematical exponents.* 
```
	This text is <sup> SUPERSCRIPT </sup> text 
```

+ The `<sub>` tag creates subscript text, which appears slightly below the normal line, commonly used in *chemical formulas* or other technical content.
```
	This text is <sub> SUPERSCRIPT </sub> text   
```

## Character Entities
In XHTML, **certain characters have special meanings that can interfere with the display of content on web pages.** For example, characters like `<, >,` and `&` are used in HTML tags and attributes, so if you want to display these characters as part of your text, you need to use character entities. 

Character entities are a way of encoding these special characters so that they can be displayed correctly in a web browser.

A character entity is typically written as an ampersand (&) followed by a code or name, and then a semicolon (;).

 ```
	<p>To write HTML code, you often need to use symbols like &lt;, &gt;, and &amp;.</p>
```

## Hyperlinks
Hyperlinks often simply called links, are a fundamental feature of the web, enabling users to navigate between different web pages and resources.

In XHTML, hyperlinks are created using the `<a>` (anchor) tag, which links a piece of text or an element to another document or a different part of the same document.
The basic structure of a hyperlink includes the `<a>` tag with an `href` (Hypertext Reference) attribute, which specifies the destination URL. The text or content inside the `<a>` tag becomes clickable, allowing users to follow the link to the specified URL  

```
	<a href="https://www.example.com">Visit Example</a>
```

Here’s the content on **Images** written in a modularized paragraph style:

---

## Images

Images are a key element in web design, allowing you to add visual content to your web pages.
In XHTML, images are embedded using the `<img>` tag. This tag is self-closing,  and it requires at least two attributes: `src` and `alt`.

+ The `src` (source) attribute specifies the path to the image file you want to display. This path can be an *absolute URL* linking to an image on the web, or a *relative path* to an image stored in your project’s directory. 

+ The `alt` (alternative text) attribute provides a text description of the image, which is displayed if the image cannot be loaded and is also used by screen readers to improve accessibility.

example : 
```xhtml
<img src="images/logo.png" alt="Company Logo" />
```

You can also control the size and appearance of images using additional attributes or CSS. For instance, the `width` and `height` attributes allow you to set the dimensions of the image directly within the `<img>` tag:

```xhtml
<img src="images/photo.jpg" alt="A beautiful landscape" width="300" height="200" />
```

## Here’s the content on **Lists** written in a modularized paragraph style:

---

## Lists

Lists are a fundamental part of web content, allows us  to organize information in a clear, structured format. 
XHTML provides three types of lists: 
	1. ordered lists, 
	2. unordered lists
	3. definition lists
Each type serves a specific purpose and is created using different tags.

### Ordered Lists

An ordered list is used when the sequence or ranking of items is important. Items in an ordered list are numbered by default. To create an ordered list, you use the `<ol>` (ordered list) tag, with each item inside the list wrapped in an `<li>` (list item) tag. 

```xhtml
<ol>
   <li>First item</li>
   <li>Second item</li>
   <li>Third item</li>
</ol>
```

### Unordered Lists

An unordered list is used when the order of items is not important. Items in an unordered list are typically marked with bullets. The `<ul>` (unordered list) tag is used to create an unordered list, with each item also wrapped in an `<li>` tag.

```xhtml
<ul>
   <li>Apples</li>
   <li>Bananas</li>
   <li>Cherries</li>
</ul>
```
### Definition Lists

A definition list is used for listing terms and their definitions. Unlike ordered and unordered lists, a definition list uses the `<dl>` (definition list) tag. Each term is wrapped in a `<dt>` (definition term) tag, and each definition is wrapped in a `<dd>` (definition description) tag.

Here’s an example:

```xhtml
<dl>
   <dt>HTML</dt>
   <dd>HyperText Markup Language</dd>
   <dt>CSS</dt>
   <dd>Cascading Style Sheets</dd>
</dl>
```

In this example, "HTML" and "CSS" are the terms, and their meanings are provided in the descriptions that follow. Definition lists are useful for glossaries, FAQs, or any content where you need to define terms.

### Nesting Lists
Lists can also be nested within each other, allowing for complex data structures. For instance, you can place an unordered list inside an ordered list item to create sub-items:

```xhtml
<ol>
   <li>Main Topic
      <ul>
         <li>Subtopic A</li>
         <li>Subtopic B</li>
      </ul>
   </li>
   <li>Another Main Topic</li>
</ol>
```

Here’s the content on **Tables** written in a modularized paragraph style:

---

## Tables
	: are used to display data in a structured and organized manner
Tables are a powerful way to present structured data on web pages. 
In XHTML, tables are created using a combination of the `<table>`, `<tr>`, `<th>`, and `<td>` tags. Each tag serves a specific purpose in defining the table’s structure and content.

### Structure  
A table is defined using the `<table>` tag. Inside this tag, rows are created with the `<tr>` (table row) tag. Each row contains one or more cells, which are defined with either `<th>` (table header) or `<td>` (table data) tags.

Example : 

```xhtml
<table>
   <tr>
      <th>Header 1</th>
      <th>Header 2</th>
   </tr>
   <tr>
      <td>Data 1</td>
      <td>Data 2</td>
   </tr>
   <tr>
      <td>Data 3</td>
      <td>Data 4</td>
   </tr>
</table>
```

### Table Attributes
Tables can be enhanced with various attributes to improve their appearance and functionality:

- **`border`**: Adds a border around the table and its cells.
  ```xhtml
  <table border="1">
  ```

- **`cellspacing`**: Adds space between the cells.
  ```xhtml
  <table cellspacing="5">
  ```

- **`width`**: Sets the width of the table.
  ```xhtml
  <table width="100%">
  ```
#### Caption
To provide additional context for a table, you can use the `<caption>` tag to add a title. 
```xhtml
<table>
   <caption>Monthly Sales Report</caption>
   <tr>
      <th>Month</th>
      <th>Sales</th>
   </tr>
</table>
```

### Spanning
Tables can also include spanning capabilities to merge cells:

- **`colspan`**: Merges cells horizontally across multiple columns.
  ```xhtml
  <td colspan="2">Merged Cell</td>
  ```

- **`rowspan`**: Merges cells vertically across multiple rows.
  ```xhtml
  <td rowspan="2">Merged Cell</td>
  ```


Here’s the content on **`<div>` and `<span>`** written in a modularized paragraph style:

---

## `<div>` and `<span>`

In XHTML, `<div>` and `<span>` are two commonly used tags for grouping and styling content, but they serve different purposes and are used in distinct contexts.

### `<div>` Tag

The `<div>` tag is a block-level element used for grouping larger sections of content on a web page. It is often used to create divisions or sections within a document, making it easier to apply styles or manipulate large blocks of content.

A block-level element like `<div>` starts on a new line and takes up the full width available, pushing any content that follows to a new line. This makes it ideal for structuring the layout of a page.

```xhtml
<div class="container">
   <h1>Welcome to My Website</h1>
   <p>This is a paragraph inside a div.</p>
</div>
```

### `<span>` Tag

The `<span>` tag is an inline element used for grouping smaller portions of content within a line of text. Unlike `<div>`, `<span>` does not create a new line and only takes up as much width as necessary for its content. This makes it ideal for applying styles or making changes to small parts of a text or inline elements without affecting the layout of the entire block.

```xhtml
<p>This is a <span class="highlight">highlighted</span> word in a paragraph.</p>
```

### Differences and Use Cases
- **`<div>`**: Used for creating larger, block-level sections in the layout of a page. Suitable for grouping and styling larger segments of content, such as sections, articles, or entire columns. Block-level elements like `<div>` start on a new line and occupy the full width of their container.

- **`<span>`**: Used for smaller, inline sections of content within a line of text. Suitable for styling or manipulating parts of text or other inline elements without affecting the layout. Inline elements like `<span>` do not start on a new line and only take up the space necessary for their content.


