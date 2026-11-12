# Internet and Web Technology

Completed: **Module I revision; JavaScript fundamentals, DOM and BOM.** Advanced JavaScript and Module III remain outlined.

Prioritise **HTML/CSS page construction, JavaScript validation and DOM operations**, followed by **XML/DTD design** in the unfinished material. These recur in the supplied papers, as do AJAX and JSON. Five-mark construction tasks and a 10-point travel task show the need to practise complete code. Recurrence guides study order; it does not predict the examination or replace the syllabus.

| Module | Reading route |
| --- | --- |
| [Module I](#module-i---the-web-html-and-css-8-hours) | Web concepts → HTTP → HTML → CSS → complete page design. |
| [Module II](#module-ii---javascript-dom-bom-and-advanced-concepts-10-hours) | JavaScript → DOM → forms → browser facilities → advanced topics. |
| [Module III](#module-iii---xml-ajax-jquery-json-reactjs-and-nodejs-12-hours) | XML → AJAX → jQuery → JSON → React → Node.js. |

Actual questions and model answers follow the relevant topics. Marks accompany the questions; source footnotes retain filenames, question numbers and pages. Original practice is labelled. Evidence and scope decisions appear at the end.

---

# Module I - The Web, HTML and CSS (8 hours)

Use this module for concise revision: understand how a resource reaches the browser, then revise the HTML and CSS needed to construct pages.

## 1. The Internet and the World Wide Web

The **Internet** connects computer networks. The **World Wide Web** uses that network to make linked pages and resources available through URLs and web protocols.

> The Internet provides the network. The Web is one service that uses it.

Email can use the Internet without being a web page. A browser retrieves web resources and presents them to the user.

### A Brief History

The Internet developed before the Web. The main milestones are:[^web-history][^internet-history]

| Year | Development |
| --- | --- |
| 1969 | ARPANET began. |
| 1983 | The adoption of TCP/IP helped establish the modern Internet. |
| 1989 | Tim Berners-Lee proposed the Web at CERN. |
| 1991 | The first website became publicly accessible. |

Hyperlinks made it easy to move between networked documents.

---

## 2. Websites, Web Applications and Web Projects

A **website** brings related pages together. A **web application** lets the user complete a task, such as registering or placing an order.

| Static website | Dynamic website |
| --- | --- |
| Serves stored pages without generating their contents for each request. | Can generate or update content using program logic and data. |

One site can combine information pages and application features.

A web project follows this sequence:

**Requirements → Content and navigation → Design → Implementation → Testing → Publishing → Maintenance**

For a tourism site, choose the audience and destinations first. Then organise the pages, implement the design and check the links, images and layout.

Important development issues include usability, accessibility, browser compatibility, loading time, input handling, security and maintainability.

### Examination Questions

**What stages and strategies are required to develop a web project?** (2 marks)[^pyq-01]

**Answer.** Identify the audience and requirements; plan content and navigation; design the interface; implement pages and functionality; test correctness, usability and browser compatibility; deploy and maintain the site. Use consistent layouts and reusable styles, and review the result against the requirements.

---

## 3. Client–Server and Three-Tier Web Architecture

In the **client-server model**, the client requests a service and the server provides it.

The browser requests resources, interprets HTML/CSS and runs browser JavaScript. The web server accepts HTTP requests and returns resources or processing results.

A **three-tier architecture** separates presentation, application logic and data storage:

```text
Browser / presentation <--> Application / business logic <--> Database
          HTTP requests and responses       data operations
```

For registration, the browser shows the form, the application validates and processes the submission, and the database stores the accepted record.

These are logical responsibilities. They need not be three physical computers.

### Examination Questions

**Explain client-server, three-tier web architecture, and their difference.** (marks not shown)[^pyq-02]

**Answer.** In client-server computing, a client sends a request and a server processes it and returns a response. Three-tier web architecture divides the system into a presentation tier for interaction, an application tier for processing/business rules, and a data tier for persistent storage. For example, a browser submits a registration to an application, which stores it in a database and returns confirmation. Three-tier architecture organises client-server communication by separating presentation, application processing and storage, as shown in the diagram above.

---

## 4. Web Protocols, Internet Standards and MIME

A **protocol** defines communication rules. Standards allow browsers and servers from different suppliers to work together.

IETF publishes Internet protocol specifications. W3C develops many web standards, while WHATWG maintains the HTML Living Standard.

| TCP/IP layer | Main responsibility | Examples |
| --- | --- | --- |
| Application | Rules for a particular service. | HTTP for web resources; DNS for domain-name resolution. |
| Transport | Transfer between applications. | TCP gives reliable, ordered delivery; UDP does not give TCP's delivery guarantees. |
| Internet | Addressing and routing between networks. | IP. |
| Network access/link | Transfer over the local network. | Ethernet or Wi-Fi. |

In the HTTP/1.1 model, HTTP defines the exchange, TCP transports it reliably, and IP handles addressing and routing. HTTPS protects communication using TLS.

**MIME (Multipurpose Internet Mail Extensions)** identifies content types. A response's `Content-Type` can be `text/html`, `text/css`, `image/png` or `application/javascript`.

A MIME type describes the content. A filename extension is part of its name.

---

## 5. Uniform Resource Locators (URLs)

A **URL (Uniform Resource Locator)** gives the address of a web resource. It tells the browser which access scheme to use, which server to contact and which resource to request.

For example:

`https://example.org:8443/books/list.html?topic=web#css`

| Part | Value | Meaning |
| --- | --- | --- |
| Scheme | `https` | How the resource is accessed. |
| Host | `example.org` | The server. |
| Port | `8443` | An explicit service port. |
| Path | `/books/list.html` | The resource on that server. |
| Query | `topic=web` | Query data. |
| Fragment | `css` | A location within the resource. |

The fragment is handled by the browser and is not sent in the HTTP request.

A relative URL such as `story.html` is resolved against the document's base URL.

---

## 6. HTTP Requests and Responses

**HTTP (Hypertext Transfer Protocol)** defines how a client requests a resource and how the server reports the result.

It is **stateless**: separate requests do not automatically become one remembered user session.[^http-overview]

A page may need several exchanges: first the HTML, then its stylesheets, images and scripts.

An HTTP/1.1 message contains:

1. A **start line**.
2. **Headers** describing the request or response.
3. A **blank line** ending the headers.
4. An optional **body** carrying content.

The request line gives the method, request target and version:

```http
GET /books/list.html?topic=web HTTP/1.1
Host: example.org:8443
Accept: text/html

```

The response begins with a version, status code and reason phrase:

```http
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 12

<h1>IWT</h1>
```

The illustrated body is 12 ASCII bytes without a trailing newline. `200` means success, `301` permanent redirection, `404` not found and `500` a server error.[^http-messages]

> HTTP defines the exchange. HTML is one type of content that it can carry.

### GET and POST

| GET | POST |
| --- | --- |
| Requests a representation of a resource. | Submits data for processing. |
| An HTML GET form places data in the URL query. | Places submitted data in the request body. |
| Intended for retrieval without changing server state. | Commonly used to create or submit information. |

POST does not itself encrypt data. HTTPS supplies transport protection.

### Examination Questions

**Differentiate GET and POST. JSP tags are excluded.** (1 mark)[^pyq-03]

**Answer.** GET requests a representation of a resource; HTML GET forms put their data in the URL query. POST submits data in the request body for processing.

---

## 7. Persistent and Non-Persistent Connections

HTTP exchanges use network connections. The distinction is whether a connection is closed after one exchange or reused for more exchanges.

A **non-persistent connection** carries one request-response exchange and then closes.

A **persistent connection** stays open for further exchanges, so the browser does not need to establish a new connection for every resource. HTTP/1.1 uses persistence by default unless the connection is closed.

---

## 8. Web Caching and Proxy Servers

A **web cache** stores reusable responses. It can serve a fresh copy without downloading it again, or ask the server whether an older copy has changed.

Caching reduces delay, network traffic and server work. A stored copy is not permanently valid.

A **proxy** forwards exchanges between client and server. It may cache responses or apply access controls, but need not cache everything.

A browser cache is local to the browser; a proxy cache is at an intermediary.

> Persistence reuses a connection. Caching reuses a response. A proxy forwards the exchange.

### Additional Practice

**Original question · Suggested 4 marks.** Explain persistent connections and proxy caching, and state one benefit of each.

**Answer.** A persistent connection carries multiple HTTP exchanges over one TCP connection, reducing repeated setup overhead. A proxy cache stores reusable server responses between clients and origin servers. It can serve a fresh copy, reducing network traffic and response time; otherwise it forwards or revalidates the request. Persistence and caching can work together, but solve different problems.

---

## 9. Cyber Laws

**Cyber laws** govern activity involving computers, networks and electronic communication. They provide accountability for electronic transactions and misuse such as unauthorised access, identity theft and online fraud.

In India, the Information Technology Act, 2000 provides a central framework for electronic records/signatures and specified computer-related offences.[^cyber-law]

For this syllabus, know the purpose and examples. Detailed penalties and case law are outside the present treatment.

---

## 10. HTML and Document Structure

**HTML (HyperText Markup Language)** describes the structure and meaning of a page.

An element usually has an opening tag, content and a closing tag. Attributes add information about the element, such as a link’s destination or an image’s location. Void elements such as `img`, `meta` and `br` have no closing tag.

### The Head and Body

The `head` contains information about the page. The `body` contains the page content presented to the reader.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="description" content="IWT revision">
  <title>IWT study page</title>
  <base href="https://example.org/course/">
  <link rel="stylesheet" href="style.css">
  <style>h1 { color: navy; }</style>
  <script src="app.js" defer></script>
</head>
<body>
  <!-- This comment is not rendered as page text. -->
  <h1>Internet and Web Technology</h1>
  <p>Welcome to the course.</p>
</body>
</html>
```

The `doctype` selects standards mode. `title` names the browser tab, while `meta` supplies metadata.

`link` references an external resource, `style` contains CSS, and `script` includes JavaScript. The optional `base` changes relative-URL resolution: here, `style.css` resolves under the specified course URL.

A visible heading such as `h1` belongs to the body; it has a different role from `head`.

### Examination Questions

**Explain script-tag attributes. Detailed Java comparison is excluded; JavaScript characteristics are covered in [JavaScript: Statements, Comments and Values](#39-javascript-statements-comments-and-values).** (1 mark)[^pyq-04]

**Answer.** `src` specifies an external script; `defer` downloads an external classic script without blocking parsing and executes it after parsing; `async` executes it when ready without preserving script order. `type` identifies the script type, for example `module`; ordinary JavaScript can omit it. Historical `language` is obsolete.

---

## 11. HTML Text Formatting

HTML gives text a structure and meaning. Use `h1`–`h6` for heading levels, `p` for paragraphs and `br` for a line break within a passage. Layout and spacing belong in CSS rather than repeated line breaks.

`strong` marks importance and `em` marks emphasis. `b` and `i` can mark text without those meanings. `sub`, `sup`, `mark`, `small`, `del` and `ins` provide common formatting and annotations.

```html
<h1>Web revision</h1>
<p><strong>Remember:</strong> H<sub>2</sub>O and x<sup>2</sup>.</p>
<p><em>Read the example.</em><br>Then write it yourself.</p>
```

The heading organises the passage; `strong` and `em` express meaning, while subscripts and superscripts format the formulae.

---

## 12. HTML Lists

A **list** groups related items. Choose its type according to whether the items form a sequence, an unordered collection or pairs of terms and descriptions.

| List | Structure and purpose |
| --- | --- |
| Unordered | `ul` contains `li` items whose order is not essential. |
| Ordered | `ol` contains `li` items in a sequence. |
| Description | `dl` contains terms in `dt` and descriptions in `dd`. |

```html
<ul><li>HTML</li><li>CSS</li></ul>
<ol><li>Plan</li><li>Implement</li><li>Test</li></ol>
<dl><dt>HTTP</dt><dd>A web request-response protocol.</dd></dl>
```

---

## 13. Hyperlinks and Anchor Navigation

An **anchor** creates a link to another resource or to a location within the current page. Its `href` attribute supplies the destination; the text or image between `<a>` and `</a>` becomes clickable.

```html
<a href="story.html">Read the travel story</a>
<a href="#contact">Go to contact details</a>
<h2 id="contact">Contact details</h2>
```

The first link opens another page. The second uses a fragment identifier to move to the element with `id="contact"`. An image can also be placed inside an anchor, as in the travel-site examination answer under [Website Layout and Complete Page Design](#38-website-layout-and-complete-page-design).

### Examination Questions

**Explain anchor navigation and scrolling with an example.** (2 marks)[^pyq-07]

**Answer.** `<a href="story.html">Story</a>` opens another document. `<a href="#contact">Contact</a>` navigates to an element such as `<h2 id="contact">Contact</h2>` within the document. The fragment causes the browser to move to that target.

---

## 14. Images in HTML

An **image** adds visual content to a page. Its `src` gives the resource location, while `alt` provides a text alternative when the image cannot be seen.

```html
<img src="puri.jpg" alt="Beach at Puri" width="300" height="180">
```

`width` and `height` specify the dimensions. `alt` is an alternative to the image, not a tooltip; `title` may supply advisory text. Place the image inside an anchor to make it clickable.

### Examination Questions

**Give image syntax and explain its attributes.** (2 marks)[^pyq-06]

**Answer.** `<img src="puri.jpg" alt="Beach at Puri" width="300" height="180">`. `src` is the image URL, `alt` is alternative text, and `width`/`height` set dimensions. It is a void element and needs no end tag.

---

## 15. Video in HTML

The **video element** embeds playable video in a web page. It can provide playback controls, a preview image and alternative media sources.

```html
<video controls width="320" poster="preview.jpg">
  <source src="tour.mp4" type="video/mp4">
  Your browser does not support this video.
</video>
```

`controls` enables playback controls, `poster` supplies the preview image, and `source` identifies a video file and its MIME type. The text inside `video` is fallback content.

---

## 16. HTML Tables

A table presents data whose meaning depends on rows and columns.

`table` encloses it, `tr` creates a row, `th` marks a header cell and `td` a data cell. `caption` supplies a title.

`colspan` spans columns and `rowspan` spans rows. For example, `<tr><td colspan="2">Total</td></tr>` places one cell across two columns.

These attributes describe structure. CSS controls borders, padding, spacing and alignment.

### Examination Questions

**Write HTML for the pictured Roll No./Student Name/Subject Name table.** (3 marks)[^pyq-09]

**Answer.**

```html
<style>
  table { border-collapse: collapse; }
  th, td { border: 1px solid black; padding: 4px; }
</style>
<table>
  <tr><th>Roll No.</th><th>Student Name</th><th>Subject Name</th></tr>
  <tr><td>1</td><td>Ram</td><td>Physics</td></tr>
  <tr><td>2</td><td>Shyam</td><td>Math</td></tr>
  <tr><td>3</td><td>Murli</td><td>Chemistry</td></tr>
</table>
```

**Explain tags/attributes for HTML/CSS tables with examples.** (2 marks)[^pyq-10]

**Answer.** `table`, `tr`, `th` and `td` define the table, rows, header and data cells. `colspan="2"` spans two columns and `rowspan="2"` two rows. `table { border-collapse: collapse; }` and `th, td { border: 1px solid; padding: 4px; }` style the table. The table in the preceding answer demonstrates the row and cell structure.

---

## 17. HTML Frames and Iframes

An **iframe** embeds a separate document inside a page:

```html
<iframe src="story.html" title="Travel story"
        style="width: 100%; height: 180px; border: 1px solid black;"></iframe>
```

A DIV groups content in the same document; an iframe displays another document.

The syllabus also names historical frames. Recognise `<frameset cols="25%,75%"><frame src="menu.html"><frame src="main.html"></frameset>`: the frameset replaced the normal body in that older document form.

`frameset` and `frame` are obsolete in HTML5. Use an iframe for the retained layout question.[^frames]

---

## 18. HTML Forms

A **form** collects related input. Its `action` identifies the receiving resource and its `method` determines the submission method.

Controls normally need a `name` to contribute submitted values. An `id` instead identifies an element in the document.

```html
<form action="/register" method="post">
  <label>Name <input name="student" required></label>
  <label>Course <select name="course"><option>IWT</option></select></label>
  <label><input type="checkbox" name="updates" value="yes">Send updates</label>
  <label>Message <textarea name="message"></textarea></label>
  <button type="submit">Register</button>
</form>
```

A label explains a control. Radio buttons with the same name represent alternatives; a checkbox represents an independent choice. Use `select` for options and `textarea` for multiline text.

A submit button initiates submission. `type="button"` performs only its programmed action.

HTML constraints and JavaScript can check input, but the receiving server must validate it again. The complete process is developed under [JavaScript Forms and Validation](#61-javascript-forms-and-validation).

### Examination Questions

**Retain the HTML registration form with first/last name, email, password, gender radio buttons and submit.** (retained portion; marks not separately given)[^pyq-12]

**Answer.**

```html
<form action="/register" method="post">
  <label>First name <input name="firstName" required></label>
  <label>Last name <input name="lastName" required></label>
  <label>Email <input type="email" name="email" required></label>
  <label>Password <input type="password" name="password" required></label>
  <fieldset><legend>Gender (optional)</legend>
    <label><input type="radio" name="gender" value="female">Female</label>
    <label><input type="radio" name="gender" value="male">Male</label>
    <label><input type="radio" name="gender" value="other">Other</label>
  </fieldset>
  <button type="submit">Submit</button>
</form>
```

The action is an illustrative endpoint, not an implementation. Servlet lifecycle, Java code, deployment descriptors and database-table creation from the original question are excluded.

**Retain the explicitly requested `index.html` login page.** (marks not shown)[^pyq-13]

**Answer.**

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>Login</title></head>
<body><form action="/login" method="post">
  <label>Username <input name="username" required></label>
  <label>Password <input type="password" name="password" required></label>
  <button type="submit">Log in</button>
</form></body></html>
```

This collects the credentials; authenticating them requires a server. The original servlet and `web.xml` portions are excluded.

---

## 19. CSS and Stylesheets

**CSS (Cascading Style Sheets)** controls presentation: colours, text, spacing and layout.

A rule such as `p { color: navy; }` has a selector (`p`) and a declaration (`color: navy`). The selector chooses elements; the declaration supplies a property and value.

### Inline, Internal and External CSS

| Method | Example | Applies to |
| --- | --- | --- |
| Inline | `<p style="color: navy;">Hello</p>` | One element. |
| Internal | `<style>p { color: navy; }</style>` in `head` | The current document. |
| External | `<link rel="stylesheet" href="site.css">` | Documents linking to that stylesheet. |

An external stylesheet lets several pages share one design.

### Examination Questions

**Explain ways of using CSS in HTML, with examples.** (2 marks)[^pyq-15]

**Answer.** Inline CSS uses the `style` attribute, as in `<p style="color: navy;">Hello</p>`. Internal CSS uses a rule such as `<style>p { color: navy; }</style>` in `head`. External CSS uses `<link rel="stylesheet" href="site.css">`, with the rule in that stylesheet, allowing several pages to share it.

---

## 20. CSS Selectors and Combinators

A **CSS selector** identifies the elements to which a rule applies. A selector can target a type of element, a reusable class, an ID or an attribute. **Combinators** narrow the selection using relationships in the document.

| Selector | Meaning |
| --- | --- |
| `p`, `.note`, `#result`, `*` | Element, class, ID and universal selector. |
| `h1, h2` | Both sets of headings. |
| `article p`, `article > p` | Descendant paragraph; direct-child paragraph. |
| `h2 + p`, `h2 ~ p` | Next sibling paragraph; later sibling paragraphs with the same parent. |
| `input[type="email"]`, `[required]` | Matching attribute value; presence of an attribute. |
| `[href^="https"]`, `[href$=".pdf"]`, `[class~="note"]` | Starts with, ends with, or contains a space-separated word. |

A class can be shared; an ID should identify one element. Commas group selectors, while combinators express relationships.

`p.note` means a paragraph with that class. `.note p` means a paragraph inside an element with that class.

### Examination Questions

**Name the selector used to specify a group of elements and justify it.** (3 marks)[^pyq-16]

**Answer.** A **class selector** applies a shared style to a group of elements assigned the same class: `.notice { color: red; }` matches both `<p class="notice">Exam</p>` and `<h2 class="notice">Revision</h2>`. Unlike an ID, a class is reusable across elements. If “group” is used to mean a **grouping selector**, explain the comma form too: `h1, h2, p { color: red; }` applies one rule to several selector groups. The printed question does not distinguish these two meanings; state the interpretation rather than silently guessing.

---

## 21. CSS Specificity

**Specificity** resolves competing selectors when their declarations are otherwise comparable. Compare IDs first, then classes/attributes/pseudo-classes, then elements/pseudo-elements. If priorities tie, the later rule wins.[^specificity]

```html
<style>
  p { color: blue; }
  .note { color: green; }
  #result { color: red; }
</style>
<p id="result" class="note">This text is red.</p>
```

The paragraph is red because `#result` has greater specificity.

Normal inline styling outranks normal stylesheet declarations. An applicable `!important` declaration can override a normal inline declaration. Therefore, placement alone does not decide every conflict.

---

## 22. CSS Pseudo-Classes and Pseudo-Elements

A **pseudo-class** selects an element in a state or relationship, such as `a:hover`, `input:focus`, `a:visited` or `li:first-child`.

A **pseudo-element** selects part of an element or generates content, such as `::first-line`, `::first-letter`, `::selection`, `::before` or `::after`.

```css
a:hover { color: red; }
p::first-letter { font-size: 2em; }
p::first-line { font-weight: bold; }
.notice::before { content: "Note: "; }
.notice::after { content: " *"; }
::selection { background: gold; }
```

> A pseudo-class describes an element's state or relationship. A pseudo-element addresses part of it or generated content.

`::before` and `::after` normally need `content` to become visible. The double colon distinguishes pseudo-elements from pseudo-classes.

### Examination Questions

**Define a pseudo-element and explain CSS pseudo-elements.** (2 marks)[^pyq-17]

**Answer.** A pseudo-element styles a selected part of an element. `::first-line` styles its first formatted line and `::first-letter` its first letter; `::before`/`::after` insert generated content; `::selection` styles selected text. For example, `p::first-letter { color: red; }`.

---

## 23. CSS Colours and Backgrounds

CSS can set the colour of text and paint a colour or image behind an element. These are separate choices: `color` affects the text, while `background-*` properties control its background.

`color` sets text colour. Colours may be named (`navy`), hexadecimal (`#003366`), RGB (`rgb(0,51,102)`) or include transparency (`rgba(0,51,102,0.5)`).

Background properties paint behind the content:

```css
body {
  color: #123;
  background-color: #eef6ff;
  background-image: url("paper.png");
  background-repeat: no-repeat;
  background-position: center top;
  background-size: cover;
  background-attachment: fixed;
}
/* Alternative shorthand for these background settings: */
.banner { background: #eef6ff url("paper.png") center top / cover no-repeat fixed; }
```

`repeat` tiles an image; `no-repeat` prevents tiling. `cover` fills the area and may crop the image. The usual `scroll` attachment moves with the element; `fixed` uses the viewport.

The shorthand can reset omitted background properties. An HTML image contributes content; a CSS background supplies presentation behind it.

### Examination Questions

**Explain CSS background properties with examples.** (2 marks)[^pyq-18]

**Answer.** `background-color: lightblue` sets a color; `background-image: url("paper.png")` supplies an image; `background-repeat: no-repeat` prevents tiling; `background-position: center` positions it; `background-attachment: fixed` keeps it fixed during scrolling. These can be combined, for example `background: lightblue url("paper.png") no-repeat center fixed;`.

---

## 24. The CSS Box Model and Units

The **box model** places padding around content, a border around the padding, and margin outside the border:

```text
margin -> border -> padding -> content -> padding -> border -> margin
```

```css
.card {
  width: 200px;
  padding: 10px;
  border: 2px solid navy;
  margin: 15px;
}
```

With default `content-box` sizing, the border-box width is `200 + 20 + 4 = 224px`. Including horizontal margins gives `254px`.

$$
W_{\text{border box}} = W_{\text{content}} + P_{\text{left}} + P_{\text{right}} + B_{\text{left}} + B_{\text{right}}.
$$

With `box-sizing: border-box`, the declared width includes content, padding and border. **Margin stays outside the declared width in both models.** A visible border also needs a style such as `solid`.

| Unit | Relative to |
| --- | --- |
| `px` | A CSS pixel. |
| `%` | The relevant reference dimension. |
| `em` | Font size; the parent's font size when setting `font-size`. |
| `rem` | Root font size. |
| `vw`, `vh` | Percentages of viewport width and height. |

Four spacing values mean top/right/bottom/left. Two mean vertical/horizontal.

### Additional Practice

**Original question · Suggested 3 marks.** A content-box element has width 180px, padding 8px, border 1px and margin 10px on every side. Find its border-box width and total horizontal space.

**Answer.** Border-box width = `180 + 2(8) + 2(1) = 198px`. Total horizontal space including margins = `198 + 2(10) = 218px`. Padding lies inside the border; margin lies outside it.

---

## 25. CSS Fonts

**Font properties** control the typeface, size, weight and style of text. `line-height` controls the spacing of its lines. Together, these properties make headings and body text readable.

```css
body { font-family: Arial, sans-serif; font-size: 16px; line-height: 1.5; }
h1 { font-weight: bold; font-style: normal; }
```

The browser tries Arial first and uses a generic sans-serif font if it is unavailable. The heading is bold and upright.

---

## 26. CSS Link Styling

Links can change appearance according to their **state**. Styling these states helps users recognise available links and see which one they are interacting with.

```css
a:link { color: navy; }
a:visited { color: purple; }
a:hover, a:focus { text-decoration: underline; }
a:active { color: red; }
```

These pseudo-classes represent an unvisited link, a visited link, hover/focus and activation. Keep `:hover` after `:visited`, and `:active` after `:hover`, so equal-priority rules produce the intended result.

---

## 27. Icons and CSS

An **icon** is a small visual symbol. It can be an image or a text symbol styled with CSS; a separate icon library is unnecessary for these examples.

```css
.icon { color: navy; font-size: 1.2em; }
```

`<span class="icon" aria-hidden="true">&#9733;</span> Favourite` displays a navy star beside its text label.

---

## 28. CSS List Styling

CSS controls a list’s marker and its position. **List styling** changes presentation while the HTML list retains its structure.

```css
ul { list-style-type: square; list-style-position: inside; }
```

The items receive square markers placed inside their content boxes. `list-style-image: url("bullet.png")` supplies image bullets, while `list-style` combines list settings.

---

## 29. CSS Table Styling

CSS gives a table its borders, cell spacing and alignment. These properties make tabular data easier to read without changing its row-and-column structure.

```css
table { width: 100%; border-collapse: collapse; }
th, td { border: 1px solid #777; padding: 6px; text-align: left; }
```

Cell padding lies inside a cell. `border-spacing` separates cells in the separated-border model; `border-collapse: collapse` instead merges adjacent borders.

---

## 30. CSS Display and Overflow

The **display** property determines how an element takes part in page layout. **Overflow** determines what happens when its content is larger than the available box.

`block` normally starts a new line, `inline` flows with text, and `inline-block` flows inline while accepting dimensions.

`display: none` removes the layout box. `visibility: hidden` preserves its space. For excess content, `overflow: auto` provides scrolling, `hidden` clips and `visible` allows overflow.

---

## 31. CSS Positioning and Alignment

The **position** property controls whether an element follows normal document flow or is placed using a positioning reference. Offsets such as `top` and `left` are interpreted according to the chosen positioning mode.

| Position setting | Effect |
| --- | --- |
| `static` | Normal flow. |
| `relative` | Offset while retaining the original space. |
| `absolute` | Removed from flow; usually placed against the nearest positioned ancestor's containing block. |
| `fixed` | Normally placed against the viewport. |
| `sticky` | Normal behaviour until a scrolling threshold is reached. |

Use `text-align: center/right` for inline content and `margin: auto` to centre a block with a suitable width. `vertical-align: middle` applies to inline-level or table-cell content, not arbitrary block boxes.

---

## 32. CSS Float, Clear and Multiple Columns

A **float** places an element to one side so that surrounding inline content can wrap beside it. **Clear** controls whether a later element may sit beside earlier floats. Multiple-column properties instead divide one content area into reading columns.

```css
.reading { column-count: 2; column-gap: 2rem; column-rule: 1px solid #aaa; }
.picture { float: left; margin-right: 1rem; }
.next { clear: both; }
```

The image floats to the left, while `.next` starts clear of earlier floats. In `.reading`, `column-count` creates two columns, `column-gap` sets the separation, and `column-rule` draws a line between them.

---

## 33. CSS Navigation Bars, Dropdowns and Image Galleries

A navigation bar presents links; a dropdown reveals subordinate links; a gallery repeats image/link items. Form styles make labels and fields easier to scan.

```html
<style>
  nav > ul { list-style: none; padding: 0; }
  nav li { display: inline-block; position: relative; }
  nav a { display: block; padding: 8px; }
  .submenu { display: none; position: absolute; background: white;
             list-style: none; padding: 0; }
  li:hover > .submenu, li:focus-within > .submenu { display: block; }
  .gallery a { display: inline-block; margin: 8px; }
  .gallery img { width: 150px; border: 1px solid; }
  label { display: block; margin: 8px 0; }
  input { padding: 6px; border: 1px solid #777; }
</style>
<nav><ul><li><a href="#sites">Destinations</a><ul class="submenu">
  <li><a href="puri.html">Puri</a></li>
</ul></li></ul></nav>
<div class="gallery" id="sites">
  <a href="puri.html"><img src="puri.jpg" alt="Puri"></a>
</div>
```

The positioned parent provides a reference for the absolute submenu. The submenu is hidden until hover or focus reveals it. Gallery images use inline-block links.

---

## 34. CSS Opacity and Text Effects

**Opacity** controls the transparency of an entire element, including its contents: `0` is fully transparent and `1` is fully opaque. An alpha background colour affects only the background. **Text effects** improve the presentation of text through shadows, wrapping or an ellipsis.

```html
<style>
  .faded { opacity: 0.5; }
  .heading { text-shadow: 1px 1px 2px #aaa; }
  .short { width: 12em; white-space: nowrap; overflow: hidden;
           text-overflow: ellipsis; }
  .wrap { overflow-wrap: anywhere; }
</style>
<p class="faded">Half opacity</p>
<h2 class="heading">Revision</h2>
<p class="short">A long sentence that does not fit in this narrow area.</p>
<p class="wrap">averylongwordthatmustwrapinsideitscontainer</p>
```

The heading receives a shadow. The narrow `.short` paragraph stays on one line and shows an ellipsis when clipped; this requires a constrained width and hidden overflow. `.wrap` allows a long unbroken word to wrap within its container.

---

## 35. CSS Animations

A **CSS animation** changes selected property values over time. A named `@keyframes` rule defines the changes, and the `animation` property applies that rule to an element.

```html
<style>
  @keyframes highlight { from { background: white; } to { background: gold; } }
  .notice { animation: highlight 2s infinite alternate; }
</style>
<p class="notice">Exam notice</p>
```

The background changes from white to gold over two seconds. `infinite` repeats the animation, and `alternate` reverses its direction on successive runs. The keyframe name connects the element to the animation; the duration determines how long one run takes.

---

## 36. CSS Tooltips

A **tooltip** reveals a short explanation when the user interacts with an element. CSS can hide the explanatory text initially and show it when the trigger is hovered or focused.

```html
<style>
  .tip { position: relative; }
  .tip span { display: none; position: absolute; top: 100%; left: 0;
              padding: 4px; background: black; color: white; }
  .tip:hover span, .tip:focus span { display: block; }
</style>
<button class="tip" type="button">Help<span>Enter your student name.</span></button>
```

The relatively positioned button provides the reference for the absolutely positioned tooltip. Hovering over the button or giving it keyboard focus changes the span from hidden to visible.

---

## 37. CSS Counters

A **CSS counter** automatically numbers repeated content. The counter is reset for a container, incremented for each item, and displayed using generated content.

```html
<style>
  .steps { counter-reset: step; }
  .steps p::before { counter-increment: step; content: counter(step) ". "; }
</style>
<div class="steps"><p>Read</p><p>Practise</p></div>
```

`counter-reset` starts `step` at zero. Each paragraph increments it, and `::before` displays the current value followed by a full stop: “1. Read”, then “2. Practise”.

---

## 38. Website Layout and Complete Page Design

A **website layout** arranges a page into areas such as a header, navigation, main content and footer. HTML identifies these areas, while CSS determines their dimensions, spacing, backgrounds and alignment. The same stylesheet can keep linked pages visually consistent.

For a construction question, first identify the required content and links. Then write the HTML structure and apply the requested CSS properties. Check that navigation works and that every pictured region or explicitly requested field is represented. The following answers combine the HTML and CSS concepts studied above.

### Examination Questions

**Display favourite holiday destinations as images linking to story pages; use external CSS for headings, images, links, margins and backgrounds.** (10 points)[^pyq-08]

**Answer.** The site consists of a destination index, linked story pages and one shared stylesheet. The named images are illustrative resources used by the answer.

`travel.html`:

```html
<!doctype html>
<html lang="en">
<head><meta charset="utf-8"><title>My travels</title>
<link rel="stylesheet" href="travel.css"></head>
<body>
<h1>My favourite destinations</h1>
<a href="puri.html"><img src="puri.jpg" alt="Puri beach">Puri</a>
<a href="konark.html"><img src="konark.jpg" alt="Konark temple">Konark</a>
</body></html>
```

`puri.html`:

```html
<!doctype html>
<html lang="en">
<head><meta charset="utf-8"><title>Puri story</title>
<link rel="stylesheet" href="travel.css"></head>
<body><h1>My visit to Puri</h1>
<p>I watched the sunrise and walked beside the sea.</p>
<a href="travel.html">Back to destinations</a></body></html>
```

`konark.html`:

```html
<!doctype html>
<html lang="en">
<head><meta charset="utf-8"><title>Konark story</title>
<link rel="stylesheet" href="travel.css"></head>
<body><h1>My visit to Konark</h1>
<p>I admired the carved wheels and learned about the Sun Temple.</p>
<a href="travel.html">Back to destinations</a></body></html>
```

`travel.css`:

```css
body { margin: 2rem; background: #eef6ff; font-family: sans-serif; }
h1 { color: navy; }
a { display: inline-block; margin: 1rem; color: #064b75; }
a:hover { color: #a33; }
img { display: block; width: 240px; height: 160px; border: 2px solid navy; }
```

The anchors make each destination image clickable; the shared stylesheet gives all pages consistent styling. Together, the pages provide the destination navigation and the corresponding travel stories.

**Design an HTML/CSS website about tourism sites of Odisha.** (5 marks)[^pyq-20]

**Answer.** The following single-page site provides a heading, destination information, navigation and CSS styling. The named images are illustrative resources for the page.

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>Explore Odisha</title>
<style>
  body { margin: 2rem; font-family: sans-serif; background: #eef6ff; }
  nav a { margin-right: 1rem; }
  article { padding: 1rem; margin: 1rem 0; border: 1px solid navy; }
  img { width: 240px; max-width: 100%; }
</style></head><body>
<header><h1>Explore Odisha</h1></header>
<nav><a href="#puri">Puri</a><a href="#konark">Konark</a></nav>
<article id="puri"><h2>Puri</h2>
<img src="puri.jpg" alt="Puri beach"><p>Visit its beach and temple town.</p></article>
<article id="konark"><h2>Konark</h2>
<img src="konark.jpg" alt="Konark Sun Temple"><p>Explore the Sun Temple.</p></article>
<footer>Plan your Odisha visit.</footer>
</body></html>
```

**Explain CSS usage and reproduce the pictured layout using the box model and different backgrounds. Retain float menu, centred header, right-aligned content/footer and inline-styled iframe; exclude the `marquee` instruction.** (marks not shown)[^pyq-21]

**Answer.** CSS controls presentation separately from HTML structure, making styles reusable. This layout uses a floated left column, an offset right column, and a cleared footer; borders/padding define the boxes.

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>CSS layout</title>
<style>
  * { box-sizing: border-box; }
  .page { width: 90%; margin: auto; border: 1px solid; }
  aside { float: left; width: 30%; background: #e6f2ff; }
  .menu { height: 200px; padding: 12px; border-bottom: 1px solid; }
  .right { margin-left: 30%; border-left: 1px solid; }
  header { height: 70px; text-align: center; background: #fff3cc;
           border-bottom: 1px solid; padding: 12px; }
  main { min-height: 300px; text-align: right; padding: 12px; background: #f2fff2; }
  footer { clear: both; border-top: 1px solid; padding: 12px;
           text-align: right; background: #eee; }
</style></head><body><div class="page">
<aside><div class="menu">Float Menu</div>
<iframe title="Notices" srcdoc="<p>Institute notices</p>"
        style="display: block; width: 100%; height: 170px; border: 0;"></iframe>
</aside>
<div class="right"><header>Header - Centre Align</header>
<main>Body content aligned right</main></div>
<footer>Footer - Right Align</footer>
</div></body></html>
```

---

# Module II - JavaScript, DOM, BOM and advanced concepts (10 hours)

Learn the language concepts first, then use them to manipulate the document, handle events and validate forms. Advanced JavaScript remains outlined for later writing.

## 39. JavaScript: Statements, Comments and Values

JavaScript makes a page respond to the user. It can calculate a bill, check a form or change a message after a button is clicked.

> HTML gives the page structure. CSS controls its appearance. JavaScript supplies its behaviour.

A **statement** performs an action. An **expression** produces a value.

In `const total = 3 * 200;`, multiplication produces a value and the declaration gives it a name. `//` begins a single-line comment; `/* ... */` encloses a block comment.

```javascript
const price = 200;          // This binding will not be reassigned.
let quantity = 2;           // It may change.
quantity = quantity + 1;
const total = price * quantity;
console.log(total);         // 600
```

`quantity` changes from 2 to 3, so `total` becomes 600.

JavaScript is **dynamically typed**: values have types, and a reassignable variable may later hold a different type.

Common values are numbers (`12`), strings (`"IWT"`) and booleans (`true`). `undefined` usually means an uninitialised or missing value; `null` can represent an intentional absence. Objects and arrays hold related data.

`12` and `"12"` are different: one is a number and the other is text.

### Examination Questions

**Retain introductory JavaScript characteristics and script attributes; exclude detailed Java study.** (retained portion; original 1+1 marks)[^pyq-23]

**Answer.** JavaScript is dynamically typed and can run in the browser to handle events, validate forms and update the document. It is a separate language, not a variant of Java. An external script is included with `<script src="app.js" defer></script>`. `src` gives its URL; `defer` waits until HTML parsing finishes before executing an external classic script. `async` executes an external script when ready. The script-attributes answer is in [HTML and Document Structure](#10-html-and-document-structure). No separate retained-only mark total is inferred for the comparison.

---

## 40. JavaScript Variables and Scope

**Variables** give names to values so that a program can use and update them. JavaScript provides `var`, `let` and `const`; choosing between them depends on where a name should be available and whether it may be reassigned.

**Scope** means where a variable can be accessed. A function creates a scope; a block groups statements inside braces.

| Declaration | Scope | Reassignment | Same-scope redeclaration | Before declaration is reached |
| --- | --- | --- | --- | --- |
| `var` | Function, or global at top level | Allowed | Usually allowed with another `var` | Reads as `undefined`. |
| `let` | Block | Allowed | Not allowed | Throws `ReferenceError`. |
| `const` | Block | Not allowed; initial value required | Not allowed | Throws `ReferenceError`. |

The difference becomes visible after leaving a block:

```javascript
function scopeExample() {
  if (true) {
    var x = 1;
    let y = 2;
    console.log(y);        // 2: inside its block
  }
  console.log(x);          // 1: still inside x's function
  // console.log(y);       // Would throw ReferenceError here.
}
scopeExample();
```

`x` belongs to the function, while `y` belongs to the inner block.[^bindings]

A `const` prevents reassignment, not changes inside an object. `const item = { qty: 1 }; item.qty = 2;` is allowed; assigning a different object to `item` is not.

### Examination Questions

**Differentiate `let` and `var`.** (2 marks)[^pyq-22]

**Answer.** `let` is block-scoped, whereas `var` is function-scoped. `let` cannot be redeclared in the same scope; `var` generally can. A `var` binding can be read as `undefined` before its declaration is executed, while accessing `let` before initialisation throws an error. For example, in `if (true) { var a = 1; let b = 2; }`, `a` remains accessible in the enclosing function but `b` does not.

---

## 41. JavaScript Operators and Decisions

An **operator** combines, compares or changes values. A **decision statement** uses a condition to choose which statements run. These are the building blocks of the calculations and validation checks required in examination programs.

| Purpose | Operators |
| --- | --- |
| Arithmetic | `+`, `-`, `*`, `/`, `%` for remainder, `**` for powers. |
| Increment/decrement | `++`, `--`. |
| Assignment/update | `=`, `+=`, `-=`. |
| Comparison | `<`, `<=`, `>`, `>=`, `===`, `!==`. |
| Logical conditions | `&&`, `\|\|`, `!`. |

Strict equality avoids type conversion: `2 === "2"` is false, while `2 == "2"` is true. `typeof 12` gives `"number"`; `typeof "12"` gives `"string"`.

The `+` operator can also join text, so `"2" + 3` becomes `"23"`. Form values are strings: check for blank input, then use `Number(value)` before arithmetic. `Number("")` produces zero.

An `if/else` chooses a branch, the conditional operator expresses a short choice, and `switch` selects among cases:

```javascript
let marks = 65;
if (marks >= 40) {
  console.log("Pass");
} else {
  console.log("Fail");
}
const result = marks >= 40 ? "Pass" : "Fail";
switch (result) {
  case "Pass": console.log("Eligible"); break;
  default: console.log("Revise and retry");
}
```

Use parentheses when grouping might be unclear. These examples use ordinary small inputs; JavaScript numbers have finite precision.

---

## 42. JavaScript Functions

A **function** packages an operation so it can be used with different inputs. Parameters name the inputs inside the function. Arguments are the values supplied when calling it. `return` supplies the result and ends that call; without an explicit result, the function returns `undefined`.

```javascript
function cost(price, quantity) {
  const total = price * quantity;    // Local to this invocation
  return total;
}
console.log(cost(200, 3));           // 600
```

Here, `price` and `quantity` are parameters. `200` and `3` are arguments. The local `total` belongs to this call, and the caller receives 600.

---

## 43. JavaScript Objects, Methods and this

An **object** groups named properties. A property containing a function is a **method**.

Use `student.name` for a known property, or `student[key]` when the name comes from a variable. Assignment adds or updates a property; `delete student.phone` removes one.

For an ordinary call `object.method()`, `this` refers to the receiving object:

```javascript
const student = {
  name: "Anu",
  marks: 65,
  result: function () {
    return this.name + ": " + (this.marks >= 40 ? "Pass" : "Fail");
  }
};
console.log(student.result());       // Anu: Pass
```

Because the call is `student.result()`, `this.name` and `this.marks` refer to that student's properties.

> The value of `this` depends on the call. It is not universally fixed by where the function was written.

Also distinguish `result` from `result()`: the first refers to a function, while the second calls it. This matters when registering event handlers later.

### Examination Questions

**State the purpose of `this` in JavaScript, with an example.** (2 marks)[^pyq-24]

**Answer.** In `object.method()`, `this` refers to the object on which the method is called, allowing access to its properties. For example, `const s = { name: "Anu", show: function () { return this.name; } }; console.log(s.show());` prints `Anu`.

**Add a function to an object and access it with an example.** (2 marks)[^pyq-25]

**Answer.**

```javascript
const item = { price: 200, qty: 3 };
item.total = function () { return this.price * this.qty; };
console.log(item.total());          // 600
```

`total` is a function-valued property; `item.total()` invokes it, with `this` referring to `item`.

---

## 44. JavaScript Classes and Objects

A **class** describes objects that share a structure and behaviour. `new` creates an instance, and `constructor` initialises its data.

```javascript
class Student {
  constructor(name, marks) {
    this.name = name;
    this.marks = marks;
  }
  result() { return this.marks >= 40 ? "Pass" : "Fail"; }
}
const anu = new Student("Anu", 65);
const ravi = new Student("Ravi", 30);
console.log(anu.result(), ravi.result()); // Pass Fail
```

The two students share the same method, but each has its own name and marks. `anu.result()` uses Anu's marks; `ravi.result()` uses Ravi's. Changing one student's data does not change the other's.

### Additional Practice

**Original question · Suggested 3 marks.** Define a Student class with a constructor and a pass/fail method, and show two objects with different results.

**Answer.** The Student class above supplies a constructor, properties, a result method and two instances. `this.marks` selects the current instance's marks: 65 produces `Pass`, while 30 produces `Fail`. The threshold is an illustrative rule for this generated question, not a rule stated in a past paper.

---

## 45. JavaScript Inheritance

**Inheritance** lets a specialised class reuse a parent's behaviour. The following example extends the `Student` class from the preceding topic. `extends` names the parent. In a subclass constructor, `super(...)` calls the parent's constructor before using `this`.

```javascript
class ResearchStudent extends Student {
  constructor(name, marks, topic) {
    super(name, marks);
    this.topic = topic;
  }
}
const scholar = new ResearchStudent("Mina", 70, "Web usability");
console.log(scholar.name, scholar.result()); // Mina Pass
```

The research student reuses the parent's name, marks and result, then adds a topic. A subclass may also replace an inherited method with its own implementation.


---

## 46. JavaScript Strings

A **string** stores text. Character positions begin at zero, and `length` is a property: `"Web".length` is 3.

Strings are **immutable**: an operation produces a new string rather than changing the existing one. `" Web ".trim()` produces `"Web"` without changing the original value. `split(",")` separates text into an array, and `replace()` produces a replaced string.

The combined Math/String examination answer under [JavaScript Math and Random Numbers](#50-javascript-math-and-random-numbers) gives five further String methods with their results.

---

## 47. JavaScript Numbers

JavaScript represents ordinary numeric values using the **Number** type. Input read from a form is text, so a calculation often begins by converting that text to a number and checking the result.

`Number("12.5")` converts a whole numeric string. `parseInt("12", 10)` parses a decimal integer, while `parseFloat("12.5")` parses a floating-point value.

Check that a field is not blank before conversion. A conversion result alone does not prove that the user entered a number.

`Number.isNaN(value)` identifies the not-a-number value, and `Number.isFinite(value)` rejects infinity and NaN.

For display, `price.toFixed(2)` returns a string rounded to two decimal places. It does not create a new numeric type.

---

## 48. JavaScript Arrays

An **array** is an ordered collection with zero-based indices. For `const a = ["HTML", "CSS"];`, `a[0] === "HTML"` and `a.length === 2`.

`push()` and `pop()` add and remove at the end. A `const` array can still have its contents changed.

Follow the array through these operations:

```javascript
const a = [10, 20, 30];
console.log(a.join("-"));           // "10-20-30"; array unchanged
const removed = a.splice(1, 1, 25); // Remove one at index 1; insert 25
console.log(removed, a);            // [20], [10, 25, 30]
console.log(a.shift(), a);          // 10, [25, 30]
console.log(a.unshift(5), a);       // 3, [5, 25, 30]
```

| Operation | Effect | Return value |
| --- | --- | --- |
| `join(separator)` | Joins elements without changing the array. | A string. |
| `splice(start, count, ...items)` | Removes/inserts elements in place. | Removed entries. |
| `shift()` | Removes the first entry. | The removed value. |
| `unshift(...items)` | Inserts at the front. | The new length. |

Do not confuse `splice()` with `slice()`, which copies a portion.

### Examination Questions

**Explain `join()`, `splice()`, `shift()` and `unshift()`.** (2 marks)[^pyq-27]

**Answer.** `join(separator)` returns a string of joined array elements; `splice(start, count, ...items)` removes/inserts elements in place and returns removed elements; `shift()` removes/returns the first element; `unshift(...items)` inserts at the front and returns the new length. The sequential example above shows all four results.

---

## 49. JavaScript Date

A **Date object** represents a date and time. Its methods let a program extract calendar components or produce a readable date for display.

`new Date()` obtains the current date/time value. `getFullYear()`, `getMonth()` and `getDate()` obtain local calendar components.

Months begin at zero. Add one for a human-readable month number. `getDay()` gives the weekday from 0 to 6, not the day of the month.

`toLocaleDateString()` gives a readable local date.

### Examination Questions

**Write a function to display today's date in the browser.** (2 marks)[^pyq-28]

**Answer.**

```html
<p id="today"></p>
<script>
  function showToday() {
    document.getElementById("today").textContent = new Date().toLocaleDateString();
  }
  showToday();
</script>
```

This uses the browser's current local date and display format. No particular date is hard-coded.

---

## 50. JavaScript Math and Random Numbers

**Math** supplies numeric functions without constructing a Math object. The examples below include absolute value, square root and rounding.

`Math.random()` returns a value from 0 inclusive to 1 exclusive. For an integer from `low` to `high` inclusive, use:

`Math.floor(Math.random() * (high - low + 1)) + low`

Thus `Math.floor(Math.random() * 6) + 1` simulates a six-sided die.

### Examination Questions

**Give five JavaScript Math methods and five String methods with examples.** (1+1 marks)[^pyq-26]

**Answer.** The following examples give five Math methods and five String methods with their results:

| Math example | Result | String example | Result |
| --- | --- | --- | --- |
| `Math.abs(-4)` | `4` | `"Web".charAt(0)` | `"W"` |
| `Math.sqrt(25)` | `5` | `"Web".indexOf("e")` | `1` |
| `Math.floor(2.8)` | `2` | `"Web".substring(1, 3)` | `"eb"` |
| `Math.ceil(2.2)` | `3` | `"Web".toUpperCase()` | `"WEB"` |
| `Math.round(2.6)` | `3` | `"Web".toLowerCase()` | `"web"` |

---

## 51. JavaScript Loops

A **loop** repeats an operation while progressing towards an ending condition.

Identify its starting value, its condition and its update. A missing update may prevent termination; a wrong boundary may cause one extra or missing iteration.

| Loop | How it works |
| --- | --- |
| `for` | Keeps initialisation, condition and update together. |
| `while` | Tests the condition before each execution of the body. |
| `do...while` | Tests the condition after the body, so it runs at least once. |

```javascript
let total = 0;
for (let i = 1; i <= 3; i++) total += i;
console.log(total);                 // 6
let n = 2;
while (n > 0) { console.log(n); n--; } // 2, 1
let count = 0;
do { count++; } while (count < 1); // Executes once.
for (const value of [10, 20]) console.log(value); // Values
for (const key in { name: "Anu", marks: 65 }) console.log(key); // Property keys
```

`for...of` visits array values. `for...in` enumerates property keys and is not the usual choice for array values.

`break` ends a loop; `continue` skips to the next iteration. Begin a sum at zero and a factorial product at one. Prime testing must reject values below 2.

> “The first n primes” counts how many to find. “Primes up to n” limits their values.

### Examination Questions

**Find a number's factorial using input from a prompt dialog.** (2 marks)[^pyq-29]

**Answer.**

```javascript
const input = prompt("Enter a non-negative integer");
if (input !== null && input.trim() !== "") {
  const n = Number(input);
  if (!Number.isInteger(n) || n < 0) {
    alert("Enter a non-negative integer.");
  } else {
    let fact = 1;
    for (let i = 2; i <= n; i++) fact *= i;
    alert(n + "! = " + fact);
  }
}
```

For ordinary small exam inputs, `5` gives `120`; `0` gives `1` because the loop does not run. Prompt cancellation is distinguished from entering zero. Large-factorial arithmetic is not required by the question.

**Write `sum()` to find the sum of the first n prime integers, taking n from element `number` in form `f`.** (3 marks)[^pyq-30]

**Answer.** The function counts the primes it finds while testing candidates from 2 upward. A divisor greater than the square root is unnecessary because a composite has a factor no greater than its square root.

```html
<form name="f" onsubmit="sum(); return false;">
  <label>How many primes? <input name="number" type="number"
                                min="0" step="1" required></label>
  <button type="submit">Find sum</button>
</form><p id="primeResult"></p>
<script>
  function isPrime(value) {
    if (value < 2) return false;
    for (let d = 2; d * d <= value; d++) {
      if (value % d === 0) return false;
    }
    return true;
  }
  function sum() {
    const field = document.forms["f"].elements.namedItem("number");
    const n = Number(field.value);
    if (field.value.trim() === "" || !Number.isInteger(n) || n < 0) {
      document.getElementById("primeResult").textContent = "Enter a valid count.";
      return;
    }
    let found = 0, candidate = 2, total = 0;
    while (found < n) {
      if (isPrime(candidate)) { total += candidate; found++; }
      candidate++;
    }
    document.getElementById("primeResult").textContent = "Sum = " + total;
    return total;
  }
</script>
```

For `n = 5`, the selected numbers are 2, 3, 5, 7 and 11, so the result is 28. Do not stop at candidate 5: n is the count of primes, not the largest candidate.

---

## 52. JavaScript Regular Expressions

A **regular expression** describes a text pattern. It can check whether a mobile number contains only digits, for example.

A literal such as `/web/i` places the pattern between slashes. `i` ignores case; `g` requests multiple matches for operations such as replacement.

| Component | Meaning |
| --- | --- |
| `^`, `$` | Start and end of text. |
| `[0-9]` | One digit. |
| `+` | One or more repetitions. |
| `*`, `?` | Zero or more; zero or one. |
| `{n}` | Exactly n repetitions. |
| `.`, `\.` | Any character except a line terminator in ordinary mode; a literal full stop. |

`/[0-9]/` asks whether text contains a digit. `/^[0-9]+$/` requires the whole value to contain one or more digits.

```javascript
const digits = /^[0-9]+$/;
console.log(digits.test("0123"));     // true
console.log(digits.test("12a"));      // false
console.log("Web Technology".search(/technology/i)); // 4
console.log("web web".replace(/web/g, "IWT"));       // "IWT IWT"
```

`test()` belongs to a RegExp and returns a boolean. The string methods `search()` and `replace()` return the first match position (or `-1`) and a new string, respectively.

For repeated form checks, a plain anchored pattern without `g` avoids the retained `lastIndex` position used by global `test()` calls.

### Examination Questions

**Define RegExp and explain `search()`, `replace()` and `test()` with examples.** (2 marks)[^pyq-31]

**Answer.** A regular expression specifies a text-matching pattern. `"IWT".search(/W/)` returns `1`; `"IWT".replace(/W/, "Web")` returns `"IWebT"`; `/^[0-9]+$/.test("123")` returns `true`. The three operations locate, replace and test a match, respectively.

---

## 53. JavaScript Errors and Exception Handling

An **error** is a problem in the syntax, execution or logic of a program. **Exception handling** gives a program a controlled way to respond when an operation throws an exception. Recognising the kind of error helps determine whether to correct the code, handle a failed operation or fix the algorithm.

| Error | What happens | Example |
| --- | --- | --- |
| Syntax | Code cannot be parsed. | A missing bracket. |
| Runtime | Failure during execution. | An undeclared variable is used. |
| Logical | Code runs but gives the wrong result. | Solving “primes up to n” instead of “the first n primes”. |

A `try...catch` statement handles an exception raised during an operation. `throw` deliberately reports an invalid condition; `finally`, when present, runs a final action after the try/catch.

```javascript
function checkedDivide(a, b) {
  if (b === 0) throw new Error("Divisor must not be zero");
  return a / b;
}
try {
  console.log(checkedDivide(10, 0));
} catch (error) {
  console.log(error.message);       // Divisor must not be zero
} finally {
  console.log("Calculation attempt finished");
}
```

The explicit divisor check is important: ordinary numeric division such as `10 / 0` produces infinity rather than automatically throwing.

A catch block cannot repair a script that failed to parse in the first place.

---

## 54. JavaScript Debugging

**Debugging** means locating and correcting errors. Reproduce the problem, read the console message and line number, then inspect relevant values. `console.log()` helps trace them.

Browser breakpoints or `debugger;` let you pause and step through execution. After correcting the problem, retest normal input and boundaries such as zero or empty input.

### Examination Questions

**What is JavaScript debugging and how can it be done?** (2 marks)[^pyq-32]

**Answer.** Debugging is locating and correcting errors in JavaScript. Use the browser console to read errors and inspect values with `console.log()`. Use developer-tools breakpoints or `debugger` to pause and step through execution while watching variables, then correct and retest the code.

---

## 55. The HTML Document Object Model (DOM)

The **Document Object Model (DOM)** represents an HTML document as a tree of objects.

JavaScript uses that tree to find elements, change content and styles, or add and remove nodes.

```text
Document
└── html
    ├── head
    │   └── title
    └── body
        ├── h1
        │   └── text: "IWT"
        └── p
            └── text: "Revision"
```

The HTML file describes the initial document. The live DOM can change after parsing, so a button can add a paragraph without rewriting the HTML file.

The next topics develop selection, editing and node operations in order. A complete five-mark DOM answer appears under [DOM Nodes: Navigation, Creation and Removal](#58-dom-nodes-navigation-creation-and-removal).

---

## 56. Selecting HTML Elements with the DOM

DOM selection finds the element or collection that a script needs to work with. Select by ID when one element has a unique identity, or use a CSS selector when the selection depends on a class, tag or document relationship.

`document` is the entry point. `document.documentElement` refers to `html`; `document.head`, `document.body`, `document.title` and `document.forms` give familiar access points.

| Method | Result |
| --- | --- |
| `getElementById("result")` | One element, or `null`. |
| `getElementsByTagName("p")` | A live HTMLCollection. |
| `getElementsByClassName("note")` | A live HTMLCollection. |
| `querySelector("p.note")` | The first CSS-selector match, or `null`. |
| `querySelectorAll("p.note")` | A static NodeList of all matches. |

Call these methods on `document`. A failed single selection returns `null`; a multiple selection may return an empty collection.

Run the script after the relevant elements exist, for example after their HTML or through an external script with `defer`.

### Examination Questions

**Access HTML elements through CSS selectors using JavaScript.** (2 marks)[^pyq-34]

**Answer.** `querySelector()` selects the first CSS-selector match; `querySelectorAll()` selects all matches.

```html
<p class="note">One</p><p class="note">Two</p>
<script>
  document.querySelector("p.note").textContent = "First note";
  const notes = document.querySelectorAll("p.note");
  for (const note of notes) note.style.color = "navy";
</script>
```

---

## 57. Changing DOM Content, Attributes and Styles

After selecting an element, JavaScript can change what it contains and how it appears. The choice of property matters: plain text, HTML markup and a form control’s current value are different kinds of content.

Use `.textContent` for plain text, `.innerHTML` for markup, and an input or textarea's `.value` for its current value.

Use `getAttribute()`, `setAttribute()` and `removeAttribute()` for attributes. For example, `image.setAttribute("alt", "Puri beach")` changes alternative text.

```html
<p id="message" class="note">Original text</p>
<script>
  const message = document.getElementById("message");
  message.textContent = "Revision started";
  message.style.backgroundColor = "lightyellow";
  message.setAttribute("title", "DOM example");
</script>
```

The example selects a paragraph, then changes its text, background and title attribute.

A CSS property such as `background-color` becomes `backgroundColor` through `.style`. Classes can be changed with `classList.add()`, `remove()` and `toggle()`.

`.style` reflects inline declarations. `getComputedStyle(element).color` reads the resolved style, including stylesheet rules.

---

## 58. DOM Nodes: Navigation, Creation and Removal

A **node** can be a document, element, text or comment. Attributes can be accessed as attribute nodes, but are not ordinary child nodes.

| Node | `nodeType` |
| --- | --- |
| Element | `1` |
| Text | `3` |
| Comment | `8` |
| Document | `9` |

A text node's `nodeValue` holds its text. An element's `nodeValue` is `null`; use `.textContent` for its descendant text.

Navigation follows relationships such as `parentNode`, `childNodes`, `firstChild`, `lastChild`, `nextSibling` and `previousSibling`.

Whitespace can create text nodes. Therefore, `firstChild` may not be the first element.

For element-only navigation, use `parentElement`, `children`, `firstElementChild`, `lastElementChild`, `nextElementSibling` and `previousElementSibling`:

```html
<ul id="tasks"><li>Read</li><li>Practise</li></ul>
<script>
  const list = document.getElementById("tasks");
  const first = list.firstElementChild;
  console.log(first.textContent);           // Read
  console.log(first.nextElementSibling.textContent); // Practise
  console.log(first.parentElement === list);         // true
</script>
```

### Creating and Changing the Tree

A newly created node is not visible until it is inserted into the document.

`createTextNode()` creates plain text. `appendChild()` inserts at the end; `insertBefore(newNode, referenceNode)` inserts before a child.

`replaceChild(newNode, oldNode)` replaces a child, and `removeChild(child)` removes one:

```javascript
// Continue with the UL from the example above.
const item = document.createElement("li");
item.appendChild(document.createTextNode("Revise"));
list.appendChild(item);
const extra = document.createElement("li");
extra.textContent = "Check examples";
list.insertBefore(extra, item);
const replacement = document.createElement("li");
replacement.textContent = "Write answers";
list.replaceChild(replacement, extra);
list.removeChild(item);
// Final element texts: Read, Practise, Write answers.
```

Appending an already attached node moves it rather than copying it.

### Examination Questions

**Define HTML DOM; name three JavaScript methods for manipulating it and explain them with examples.** (5 marks)[^pyq-33]

**Answer.** The HTML DOM represents an HTML document as a tree of objects/nodes. JavaScript can use it to find elements, alter their content and add/remove nodes. Three useful methods are `getElementById()` to select an element, `createElement()` to create an element, and `appendChild()` to attach a node to a parent.

```html
<div id="content"></div>
<script>
  const container = document.getElementById("content"); // Select existing node.
  const paragraph = document.createElement("p");        // Create a detached p.
  paragraph.textContent = "Prepared using the DOM";     // Set its text.
  container.appendChild(paragraph);                    // Insert into the tree.
</script>
```

Initially the DIV is empty; afterwards it contains a paragraph. `createElement()` alone does not display anything: insertion into the document does. The example connects selection, creation and insertion in one operation.

---

## 59. DOM NodeLists and HTMLCollections

A **NodeList** is an indexed collection, accessed with `[i]` or `item(i)`, measured by `.length` and traversed with a loop. It is not an Array and may include non-element nodes.

`querySelectorAll()` returns a static NodeList; `childNodes` returns a live NodeList. `children`, `getElementsByTagName()` and `getElementsByClassName()` return HTMLCollections.

The example continues with the `list` variable and `<ul id="tasks">` from [DOM Nodes: Navigation, Creation and Removal](#58-dom-nodes-navigation-creation-and-removal).

```javascript
const snapshot = document.querySelectorAll("#tasks li");
const liveElements = list.children;
const before = snapshot.length;
const added = document.createElement("li");
added.textContent = "Review";
list.appendChild(added);
console.log(snapshot.length === before);     // true: snapshot membership unchanged
console.log(liveElements.length === before + 1); // true: live collection updated
```

> “Static” fixes the collection's membership. The nodes already in it still reflect edits to their contents.[^collections]

---

## 60. DOM Events and Event Listeners

An **event** reports an action such as a click, value change or form submission. A listener is the function that responds.

`addEventListener("click", handler)` registers a function. `handler()` would call it immediately. `onclick` provides one handler slot; `addEventListener` can register several listeners.

```html
<button id="change" type="button">Change message</button><p id="eventMessage"></p>
<script>
  document.getElementById("change").addEventListener("click", function (event) {
    document.getElementById("eventMessage").textContent = "Button activated";
    console.log(event.currentTarget.id); // change
  });
</script>
```

`click` reports activation, `input` reports value edits, and `change` reports a committed value change. `submit` reports form submission.

`keydown` and `keyup` respond to key actions; `load` reports resource loading. `DOMContentLoaded` reports that parsing has finished; deferred scripts can usually access elements without a separate readiness listener.

`mousedown` means a button was pressed and `mouseup` that it was released. `mouseover` and `mouseout` report entry and exit; movement across descendants can also trigger them because they bubble.

`event.target` is where an event originated. `event.currentTarget` is the element whose listener is running.

Many events reach ancestors after the target: this is **bubbling**. Event names in `addEventListener` omit the `on` prefix.

> `preventDefault()` prevents a default action, such as form navigation. `stopPropagation()` stops further propagation. They do different jobs.

### Examination Questions

**Write functions to handle `mouseup`, `mousedown`, `mouseover` and `mouseout`.** (2 marks)[^pyq-36]

**Answer.**

```html
<div id="zone" style="padding: 20px; border: 1px solid;">Use the mouse here</div>
<p id="mouseStatus"></p>
<script>
  const zone = document.getElementById("zone");
  const status = document.getElementById("mouseStatus");
  function up() { status.textContent = "Mouse button released"; }
  function down() { status.textContent = "Mouse button pressed"; }
  function over() { status.textContent = "Mouse entered"; }
  function out() { status.textContent = "Mouse left"; }
  zone.addEventListener("mouseup", up);
  zone.addEventListener("mousedown", down);
  zone.addEventListener("mouseover", over);
  zone.addEventListener("mouseout", out);
</script>
```

Each function reports one mouse action, and each listener connects that function to its corresponding event.

---

## 61. JavaScript Forms and Validation

**Form validation** checks whether submitted input follows the required rules before the program uses it. It combines JavaScript conditions with DOM access: read the controls, check the values, and either explain the problem or process the accepted input.

> Read the input → Check the rules → Display or submit the accepted result.

### Reading Form Controls

Use `document.getElementById("name")` to obtain a control by ID, or `document.forms["f"].elements.namedItem("name")` to obtain it through a named form.

`.value` gives current input text. `.checked` tells whether a checkbox or radio button is selected.

Trim unwanted outside whitespace before checking text. Keep telephone numbers as strings to preserve leading zeros; convert values to numbers when doing arithmetic.

### Checking Input

An empty name, letters in a numeric mobile field, or a quantity below one should be rejected before use. A regular expression is useful when the rule describes allowed characters.

HTML can declare many constraints directly:

| Constraint | Purpose |
| --- | --- |
| `required` | A value must be supplied. |
| `type="email"` | Email syntax. |
| `min`, `max`, `step` | Numeric range and step. |
| `minlength`, `maxlength` | Text length. |
| `pattern` | A text pattern. |

`checkValidity()` returns whether constraints pass. `reportValidity()` also displays the browser's validation message.

Use `setCustomValidity("message")` for a custom error and `setCustomValidity("")` to clear it after correction.[^validation]

### Responding to Submission

A `submit` handler receives an event. `event.preventDefault()` stops the normal submission/navigation so that the page can show its result.

For plain output, use `.textContent`, or `.value` in a textarea. `innerHTML` would interpret the data as markup.

These examples demonstrate front-end behaviour. A real receiving server must validate again because browser checks can be bypassed.

### Examination Questions

**Create a registration form for name, mobile and email; name must be nonempty/alphabetic, mobile numeric, email nonempty; show entered data in a textarea.** (marks not shown)[^pyq-37]

**Answer.** This version uses explicit JavaScript checks. The name check enforces letters only as stated; it does not add an unasked mobile length or email-domain rule.

```html
<form id="reg" novalidate>
  <label>Name <input id="regName" name="student"></label>
  <label>Mobile <input id="regMobile" name="mobile" inputmode="numeric"></label>
  <label>Email <input id="regEmail" name="email"></label>
  <button type="submit">Register</button>
</form>
<textarea id="regOutput" aria-label="Registration details" readonly></textarea>
<script>
  document.getElementById("reg").addEventListener("submit", function (event) {
    event.preventDefault();
    const name = document.getElementById("regName").value.trim();
    const mobile = document.getElementById("regMobile").value.trim();
    const email = document.getElementById("regEmail").value.trim();
    const output = document.getElementById("regOutput");
    output.value = "";
    if (!/^[A-Za-z]+$/.test(name)) {
      alert("Enter a nonempty alphabetic name."); return;
    }
    if (!/^[0-9]+$/.test(mobile)) {
      alert("Mobile must contain digits only."); return;
    }
    if (email === "") {
      alert("Email must not be empty."); return;
    }
    output.value = "Name: " + name + "\nMobile: " + mobile + "\nEmail: " + email;
  });
</script>
```

The anchored patterns test the whole name/number, not just one matching character. Output is cleared first so invalid resubmission cannot leave an earlier success visible.

**Design a vaccination-registration form, validate it using JavaScript, display submitted details and provide a confirm button.** (marks not verifiable)[^pyq-38]

**Answer.** The paper does not prescribe the fields, so name, age and contact below are illustrative form-design choices. The age check establishes a positive integer; it is not a vaccination-eligibility rule.

```html
<form id="vac">
  <label>Name <input id="vacName" required></label>
  <label>Age <input id="vacAge" type="number" min="1" step="1" required></label>
  <label>Contact <input id="vacPhone" pattern="[0-9]+" required></label>
  <button type="submit">Review details</button>
</form>
<pre id="vacDetails"></pre>
<button id="vacConfirm" type="button" disabled>Confirm</button>
<script>
  const vacForm = document.getElementById("vac");
  const vacDetails = document.getElementById("vacDetails");
  const vacConfirm = document.getElementById("vacConfirm");
  vacForm.addEventListener("input", function () {
    vacConfirm.disabled = true;
    vacDetails.textContent = "";
  });
  vacForm.addEventListener("submit", function (event) {
    event.preventDefault();
    if (!vacForm.reportValidity()) return;
    const name = document.getElementById("vacName").value.trim();
    if (name === "") { alert("Enter a name."); return; }
    vacDetails.textContent = "Name: " + name +
      "\nAge: " + document.getElementById("vacAge").value +
      "\nContact: " + document.getElementById("vacPhone").value;
    vacConfirm.disabled = false;
  });
  vacConfirm.addEventListener("click", function () {
    vacDetails.textContent += "\nDetails confirmed.";
    vacConfirm.disabled = true;
  });
</script>
```

The first action validates and displays; the second confirms the displayed data. Editing the form disables confirmation until the updated values are reviewed again.

**Design the HTML/CSS/JavaScript application page for IIIT Bhubaneswar's cyber-security hackathon: colleges enter groups of three; three winning groups receive prizes; students stay in institute residences and faculty mentors in the Guest House.** (5 marks)[^pyq-39]

**Answer.** The page presents the event conditions, collects an institute, exactly three participants and their mentor, and uses JavaScript to show the application. The paper does not ask for a server/database.

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>Hackathon application</title>
<style>
  body { font-family: sans-serif; max-width: 650px; margin: 2rem auto; }
  form { padding: 1rem; border: 1px solid navy; background: #eef6ff; }
  label { display: block; margin: 8px 0; }
  input { padding: 5px; }
</style></head><body>
<h1>IIIT Bhubaneswar Cyber Security Hackathon</h1>
<p>Technical colleges of Odisha may apply in teams of three.
Prizes will be awarded to the three winning groups. Students will stay in
institute residences; each college's faculty mentor will stay in the Guest House.</p>
<form id="hack">
  <label>College <input name="college" required></label>
  <label>Participant 1 <input name="p1" required></label>
  <label>Participant 2 <input name="p2" required></label>
  <label>Participant 3 <input name="p3" required></label>
  <label>Faculty mentor <input name="mentor" required></label>
  <label>Contact email <input name="email" type="email" required></label>
  <button type="submit">Review application</button>
</form><pre id="hackResult"></pre>
<script>
  document.getElementById("hack").addEventListener("submit", function (event) {
    event.preventDefault();
    const fields = this.elements;
    const names = ["college", "p1", "p2", "p3", "mentor", "email"];
    document.getElementById("hackResult").textContent = "";
    for (const name of names) {
      if (fields.namedItem(name).value.trim() === "") {
        alert("Complete every field."); return;
      }
    }
    document.getElementById("hackResult").textContent =
      "College: " + fields.namedItem("college").value +
      "\nTeam: " + fields.namedItem("p1").value + ", " +
      fields.namedItem("p2").value + ", " + fields.namedItem("p3").value +
      "\nMentor: " + fields.namedItem("mentor").value +
      "\nContact: " + fields.namedItem("email").value +
      "\nStudents: institute residences. Mentor: Institute Guest House.";
  });
</script></body></html>
```

The three required participant controls match the team-size rule; the native required/email checks run before a valid submit event, and the handler rejects whitespace-only entries. The page combines the event information, required controls, styling and a JavaScript review action.

**What is constraint validation, and which attributes can achieve it?** (2 marks)[^pyq-40]

**Answer.** Constraint validation checks whether form input satisfies declared restrictions. For example, `<input type="number" min="1" max="10" required>` accepts a required number within the range; `pattern`, `minlength`, `maxlength` and suitable input types provide other restrictions. JavaScript can test them using `checkValidity()` or show messages with `reportValidity()`.

---

## 62. DOM and Form Applications

The following questions combine content updates, event listeners and input checking. In a written answer, show the required HTML controls and the JavaScript that reads them, performs the calculation or update, and displays the result.

### Examination Questions

**Display a paragraph in a DIV with user-supplied width/height; wrap its text according to the DIV width.** (marks not shown)[^pyq-35]

**Answer.** Numeric inputs supply the dimensions, CSS controls wrapping, and the submit handler applies those dimensions and creates the paragraph.

```html
<form id="sizeForm">
  <label>Width in pixels <input name="width" type="number" min="1" required></label>
  <label>Height in pixels <input name="height" type="number" min="1" required></label>
  <label>Paragraph <textarea name="text" required></textarea></label>
  <button type="submit">Display paragraph</button>
</form>
<div id="textBox" style="border: 1px solid; overflow: auto;
                          overflow-wrap: anywhere; white-space: normal;"></div>
<script>
  document.getElementById("sizeForm").addEventListener("submit", function (event) {
    event.preventDefault();
    const fields = this.elements;
    const width = Number(fields.namedItem("width").value);
    const height = Number(fields.namedItem("height").value);
    if (!Number.isFinite(width) || !Number.isFinite(height) || width <= 0 || height <= 0) {
      alert("Enter positive dimensions."); return;
    }
    const box = document.getElementById("textBox");
    box.style.width = width + "px";
    box.style.height = height + "px";
    const paragraph = document.createElement("p");
    paragraph.textContent = fields.namedItem("text").value;
    box.textContent = "";
    box.appendChild(paragraph);
  });
</script>
```

Text normally wraps at spaces; `overflow-wrap: anywhere` also permits a long unbroken word to wrap. `overflow: auto` makes excess content accessible when the chosen height is too small. The dimensions need the CSS `px` unit when assigned as these strings.

**Design a local-product shopping site with catalogue, ordering and billing pages.** (5 marks)[^pyq-14]

**Answer.** Three connected pages present a local product, accept an order and display its bill. Here the product and price are illustrative choices, not details supplied by the paper. The GET form carries the quantity in the URL query; the billing page reads it and computes the displayed total. This is a front-end exam demonstration, not payment processing or authoritative server billing.

`catalogue.html`:

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>Local crafts</title>
<style>body { margin: 2rem; font-family: sans-serif; }
article { border: 1px solid; padding: 1rem; }</style></head>
<body><h1>Local crafts catalogue</h1><article>
<h2>Handwoven basket</h2><p>Price: Rs. 200 each</p>
<a href="order.html">Order this product</a>
</article></body></html>
```

`order.html`:

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>Order</title></head>
<body><h1>Order a basket</h1>
<form action="bill.html" method="get">
  <label>Quantity <input type="number" name="qty" min="1" max="20"
                         step="1" value="1" required></label>
  <button type="submit">Show bill</button>
</form><a href="catalogue.html">Back to catalogue</a></body></html>
```

`bill.html`:

```html
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><title>Bill</title></head>
<body><h1>Your bill</h1><p id="bill"></p>
<a href="order.html">Change order</a>
<script>
  const params = new URLSearchParams(window.location.search);
  const qty = Number(params.get("qty"));
  document.getElementById("bill").textContent =
    Number.isInteger(qty) && qty >= 1 && qty <= 20
      ? "Basket: " + qty + " x Rs. 200 = Rs. " + (qty * 200)
      : "Enter a valid quantity on the ordering page.";
</script></body></html>
```

The catalogue leads to the order form, which passes the quantity to the billing page. Together they demonstrate the three requested pages, navigation, input checking and calculation.

---

## 63. The Browser Object Model and Window

The **Browser Object Model (BOM)** refers to facilities provided by the surrounding browser environment.

> DOM concerns the document. BOM concerns the window, history, browser information and timers.

`window` is the browser window/global object, and `window.document` refers to its document. BOM is a conventional teaching grouping rather than one single interface specification.

### Window Methods and Dimensions

| Facility | Purpose |
| --- | --- |
| `window.alert("Saved")` | Displays a message. |
| `prompt("Name?")` | Returns entered text or `null` if cancelled. |
| `confirm("Continue?")` | Returns a boolean. |
| `window.innerWidth`, `window.innerHeight` | Viewport dimensions in CSS pixels. |
| `outerWidth`, `outerHeight` | Dimensions including the outer browser window. |

Viewport size is different from the document's total scrollable size:

```html
<button type="button" onclick="history.back()">Back</button>
<p id="viewport"></p>
<script>
  function showSize() {
    document.getElementById("viewport").textContent =
      window.innerWidth + " x " + window.innerHeight + " CSS pixels";
  }
  window.addEventListener("resize", showSize);
  showSize();
</script>
```

The example refreshes the viewport dimensions on resize. The Back button uses session-history navigation, explained in [Browser History](#64-browser-history).

A prompt returns text, so convert numeric input deliberately.

---

## 64. Browser History

The **history object** provides access to navigation within the current tab’s session history. It lets a script move to an existing previous or next entry, much like the browser’s Back and Forward buttons.

| Member | Purpose |
| --- | --- |
| `history.back()` | Move back one entry. |
| `history.forward()` | Move forward one entry. |
| `history.go(-1)` | Move by an offset; `-1` moves back one entry. |
| `history.length` | Report the number of session-history entries. |

For example, `<button type="button" onclick="history.back()">Back</button>` returns to the previous entry if one exists. History navigation requires a corresponding entry; the object does not expose an unrestricted list of browsing URLs.

---

## 65. Navigator and Browser Detection

The **navigator object** reports information about the browser and its environment. It is used for basic browser detection and for checking indicators such as language, connectivity and cookie support.

`navigator.userAgent`, `navigator.language`, `navigator.onLine` and `navigator.cookieEnabled` report environment information.

`onLine` is only a connectivity indicator, not proof that a particular server is reachable.

`navigator.userAgent.includes("Firefox/")` finds a reported Firefox token. User-agent strings may be reduced, imitated or overlap between browsers.

When checking a capability, feature detection such as `typeof document.querySelector === "function"` directly tests what the program needs.

---

## 66. JavaScript Timing Events

A **timer** schedules a function to run later. Delay is measured in milliseconds; it does not pause the rest of the script.

| Function | Purpose |
| --- | --- |
| `setTimeout(function, delay)` | Schedule one call. |
| `setInterval(function, delay)` | Schedule repeated calls. |
| `clearTimeout(id)` | Cancel the pending one-time timer. |
| `clearInterval(id)` | Cancel the repeating timer. |

The scheduling functions return IDs used for cancellation. Pass a function, not the result of calling it.

```html
<p id="reminder"></p>
<button id="cancelReminder" type="button">Cancel reminder</button>
<p id="countdown"></p>
<script>
  const reminderId = setTimeout(function () {
    document.getElementById("reminder").textContent = "Time to revise DOM";
  }, 2000);
  document.getElementById("cancelReminder").addEventListener("click", function () {
    clearTimeout(reminderId);
    document.getElementById("reminder").textContent = "Reminder cancelled";
  });
  let remaining = 3;
  const intervalId = setInterval(function () {
    document.getElementById("countdown").textContent = remaining;
    remaining--;
    if (remaining === 0) clearInterval(intervalId);
  }, 1000);
</script>
```

The reminder runs once unless cancelled first. The interval displays 3, 2 and 1, then clears itself.

A delay does not guarantee an exact execution time. Cancelling cannot undo a callback that has already run. Deeper scheduling belongs to the planned advanced material.

### Additional Practice

**Original question · Suggested 5 marks.** Distinguish DOM from BOM, distinguish NodeList membership from node contents, and show a cancellable one-time reminder.

**Answer.** DOM represents/manipulates document nodes; BOM refers to browser-environment facilities such as window/history/timers. `querySelectorAll()` returns a static NodeList: later additions do not change its membership, but its node objects still reflect edits. A reminder can be written as `const id = setTimeout(function () { alert("Revise"); }, 2000);` and cancelled before execution using `clearTimeout(id)`. Here, 2000 is a delay in milliseconds; cancellation does not undo a callback that has already executed.

---

## 67. Cookies and JavaScript

A **cookie** is a small name/value item stored by the browser for a site and included in applicable HTTP requests. It can retain a preference or a session identifier across independent HTTP exchanges. It does not inherently contain the whole session and is not a JavaScript object.

Assigning to `document.cookie` sets one accessible cookie. Reading it returns accessible `name=value` pairs separated by semicolons.

| Attribute | Meaning |
| --- | --- |
| `max-age` | Lifetime in seconds. |
| `expires` | Expiry date in UTC. |
| `path` | Applicable URL path. |

Without `max-age` or `expires`, the cookie is normally a session cookie. Updating or deleting requires the same name/path/domain combination; deletion uses an expired lifetime.[^cookies][^cookie-mechanism]

```javascript
// Create, read and update a preference.
document.cookie = "student=" + encodeURIComponent("Anu Rao") + "; max-age=3600; path=/";
console.log(document.cookie);
document.cookie = "student=" + encodeURIComponent("Mina") + "; max-age=3600; path=/";

function readCookie(name) {
  const prefix = encodeURIComponent(name) + "=";
  for (const part of document.cookie.split(";")) {
    const pair = part.trim();
    if (pair.startsWith(prefix)) return decodeURIComponent(pair.slice(prefix.length));
  }
  return null;
}
console.log(readCookie("student")); // Mina, if this context permits the cookie.
// Delete the same name/path cookie.
document.cookie = "student=; max-age=0; path=/";
```

Encoding keeps spaces and separators from corrupting cookie syntax. The reading function finds the name and decodes its value; the last assignment deletes the matching cookie.

Server-set `HttpOnly` cookies are not exposed through `document.cookie`. Browser settings and context can restrict cookies, so use a served page for practical examples rather than assuming identical behaviour for `file:` pages.

`navigator.cookieEnabled` reports an indicator, not a guarantee that every context accepts every cookie.[^cookie-indicator]

> A persistent cookie has a specified lifetime. A persistent HTTP connection reuses a connection. These are separate mechanisms.

### Examination Questions

**Create and delete cookies in JavaScript, with examples.** (3 marks)[^pyq-41]

**Answer.** A cookie stores a small name/value pair for a site. Assign `document.cookie = "user=Anu; max-age=3600; path=/";` to create a one-hour cookie. Read accessible cookies using `document.cookie`. Delete the same cookie using `document.cookie = "user=; max-age=0; path=/";`, or by setting an expiry date in the past with the same path/domain.

**Define cookies and write a function displaying whether they are enabled.** (2 marks)[^pyq-42]

**Answer.** Cookies are small name/value items stored by the browser for a site and included in applicable HTTP requests, allowing state to be retained.

```html
<p id="cookieStatus"></p>
<script>
  function showCookieStatus() {
    document.getElementById("cookieStatus").textContent =
      navigator.cookieEnabled ? "Cookies enabled" : "Cookies disabled";
  }
  showCookieStatus();
</script>
```

This displays the browser’s cookie-support indicator; individual contexts can still restrict cookies.

---

> **Planned topics:** The remaining JavaScript topics below retain their coverage and question index. Their explanations and model answers are still to be written. Reference gaps: Appendix B.

## 68. JavaScript Closures

**Coverage:** Closures and the scope context needed to explain them.

**PYQs:** No direct PYQ. The scope comparison in [Topic 40](#40-javascript-variables-and-scope) is related groundwork.

---

## 69. JavaScript Hoisting

**Coverage:** Hoisting of declarations, including the distinction between `var`, `let` and `const`.

**PYQs:** No direct PYQ. The scope comparison in [Topic 40](#40-javascript-variables-and-scope) is related groundwork.

---

## 70. Immediately Invoked Function Expressions (IIFEs)

**Coverage:** IIFE syntax, immediate invocation and its scope purpose.

**PYQs:** No direct PYQ. The scope comparison in [Topic 40](#40-javascript-variables-and-scope) is related groundwork.

---

## 71. The JavaScript Event Loop

**Coverage:** Event loops and the execution context needed to explain asynchronous callbacks.

**PYQs:** No direct PYQ found.

---

## 72. JavaScript Callback Functions

**Coverage:** Callback functions and their use in asynchronous work.

**PYQs:** [2023 collection][paper-2023], Q2(b), p. 1, 5 marks overall: synchronous/asynchronous AJAX requests, callback role and XHR ready states. This is an application of callbacks/asynchronous programming, not a direct promises or event-loop question. Full question mapping: [Topic 85](#85-xmlhttprequest-and-server-responses).

---

## 73. JavaScript Promises and async/await

**Coverage:** Promises; async/await; their relationship to callbacks and asynchronous completion.

**PYQs:** No direct PYQ found.

---

## 74. Functional Programming and Higher-Order Functions

**Coverage:** Functional programming; functions as values; higher-order functions.

**PYQs:** No direct PYQ found.

---

## 75. JavaScript Generators

**Coverage:** Generators and their prescribed use.

**PYQs:** No direct PYQ found.

---

## 76. Memoization

**Coverage:** Memoization as reuse of previously computed results.

**PYQs:** No direct PYQ found.

---

## 77. Currying

**Coverage:** Currying and its relationship to function arguments.

**PYQs:** No direct PYQ found.

---

# Module III - XML, AJAX, jQuery, JSON, React.js and Node.js (12 hours)

The syllabus coverage and verified question index below remain planned. Teaching and model answers are still to be written.

## 78. XML: Introduction and Document Structure

**Coverage:** XML introduction; XML vs HTML; structure of an XML document; well-formed XML documents.

**PYQs:**

- **I | [2021 paper, 2018-22 batch][paper-2021-a], Q5(ii-iii), p. 3, marks not visible:** Provide a sample pizza-order XML message for the DTD and identify its building blocks. Q5(i) is indexed in [Topic 79](#79-dtd-and-xml-validation).
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(i), p. 2, marks not visible:** Well-formed vs valid XML, with DTD/types/examples; shared with [Topic 79](#79-dtd-and-xml-validation).
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(ii), p. 2, marks not visible:** Book-catalogue DTD, corresponding XML message and explanation of XML structure; shared with [Topic 79](#79-dtd-and-xml-validation).

---

## 79. DTD and XML Validation

**Coverage:** Document Type Declaration (DTD), as worded in the syllabus, and DTD definitions; internal/external DTD; XML validation; valid XML document; relation to well-formedness.

**PYQs:**

- **I | [2019 paper][paper-2019], Q2.B(i), p. 1, 1+2 marks:** Define DTD and write one for the supplied `book` XML with `id`, title and author.
- **I | [2021 paper, 2018-22 batch][paper-2021-a], Q5(i-iii), p. 3, marks not visible:** Pizza-order message DTD, a sample XML message and its building blocks.
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(i), p. 2, marks not visible:** Well-formed/valid XML; DTD and its types with examples.
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(ii), p. 2, marks not visible:** DTD and sample book-catalogue XML message with a structural explanation.

---

## 80. XML Namespaces

**Coverage:** XML namespaces and the naming conflicts they address.

**PYQs:** No direct PYQ found.

---

## 81. XML Schema

**Coverage:** XML Schema; schema-based validation; relationship to DTD.

**PYQs:** No direct Schema-specific question found. Generic XML validity questions do not establish a Schema occurrence.

---

## 82. The XML DOM

**Coverage:** XML DOM and working with XML document nodes.

**PYQs:** No direct XML-DOM question found. HTML DOM questions are indexed separately in Module II.

---

## 83. XSL and XSL Transformation

**Coverage:** XSL; XSL Transformation; necessary XML selection/template context within transformation examples.

**PYQs:** No direct PYQ found.

---

## 84. AJAX and Client–Server Flow

**Coverage:** AJAX introduction; relation to JavaScript; asynchronous page updates; client-server architecture as context for AJAX operation.

**PYQs:**

- **I | [2019 paper][paper-2019], Q4.A, p. 2, 1+2+2 marks:** Define AJAX, explain implementation steps and important XMLHttpRequest properties/methods. Same question as [Topic 85](#85-xmlhttprequest-and-server-responses).
- **P | [2023 collection][paper-2023], Q4(b), p. 1, 2.5 marks per selected short note:** Retain JSON and AJAX options only; exclude Spring and Struts. Answer-any-two choice applies to the original question.
- **I | [2023 collection][paper-2023], Group A Q1(a), p. 3, 2 marks:** Difference between AJAX and JavaScript.
- **P | [2023 collection][paper-2023], Group B Q2, p. 3, 10 marks overall:** Retain JSON in AJAX and the AJAX client-server architecture diagram/explanation. The “types of post backs” clause is U; no retained-only marks are specified.

---

## 85. XMLHttpRequest and Server Responses

**Coverage:** XMLHttpRequest object; request creation/sending; properties/methods; server response; ready states; response handlers and synchronous/asynchronous request context.

**PYQs:**

- **I | [2019 paper][paper-2019], Q4.A, p. 2, 1+2+2 marks overall:** AJAX definition/steps and important XHR properties/methods; the final portion is 2 marks.
- **I | [2023 collection][paper-2023], Q1(b), p. 1, 2 marks:** Different ready states of an AJAX request.
- **I | [2023 collection][paper-2023], Q2(b), p. 1, 5 marks:** Synchronous/asynchronous requests, role of AJAX callbacks and request ready states.

---

## 86. AJAX with XML and Databases

**Coverage:** AJAX XML; AJAX Database; browser request, endpoint response and DOM-update flow in these examples.

**PYQs:** No direct question specifically requiring AJAX XML/database integration found. Do not relabel old JDBC or servlet database questions as AJAX questions.

---

## 87. jQuery DOM Selectors

**Coverage:** jQuery DOM selectors; selecting elements by the prescribed DOM-selection context.

**PYQs:**

- **I | [2023 collection][paper-2023], Group A Q1(b), p. 3, 2 marks:** Explain jQuery DOM selectors.

---

## 88. jQuery HTML Content and DOM Manipulation

**Coverage:** HTML Content; jQuery HTML DOM; reading/changing content and attributes; adding/removing DOM elements.

**PYQs:**

- **P | [2023 collection][paper-2023], Group B Q4, p. 3, 10 marks overall:** Retain built-in functions that operate on the prescribed selectors/HTML content/CSS/DOM, plus the background-color task in [Topic 89](#89-jquery-css-styles). Do not expand this broad wording into every jQuery API; no subpart split is printed.
- **U - REVIEW | [2023 collection][paper-2023], Q1(e), p. 1, 2 marks:** Explain `ready()`, `mouseenter()`, `mousedown()` and `toggle()`. These span DOM readiness, event helpers and effects; jQuery events/effects are not explicitly among the four prescribed jQuery topics. Confirm intended depth before including the item as required study.

---

## 89. jQuery CSS Styles

**Coverage:** jQuery CSS Styles; reading/updating styles and classes in the DOM context.

**PYQs:**

- **P | [2023 collection][paper-2023], Group B Q4, p. 3, 10 marks overall:** Write jQuery code to get the background color of an element in a paragraph; explain only syllabus-aligned built-in functions. Same question as [Topic 88](#88-jquery-html-content-and-dom-manipulation); background-color-only marks are not printed.

---

## 90. JSON: Syntax, Types, Objects and Arrays

**Coverage:** Introduction; syntax; data types; Object; Arrays; nesting and structured data as applications of these topics.

**PYQs:**

- **I | [2021 paper, 2018-22 batch][paper-2021-a], Q5(iv-v), p. 3, marks not visible:** What JSON is and four reasons for preferring JSON over XML for message exchange. Treat the requested preference as a question to assess, not a universal rule.
- **P | [2023 collection][paper-2023], Q4(b), p. 1, 2.5 marks per selected short note:** JSON option only here; AJAX is indexed in [Topic 84](#84-ajax-and-clientserver-flow); Spring/Struts are excluded.
- **I | [2023 collection][paper-2023], Group A Q1(c), p. 3, 2 marks:** JSON syntax and its data types.
- **P | [2023 collection][paper-2023], Group B Q2, p. 3, 10 marks overall:** JSON in AJAX, within the retained portion; exclude unresolved postback taxonomy.
- **I | [2023 collection][paper-2023], Group B Q3, p. 3, 10 marks:** JSON applications and a program storing five books by author, topic and edition.

---

## 91. JSON Parsing and Stringifying

**Coverage:** Parsing JSON; stringifying JavaScript values; connections to JSON objects/arrays and data interchange.

**PYQs:** No direct parsing/stringifying question found. The five-book question does not explicitly demand either operation.

---

## 92. React, ES6, Rendering and JSX

**Coverage:** React.js introduction; ES6; Render HTML; JSX.

**PYQs:**

- **I | [2023 collection][paper-2023], Q2(a), p. 1, 5 marks overall:** Creator/company, React advantages, props, JSX and how JSX works with an example. Props are also indexed in [Topic 93](#93-react-components-and-props); no subpart marks are printed.
- **I | [2023 collection][paper-2023], Group A Q1(d), p. 3, 2 marks:** What ES6 and JSX are.

---

## 93. React Components and Props

**Coverage:** Components; passing data through props.

**PYQs:** [2023 collection][paper-2023], Q2(a), p. 1, 5 marks overall: props portion of the combined React/JSX question; see [Topic 92](#92-react-es6-rendering-and-jsx). No subpart mark split is printed.

---

## 94. React State

**Coverage:** State and the behaviour needed to explain component updates.

**PYQs:** No direct PYQ found.

---

## 95. React Component Lifecycle

**Coverage:** Component lifecycle. The stray “2” before “Lifecycle” in the syllabus scan does not define another topic.

**PYQs:** No direct PYQ found.

---

## 96. React Events and Forms

**Coverage:** Events; forms in React.

**PYQs:** No direct React-specific question found. Plain HTML/JavaScript form questions are not React occurrences.

---

## 97. CSS in React

**Coverage:** Applying CSS in React.

**PYQs:** No direct PYQ found.

---

## 98. Node.js and the Development Environment

**Coverage:** Introduction to Node.js; setup development environment; running an application as setup context.

**PYQs:**

- **I | [2023 collection][paper-2023], Q1(a), p. 1, 2 marks overall:** What Node.js can do and syntax to include the HTTP module; module portion also indexed in [Topic 99](#99-nodejs-modules-and-npm).

---

## 99. Node.js Modules and npm

**Coverage:** Node.js modules; Node Package Manager; importing/exporting modules and managing packages as applications of these topics.

**PYQs:**

- **I | [2023 collection][paper-2023], Q1(a), p. 1, 2 marks overall:** Include the HTTP module in a Node.js program; same item as [Topic 98](#98-nodejs-and-the-development-environment).
- **I | [2023 collection][paper-2023], Group A Q1(e), p. 3, 2 marks:** Explain Node.js modules.

---

## 100. Node.js Web Servers and Events

**Coverage:** Creating a web server; Events; event-driven request handling.

**PYQs:**

- **I | [2023 collection][paper-2023], Q1(a), p. 1, 2 marks overall:** Node capabilities and including HTTP are relevant foundations; the actual prompt does not ask for a complete server implementation.

---

## 101. The Node.js File System

**Coverage:** File System operations in Node.js.

**PYQs:** No direct Node-specific file-system question found.

---

## 102. Debugging a Node.js Application

**Coverage:** Debugging Node.js applications.

**PYQs:** No direct Node-specific debugging question found. The 2024 browser JavaScript debugging question belongs to [Topic 54](#54-javascript-debugging).

---

## 103. Express.js and Serving Static Resources

**Coverage:** Express.js; Serving Static Resources.

**PYQs:** No direct PYQ found.

---

## 104. Node.js Database Connectivity

**Coverage:** Database Connectivity in the Node.js context.

**PYQs:** No direct Node.js database-connectivity question found. Older Java/JDBC/servlet questions remain excluded; do not rewrite them into invented Node questions.

---

## Appendix A - Examination Evidence

**Authority:** [Official syllabus](../Syllabus/IWT-7th-Semester-IT.pdf), Module I p. 2, Module II pp. 2–3, Module III p. 3.

**Observed recurrence and marks:**

- **HTML/CSS construction:** 4 source sets—2019, both 2021 files and 2024. The travel task is 10 points; 2024 website tasks are 5 marks each. **Form validation:** 3 sets—both 2021 files and 2024.
- **XML/DTD:** 3 sets—2019 and both 2021 files. The 2019 task is 1+2 marks; 2021 requires complete XML/DTD examples, with marks not visible.
- **AJAX:** 2019 and dated 2023; **JSON:** the 2018–22 batch file and dated 2023. Both also appear on the undated sheet. AJAX/XHR is 5 marks in 2019; synchronous/asynchronous AJAX is 5 marks in dated 2023.
- **jQuery, React and Node.js:** dated 2023 and the separate undated sheet. That sheet has 10-mark JSON/jQuery questions; dated 2023 React is 5 marks and Node is 2 marks. Some jQuery wording remains uncertain.

Counts record presence once per topic family per source set. The paired 2024 images count as one paper; the undated sheet is separate. Cross-topic references do not create occurrences. Partial questions count only for retained content; uncertain questions are excluded from counts. The sample spans different semesters/branches and includes incomplete papers.

**Observed formats:**

| Source | Visible examination pattern |
| --- | --- |
| 2019 | 50 marks, 2.5 hours; any five of six 10-mark questions; 1–3 mark subparts and 2.5-mark short notes. |
| Dated 2023 | Header: 50 marks, 2.5 hours, answer all; only 40 marks are visible. |
| Undated sheet | Five compulsory 2-mark items; any two of three 10-mark questions. |
| November 2024 | 50 marks, 2.5 hours, answer all; five 10-mark blocks. Q1/Q3 contain two 5-mark tasks; Q2/Q4/Q5 contain five 2-mark items. |
| 2021 collections | No complete timed-paper format is established. |

**Study priority is a judgement, not a forecast.** Low-frequency syllabus topics remain required. Module hours are **8/10/12** (30 total), not examination weightages. The 2024 focus on Modules I–II does not remove Module III. Syllabus p. 4 assigns end-term assessment 50% of course evaluation, not a guaranteed question pattern.

## Appendix B - Sources and reference limits

**Scope labels:** **I** = in scope; **P** = retain only aligned portions; **O** = excluded; **U** = uncertain, held for review and excluded from frequency counts.

Question descriptions are faithful compact paraphrases. Unverified marks are labelled; no multipart mark split is assumed. PDF pages are **1-based file pages**. PNGs use filenames, with sequence inferred from question continuity. “No direct PYQ” records an evidence gap, not a syllabus exclusion.

- **[CS201_Internet_and_Web_Technology_April_2019.pdf](../Papers/CS201_Internet_and_Web_Technology_April_2019.pdf)** — 2 PDF pages; April 2019, sixth semester, EEE, CS201. Older course context; filter against the present IT syllabus.

- **[IWT 2021 Endsem (2018-22 batch).pdf](<../Papers/IWT 2021 Endsem (2018-22 batch).pdf>)** — 3 PDF pages of screenshots. Filename supplies year/batch. Travel prompt has no printed question number; vaccination form is identified as q2 in its screenshot title. Q3-Q5 are numbered. The travel prompt shows 10 points; the vaccination mark label is clipped.

- **[IWT 2021 Endsem (2019-23 batch).pdf](<../Papers/IWT 2021 Endsem (2019-23 batch).pdf>)** — 5 PDF pages; Q1-Q5 on pp. 1-4, p. 5 blank. Filename supplies year/batch. Marks are not visible. Q5(ii)'s final instruction is cut off; its HTML/servlet requirement is readable.

- **[IWT_Question_Papers_2023.pdf](../Papers/IWT_Question_Papers_2023.pdf), p. 1** — Dated November 2023, seventh semester IT, IWT II. Header: two pages, 50 marks. Only Q1–Q4 (40 marks) are visible, without a coherent continuation.

- **Same PDF, p. 2** — Android fragment: XML checkboxes, contextual menu, implicit intents and ConstraintLayout. Inconsistent with p. 1; excluded from IWT frequency.

- **Same PDF, p. 3** — Separate undated sheet headed Internet and Web Technologies-2, seventh semester IT, Groups A/B, 30 attempted marks. Its examination year is unverified.

- **[A_1.png](../Papers/A_1.png) and [A_2.png](../Papers/A_2.png)** — Paired November 2024 end-semester paper, IT. A_1: Q1, Q2(a–b); A_2: Q2(c–e), Q3–Q5. Count as one paper.

### Reference material: use and gaps

The six supplied references support later writing within the syllabus. Ranges are PDF file pages.

- **[XML.pdf](../Sources/XML.pdf), 15 pp.** — Introduction/HTML comparison pp. 1-5; structure pp. 5-7; namespaces pp. 7-8; DTD pp. 8-10; Schema/validation pp. 10-11; XSL/transformation overview pp. 12-15. **Limits:** XML DOM is only briefly mentioned (p. 6); worked DOM/XSLT coverage is insufficient. Android/configuration examples do not prescribe Android development.

- **[AJAX.pdf](../Sources/AJAX.pdf), 11 pp.** — Introduction/architecture pp. 1-2; XHR/callback/response example pp. 3-4; XML interaction pp. 4-7; database interaction pp. 7-11. **Limits:** PHP/MySQL are example endpoints, not independent prescribed PHP/JDBC topics. XHR states need fuller treatment than the sample's completion check.

- **[jQuery.pdf](../Sources/jQuery.pdf), 16 pp.** — Basics/selectors pp. 4-7, 12; chaining p. 8; styles p. 9; markup pp. 10, 14; DOM overview p. 11. **Limits:** Events/effects on pp. 13, 15 do not expand the four listed jQuery syllabus topics. Some spellings/examples need checking when writing, including `ccs` on p. 9 and `xss` on p. 14.

- **[JSON.pdf](../Sources/JSON.pdf), 33 pp.** — Introduction pp. 2-5; syntax/objects/arrays pp. 7-11; types pp. 13-19; nesting pp. 20-22; XML comparison pp. 24-31. **Limits:** Does not teach the prescribed JavaScript parsing/stringifying operations. Java/Gson material on p. 32 is not prescribed.

- **[reactjs.pdf](../Sources/reactjs.pdf), 26 pp.** — Intro/rendering pp. 2, 4-12; JSX pp. 13-17; components/props pp. 18-21; Babel p. 22. **Limits:** State, lifecycle, events, forms and React CSS are not developed. The reference's own “Syllabus” on p. 3 is not the official course scope; do not import Router, virtualized lists, webpack or fetch-hook topics from it.

- **[nodejs.pdf](../Sources/nodejs.pdf), 42 pp.** — Intro/running/REPL pp. 1-5; npm/modules pp. 6-9; callbacks pp. 10-12; event loop/events pp. 13-24; HTTP server pp. 29-33; file system pp. 34-42. **Limits:** Installation detail is limited; debugging, Express, static serving and database connectivity are missing. Streams pp. 25-29 may support file/server examples but are not a separate syllabus unit.

Most Module I and advanced JavaScript topics lack supplied-reference coverage. Supplementary support for completed material is listed in Appendix D.

## Appendix C - Past-paper scope audit

This register accounts for every visible question. The entries explain **P/O/U** boundaries; page and group labels distinguish questions in the mixed 2023 PDF.

### Complete classification register

| File / page | I: in scope | P: retain only aligned portions | O: exclude | U: review |
| --- | --- | --- | --- | --- |
| `CS201_Internet_and_Web_Technology_April_2019.pdf`, pp. 1-2 | Q1.A(i-ii), Q1.B(i-ii); Q2.A(i-ii), Q2.B(i-ii); Q4.A; Q5.B(ii); Q6.A(ii) | Q3.A(i), Q3.B, Q6.A(i) | Q3.A(ii), Q4.B, Q5.A(i), Q5.B(i), Q6.B(i), Q6.B(iii) | Q5.A(ii) |
| `IWT 2021 Endsem (2018-22 batch).pdf`, pp. 1-3 | Unnumbered travel prompt; Q2; Q5(i-v) | None | Q3, Q4 | None; travel numbering and Q2 marks are provenance limitations |
| `IWT 2021 Endsem (2019-23 batch).pdf`, pp. 1-4 | Q1(i); Q2(i-ii); Q3(i-ii) | Q1(ii), Q5(ii) | Q4(i-ii), Q5(i) | None; Q5(ii)'s closing instruction is cut off |
| `IWT_Question_Papers_2023.pdf`, p. 1, dated exam | Q1(a-b), Q2(a-b) | Q4(b) | Q1(c), Q3(a-b), Q4(a) | Q1(d-e) |
| Same PDF, p. 2, Android fragment | None | None | Checkbox prompt; contextual-menu prompt; Q2(a-b) | Checkbox subpart label is obscured; contextual-menu label appears to be (j). Identity/continuity needs review, but the Android tasks are excluded. |
| Same PDF, p. 3, undated Group A/B sheet | Group A Q1(a-e); Group B Q3 | Group B Q2, Q4 | None | Group B Q2's “types of post backs” clause only; parent question classified P |
| `A_1.png` and `A_2.png`, paired 2024 paper | Q1(a-b); Q2(a-e); Q3(a-b); Q4(a-e); Q5(a-e) | None | None | None |

### Partially in-scope questions: exact retention boundaries

- **`CS201_Internet_and_Web_Technology_April_2019.pdf`, Q3.A(i), p. 1, 2+1** — **Retain:** GET vs POST (1 mark), [HTTP Requests and Responses](#6-http-requests-and-responses). **Exclude/review:** JSP tags and examples (2 marks). JSP is not prescribed.

- **Same file, Q3.B, p. 2, 1+4 overall** — **Retain:** Explicit HTML registration-form portion, [HTML Forms](#18-html-forms). No HTML-only mark split given. **Exclude/review:** Servlet lifecycle, servlet code, deployment descriptor and database-table implementation. Node database connectivity does not prescribe this Java stack.

- **Same file, Q6.A(i), p. 2, 1+1** — **Retain:** JavaScript introductory characteristics (from the comparison) and `script` attributes, [HTML and Document Structure](#10-html-and-document-structure)/[JavaScript: Statements, Comments and Values](#39-javascript-statements-comments-and-values). Script-attributes portion is 1 mark; do not claim a retained-only total for the comparison. **Exclude/review:** Detailed Java-language study from the Java-vs-JavaScript comparison.

- **`IWT 2021 Endsem (2019-23 batch).pdf`, Q1(ii), p. 1, marks not visible** — **Retain:** CSS purpose, box model, colors, alignment/layout, iframe and inline styles, [Website Layout](#38-website-layout-and-complete-page-design) and [Iframes](#17-html-frames-and-iframes). **Exclude/review:** The diagram's `marquee` instruction. Frames and CSS animation do not explicitly prescribe this old HTML tag.

- **Same file, Q5(ii), p. 4, marks not visible** — **Retain:** Explicit HTML login page (`index.html`), [HTML Forms](#18-html-forms). **Exclude/review:** Servlet authentication/code and `web.xml` mapping. Do not infer the cut-off final instruction.

- **`IWT_Question_Papers_2023.pdf`, Q4(b), p. 1, 2.5+2.5 for any two options** — **Retain:** JSON and AJAX short notes, [AJAX and Client–Server Flow](#84-ajax-and-clientserver-flow)/[JSON: Syntax, Types, Objects and Arrays](#90-json-syntax-types-objects-and-arrays). **Exclude/review:** Spring framework and Struts options. Original choice rule does not make them prescribed.

- **Same file, Group B Q2, p. 3, 10 overall** — **Retain:** JSON in AJAX and client-server architecture diagram/explanation, [AJAX and Client–Server Flow](#84-ajax-and-clientserver-flow)/[JSON: Syntax, Types, Objects and Arrays](#90-json-syntax-types-objects-and-arrays). No marks assigned to retained clauses separately. **Exclude/review:** “Types of post backs in AJAX” is U: intended taxonomy/technology is unspecified. Do not add ASP.NET postback material without clarification.

- **Same file, Group B Q4, p. 3, 10 overall** — **Retain:** Built-in jQuery functions for selectors, HTML content, CSS styles and HTML DOM; requested background-color getter, [jQuery HTML Content and DOM Manipulation](#88-jquery-html-content-and-dom-manipulation)/[jQuery CSS Styles](#89-jquery-css-styles). **Exclude/review:** Unbounded coverage of all jQuery built-ins, including effects/plugins and library-specific event APIs not explicitly prescribed. No separate getter marks are printed.

### Out-of-scope questions and options

- **`CS201_Internet_and_Web_Technology_April_2019.pdf`, Q3.A(ii), p. 2, 1+1 marks** — **Question:** JSP vs servlet; use of a JDBC driver. **Reason:** Neither Java server technology nor JDBC is prescribed.

- **Same file, Q4.B, p. 2, 2+3 marks** — **Question:** Five steps connecting Java to a database and a JDBC program. **Reason:** Node database connectivity is a different prescribed context.

- **Same file, Q5.A(i), p. 2, 1+2 marks** — **Question:** Class vs interface and a class with multiple constructors. **Reason:** Java context, not a verified JavaScript-class task.

- **Same file, Q5.B(i), p. 2, 1+1+1 marks** — **Question:** JavaBean example, serializable interface and EJB types. **Reason:** JavaBeans/EJB/Java serialization have no module-level topic. The general outcome's Java Beans mention does not prescribe this detailed Java stack; flag the wording discrepancy for review below.

- **Same file, Q6.B(i), p. 2, 2.5 marks** — **Question:** EJB vs RMI. **Reason:** Neither is a prescribed module topic.

- **Same file, Q6.B(iii), p. 2, 2.5 marks** — **Question:** VBScript short note. **Reason:** VBScript is not prescribed. The second listed short-note label is printed “iii”; do not renumber it to “ii”.

- **`IWT 2021 Endsem (2018-22 batch).pdf`, Q3, p. 2, marks not visible** — **Question:** Java Person -> StudentIIIT -> MTechStudent/BTechStudent/PhDStudent classes; accessors/mutators, constructors, `this`/`super`. **Reason:** Explicit Java program, not JavaScript inheritance.

- **Same file, Q4, p. 2, marks not visible** — **Question:** Health-camp servlet that processes height/weight/health data, displays BMI/status and stores data in a database. **Reason:** Explicit servlet implementation; there is no separately requested HTML-file subtask to retain. Do not transform it into a new JavaScript/Node question.

- **`IWT 2021 Endsem (2019-23 batch).pdf`, Q4(i), p. 3, marks not visible** — **Question:** Java command-line arithmetic program handling arithmetic exceptions. **Reason:** Explicit Java, not the prescribed JavaScript errors topic.

- **Same file, Q4(ii), p. 3, marks not visible** — **Question:** Implement Java Item/MP3/DVD/Book inheritance diagram and create objects/attributes. **Reason:** Explicit Java, not JavaScript classes.

- **Same file, Q5(i), p. 4, marks not visible** — **Question:** Java/JDBC connection; create a students table, insert two rows, display contents. **Reason:** Java/JDBC stack is not prescribed; do not count as Node connectivity.

- **`IWT_Question_Papers_2023.pdf`, Q1(c), p. 1, 2 marks** — **Question:** J2EE concepts/types. **Reason:** J2EE is not prescribed.

- **Same file, Q3(a), p. 1, 2+1+2 marks** — **Question:** EJB definition, types and differences. **Reason:** EJB is not prescribed.

- **Same file, Q3(b), p. 1, 2+2+1 marks** — **Question:** Hibernate architecture, components and object states. **Reason:** Hibernate is not prescribed.

- **Same file, Q4(a), p. 1, 1+2+2 marks** — **Question:** Microservices, advantages and design best practices with examples. **Reason:** Microservices-specific architecture/design is not a named module topic; broad “web architecture” does not justify importing this full unit.

- **Same file, Q4(b)(i-ii), p. 1, 2.5 per selected note** — **Question:** Spring framework and Struts. **Reason:** These are excluded options in the partially retained short-note question.

- **Same file, p. 2, checkbox prompt, label obscured, marks not visible** — **Question:** XML UI checkboxes for chocolate syrup, sprinkles and crushed nuts. **Reason:** Android layout task in the Android fragment, not web XML/DTD.

- **Same file, p. 2, contextual-menu prompt, label appears (j), marks not visible** — **Question:** Define a contextual menu and steps to create it. **Reason:** Android context established by adjacent UI and Activity/manifest tasks; not a CSS navigation-menu question.

- **Same file, Q2(a), p. 2, 5 marks** — **Question:** Android layout/Java/manifest for one Activity opening a website/map and sharing text, using editable default-valued fields. **Reason:** Android Activity/intents/manifest development is not prescribed. Opening a website does not make it an IWT web-development question.

- **Same file, Q2(b), p. 2, 5 marks** — **Question:** Android Hello Constraint app using ConstraintLayout, with layout/Java/manifest files. **Reason:** Android ConstraintLayout is not CSS layout.

### Uncertain classifications and source issues to review

- **`CS201_Internet_and_Web_Technology_April_2019.pdf`, Q5.A(ii), p. 2, 2 marks** — **Review:** “Exception handling” does not name its language; surrounding questions are Java-oriented. **Treatment:** U; held out of required question frequency. Retain only if confirmed to ask JavaScript error handling.

- **`IWT_Question_Papers_2023.pdf`, Q1(d), p. 1, 2 marks** — **Review:** MVC's relation to generic prescribed web architecture versus an older framework-specific unit. **Treatment:** U; retained in this audit for review, with no MVC/framework expansion.

- **Same file, Q1(e), p. 1, 2 marks** — **Review:** jQuery readiness/event/effect methods exceed the four explicitly listed jQuery topics; intended DOM-topic depth is unclear. **Treatment:** U; listed in [jQuery HTML Content and DOM Manipulation](#88-jquery-html-content-and-dom-manipulation) for review, excluded from confirmed frequency.

- **Same file, Group B Q2, p. 3, part of 10 marks** — **Review:** “Types of post backs” may refer to a technology-specific taxonomy absent from the syllabus. **Treatment:** Parent question P; this clause U. Study JSON/AJAX architecture only until clarified.

- **Official syllabus, p. 1, course-outcome reference to Java Beans** — **Review:** Modules pp. 2–3 prescribe Node.js, without a JavaBeans/JSP/servlet/JDBC unit. **Treatment:** Flag the discrepancy; the explicit module topics control scope.

- **2023 PDF composition/date** — **Review:** P. 1 has no coherent continuation; p. 2 is Android; p. 3 is undated IWT. **Treatment:** Keep page-specific attribution. Do not reconstruct missing marks, merge the sheets or date the undated one.

- **2021 screenshot provenance/marks** — **Review:** Filename-based dates; absent travel number; clipped vaccination marks; missing marks/truncated Q5(ii) in the second file. **Treatment:** Retain visible locators; label unverified details.

---

## Appendix D - Source Notes and Continuation Guide

Continue with numbered topics, connected explanations, focused examples and questions after teaching.

[RecSys](https://github.com/souiiii/Everything/tree/main/Midsem/RecSys) guides presentation; IWT material determines scope and content.

### Shared Applications

- Styled headings and travel text are included in the [complete travel answer](#38-website-layout-and-complete-page-design); no separate text-formatting marks are printed.[^pyq-05]
- The [retained layout answer](#38-website-layout-and-complete-page-design) includes the inline-styled iframe; `marquee` remains excluded.[^pyq-11]
- The [layout and travel answers](#38-website-layout-and-complete-page-design) apply the box model and margins.[^pyq-19]

### Examination Question Sources

[^pyq-01]: [2019 paper][paper-2019], Q1.A(i), PDF p. 1, 2 marks
[^pyq-02]: [2021 paper, 2019-23 batch][paper-2021-b], Q1(i), PDF p. 1, marks not visible
[^pyq-03]: [2019 paper][paper-2019], Q3.A(i), PDF p. 1, retained GET/POST part: 1 mark; original 2+1 marks · Retained portion
[^pyq-04]: [2019 paper][paper-2019], Q6.A(i), PDF p. 2, script-attributes part: 1 mark; original 1+1 marks · Retained portion
[^pyq-05]: [2021 paper, 2018-22 batch][paper-2021-a], unnumbered travel prompt, PDF p. 1, 10 points overall · Shared application.
[^pyq-06]: [2024 paper, image 1][paper-2024-a], Q2(a), 2 marks
[^pyq-07]: [2024 paper, image 2][paper-2024-b], Q2(e), 2 marks
[^pyq-08]: [2021 paper, 2018-22 batch][paper-2021-a], unnumbered travel prompt, PDF p. 1, 10 points
[^pyq-09]: [2019 paper][paper-2019], Q1.A(ii), PDF p. 1, 3 marks
[^pyq-10]: [2024 paper, image 2][paper-2024-b], Q2(d), 2 marks
[^pyq-11]: [2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), PDF p. 1, marks not visible · Retained portion · Shared application.
[^pyq-12]: [2019 paper][paper-2019], Q3.B, PDF p. 2, original 1+4 marks; no HTML-only split · Retained portion
[^pyq-13]: [2021 paper, 2019-23 batch][paper-2021-b], Q5(ii), PDF p. 4, marks not visible · Retained portion
[^pyq-14]: [2024 paper, image 2][paper-2024-b], Q3(a), 5 marks
[^pyq-15]: [2019 paper][paper-2019], Q1.B(i), PDF p. 1, 2 marks
[^pyq-16]: [2019 paper][paper-2019], Q1.B(ii), PDF p. 1, 3 marks
[^pyq-17]: [2024 paper, image 2][paper-2024-b], Q2(c), 2 marks
[^pyq-18]: [2024 paper, image 1][paper-2024-a], Q2(b), 2 marks
[^pyq-19]: [2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), PDF p. 1, marks not visible · Retained portion · Shared application.
[^pyq-20]: [2024 paper, image 1][paper-2024-a], Q1(a), 5 marks
[^pyq-21]: [2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), PDF p. 1, marks not visible · Retained portion
[^pyq-22]: [2024 paper, image 2][paper-2024-b], Q4(c), 2 marks
[^pyq-23]: [2019 paper][paper-2019], Q6.A(i), PDF p. 2, original 1+1 marks · Retained portion
[^pyq-24]: [2019 paper][paper-2019], Q2.A(i), PDF p. 1, 2 marks
[^pyq-25]: [2024 paper, image 2][paper-2024-b], Q4(a), 2 marks
[^pyq-26]: [2019 paper][paper-2019], Q5.B(ii), PDF p. 2, 1+1 marks
[^pyq-27]: [2024 paper, image 2][paper-2024-b], Q4(d), 2 marks
[^pyq-28]: [2024 paper, image 2][paper-2024-b], Q4(e), 2 marks
[^pyq-29]: [2019 paper][paper-2019], Q2.B(ii), PDF p. 1, 2 marks
[^pyq-30]: [2019 paper][paper-2019], Q6.A(ii), PDF p. 2, 3 marks
[^pyq-31]: [2024 paper, image 2][paper-2024-b], Q4(b), 2 marks
[^pyq-32]: [2024 paper, image 2][paper-2024-b], Q5(d), 2 marks
[^pyq-33]: [2024 paper, image 2][paper-2024-b], Q3(b), 5 marks
[^pyq-34]: [2024 paper, image 2][paper-2024-b], Q5(c), 2 marks
[^pyq-35]: [2021 paper, 2019-23 batch][paper-2021-b], Q2(ii), PDF p. 2, marks not visible
[^pyq-36]: [2024 paper, image 2][paper-2024-b], Q5(b), 2 marks for the entire item
[^pyq-37]: [2021 paper, 2019-23 batch][paper-2021-b], Q2(i), PDF p. 2, marks not visible
[^pyq-38]: [2021 paper, 2018-22 batch][paper-2021-a], Q2 (screenshot title), PDF p. 1, marks clipped/not verifiable
[^pyq-39]: [2024 paper, image 1][paper-2024-a], Q1(b), 5 marks
[^pyq-40]: [2024 paper, image 2][paper-2024-b], Q5(e), 2 marks
[^pyq-41]: [2019 paper][paper-2019], Q2.A(ii), PDF p. 1, 3 marks
[^pyq-42]: [2024 paper, image 2][paper-2024-b], Q5(a), 2 marks

### Supplementary source notes

Supplementary support for the completed topics:

[^web-history]: CERN, [A short history of the Web](https://home.cern/science/computing/the-birth-of-the-web/short-history-web/).
[^internet-history]: Internet Society, [A Brief History of the Internet](https://www.internetsociety.org/internet/history-internet/brief-history-internet/).
[^http-overview]: MDN, [Overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview).
[^http-messages]: MDN, [HTTP messages](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages).
[^cyber-law]: India Code, [Information Technology Act, 2000](https://www.indiacode.nic.in/bitstream/123456789/13116/1/it_act_2000_updated.pdf).
[^frames]: MDN, [The frameset element](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/frameset).
[^specificity]: MDN, [Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Specificity).
[^bindings]: MDN, [let declarations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let).
[^validation]: MDN, [Constraint validation](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Constraint_validation).
[^collections]: MDN, [querySelectorAll()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll).
[^cookies]: MDN, [Document.cookie](https://developer.mozilla.org/en-US/docs/Web/API/Document/cookie).
[^cookie-mechanism]: RFC Editor, [HTTP State Management Mechanism, RFC 6265](https://www.rfc-editor.org/info/rfc6265/).
[^cookie-indicator]: MDN, [Navigator.cookieEnabled](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/cookieEnabled).

[paper-2019]: <../Papers/CS201_Internet_and_Web_Technology_April_2019.pdf>
[paper-2021-a]: <../Papers/IWT 2021 Endsem (2018-22 batch).pdf>
[paper-2021-b]: <../Papers/IWT 2021 Endsem (2019-23 batch).pdf>
[paper-2023]: <../Papers/IWT_Question_Papers_2023.pdf>
[paper-2024-a]: <../Papers/A_1.png>
[paper-2024-b]: <../Papers/A_2.png>
