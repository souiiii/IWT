# Internet and Web Technology

## A guide to examination preparation

These notes follow the [official syllabus](../Syllabus/IWT-7th-Semester-IT.pdf). Module I is concise revision of familiar material; the completed JavaScript, DOM and BOM chapters explain the ideas more fully before applying them to examination problems. Advanced JavaScript and Module III remain clearly marked outlines.

Prioritise HTML/CSS construction, form validation and XML/DTD design: they recur across several supplied papers. Prepare AJAX, JSON, jQuery, React and Node.js as prescribed, even though their evidence comes from fewer, sometimes incomplete, papers. These priorities guide study time; they do not predict the next examination or exclude less frequently tested syllabus topics.

| Reading route | Purpose |
| --- | --- |
| [Module I](#module-i---the-web-html-and-css-8-hours) | Revise web fundamentals, HTTP, HTML and CSS. |
| [Module II](#module-ii---javascript-dom-bom-and-advanced-concepts-10-hours) | Learn JavaScript, then the DOM, forms and the browser environment. |
| [Module III](#module-iii---xml-ajax-jquery-json-reactjs-and-nodejs-12-hours) | Follow the remaining syllabus outline and question index. |
| [Examination evidence](#appendix-a---examination-evidence) and [source audit](#appendix-c---past-paper-scope-audit) | Check recurrence, original question details and scope decisions. |

Questions from the papers are identified by source, question number, page and verifiable marks; original practice is labelled separately. A **retained portion** answers only the syllabus-aligned part of an older question. Full filenames, source limitations and uncertain classifications are kept in the appendices so they do not interrupt the teaching.

## Module I - The Web, HTML and CSS (8 hours)

The Web brings together three familiar responsibilities: HTML describes a page, CSS presents it, and JavaScript controls its behaviour. This module revisits the network and document ideas on which those responsibilities depend. Read it as concise revision, paying particular attention to the distinctions that often become short examination questions.

### I.1 Internet, WWW and their histories

The **Internet** is a worldwide network of interconnected networks. It provides the communication infrastructure that allows computers to exchange data using the TCP/IP protocol suite. The **World Wide Web (WWW)** is one service built on that infrastructure: it makes linked pages and other resources available through URLs and web protocols. Email, for example, can use the Internet without being a web page.

A website brings related pages together, and a browser retrieves and presents them. Within a page, HTML describes the structure, CSS controls the presentation, and JavaScript supplies behaviour. Keeping these responsibilities separate makes the later topics easier to place.

The prescribed history can be remembered as a short sequence. ARPANET began in 1969, and the adoption of TCP/IP in 1983 helped establish the modern Internet. Tim Berners-Lee proposed the Web at CERN in 1989; the first website became publicly accessible in 1991. Hyperlinks then gave readers a straightforward way to move between networked documents.[^web-history][^internet-history]

> The Internet supplies the network; the Web uses that network to connect information and applications.

### I.2 Websites, web applications, web projects and development issues

A website may simply present information or allow the visitor to perform a task. A **static website** serves stored pages without needing to generate their contents for each request. A **dynamic website** can generate or update content using program logic and data. A **web application**, such as a registration or ordering system, is organised around a task the user wants to complete. One site may combine all of these features.

A web project begins by deciding who will use it and what they need. Those requirements guide the content, navigation and page design. Implementation follows the design; testing checks whether the result works; publishing makes it available; maintenance keeps it correct and useful.

For a tourism website, this means choosing the destinations and audience before writing pages, then checking that visitors can find the information and follow the links. Good development also considers usability, accessibility, browser compatibility, loading time, input handling, security and maintainability. Design succeeds when the site both communicates clearly and lets the user complete the intended task.

#### Examination practice

**Question 1.** What stages and strategies are required to develop a web project?

*[2019 paper][paper-2019], Q1.A(i), PDF p. 1, 2 marks*

**Answer.** Identify the audience and requirements; plan content and navigation; design the interface; implement pages and functionality; test correctness, usability and browser compatibility; deploy and maintain the site. Use consistent layouts and reusable styles, and review the result against the requirements.

See also: [2024 paper, image 1][paper-2024-a], Q1(a), 5 marks, Odisha tourism: full answer in [I.20](#i20-display-positioning-and-website-layout). [2024 paper, image 2][paper-2024-b], Q3(a), 5 marks, catalogue/ordering/billing pages: full answer in [I.13](#i13-html-forms-and-integrated-page-construction).

### I.3 Web architecture, web servers and browsers

In the **client-server model**, one program requests a service and another provides it. On the Web, the browser acts as a client: it requests resources, interprets HTML and CSS, and runs browser JavaScript. The web server accepts HTTP requests and returns the requested resources or the results of processing them.

A larger application often separates its work into three responsibilities. The presentation tier handles interaction, the application tier applies the business rules, and the data tier stores and retrieves information. This arrangement is called **three-tier web architecture**.

```text
Browser / presentation <--> Application / business logic <--> Database
          HTTP requests and responses       data operations
```

Imagine submitting a registration form. The browser presents the fields, the application checks and processes the submission, and the database stores the accepted record. The tiers describe a logical separation of work; they do not necessarily require three physical computers.

Client-server therefore describes the relationship between communicating roles, while three-tier architecture describes how an application divides its responsibilities.

#### Examination practice

**Question 1.** Explain client-server, three-tier web architecture, and their difference.

*[2021 paper, 2019-23 batch][paper-2021-b], Q1(i), PDF p. 1, marks not visible*

**Answer.** In client-server computing, a client sends a request and a server processes it and returns a response. Three-tier web architecture divides the system into a presentation tier for interaction, an application tier for processing/business rules, and a data tier for persistent storage. For example, a browser submits a registration to an application, which stores it in a database and returns confirmation. Three-tier architecture organises client-server communication by separating presentation, application processing and storage, as shown in the diagram above.

### I.4 Web protocols, Internet standards, TCP/IP and MIME

A **protocol** is a set of rules that communicating systems agree to follow. Standards make it possible for a browser and a server produced by different organisations to understand one another. IETF publishes Internet protocol specifications; W3C develops many web standards, while WHATWG maintains the HTML Living Standard.

The TCP/IP suite divides communication into layers. Each layer has a particular responsibility and relies on the layer beneath it.

| TCP/IP layer | Responsibility | Relevant examples |
| --- | --- | --- |
| Application | Defines communication for a particular service. | HTTP retrieves web resources; DNS resolves domain names. |
| Transport | Transfers data between applications. | TCP provides reliable, ordered delivery; UDP sends datagrams without TCP's delivery guarantees. |
| Internet | Addresses hosts and routes packets between networks. | IP. |
| Network access/link | Carries data across the local network. | Ethernet or Wi-Fi. |

In the HTTP/1.1 model used here, HTTP defines the requests and responses, TCP transports them reliably, and IP handles addressing and routing. HTTPS adds protection through TLS. These are different responsibilities within the same communication process.

The response must also tell the browser what kind of content it contains. **MIME (Multipurpose Internet Mail Extensions)** provides content-type conventions; on the Web, the `Content-Type` header identifies representations such as `text/html`, `text/css`, `image/png` or `application/javascript`. A MIME type describes the content, whereas a filename extension is part of its name.

### I.5 URL anatomy and HTTP messages

A browser needs both an address for a resource and rules for requesting it. The **URL (Uniform Resource Locator)** supplies the address; **HTTP (Hypertext Transfer Protocol)** defines the exchange between the browser and server.

#### Reading a URL

Consider `https://example.org:8443/books/list.html?topic=web#css`:

| Part | Value | Purpose |
| --- | --- | --- |
| Scheme | `https` | Identifies how the resource is accessed. |
| Host | `example.org` | Identifies the server. |
| Port | `8443` | Specifies an explicit service port. |
| Path | `/books/list.html` | Identifies the resource on that server. |
| Query | `topic=web` | Carries query data. |
| Fragment | `css` | Identifies a location within the resource. |

The fragment is handled by the browser and is not sent in the HTTP request. A relative URL such as `story.html` is resolved against the document's base URL.

#### From a request to a response

HTTP defines what the client requests and how the server reports the result. It is **stateless**: separate requests do not automatically become one remembered user session. Loading a page may involve several exchanges, beginning with HTML and continuing with its referenced stylesheets, images and scripts.[^http-overview]

An HTTP/1.1 message contains a start line, headers, a blank line, and an optional body. The request line identifies the method, request target and version:

```http
GET /books/list.html?topic=web HTTP/1.1
Host: example.org:8443
Accept: text/html

```

The response begins with a status line containing the version, status code and reason phrase. Headers describe the response, while the body carries its content:

```http
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 12

<h1>IWT</h1>
```

The body shown is 12 ASCII bytes without a trailing newline. `200` indicates success; `301` indicates permanent redirection, `404` that a resource was not found, and `500` a server error. The blank line separates metadata from content.[^http-messages]

The request method identifies the intended operation. **GET** requests a representation of a resource; an HTML GET form places its data in the URL query. **POST** submits data in the request body for processing, commonly to create or submit information. GET is intended for retrieval without changing server state. POST does not itself encrypt the data; HTTPS supplies transport protection.

> HTTP governs the exchange. HTML is one kind of content that exchange can carry.

#### Examination practice

**Question 1.** Differentiate GET and POST. JSP tags are excluded.

*[2019 paper][paper-2019], Q3.A(i), PDF p. 1, retained GET/POST part: 1 mark; original 2+1 marks · Retained portion*

**Answer.** GET requests a representation of a resource; HTML GET forms put their data in the URL query. POST submits data in the request body for processing.

### I.6 Connections, web caching and proxies

Opening a connection takes work. A **non-persistent HTTP connection** is used for one request-response exchange and then closed, so another exchange needs another connection. A **persistent connection** can be reused, avoiding repeated setup. HTTP/1.1 uses persistence by default unless the connection is closed. This describes connection reuse, rather than whether the user is logged in.

Caching saves a different kind of work. A **web cache** keeps reusable responses so that a fresh copy can be served without downloading it again. When necessary, the cache can ask the server whether its copy has changed. Reusing a valid response reduces delay, network traffic and server processing; storing it does not make it permanently valid.

A **proxy** forwards requests and responses between a client and a server. It may also cache responses or enforce access controls. A browser cache is local to the browser, whereas a proxy cache sits at an intermediary. A proxy does not have to cache every response.

> Persistence reuses a connection; caching reuses a response; a proxy provides an intermediary through which an exchange may pass.

#### Additional practice

**Original question · Suggested 4 marks.** Explain persistent connections and proxy caching, and state one benefit of each.

**Answer.** A persistent connection carries multiple HTTP exchanges over one TCP connection, reducing repeated setup overhead. A proxy cache stores reusable server responses between clients and origin servers. It can serve a fresh copy, reducing network traffic and response time; otherwise it forwards or revalidates the request. Persistence and caching can work together, but solve different problems.

### I.7 Cyber laws

**Cyber laws** govern conduct involving computers, networks and electronic communication. They provide legal accountability in a setting where people exchange personal information, enter electronic transactions and may encounter unauthorised access, identity theft or fraud.

In India, the Information Technology Act, 2000 provides a central framework for electronic records and signatures, as well as specified computer-related offences. Recognition of electronic records and offences involving identity theft or online impersonation are useful examples of its relevance to web activity.[^cyber-law]

For revision, connect the definition to its purpose: online activity needs recognised rights, responsibilities and consequences. The syllabus does not specify a list of provisions, so a clear explanation and relevant examples are sufficient here; detailed penalties and case law are not part of this treatment.

### I.8 HTML foundations and document metadata

**HTML (HyperText Markup Language)** describes the structure and meaning of a page. An element usually consists of an opening tag, its content and a closing tag. Attributes supply additional information about the element. Void elements, including `img`, `meta` and `br`, have no closing tag.

An HTML document separates information about the page from the page content itself. The `head` holds metadata and references to resources; the `body` holds the content presented to the reader. The following document shows both roles:

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

The `doctype` selects standards mode. Within the head, `title` names the browser tab, `meta` supplies metadata, `link` references an external resource, `style` contains CSS, and `script` includes JavaScript. The optional `base` element changes how relative URLs are resolved: here, `style.css` resolves under the specified course URL.

A useful distinction is that `head` describes the document, while a visible heading such as `h1` belongs to its content. HTML establishes that structure; CSS determines its appearance.

#### Examination practice

**Question 1.** Explain script-tag attributes. Detailed Java comparison is excluded; JavaScript characteristics are covered in II.1.

*[2019 paper][paper-2019], Q6.A(i), PDF p. 2, script-attributes part: 1 mark; original 1+1 marks · Retained portion*

**Answer.** `src` specifies an external script; `defer` downloads an external classic script without blocking parsing and executes it after parsing; `async` executes it when ready without preserving script order. `type` identifies the script type, for example `module`; ordinary JavaScript can omit it. Historical `language` is obsolete.

See also: the 2021 travel prompt requires an external stylesheet; its complete answer is in I.10.

### I.9 HTML text, headings and lists

Text becomes easier to follow when its structure is explicit. Use `h1`-`h6` for levels of headings, `p` for paragraphs and `br` for a line break within a passage. A heading identifies a section; it is more than a way to make text larger. Spacing and page layout belong in CSS rather than in repeated line breaks.

Formatting elements can also communicate meaning. `strong` marks importance and `em` emphasis; `b` and `i` can mark text without those meanings. `sub`, `sup`, `mark`, `small`, `del` and `ins` express common formatting and annotation needs.

```html
<h1>Web revision</h1>
<p><strong>Remember:</strong> H<sub>2</sub>O and x<sup>2</sup>.</p>
<p><em>Read the example.</em><br>Then write it yourself.</p>
<ul><li>HTML</li><li>CSS</li></ul>
<ol><li>Plan</li><li>Implement</li><li>Test</li></ol>
<dl><dt>HTTP</dt><dd>A web request-response protocol.</dd></dl>
```

The three list forms organise different relationships. An unordered list (`ul`) groups items whose order is not essential; an ordered list (`ol`) presents a sequence; a description list (`dl`) pairs terms (`dt`) with descriptions (`dd`). Choose the structure that expresses the relationship between the items.

#### Examination practice

**Application in a shared question.** Styled headings and travel-story text are part of the integrated task. The complete model in I.10 includes both; no separate marks for text formatting are printed.

*[2021 paper, 2018-22 batch][paper-2021-a], unnumbered travel prompt, PDF p. 1, 10 points overall*

### I.10 Anchors, images and video

Links and media give a page something to navigate and something to show. An anchor's `href` identifies its destination, whether another resource or a fragment within the current document. An image's `src` identifies the image, while `alt` supplies a text alternative and `width`/`height` specify dimensions. A `video` element can provide playback controls and alternative sources.

```html
<a href="story.html">Read the travel story</a>
<a href="#contact">Go to contact details</a>
<img src="puri.jpg" alt="Beach at Puri" width="300" height="180">
<video controls width="320" poster="preview.jpg">
  <source src="tour.mp4" type="video/mp4">
  Your browser does not support this video.
</video>
<h2 id="contact">Contact details</h2>
```

The first link opens another page. The second uses `#contact` to move to the element whose `id` is `contact`. Placing an image inside an anchor makes the image itself clickable, which is the key idea in the travel-page question below.

An image's `alt` text serves as an alternative to the image; it is not a tooltip. The `title` attribute may supply advisory text. Keeping these roles distinct makes both definitions and examples more precise.

#### Examination practice

**Question 1.** Give image syntax and explain its attributes.

*[2024 paper, image 1][paper-2024-a], Q2(a), 2 marks*

**Answer.** `<img src="puri.jpg" alt="Beach at Puri" width="300" height="180">`. `src` is the image URL, `alt` is alternative text, and `width`/`height` set dimensions. It is a void element and needs no end tag.

**Question 2.** Explain anchor navigation and scrolling with an example.

*[2024 paper, image 2][paper-2024-b], Q2(e), 2 marks*

**Answer.** `<a href="story.html">Story</a>` opens another document. `<a href="#contact">Contact</a>` navigates to an element such as `<h2 id="contact">Contact</h2>` within the document. The fragment causes the browser to move to that target.

**Question 3.** Display favourite holiday destinations as images linking to story pages; use external CSS for headings, images, links, margins and backgrounds.

*[2021 paper, 2018-22 batch][paper-2021-a], unnumbered travel prompt, PDF p. 1, 10 points*

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

### I.11 HTML tables

A table presents data whose meaning depends on rows and columns. The `table` element encloses the structure, `tr` creates a row, `th` marks a header cell and `td` a data cell. A `caption` gives the table a title. Use header cells for labels and data cells for entries so that the structure remains clear.

When one entry covers several positions, `colspan` spans columns and `rowspan` spans rows. For example, `<tr><td colspan="2">Total</td></tr>` places one cell across two columns. These attributes describe the table's structure; borders, padding, spacing and alignment are controlled with CSS.

The following examination examples show how that small set of elements produces a complete table.

#### Examination practice

**Question 1.** Write HTML for the pictured Roll No./Student Name/Subject Name table.

*[2019 paper][paper-2019], Q1.A(ii), PDF p. 1, 3 marks*

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

**Question 2.** Explain tags/attributes for HTML/CSS tables with examples.

*[2024 paper, image 2][paper-2024-b], Q2(d), 2 marks*

**Answer.** `table`, `tr`, `th` and `td` define the table, rows, header and data cells. `colspan="2"` spans two columns and `rowspan="2"` two rows. `table { border-collapse: collapse; }` and `th, td { border: 1px solid; padding: 4px; }` style the table. The table in the preceding answer demonstrates the row and cell structure.

### I.12 Frames

A **frame** displays another HTML document within a browsing area. The `iframe` element embeds that document inside an ordinary page, giving it its own display area:

```html
<iframe src="story.html" title="Travel story"
        style="width: 100%; height: 180px; border: 1px solid black;"></iframe>
```

This differs from a DIV: a DIV groups content in the same document, whereas an iframe contains a separate document.

The syllabus also uses the historical term “frames”, so recognise `<frameset cols="25%,75%"><frame src="menu.html"><frame src="main.html"></frameset>`. In that older document form, a frameset replaced the normal body. The `frameset` and `frame` elements are obsolete in HTML5; the retained layout task uses an iframe.[^frames]

#### Examination practice

**Application in a shared question.** The diagram includes an iframe with inline styles. The full retained layout answer is in I.20. Its additional `marquee` requirement remains excluded.

*[2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), PDF p. 1, marks not visible · Retained portion*

### I.13 HTML forms and integrated page construction

A **form** collects related input and gives the user a way to submit it. Its `action` identifies the receiving resource and its `method` determines the submission method. Controls normally need `name` attributes to contribute values to the submission; an `id` instead identifies an element within the document.

Different controls suit different kinds of input. Radio buttons sharing one name represent alternatives, while a checkbox represents an independent choice. A `select` provides a list of options, and a `textarea` accepts multiline text. Labels explain what each control expects.

```html
<form action="/register" method="post">
  <label>Name <input name="student" required></label>
  <label>Course <select name="course"><option>IWT</option></select></label>
  <label><input type="checkbox" name="updates" value="yes">Send updates</label>
  <label>Message <textarea name="message"></textarea></label>
  <button type="submit">Register</button>
</form>
```

A submit button initiates submission. A button with `type="button"` performs only its programmed action. Constraints such as `required`, input types and JavaScript checks help the user provide suitable data, but a receiving server must still validate it. The fuller treatment in II.11 combines the language and DOM techniques needed to read, check and display form values.

#### Examination practice

**Question 1.** Retain the HTML registration form with first/last name, email, password, gender radio buttons and submit.

*[2019 paper][paper-2019], Q3.B, PDF p. 2, original 1+4 marks; no HTML-only split · Retained portion*

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

**Question 2.** Retain the explicitly requested `index.html` login page.

*[2021 paper, 2019-23 batch][paper-2021-b], Q5(ii), PDF p. 4, marks not visible · Retained portion*

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

See also: both 2021 registration/validation tasks and [2024 paper, image 1][paper-2024-a], Q1(b), 5 marks, hackathon application, have complete models in II.11. Reuse those answers rather than studying duplicate implementations.

**Question 3.** Design a local-product shopping site with catalogue, ordering and billing pages.

*[2024 paper, image 2][paper-2024-b], Q3(a), 5 marks*

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

### I.14 Inline, internal and external CSS

CSS separates how a document looks from what its HTML means. A rule such as `p { color: navy; }` selects paragraphs and gives their text a navy colour. The selector identifies the elements; the declaration block contains property-value pairs that describe their presentation.

The same rule can be attached to a document in three ways:

| Method | Example | Where it applies |
| --- | --- | --- |
| Inline | `<p style="color: navy;">Hello</p>` | The individual element. |
| Internal | `<style>p { color: navy; }</style>` in `head` | The current document. |
| External | `<link rel="stylesheet" href="site.css">`, with the rule in that stylesheet | Any document that links to the stylesheet. |

External CSS is especially useful when several pages share one design: changing the stylesheet can update them together. The placement of a rule, however, is only part of deciding whether it wins. The next topic explains how matching selectors and specificity resolve competing declarations.

#### Examination practice

**Question 1.** Explain ways of using CSS in HTML, with examples.

*[2019 paper][paper-2019], Q1.B(i), PDF p. 1, 2 marks*

**Answer.** Inline CSS uses the `style` attribute, as in `<p style="color: navy;">Hello</p>`. Internal CSS uses a rule such as `<style>p { color: navy; }</style>` in `head`. External CSS uses `<link rel="stylesheet" href="site.css">`, with the rule in that stylesheet, allowing several pages to share it.

See also: the unnumbered travel task in [2021 paper, 2018-22 batch][paper-2021-a], p. 1, 10 points, is answered fully in I.10; the retained CSS/iframe task in [2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), p. 1, marks not visible, is answered in I.20.

### I.15 CSS selectors, combinators, attribute selectors and specificity

A **selector** describes which elements a CSS rule should affect. Some selectors identify an element directly, while others describe a group or a relationship. A class may be shared across several elements; an ID should identify one element in the document. A comma combines separate selectors, whereas a **combinator** describes how elements are related.

#### Selecting elements and relationships

| Selector | Meaning |
| --- | --- |
| `p`, `.note`, `#result`, `*` | Element, class, ID and universal selector. |
| `h1, h2` | Both sets of headings. |
| `article p`, `article > p` | Any descendant paragraph; a direct-child paragraph. |
| `h2 + p`, `h2 ~ p` | The next sibling paragraph; later sibling paragraphs with the same parent. |
| `input[type="email"]`, `[required]` | A matching attribute value; the presence of an attribute. |
| `[href^="https"]`, `[href$=".pdf"]`, `[class~="note"]` | A value that starts with, ends with, or contains a space-separated word. |

Notice the difference between `p.note` and `.note p`. The first selects a paragraph that itself has the class `note`; the second selects a paragraph inside an element with that class. Reading a selector as a description of elements helps avoid confusing the two.

#### Resolving competing rules

**Specificity** compares matching selectors when their declarations are otherwise comparable. Count IDs first, then classes/attributes/pseudo-classes, then elements/pseudo-elements. Thus `#result` outranks `.note`, which outranks `p`. If competing rules remain equal, the later declaration wins.[^specificity]

```html
<style>
  p { color: blue; }
  .note { color: green; }
  #result { color: red; }
</style>
<p id="result" class="note">This text is red.</p>
```

The paragraph is red because the ID selector has greater specificity. Normal inline styling outranks normal stylesheet declarations, while an applicable `!important` declaration can override a normal inline declaration. This is why “internal always beats external” is not a reliable rule: the cascade must first compare the declarations and their selectors, then use source order when the relevant priorities tie.

#### Examination practice

**Question 1.** Name the selector used to specify a group of elements and justify it.

*[2019 paper][paper-2019], Q1.B(ii), PDF p. 1, 3 marks*

**Answer.** A **class selector** applies a shared style to a group of elements assigned the same class: `.notice { color: red; }` matches both `<p class="notice">Exam</p>` and `<h2 class="notice">Revision</h2>`. Unlike an ID, a class is reusable across elements. If “group” is used to mean a **grouping selector**, explain the comma form too: `h1, h2, p { color: red; }` applies one rule to several selector groups. The printed question does not distinguish these two meanings; state the interpretation rather than silently guessing.

See also: [2024 paper, image 2][paper-2024-b], Q5(c), 2 marks, JavaScript access through selectors: full model in II.8.

### I.16 Pseudo-classes and pseudo-elements

A page often needs to distinguish an element's state from a particular part of its content. A **pseudo-class** selects an element in a state or relationship: `a:hover` selects a hovered link, `input:focus` the focused input, and `li:first-child` a list item that is its parent's first child. `a:visited` describes a link's visited state.

A **pseudo-element** instead selects part of an element or supplies generated content. For example, `p::first-line` refers to the first formatted line and `p::first-letter` to the first letter. `::before` and `::after` generate content around an element's content, while `::selection` styles selected text.

```css
a:hover { color: red; }
p::first-letter { font-size: 2em; }
p::first-line { font-weight: bold; }
.notice::before { content: "Note: "; }
.notice::after { content: " *"; }
::selection { background: gold; }
```

> A pseudo-class describes the element's state or relationship. A pseudo-element addresses a part of it or generated content.

The double colon distinguishes pseudo-elements from pseudo-classes. In particular, `::before` and `::after` normally need a `content` declaration to produce visible generated content.

#### Examination practice

**Question 1.** Define a pseudo-element and explain CSS pseudo-elements.

*[2024 paper, image 2][paper-2024-b], Q2(c), 2 marks*

**Answer.** A pseudo-element styles a selected part of an element. `::first-line` styles its first formatted line and `::first-letter` its first letter; `::before`/`::after` insert generated content; `::selection` styles selected text. For example, `p::first-letter { color: red; }`.

### I.17 Colors and backgrounds

The `color` property sets the text colour, while background properties paint the area behind the content. A colour can be written as a name such as `navy`, a hexadecimal value such as `#003366`, an RGB value such as `rgb(0,51,102)`, or a value with transparency such as `rgba(0,51,102,0.5)`.

A background may combine a colour with an image. The properties below specify the image's repetition, position, size and behaviour during scrolling:

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

`repeat` tiles the image, while `no-repeat` prevents tiling. `cover` scales it to cover the area and may crop it. The usual `scroll` attachment moves with the element; `fixed` keeps the background fixed relative to the viewport.

The shorthand collects several settings into one declaration, but it can also reset omitted component properties. Read it as a complete background setting rather than assuming it preserves every earlier value. An HTML image contributes content to the document; a CSS background supplies presentation behind that content.

#### Examination practice

**Question 1.** Explain CSS background properties with examples.

*[2024 paper, image 1][paper-2024-a], Q2(b), 2 marks*

**Answer.** `background-color: lightblue` sets a color; `background-image: url("paper.png")` supplies an image; `background-repeat: no-repeat` prevents tiling; `background-position: center` positions it; `background-attachment: fixed` keeps it fixed during scrolling. These can be combined, for example `background: lightblue url("paper.png") no-repeat center fixed;`.

See also: the travel prompt ([2021 paper, 2018-22 batch][paper-2021-a], p. 1, 10 points) and retained layout task ([2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), p. 1, marks not visible) are answered in I.10 and I.20.

### I.18 Borders, margins, padding and units

Every rendered element occupies a box. Starting at its content, the **box model** adds padding, then a border, then an outside margin. Padding gives the content room inside its border; margin separates the box from its neighbours. A visible border needs a style such as `solid` as well as its width and colour.

```text
margin -> border -> padding -> content -> padding -> border -> margin
```

#### Calculating the space a box occupies

Consider the following rule:

```css
.card {
  width: 200px;
  padding: 10px;
  border: 2px solid navy;
  margin: 15px;
}
```

With the default `content-box` sizing, `width` refers to the content alone. Adding the left and right padding and borders gives a border-box width of `200 + 20 + 4 = 224px`. Including the horizontal margins gives `254px` of occupied space.

The calculation is:

$$
W_{\text{border box}} = W_{\text{content}} + P_{\text{left}} + P_{\text{right}} + B_{\text{left}} + B_{\text{right}}.
$$

With `box-sizing: border-box`, the declared width already includes content, padding and border. **Margins remain outside the declared width in both models.**

#### Choosing units and shorthand values

A `px` is a CSS pixel; `%` uses the relevant reference dimension. An `em` is relative to font size, or to the parent's font size when setting `font-size`; `rem` refers to the root font size. The units `vw` and `vh` are percentages of the viewport's width and height.

Spacing shorthand follows a consistent order. Four values mean top, right, bottom and left; two values mean vertical and horizontal. Keeping padding inside the border and margin outside it is more useful than memorising the properties as interchangeable spacing controls.

#### Examination practice

**Application in a shared question.** The CSS box-model layout is answered in I.20. Margins also appear in the 10-point travel task answered in I.10.

*[2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), PDF p. 1, marks not visible · Retained portion*

#### Additional practice

**Original question · Suggested 3 marks.** A content-box element has width 180px, padding 8px, border 1px and margin 10px on every side. Find its border-box width and total horizontal space.

**Answer.** Border-box width = `180 + 2(8) + 2(1) = 198px`. Total horizontal space including margins = `198 + 2(10) = 218px`. Padding lies inside the border; margin lies outside it.

### I.19 Fonts, links, icons, lists and table styling

Typography and the styling of familiar HTML structures make a page readable and its controls recognisable. Font properties choose a typeface, size, weight and style; link rules indicate interaction states; list and table properties clarify how items belong together.

```css
body { font-family: Arial, sans-serif; font-size: 16px; line-height: 1.5; }
h1 { font-weight: bold; font-style: normal; }
a:link { color: navy; }
a:visited { color: purple; }
a:hover, a:focus { text-decoration: underline; }
a:active { color: red; }
.icon { color: navy; font-size: 1.2em; }
ul { list-style-type: square; list-style-position: inside; }
table { width: 100%; border-collapse: collapse; }
th, td { border: 1px solid #777; padding: 6px; text-align: left; }
```

A generic fallback such as `sans-serif` lets the browser choose a suitable font when the preferred typeface is unavailable. Link states such as `:hover` and `:visited` are pseudo-classes, so their styles apply when the corresponding state holds.

An **icon** is a small visual symbol. It can be an image or a text symbol styled with CSS; for example, `<span class="icon" aria-hidden="true">&#9733;</span> Favourite` places a styled star beside its text label. No icon library is needed for this topic.

For lists, `list-style-image: url("bullet.png")` supplies image bullets, and `list-style` combines the list settings. In a table, cell padding creates room inside each cell. By contrast, `border-spacing` separates cells in a separated-border table, while `border-collapse: collapse` merges adjacent borders. These properties solve different spacing problems.

#### Examination practice

Related examination practice: [2024 paper, image 2][paper-2024-b], Q2(d), 2 marks, table tags/styling has a full model in I.11; the 2021 travel prompt, p. 1, 10 points overall, includes styled headings/links and is answered in I.10.

### I.20 Display, positioning and website layout

A page layout determines where elements appear, how much room they occupy and what happens when content does not fit. Begin with normal document flow, then consider the properties that change it.

#### Display and overflow

A block box normally begins on a new line; inline content flows with surrounding text. `inline-block` keeps an element in that inline flow while allowing explicit dimensions. Hiding an element also has two distinct meanings: `display: none` removes its layout box, while `visibility: hidden` preserves the space but hides the contents.

When content exceeds its box, `overflow: auto` provides scrolling when needed, `hidden` clips the excess and `visible` lets it extend beyond the box.

#### Positioning, alignment and columns

| Setting | Effect |
| --- | --- |
| `position: static` | Uses normal flow. |
| `position: relative` | Offsets the element while retaining its original space. |
| `position: absolute` | Removes the element from normal flow and places it against its containing block, usually the nearest positioned ancestor. |
| `position: fixed` | Normally positions the element against the viewport. |
| `position: sticky` | Keeps normal behaviour until a specified scrolling threshold is reached. |
| `float: left/right` | Lets surrounding inline content wrap beside the floated element. |
| `clear` | Prevents an element from sitting beside earlier floats. |

For horizontal alignment, `text-align: center/right` aligns inline content; `margin: auto` centres a block that has a suitable width. `vertical-align: middle` applies to inline-level or table-cell content, rather than to arbitrary block boxes.

Text can also flow through newspaper-style columns using `column-count`, `column-gap` and `column-rule`. The following rules combine that idea with a floated picture and a section that clears earlier floats:

```css
.reading { column-count: 2; column-gap: 2rem; column-rule: 1px solid #aaa; }
.picture { float: left; margin-right: 1rem; }
.next { clear: both; }
```

A complete website arranges these boxes into navigation, a header, content and a footer. The examination tasks below apply the same properties to recognisable pages.

#### Examination practice

**Question 1.** Design an HTML/CSS website about tourism sites of Odisha.

*[2024 paper, image 1][paper-2024-a], Q1(a), 5 marks*

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

**Question 2.** Explain CSS usage and reproduce the pictured layout using the box model and different backgrounds. Retain float menu, centred header, right-aligned content/footer and inline-styled iframe; exclude the `marquee` instruction.

*[2021 paper, 2019-23 batch][paper-2021-b], Q1(ii), PDF p. 1, marks not visible · Retained portion*

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

See also: [2021 paper, 2019-23 batch][paper-2021-b], Q2(ii), p. 2, marks not visible, user-sized DIV/text wrapping: complete JavaScript/DOM model in II.8.

### I.21 Navigation bars, dropdowns, image galleries and styled forms

A navigation bar, dropdown, gallery or styled form is a composition of the selectors and layout properties already introduced. A navigation bar presents links consistently; a dropdown reveals a subordinate group of links; a gallery repeats image or image-link items. Form styles help readers distinguish labels, fields and actions.

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

In this example, the dropdown's parent is positioned so that its absolutely positioned submenu is placed relative to that parent. The submenu is normally hidden and appears when the parent is hovered or contains focus. The gallery uses inline-block links to place images alongside one another.

The same principles apply to forms: consistent spacing, readable labels and a clear border make fields easier to scan. Meaningful link destinations and image alternatives remain important regardless of the styling.

#### Examination practice

Related examination practice: the travel/gallery task ([2021 paper, 2018-22 batch][paper-2021-a], p. 1, 10 points) has its complete answer in I.10. The hackathon form ([2024 paper, image 1][paper-2024-a], Q1(b), 5 marks) is answered in II.11.

### I.22 Opacity, text effects, animations, tooltips and counters

The remaining CSS effects refine the presentation of content without changing its underlying structure. **Opacity** controls the transparency of the entire element, including its contents: `0` is transparent and `1` is opaque. An alpha background colour instead changes only that background.

**Text effects** include shadows, wrapping and an ellipsis when text is clipped. An **animation** changes property values through named keyframes over time. A **tooltip** reveals a short explanation, while a **counter** numbers repeated elements automatically.

```html
<style>
  .faded { opacity: 0.5; }
  .heading { text-shadow: 1px 1px 2px #aaa; }
  .short { width: 12em; white-space: nowrap; overflow: hidden;
           text-overflow: ellipsis; }
  .wrap { overflow-wrap: anywhere; }
  @keyframes highlight { from { background: white; } to { background: gold; } }
  .notice { animation: highlight 2s infinite alternate; }
  .tip { position: relative; }
  .tip span { display: none; position: absolute; top: 100%; left: 0;
              padding: 4px; background: black; color: white; }
  .tip:hover span, .tip:focus span { display: block; }
  .steps { counter-reset: step; }
  .steps p::before { counter-increment: step; content: counter(step) ". "; }
</style>
<p class="faded">Half opacity</p>
<h2 class="heading">Revision</h2>
<p class="short">A long sentence that does not fit in this narrow area.</p>
<p class="wrap">averylongwordthatmustwrapinsideitscontainer</p>
<p class="notice">Exam notice</p>
<button class="tip" type="button">Help<span>Enter your student name.</span></button>
<div class="steps"><p>Read</p><p>Practise</p></div>
```

Each effect depends on a small mechanism. The ellipsis needs a constrained width and clipping; the animation needs keyframes and a duration. The tooltip is hidden until interaction reveals it, and the counter is reset, incremented and displayed through generated content.

These CSS mechanisms are sufficient for the prescribed topics. CSS animation remains distinct from the historical `marquee` instruction excluded from the older paper.

## Module II - JavaScript, DOM, BOM and advanced concepts (10 hours)

JavaScript turns a page into something a reader can use: it calculates, responds to actions and updates what the browser displays. Begin with the language itself, then learn how it reaches the document through the DOM. The form examples bring those ideas together; the BOM topics that follow explain the surrounding browser environment.

### II.1 JavaScript introduction, statements, comments and bindings

JavaScript gives a page behaviour. It can calculate a total, check a form, respond to a button or change the text the reader sees. HTML supplies the structure and CSS the presentation; JavaScript expresses the decisions and actions that make the page interactive.

#### Values, variables and statements

A **statement** performs an action, while an **expression** produces a value. In `const total = 3 * 200;`, the multiplication is an expression and the declaration gives its result a name. Comments explain the code without running as instructions: `//` begins a single-line comment and `/* ... */` encloses a block comment.

A variable is a named binding to a value. JavaScript is **dynamically typed**: a value has a type, and a reassignable variable can later hold a value of another type. Common values include numbers (`12`), strings (`"IWT"`) and booleans (`true`). `undefined` usually indicates an uninitialised or missing value, while `null` can express an intentional absence. Objects and arrays hold related data.

Quotes matter: `"12"` is text, whereas `12` is a number. The following example uses numeric values to calculate a cost:

```javascript
const price = 200;          // This binding will not be reassigned.
let quantity = 2;           // It may change.
quantity = quantity + 1;
const total = price * quantity;
console.log(total);         // 600
```

#### Scope and declarations

**Scope** describes where a binding can be accessed. A function introduces a scope, and a block groups statements between braces. The choice of declaration determines whether a binding belongs to the whole function or to a particular block.

| Declaration | Scope | Reassignment | Same-scope redeclaration | Access before the declaration is reached |
| --- | --- | --- | --- | --- |
| `var` | Function scope, or global at top level | Allowed | Usually allowed with another `var` | The binding exists with `undefined`. |
| `let` | Block scope | Allowed | Not allowed | Throws `ReferenceError`. |
| `const` | Block scope | Not allowed; requires an initial value | Not allowed | Throws `ReferenceError`. |

The scope difference becomes visible when the code leaves a block:

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

A `const` declaration prevents reassignment of its binding, but does not freeze an object. Thus `const item = { qty: 1 }; item.qty = 2;` is allowed, while assigning a different object to `item` is not. The access-before-initialisation distinction in the table is enough for the present comparison; hoisting is developed in the planned advanced section.[^bindings]

#### Operators and decisions

Arithmetic operators calculate values: `+`, `-`, `*`, `/`, `%` for remainder and `**` for powers. `++` and `--` increment or decrement, while `=`, `+=` and `-=` assign or update values. Comparisons such as `<`, `<=`, `>`, `>=`, `===` and `!==` test relationships; `&&`, `||` and `!` combine or negate logical conditions.

Strict equality compares without converting types: `2 === "2"` is false, while `2 == "2"` is true because `==` permits conversion. Likewise, `typeof 12` is `"number"` and `typeof "12"` is `"string"`. The `+` operator can also join text, so `"2" + 3` produces `"23"`. Form values arrive as strings: check for blank input, then use `Number(value)` when arithmetic is intended. In particular, `Number("")` produces zero.

An `if/else` selects a branch, the conditional operator expresses a short choice, and a `switch` selects among cases:

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

> Assignment changes a value; comparison tests a relationship. A number and text that looks like a number are still different values.

Use parentheses when the intended grouping of an expression might be unclear. The numeric examples here use ordinary small inputs; JavaScript numbers have finite precision.

#### Examination practice

**Question 1.** Differentiate `let` and `var`.

*[2024 paper, image 2][paper-2024-b], Q4(c), 2 marks*

**Answer.** `let` is block-scoped, whereas `var` is function-scoped. `let` cannot be redeclared in the same scope; `var` generally can. A `var` binding can be read as `undefined` before its declaration is executed, while accessing `let` before initialisation throws an error. For example, in `if (true) { var a = 1; let b = 2; }`, `a` remains accessible in the enclosing function but `b` does not.

**Question 2.** Retain introductory JavaScript characteristics and script attributes; exclude detailed Java study.

*[2019 paper][paper-2019], Q6.A(i), PDF p. 2, original 1+1 marks · Retained portion*

**Answer.** JavaScript is dynamically typed and can run in the browser to handle events, validate forms and update the document. It is a separate language, not a variant of Java. Script inclusion/attributes are answered in I.8. No separate retained-only mark total is inferred for the comparison.

### II.2 Functions, objects and `this`

A **function** gives a name to an operation so that the program can perform it with different inputs. Parameters name those inputs inside the function; arguments are the actual values supplied by a call. A `return` statement supplies the result and ends that invocation. Without an explicit result, the function returns `undefined`.

```javascript
function cost(price, quantity) {
  const total = price * quantity;    // Local to this invocation
  return total;
}
console.log(cost(200, 3));           // 600
```

Here, `price` and `quantity` are parameters, while `200` and `3` are arguments. The local `total` belongs to that invocation, and `return` makes its value available to the caller.

#### Objects, methods and `this`

An **object** groups named properties that belong together. A property whose value is a function is a **method**. Dot access uses a known property name, as in `student.name`; bracket access can use a variable, as in `student[key]`. Assignment adds or updates a property, while `delete student.phone` removes one.

When an ordinary method is called as `object.method()`, **`this` refers to the receiving object**. The method can therefore use that object's current data instead of hard-coding the object's name:

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

The call `student.result()` makes `student` the receiver, so `this.name` and `this.marks` refer to that student's properties. The value of `this` depends on the call; it is not universally fixed by where a function was written.

It also helps to distinguish a function from a call to it. `result` refers to a function, while `result()` invokes it. This distinction will matter again when functions are registered as event handlers.

#### Examination practice

**Question 1.** State the purpose of `this` in JavaScript, with an example.

*[2019 paper][paper-2019], Q2.A(i), PDF p. 1, 2 marks*

**Answer.** In `object.method()`, `this` refers to the object on which the method is called, allowing access to its properties. For example, `const s = { name: "Anu", show: function () { return this.name; } }; console.log(s.show());` prints `Anu`.

**Question 2.** Add a function to an object and access it with an example.

*[2024 paper, image 2][paper-2024-b], Q4(a), 2 marks*

**Answer.**

```javascript
const item = { price: 200, qty: 3 };
item.total = function () { return this.price * this.qty; };
console.log(item.total());          // 600
```

`total` is a function-valued property; `item.total()` invokes it, with `this` referring to `item`.

See also: [2019 paper][paper-2019], Q6.A(ii), p. 2, 3 marks, sum of the first n primes: complete model in II.4.

### II.3 Strings, numbers, arrays, Date, Math and random values

Programs commonly work with text, numerical values, ordered collections and dates. JavaScript provides built-in facilities for each, so many examination tasks reduce to choosing the right value and operation.

#### Working with text

A **string** stores text, with character positions counted from zero. Its `length` is a property rather than a method: `"Web".length` is `3`. Strings are immutable, so operations produce results without altering the original string. For example, `" Web ".trim()` produces `"Web"` while leaving the original value unchanged.

Other useful operations follow the same idea. `split(",")` separates comma-delimited text into an array, and `replace()` produces text with a replacement. The examination table below gives five further method examples with their results.

#### Converting and displaying numbers

A **number** supports arithmetic. `Number("12.5")` converts a whole numeric string; `parseInt("12", 10)` parses a decimal integer and `parseFloat("12.5")` a floating-point value. Before converting a form field, check that it is not blank: conversion alone does not establish that the user supplied a number.

`Number.isNaN(value)` identifies the special not-a-number value, while `Number.isFinite(value)` rejects infinity and NaN. For presentation, `price.toFixed(2)` produces a string rounded to two decimal places; it does not create a new numeric type.

#### Arrays and changes to their contents

An **array** stores an ordered collection using zero-based indices. With `const a = ["HTML", "CSS"];`, the first entry is `a[0] === "HTML"` and `a.length === 2`. `push()` and `pop()` add and remove at the end. The contents may change even when the array's binding was declared with `const`.

The next example shows several operations in sequence, making both their return values and their effects visible:

```javascript
const a = [10, 20, 30];
console.log(a.join("-"));           // "10-20-30"; array unchanged
const removed = a.splice(1, 1, 25); // Remove one at index 1; insert 25
console.log(removed, a);            // [20], [10, 25, 30]
console.log(a.shift(), a);          // 10, [25, 30]
console.log(a.unshift(5), a);       // 3, [5, 25, 30]
```

`join()` produces a string without changing the array. `splice()` changes the array and returns the removed entries; `slice()` instead copies a portion. `shift()` returns the first entry it removes, while `unshift()` returns the new length after inserting at the front.

#### Dates, mathematical functions and random values

A **Date** represents a date/time value. `new Date()` obtains the current value; `getFullYear()`, `getMonth()` and `getDate()` extract local calendar components. Months start at zero, so add one for a human-readable month number. `getDay()` returns the weekday from 0 to 6, not the day of the month. `toLocaleDateString()` gives a readable local date.

**Math** supplies numeric functions without requiring a Math object to be constructed. For random values, `Math.random()` returns a number from 0 inclusive to 1 exclusive. To obtain an integer from `low` to `high` inclusive, use `Math.floor(Math.random() * (high - low + 1)) + low`. Thus `Math.floor(Math.random() * 6) + 1` simulates a six-sided die.

#### Examination practice

**Question 1.** Give five JavaScript Math methods and five String methods with examples.

*[2019 paper][paper-2019], Q5.B(ii), PDF p. 2, 1+1 marks*

**Answer.** The following examples give five Math methods and five String methods with their results:

| Math example | Result | String example | Result |
| --- | --- | --- | --- |
| `Math.abs(-4)` | `4` | `"Web".charAt(0)` | `"W"` |
| `Math.sqrt(25)` | `5` | `"Web".indexOf("e")` | `1` |
| `Math.floor(2.8)` | `2` | `"Web".substring(1, 3)` | `"eb"` |
| `Math.ceil(2.2)` | `3` | `"Web".toUpperCase()` | `"WEB"` |
| `Math.round(2.6)` | `3` | `"Web".toLowerCase()` | `"web"` |

**Question 2.** Explain `join()`, `splice()`, `shift()` and `unshift()`.

*[2024 paper, image 2][paper-2024-b], Q4(d), 2 marks*

**Answer.** `join(separator)` returns a string of joined array elements; `splice(start, count, ...items)` removes/inserts elements in place and returns removed elements; `shift()` removes/returns the first element; `unshift(...items)` inserts at the front and returns the new length. The sequential example above shows all four results.

**Question 3.** Write a function to display today's date in the browser.

*[2024 paper, image 2][paper-2024-b], Q4(e), 2 marks*

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

### II.4 Loops and small programs

A **loop** repeats an operation while moving towards an ending condition. To understand one, identify where it starts, what keeps it running and what changes on each iteration. A missing update can prevent it from finishing; a mistaken boundary can make it run once too often or once too few.

| Loop | How it is controlled |
| --- | --- |
| `for` | Keeps initialisation, condition and update together. |
| `while` | Tests the condition before each execution of the body. |
| `do...while` | Tests afterwards, so the body runs at least once. |

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

The `for...of` form visits array values, while `for...in` enumerates property keys and is not the usual choice for array values. Within a loop, `break` ends repetition and `continue` skips to the next iteration.

The starting value should match the calculation: begin a sum at zero and a factorial product at one. Prime testing must reject values below 2. These small decisions are central to the numerical questions below.

> “The first n primes” counts how many primes to find. “Primes up to n” sets a limit on their values.

#### Examination practice

**Question 1.** Find a number's factorial using input from a prompt dialog.

*[2019 paper][paper-2019], Q2.B(ii), PDF p. 1, 2 marks*

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

**Question 2.** Write `sum()` to find the sum of the first n prime integers, taking n from element `number` in form `f`.

*[2019 paper][paper-2019], Q6.A(ii), PDF p. 2, 3 marks*

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

### II.5 Regular expressions

A **regular expression** describes a pattern to look for in text. It is useful when validity depends on the characters a value contains, such as requiring a mobile number to contain digits only. A literal such as `/web/i` supplies the pattern between slashes; the `i` flag makes matching ignore case. The `g` flag requests multiple matches for operations such as replacement.

| Pattern component | Meaning |
| --- | --- |
| `^` and `$` | Start and end of the text. |
| `[0-9]` | One digit in the specified range. |
| `+` | One or more repetitions. |
| `*` and `?` | Zero or more repetitions; zero or one repetition. |
| `{n}` | Exactly n repetitions. |
| `.` and `\.` | Any character except a line terminator in the ordinary mode; a literal full stop. |

Combining these components gives a rule for a complete value. `/[0-9]/` asks whether the text contains a digit, whereas `/^[0-9]+$/` requires the entire text to consist of one or more digits.

```javascript
const digits = /^[0-9]+$/;
console.log(digits.test("0123"));     // true
console.log(digits.test("12a"));      // false
console.log("Web Technology".search(/technology/i)); // 4
console.log("web web".replace(/web/g, "IWT"));       // "IWT IWT"
```

The operations answer different questions. A RegExp's `test()` returns a boolean, a string's `search()` returns the first match position or `-1`, and `replace()` returns a new string with the replacement applied.

For repeated form checks, use a plain anchored pattern without `g`; this avoids the retained `lastIndex` position used by global `test()` calls. The main aim is to express the actual validation rule clearly, rather than to introduce a more elaborate pattern than the question requires.

#### Examination practice

**Question 1.** Define RegExp and explain `search()`, `replace()` and `test()` with examples.

*[2024 paper, image 2][paper-2024-b], Q4(b), 2 marks*

**Answer.** A regular expression specifies a text-matching pattern. `"IWT".search(/W/)` returns `1`; `"IWT".replace(/W/, "Web")` returns `"IWebT"`; `/^[0-9]+$/.test("123")` returns `true`. The three operations locate, replace and test a match, respectively.

See also: the registration validation in [2021 paper, 2019-23 batch][paper-2021-b], Q2(i), p. 2, marks not visible, is answered in II.11. RegExp is a suitable solution choice, not an explicitly demanded technique in that prompt.

### II.6 Errors and debugging

An incorrect program can fail in different ways. Recognising the kind of error helps you decide where to look and whether the program can handle it while running.

| Kind of error | What happens | Example |
| --- | --- | --- |
| Syntax | The code cannot be parsed. | A missing closing bracket. |
| Runtime | An error occurs during execution. | Using an undeclared variable. |
| Logical | The code runs but gives an incorrect result. | Summing primes up to n when the task asks for the first n primes. |

#### Reporting and handling exceptions

A `try...catch` statement handles an exception raised while an operation is running. Its `try` block contains that operation. `catch` receives a thrown error so that the program can respond to it, and `throw` deliberately reports an invalid condition. A `finally` block, when present, performs a final action after the try/catch whether or not an exception occurred.

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

The explicit divisor check gives the caller a meaningful error. Ordinary JavaScript numeric division does not automatically throw for a zero divisor: a calculation such as `10 / 0` produces infinity. A catch block also cannot repair a script that failed to parse in the first place.

#### Finding the cause through debugging

**Debugging** means locating and correcting an error. First reproduce the problem and read any console message and line number. Then inspect the relevant values, using `console.log()` where useful. A breakpoint in browser developer tools, or `debugger;` while a debugger is active, lets you pause and follow execution until the first incorrect result appears.

After making a correction, retest a normal case and relevant boundaries such as zero or empty input. Handling an exception keeps the program in control; debugging finds and fixes the reason something went wrong.

#### Examination practice

**Question 1.** What is JavaScript debugging and how can it be done?

*[2024 paper, image 2][paper-2024-b], Q5(d), 2 marks*

**Answer.** Debugging is locating and correcting errors in JavaScript. Use the browser console to read errors and inspect values with `console.log()`. Use developer-tools breakpoints or `debugger` to pause and step through execution while watching variables, then correct and retest the code.

### II.7 JavaScript classes and inheritance

A **class** describes how to create objects with a shared structure and behaviour. Its `constructor` initialises a new instance, and its methods operate on that instance's data through `this`. Calling the class with `new` creates an object from the definition.

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

Both students use the same `result()` method, but each has its own name and marks. Changing one student's marks therefore does not change the other student's result. The distinction is between the class as a definition and an instance as an individual object.

#### Reusing behaviour through inheritance

**Inheritance** allows a specialised class to reuse a parent class's behaviour. `extends` names the parent. When the subclass defines a constructor, `super(...)` calls the parent's constructor before the subclass uses `this`.

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

The research student gains the parent's name, marks and result behaviour, then adds a topic. A subclass may also replace an inherited method with its own implementation. This short treatment establishes the relationship between classes, objects, constructors and specialisation; deeper advanced material remains planned.

#### Additional practice

**Original question · Suggested 3 marks.** Define a Student class with a constructor and a pass/fail method, and show two objects with different results.

**Answer.** The Student class above supplies a constructor, properties, a result method and two instances. `this.marks` selects the current instance's marks: 65 produces `Pass`, while 30 produces `Fail`. The threshold is an illustrative rule for this generated question, not a rule stated in a past paper.

### II.8 HTML DOM foundations, selection and manipulation

The browser does more than display HTML source. It builds a tree of objects representing the document, and JavaScript works with that tree through the **Document Object Model (DOM)**. Selecting an element gives the program access to its content, attributes, styles and position in the document. Changes to the tree can then change what the reader sees.

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

The HTML source describes the initial document; the live DOM may change after parsing. The distinction explains how a button can add a paragraph without the original HTML file itself being rewritten.

#### Finding the document and its elements

The entry point is `document`. Its `document.documentElement` refers to `html`; `document.head`, `document.body`, `document.title` and `document.forms` provide access to familiar parts of the page. Selection methods then locate the element or group of elements a program needs.

| Method | Result |
| --- | --- |
| `document.getElementById("result")` | One element with that ID, or `null`. |
| `document.getElementsByTagName("p")` | A live HTMLCollection of matching elements. |
| `document.getElementsByClassName("note")` | A live HTMLCollection of elements with that class. |
| `document.querySelector("p.note")` | The first matching element, or `null`. |
| `document.querySelectorAll("p.note")` | A static NodeList of all matches. |

A single-element selection can fail to find anything and return `null`; a multiple selection can return an empty collection. A live collection updates its membership as the document changes, while a static collection keeps the membership found at selection time. II.10 develops that distinction further.

Selection must happen after the relevant HTML exists. A script placed after the elements, or an external script loaded with `defer`, can access them once they have been parsed.

#### Changing content, attributes and styles

Use `.textContent` to read or write plain text. Use `.innerHTML` when markup is intended to be parsed or serialised, and `.value` for the current contents of an input or textarea. These properties serve different purposes: writing text is not the same operation as supplying new HTML.

Attributes can be read with `getAttribute()`, changed with `setAttribute()` or removed with `removeAttribute()`. For example, `image.setAttribute("alt", "Puri beach")` changes an image's alternative text.

Styles can be changed through properties such as `element.style.backgroundColor`, or through `classList.add()`, `remove()` and `toggle()`. The `.style` object reflects inline declarations; `getComputedStyle(element).color` reads the resolved style, including stylesheet rules. Notice that `background-color` in CSS becomes `backgroundColor` through the style object.

```html
<p id="message" class="note">Original text</p>
<script>
  const message = document.getElementById("message");
  message.textContent = "Revision started";
  message.style.backgroundColor = "lightyellow";
  message.setAttribute("title", "DOM example");
</script>
```

This example first selects the paragraph, then changes its text, background and title attribute. Structural operations, such as creating and inserting another paragraph, use a different set of DOM methods, as the examination examples show.

#### Examination practice

**Question 1.** Define HTML DOM; name three JavaScript methods for manipulating it and explain them with examples.

*[2024 paper, image 2][paper-2024-b], Q3(b), 5 marks*

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

**Question 2.** Access HTML elements through CSS selectors using JavaScript.

*[2024 paper, image 2][paper-2024-b], Q5(c), 2 marks*

**Answer.** `querySelector()` selects the first CSS-selector match; `querySelectorAll()` selects all matches.

```html
<p class="note">One</p><p class="note">Two</p>
<script>
  document.querySelector("p.note").textContent = "First note";
  const notes = document.querySelectorAll("p.note");
  for (const note of notes) note.style.color = "navy";
</script>
```

**Question 3.** Display a paragraph in a DIV with user-supplied width/height; wrap its text according to the DIV width.

*[2021 paper, 2019-23 batch][paper-2021-b], Q2(ii), PDF p. 2, marks not visible*

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

### II.9 JavaScript and DOM events

An **event** tells a program that something has happened: a button was activated, a value changed or a form was submitted. An **event handler** or **listener** is the function that responds. The program first registers the function, then the browser calls it when the event occurs.

This is the function-reference distinction from II.2 in practice. `addEventListener("click", handler)` registers a function; passing `handler()` would call it immediately and pass its result instead. A property such as `button.onclick = handler` provides one handler slot, while `addEventListener` can register several listeners.

```html
<button id="change" type="button">Change message</button><p id="eventMessage"></p>
<script>
  document.getElementById("change").addEventListener("click", function (event) {
    document.getElementById("eventMessage").textContent = "Button activated";
    console.log(event.currentTarget.id); // change
  });
</script>
```

#### Choosing the event

Use `click` for activation, `input` for value edits, `change` for a committed value change, and `submit` for form submission. `keydown` and `keyup` respond to keyboard actions, while `load` reports resource loading. `DOMContentLoaded` reports that the document has been parsed; a deferred script can usually access its elements without a separate readiness listener.

For mouse actions, `mousedown` occurs when a button is pressed and `mouseup` when it is released. `mouseover` and `mouseout` respond to entering and leaving an element; because these events bubble, movement across descendants can also trigger them. Event names supplied to `addEventListener` omit the `on` prefix.

#### Understanding the event object

The event object describes the occurrence. `event.target` is where the event originated, while `event.currentTarget` is the element whose listener is currently running. Many events **bubble**, reaching ancestors after the target's handler runs.

> `preventDefault()` prevents a default action, such as form navigation. `stopPropagation()` stops further event propagation. Preventing one does not automatically stop the other.

These distinctions let a form respond to submission or a page respond to mouse activity without confusing the browser's default behaviour with the program's own handler.

#### Examination practice

**Question 1.** Write functions to handle `mouseup`, `mousedown`, `mouseover` and `mouseout`.

*[2024 paper, image 2][paper-2024-b], Q5(b), 2 marks for the entire item*

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

The four small functions and registrations directly answer the task. jQuery-specific event/effect methods in the uncertain 2023 question are not substituted for these plain JavaScript events.

### II.10 DOM navigation, nodes and NodeList

Every item in the DOM tree is a **node**, but not every node is an element. Documents, elements, text and comments are different kinds of nodes. Attributes can also be accessed as attribute nodes, although they are not ordinary children of an element.

| Node kind | `nodeType` |
| --- | --- |
| Element | `1` |
| Text | `3` |
| Comment | `8` |
| Document | `9` |

A text node's `nodeValue` holds its text. An element's `nodeValue` is `null`; to read the text inside it, use `.textContent`. This distinction prevents a common mistake when navigating from an element to its contents.

#### Following relationships in the tree

A node has a `parentNode` and may have `childNodes`, a `firstChild`/`lastChild`, and `nextSibling`/`previousSibling` nodes. Whitespace in HTML can create text nodes, so `firstChild` is not necessarily the first element the reader notices.

When only elements are intended, use `parentElement`, `children`, `firstElementChild`, `lastElementChild`, `nextElementSibling` and `previousElementSibling` instead:

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

#### Creating, inserting and removing nodes

Creating a node does not display it; the node must be attached to the document tree. `createTextNode()` creates plain text and `appendChild()` inserts a node at the end of a parent's children. `insertBefore(newNode, referenceNode)` inserts before a child, `replaceChild(newNode, oldNode)` replaces one, and `removeChild(child)` removes one.

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

These operations change the relationships in the tree. Appending an already attached node moves it rather than creating a copy.

#### Understanding NodeList membership

A **NodeList** is an indexed collection of nodes, accessed with `[i]` or `item(i)`, measured with `.length` and traversed with a loop. It is not an Array, and its contents depend on how it was obtained: a NodeList can include text or other non-element nodes.

`querySelectorAll()` returns a static NodeList, while `childNodes` returns a live NodeList. The `children` property and the `getElementsBy...` methods discussed earlier return HTMLCollections instead. The following example makes the effect of live and static membership visible:

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

> A static NodeList fixes which nodes belong to the collection. It does not freeze those nodes or make copies of their contents.

The nodes already in the snapshot still reflect edits, even though later additions do not change its membership.[^collections]

### II.11 Documents, forms and validation

A form brings several earlier ideas together. The DOM gives the program access to controls, strings and numbers represent their values, regular expressions check character patterns, and events determine when the program should respond. The overall sequence is straightforward: read the input, check it, then display or submit the accepted result.

#### Reading and checking the controls

`document.getElementById("name")` obtains a control by ID, while `document.forms["f"].elements.namedItem("name")` accesses one through a named form. An input's `.value` supplies its current text; a checkbox or radio button's `.checked` reports whether it is selected.

**Validation** asks whether those values satisfy the required rules. A name may be empty, a mobile number may contain letters, or a quantity may be below one. Trim unwanted outside whitespace before checking text. Keep telephone numbers as strings to preserve leading zeros, and use numeric conversion when a calculation is intended. A regular expression is suitable when the rule concerns a pattern of characters.

The `submit` handler receives an event. Calling `event.preventDefault()` stops the normal navigation or submission so that the current page can show the result. The examples below demonstrate that front-end behaviour; they do not store a registration on a server.

#### Using HTML constraint validation

HTML can declare many rules directly on its controls:

| Constraint | What it checks |
| --- | --- |
| `required` | A value must be supplied. |
| `type="email"` | The value must have email syntax. |
| `min`, `max`, `step` | A number must satisfy range and step restrictions. |
| `minlength`, `maxlength` | Text length must satisfy the restriction. |
| `pattern` | Text must match the declared pattern. |

JavaScript can inspect these constraints with `checkValidity()`, which returns a boolean, or use `reportValidity()` to ask the browser to display its validation message as well. A custom error is set with `setCustomValidity("message")` and cleared with `setCustomValidity("")` after correction.[^validation]

Validation should precede use of the data and explain the particular problem. Display accepted plain text through `.textContent`, or through `.value` in a textarea; `innerHTML` would interpret it as markup. These browser checks improve the user's interaction, but a receiving server must still validate data because client-side checks can be bypassed.

#### Examination practice

**Question 1.** Create a registration form for name, mobile and email; name must be nonempty/alphabetic, mobile numeric, email nonempty; show entered data in a textarea.

*[2021 paper, 2019-23 batch][paper-2021-b], Q2(i), PDF p. 2, marks not visible*

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

**Question 2.** Design a vaccination-registration form, validate it using JavaScript, display submitted details and provide a confirm button.

*[2021 paper, 2018-22 batch][paper-2021-a], Q2 (screenshot title), PDF p. 1, marks clipped/not verifiable*

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

**Question 3.** Design the HTML/CSS/JavaScript application page for IIIT Bhubaneswar's cyber-security hackathon: colleges enter groups of three; three winning groups receive prizes; students stay in institute residences and faculty mentors in the Guest House.

*[2024 paper, image 1][paper-2024-a], Q1(b), 5 marks*

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

**Question 4.** What is constraint validation, and which attributes can achieve it?

*[2024 paper, image 2][paper-2024-b], Q5(e), 2 marks*

**Answer.** Constraint validation checks whether form input satisfies declared restrictions. For example, `<input type="number" min="1" max="10" required>` accepts a required number within the range; `pattern`, `minlength`, `maxlength` and suitable input types provide other restrictions. JavaScript can test them using `checkValidity()` or show messages with `reportValidity()`.

### II.12 Browser Object Model

The document is only one part of the browser environment. The **DOM** represents the page, while the conventional term **Browser Object Model (BOM)** groups facilities involving the window, history, browser information and timers. `window` is the browser window/global object, and `window.document` refers to its document. BOM is a teaching grouping rather than one single interface specification.

#### Working with the window and history

| Facility | Use |
| --- | --- |
| `window.alert("Saved")` | Displays a message. |
| `prompt("Name?")` | Returns entered text or `null` if cancelled. |
| `confirm("Continue?")` | Returns a boolean response. |
| `window.innerWidth`, `window.innerHeight` | Report viewport dimensions in CSS pixels. |
| `outerWidth`, `outerHeight` | Include the outer browser window. |
| `history.back()`, `history.forward()`, `history.go(-1)` | Navigate session history when a corresponding entry exists. |
| `history.length` | Reports the number of history entries. |

Viewport size is different from the document's total scrollable size. The next example displays that size and updates it when the browser window is resized:

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

History supplies navigation, not an unrestricted list of the user's browsing URLs. Similarly, a prompt supplies text, so numeric input must be converted deliberately before arithmetic is performed.

#### Navigator and browser detection

The `navigator` object supplies environment information through properties such as `navigator.userAgent`, `navigator.language`, `navigator.onLine` and `navigator.cookieEnabled`. The online property is a connectivity indicator; it does not prove that a particular server can be reached.

Browser detection can inspect the user-agent string. For example, `navigator.userAgent.includes("Firefox/")` finds a reported Firefox token, but the string may be reduced, imitated or overlap between browsers. When the real question is whether a capability exists, feature detection such as `typeof document.querySelector === "function"` checks that capability directly.

The distinction to retain is the responsibility of each object: `document` provides the page, `window` its surrounding environment, `history` navigation and `navigator` browser information. Timing and cookies are developed in the next two topics.

#### Examination practice

See also: [2019 paper][paper-2019], Q2.B(ii), p. 1, 2 marks, prompt-based factorial is fully answered in II.4. [2024 paper, image 2][paper-2024-b], Q5(a), 2 marks, cookie-enabled detection is fully answered in II.14.

### II.13 JavaScript timing events

A **timer** asks the browser to run a function later. `setTimeout(function, delay)` schedules a single call, while `setInterval(function, delay)` schedules repeated calls. The delay is measured in milliseconds; it schedules the work rather than pausing the rest of the script.

Both functions return timer IDs. Passing the appropriate ID to `clearTimeout(id)` or `clearInterval(id)` cancels pending work. The function supplied to the timer is a callback, so pass the function itself rather than the result of calling it.

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

The first timer schedules a reminder once, and its button can cancel it before it runs. The interval displays 3, 2 and 1 on successive calls, then clears itself. Clearing a timer does not undo a callback that has already executed.

A delay also does not promise an exact execution time: the browser runs the callback when it can. The deeper scheduling mechanism belongs to the planned advanced JavaScript material; the essential distinction here is between one-time work, repeated work and cancellation.

#### Additional practice

**Original question · Suggested 5 marks.** Distinguish DOM from BOM, distinguish NodeList membership from node contents, and show a cancellable one-time reminder.

**Answer.** DOM represents/manipulates document nodes; BOM refers to browser-environment facilities such as window/history/timers. `querySelectorAll()` returns a static NodeList: later additions do not change its membership, but its node objects still reflect edits. A reminder can be written as `const id = setTimeout(function () { alert("Revise"); }, 2000);` and cancelled before execution using `clearTimeout(id)`. Here, 2000 is a delay in milliseconds; cancellation does not undo a callback that has already executed.

### II.14 Cookies and working with cookies in JavaScript

HTTP treats separate exchanges independently, yet many sites need to remember a preference or recognise a session. A **cookie** helps provide that continuity. It is a small named value stored by the browser for a site and included in applicable HTTP requests. It may hold a preference or session identifier; it does not inherently contain the whole session and is not a JavaScript object.

#### Creating, reading and updating a cookie

For cookies accessible to scripts, assigning to `document.cookie` sets one cookie rather than replacing every existing cookie. Reading the property returns accessible `name=value` pairs separated by semicolons.

A cookie's `max-age` gives its lifetime in seconds; `expires` can instead provide an expiry date in UTC. Without either, it is normally a session cookie. Its `path` controls the applicable URL path. Updating or deleting it requires the same name/path/domain combination, with deletion achieved through an expired lifetime.[^cookies][^cookie-mechanism]

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

The value is encoded so spaces or separators do not corrupt cookie syntax. The reading function finds the matching name and decodes its value; the final assignment deletes the same name/path cookie. Server-set `HttpOnly` cookies are not exposed through `document.cookie`.

#### Interpreting cookie availability

Browser settings and page context may restrict cookies, so practical examples should use a served page rather than assuming every `file:` page behaves identically. `navigator.cookieEnabled` reports the browser's cookie-enabled indicator, but does not guarantee that every cookie will be accepted in every context.[^cookie-indicator]

> A persistent cookie has a specified lifetime. A persistent HTTP connection reuses a connection. The two uses of “persistent” describe different mechanisms.

#### Examination practice

**Question 1.** Create and delete cookies in JavaScript, with examples.

*[2019 paper][paper-2019], Q2.A(ii), PDF p. 1, 3 marks*

**Answer.** A cookie stores a small name/value pair for a site. Assign `document.cookie = "user=Anu; max-age=3600; path=/";` to create a one-hour cookie. Read accessible cookies using `document.cookie`. Delete the same cookie using `document.cookie = "user=; max-age=0; path=/";`, or by setting an expiry date in the past with the same path/domain.

**Question 2.** Define cookies and write a function displaying whether they are enabled.

*[2024 paper, image 2][paper-2024-b], Q5(a), 2 marks*

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

This reports the navigator indicator requested by the exam; it is not a test that every storage context accepts cookies.

> **Planned material.** The advanced JavaScript sections below retain their original coverage and question index; they are not yet completed notes.

### II.15 Closures, hoisting and IIFEs

**Planned coverage.** Closures; hoisting; immediately invoked function expressions (IIFEs); necessary scope context.

**Question index.** No direct question found. `let`/`var` in [2024 paper, image 2][paper-2024-b], Q4(c), is a related foundation, not an explicit closures/hoisting/IIFE question.

*Reference support:* supplied references do not develop these topics.

### II.16 Event loops, callbacks, promises and async/await

**Planned coverage.** Event loops; callback functions; promises; async/await.

**Question index.**

- **I | [2023 collection][paper-2023], Q2(b), p. 1, 5 marks overall:** Synchronous/asynchronous requests, callback role in AJAX and XHR ready states. Retain its callback/asynchronous-programming application here; full AJAX mapping is III.7.

*Reference support:* `Sources/nodejs.pdf`, pp. 10-24, supports callbacks/event loops. No direct promises/async-await question found and reference coverage is limited.

### II.17 Functional programming and reusable computation

**Planned coverage.** Functional programming; higher-order functions; generators; memoization; currying.

**Question index.** No direct question found.

*Reference support:* supplied references do not adequately develop these topics.

## Module III - XML, AJAX, jQuery, JSON, React.js and Node.js (12 hours)

The following topics retain their syllabus outline and verified question index. Teaching material and model answers are still to be written.

### III.1 XML introduction, HTML comparison and document structure

**Planned coverage.** XML introduction; XML vs HTML; structure of an XML document; well-formed XML documents.

**Question index.**

- **I | [2021 paper, 2018-22 batch][paper-2021-a], Q5(ii-iii), p. 3, marks not visible:** Provide a sample pizza-order XML message for the DTD and identify its building blocks. Q5(i) is indexed in III.2.
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(i), p. 2, marks not visible:** Well-formed vs valid XML, with DTD/types/examples; shared with III.2.
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(ii), p. 2, marks not visible:** Book-catalogue DTD, corresponding XML message and explanation of XML structure; shared with III.2.

*Reference support:* `Sources/XML.pdf`, pp. 1-7.

### III.2 DTD, XML validation and valid documents

**Planned coverage.** Document Type Declaration (DTD), as worded in the syllabus, and DTD definitions; internal/external DTD; XML validation; valid XML document; relation to well-formedness.

**Question index.**

- **I | [2019 paper][paper-2019], Q2.B(i), p. 1, 1+2 marks:** Define DTD and write one for the supplied `book` XML with `id`, title and author.
- **I | [2021 paper, 2018-22 batch][paper-2021-a], Q5(i-iii), p. 3, marks not visible:** Pizza-order message DTD, a sample XML message and its building blocks.
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(i), p. 2, marks not visible:** Well-formed/valid XML; DTD and its types with examples.
- **I | [2021 paper, 2019-23 batch][paper-2021-b], Q3(ii), p. 2, marks not visible:** DTD and sample book-catalogue XML message with a structural explanation.

*Reference support:* `Sources/XML.pdf`, pp. 8-11.

### III.3 XML namespaces and XML Schema

**Planned coverage.** XML Namespaces; XML Schema; schema-based validation and its relation to DTD.

**Question index.** No direct question found. Generic XML validity questions above do not establish a Schema-specific occurrence.

*Reference support:* `Sources/XML.pdf`, pp. 7-11.

### III.4 XML DOM

**Planned coverage.** XML DOM and working with XML document nodes.

**Question index.** No direct XML-DOM question found. HTML DOM questions are indexed separately in Module II.

*Reference support:* only a brief mention in `Sources/XML.pdf`, p. 6; AJAX XML example in `Sources/AJAX.pdf`, pp. 4-7, offers limited context.

### III.5 XSL and XSL transformation

**Planned coverage.** XSL; XSL Transformation; necessary XML selection/template context within transformation examples.

**Question index.** No direct question found.

*Reference support:* `Sources/XML.pdf`, pp. 12-15, is introductory and lacks a complete worked transformation.

### III.6 AJAX introduction and client-server flow

**Planned coverage.** AJAX introduction; relation to JavaScript; asynchronous page updates; client-server architecture as context for AJAX operation.

**Question index.**

- **I | [2019 paper][paper-2019], Q4.A, p. 2, 1+2+2 marks:** Define AJAX, explain implementation steps and important XMLHttpRequest properties/methods. Same question as III.7.
- **P | [2023 collection][paper-2023], Q4(b), p. 1, 2.5 marks per selected short note:** Retain JSON and AJAX options only; exclude Spring and Struts. Answer-any-two choice applies to the original question.
- **I | [2023 collection][paper-2023], Group A Q1(a), p. 3, 2 marks:** Difference between AJAX and JavaScript.
- **P | [2023 collection][paper-2023], Group B Q2, p. 3, 10 marks overall:** Retain JSON in AJAX and the AJAX client-server architecture diagram/explanation. The “types of post backs” clause is U; no retained-only marks are specified.

*Reference support:* `Sources/AJAX.pdf`, pp. 1-4.

### III.7 XMLHttpRequest and server responses

**Planned coverage.** XMLHttpRequest object; request creation/sending; properties/methods; server response; ready states; response handlers and synchronous/asynchronous request context.

**Question index.**

- **I | [2019 paper][paper-2019], Q4.A, p. 2, 1+2+2 marks overall:** AJAX definition/steps and important XHR properties/methods; the final portion is 2 marks.
- **I | [2023 collection][paper-2023], Q1(b), p. 1, 2 marks:** Different ready states of an AJAX request.
- **I | [2023 collection][paper-2023], Q2(b), p. 1, 5 marks:** Synchronous/asynchronous requests, role of AJAX callbacks and request ready states.

*Reference support:* `Sources/AJAX.pdf`, pp. 3-6, illustrates a completion/status check; expand to the full prescribed object/response topic later.

### III.8 AJAX with XML and databases

**Planned coverage.** AJAX XML; AJAX Database; browser request, endpoint response and DOM-update flow in these examples.

**Question index.** No direct question specifically requiring AJAX XML/database integration found. Do not relabel old JDBC or servlet database questions as AJAX questions.

*Reference support:* `Sources/AJAX.pdf`, pp. 4-7 (XML), pp. 7-11 (database). Keep PHP as incidental example code, not a separate study unit.

### III.9 jQuery DOM selectors

**Planned coverage.** jQuery DOM selectors; selecting elements by the prescribed DOM-selection context.

**Question index.**

- **I | [2023 collection][paper-2023], Group A Q1(b), p. 3, 2 marks:** Explain jQuery DOM selectors.

*Reference support:* `Sources/jQuery.pdf`, pp. 4-8, 12. Check legacy selector examples when writing.

### III.10 jQuery HTML content and HTML DOM

**Planned coverage.** HTML Content; jQuery HTML DOM; reading/changing content and attributes; adding/removing DOM elements.

**Question index.**

- **P | [2023 collection][paper-2023], Group B Q4, p. 3, 10 marks overall:** Retain built-in functions that operate on the prescribed selectors/HTML content/CSS/DOM, plus the background-color task in III.11. Do not expand this broad wording into every jQuery API; no subpart split is printed.
- **U - REVIEW | [2023 collection][paper-2023], Q1(e), p. 1, 2 marks:** Explain `ready()`, `mouseenter()`, `mousedown()` and `toggle()`. These span DOM readiness, event helpers and effects; jQuery events/effects are not explicitly among the four prescribed jQuery topics. Confirm intended depth before including the item as required study.

*Reference support:* `Sources/jQuery.pdf`, pp. 8, 10-11, 14. Its event/effect pages do not resolve the syllabus boundary.

### III.11 jQuery CSS styles

**Planned coverage.** jQuery CSS Styles; reading/updating styles and classes in the DOM context.

**Question index.**

- **P | [2023 collection][paper-2023], Group B Q4, p. 3, 10 marks overall:** Write jQuery code to get the background color of an element in a paragraph; explain only syllabus-aligned built-in functions. Same question as III.10; background-color-only marks are not printed.

*Reference support:* `Sources/jQuery.pdf`, pp. 9, 14; check the reference's method-name typos during later writing.

### III.12 JSON introduction, syntax, types, objects and arrays

**Planned coverage.** Introduction; syntax; data types; Object; Arrays; nesting and structured data as applications of these topics.

**Question index.**

- **I | [2021 paper, 2018-22 batch][paper-2021-a], Q5(iv-v), p. 3, marks not visible:** What JSON is and four reasons for preferring JSON over XML for message exchange. Treat the requested preference as a question to assess, not a universal rule.
- **P | [2023 collection][paper-2023], Q4(b), p. 1, 2.5 marks per selected short note:** JSON option only here; AJAX is indexed in III.6; Spring/Struts are excluded.
- **I | [2023 collection][paper-2023], Group A Q1(c), p. 3, 2 marks:** JSON syntax and its data types.
- **P | [2023 collection][paper-2023], Group B Q2, p. 3, 10 marks overall:** JSON in AJAX, within the retained portion; exclude unresolved postback taxonomy.
- **I | [2023 collection][paper-2023], Group B Q3, p. 3, 10 marks:** JSON applications and a program storing five books by author, topic and edition.

*Reference support:* `Sources/JSON.pdf`, pp. 2-31, filtered to the current syllabus.

### III.13 JSON parsing and stringify

**Planned coverage.** Parsing JSON; stringifying JavaScript values; connections to JSON objects/arrays and data interchange.

**Question index.** No direct parsing/stringifying question found. The five-book question does not explicitly demand either operation.

*Reference support:* supplied JSON reference does not develop these operations.

### III.14 React introduction, ES6, rendering HTML and JSX

**Planned coverage.** React.js introduction; ES6; Render HTML; JSX.

**Question index.**

- **I | [2023 collection][paper-2023], Q2(a), p. 1, 5 marks overall:** Creator/company, React advantages, props, JSX and how JSX works with an example. Props are also indexed in III.15; no subpart marks are printed.
- **I | [2023 collection][paper-2023], Group A Q1(d), p. 3, 2 marks:** What ES6 and JSX are.

*Reference support:* `Sources/reactjs.pdf`, pp. 2, 4-17, 22. Develop ES6 coverage within the syllabus rather than importing the reference's separate course outline.

### III.15 React components, props, state and lifecycle

**Planned coverage.** Components; props; state; lifecycle. The stray “2” before “Lifecycle” in the scan does not define an additional topic.

**Question index.**

- **I | [2023 collection][paper-2023], Q2(a), p. 1, 5 marks overall:** Props portion of the React/JSX question; same question as III.14.

*Reference support:* `Sources/reactjs.pdf`, pp. 18-21, supports components/props. State and lifecycle need further support. No direct state/lifecycle question found.

### III.16 React events, forms and CSS

**Planned coverage.** Events; forms; CSS in React.

**Question index.** No direct React-specific question found. Plain HTML/JavaScript form questions are not React occurrences.

*Reference support:* supplied React reference does not develop these prescribed topics.

### III.17 Node.js introduction and development environment

**Planned coverage.** Introduction to Node.js; setup development environment; running an application as setup context.

**Question index.**

- **I | [2023 collection][paper-2023], Q1(a), p. 1, 2 marks overall:** What Node.js can do and syntax to include the HTTP module; module portion also indexed in III.18.

*Reference support:* `Sources/nodejs.pdf`, pp. 1-5; installation/setup coverage needs supplementation.

### III.18 Node.js modules and npm

**Planned coverage.** Node.js modules; Node Package Manager; importing/exporting modules and managing packages as applications of these topics.

**Question index.**

- **I | [2023 collection][paper-2023], Q1(a), p. 1, 2 marks overall:** Include the HTTP module in a Node.js program; same item as III.17.
- **I | [2023 collection][paper-2023], Group A Q1(e), p. 3, 2 marks:** Explain Node.js modules.

*Reference support:* `Sources/nodejs.pdf`, pp. 6-9, 17. No direct npm question found.

### III.19 Node.js web server and events

**Planned coverage.** Creating a web server; Events; event-driven request handling.

**Question index.**

- **I | [2023 collection][paper-2023], Q1(a), p. 1, 2 marks overall:** Node capabilities and including HTTP are relevant foundations; the actual prompt does not ask for a complete server implementation.

*Reference support:* `Sources/nodejs.pdf`, pp. 13-24, 29-33. No direct full-server or EventEmitter implementation question found.

### III.20 Node.js file system and debugging

**Planned coverage.** File System; Debugging Node.js Application.

**Question index.** No direct Node-specific file-system/debugging question found. The 2024 browser JavaScript debugging item belongs to II.6.

*Reference support:* `Sources/nodejs.pdf`, pp. 34-42, covers file operations. Debugging needs further support.

### III.21 Express.js and serving static resources

**Planned coverage.** Express.js; Serving Static Resources.

**Question index.** No direct question found.

*Reference support:* the npm reference installs Express as an example but does not teach Express or static serving.

### III.22 Node.js database connectivity

**Planned coverage.** Database Connectivity in the Node.js context.

**Question index.** No direct Node.js database-connectivity question found. Older Java/JDBC/servlet questions remain excluded; do not rewrite them into invented Node questions.

*Reference support:* supplied Node reference does not cover this topic.

## Appendix A - Examination evidence

**Scope authority:** [IWT-7th-Semester-IT.pdf](../Syllabus/IWT-7th-Semester-IT.pdf), Module I on PDF p. 2, Module II on pp. 2-3, Module III on p. 3. Completed teaching covers Module I and JavaScript fundamentals, DOM and BOM through II.14; advanced JavaScript and Module III retain their planned outlines.

| Study priority | Evidence in the supplied questions | Planning decision |
| --- | --- | --- |
| First: HTML/CSS construction and JavaScript forms/DOM | HTML/CSS tasks occur in the 2019 paper, both 2021 files and the 2024 images: **4 source sets**. Explicit form-validation tasks occur in both 2021 files and 2024: **3 sets**. The 2018-22 batch travel task carries 10 points; 2024 website tasks carry 5 marks each. | Practise page construction, styling, validation and DOM updates together after learning their foundations. |
| First: XML structure, well-formedness, validity and DTD design | DTD questions occur in 2019 and both 2021 files: **3 sets**. The 2019 DTD task is 1+2 marks; the 2021 questions require complete XML/DTD examples, but their marks are not visible. | Prepare both short distinctions and document-design answers. |
| Next: AJAX and JSON | AJAX occurs in 2019 and the dated 2023 page; JSON occurs in the 2018-22 batch file and the dated 2023 page. Both also occur on the separate undated sheet in the 2023 PDF. AJAX implementation/XHR is 5 marks in 2019; the dated 2023 synchronous/asynchronous AJAX question is 5 marks. | Prioritise request flow, XHR states/responses, JSON syntax and structured data; retain all prescribed parsing/stringifying topics. |
| Next: jQuery, React and Node.js | Each appears on the dated 2023 page and the separate undated sheet. The latter offers 10-mark JSON and jQuery questions; dated 2023 React is 5 marks and Node.js is 2 marks. Some jQuery wording needs scope review. | Prepare the exact Module III topics. These two pages are different assessment fragments, not two verified exam years. |
| Required despite little/no direct past-question evidence | HTTP details, web history/standards/cyber laws, many CSS properties, advanced JavaScript, XML Schema/XSL/XML DOM, React state/lifecycle/forms/CSS, Node debugging/Express/static resources/database connectivity. | Keep every prescribed subtopic. Lack of observed questions is not evidence of exclusion. |

**Frequency means observed presence, not predicted probability.** Counts above are by source set, once per topic family per set, across 2019, the two 2021 files, the dated 2023 page and the paired 2024 images. The undated sheet is reported separately. Repeated references to one question below do not add occurrences. Partial questions count only for their retained topic; uncertain items do not support frequency claims. These are small, uneven and sometimes incomplete samples from different semesters/branches.

**Observed formats:** 2019 is 50 marks/2.5 hours, any five of six 10-mark questions, with 1-3 mark subparts and 2.5-mark short notes. The dated 2023 page says 50 marks/2.5 hours and answer all, but only 40 marks are visible. The undated sheet has five compulsory 2-mark items and any two of three 10-mark questions. The paired November 2024 images show 50 marks/2.5 hours, answer all, arranged as five 10-mark blocks: Q1/Q3 have two 5-mark tasks; Q2/Q4/Q5 have five 2-mark items. The 2021 screenshot collections do not establish a complete timed-paper format.

**Prediction boundary:** the study order above is a judgement from coverage, recurrence and task size, not a forecast of the next paper or a promised marks distribution. The current syllabus allocates **8/10/12 teaching hours** to Modules I/II/III, respectively (30 total); this is not an exam-weightage rule. The supplied 2024 paper tests Modules I-II, which does not remove Module III from the current syllabus. Syllabus p. 4 assigns the end-term exam 50% of course evaluation, not a guaranteed question pattern.

## Appendix B - Sources and reference limits

- **I = in scope:** the asked task fits a prescribed topic.
- **P = partially in scope:** study only the explicitly retained portion; the rest is excluded in the audit.
- **O = out of scope:** recorded only in the audit, with no planned study section.
- **U = uncertain; REVIEW:** wording/context does not establish syllabus alignment. Do not treat it as prescribed or count it as recurrence.
- Question descriptions are compact paraphrases of actual prompts, not invented practice questions. `Not visible` means the source does not verify the marks; no equal split is assumed for a multipart question.
- PDF page numbers are **1-based file pages**, not inferred printed page labels. For PNGs, use the image filename; their page order is inferred from question continuity and is not printed pagination.
- A section's **Planned coverage** paragraph identifies material still to be written. **No direct question found** records an evidence gap, not permission to skip the section. Cross-topic questions may appear in more than one section.

| Supplied paper file | Identity and limitations |
| --- | --- |
| [CS201_Internet_and_Web_Technology_April_2019.pdf](../Papers/CS201_Internet_and_Web_Technology_April_2019.pdf) | 2 PDF pages; April 2019, sixth semester, EEE, CS201. Older course context; filter against the present IT syllabus. |
| [IWT 2021 Endsem (2018-22 batch).pdf](<../Papers/IWT 2021 Endsem (2018-22 batch).pdf>) | 3 PDF pages of screenshots. Year/batch are supplied by filename. Travel prompt has no printed question number; vaccination form is identified as q2 in its screenshot title. Q3-Q5 are numbered. The travel prompt shows 10 points; the vaccination mark label is clipped. |
| [IWT 2021 Endsem (2019-23 batch).pdf](<../Papers/IWT 2021 Endsem (2019-23 batch).pdf>) | 5 PDF pages; Q1-Q5 on pp. 1-4, p. 5 blank. Year/batch are supplied by filename. Marks are not visible. Q5(ii)'s final instruction is cut off; its HTML/servlet requirement is readable. |
| [IWT_Question_Papers_2023.pdf](../Papers/IWT_Question_Papers_2023.pdf), p. 1 | Dated November 2023, seventh semester IT, IWT II. Header declares two pages and 50 marks, but the file does not contain a coherent continuation: only Q1-Q4, totalling 40 marks, are visible here. Missing questions cannot be reconstructed. |
| Same PDF, p. 2 | Android fragment: XML checkboxes, contextual menu, implicit intents and ConstraintLayout. It is not a continuation consistent with the IWT questions on p. 1. Excluded from IWT frequency. |
| Same PDF, p. 3 | Separate undated sheet headed Internet and Web Technologies-2, seventh semester IT, Groups A/B, 30 attempted marks. Do not assign it a verified 2023 exam date just because of the container filename. |
| [A_1.png](../Papers/A_1.png) and [A_2.png](../Papers/A_2.png) | Paired November 2024 end-semester paper, IT. A_1 has Q1 and Q2(a-b); A_2 continues Q2(c-e), then Q3-Q5. One paper for recurrence counting. |

### Reference material: use and gaps

All six supplied references were read. They support later writing but cannot add syllabus topics. Page ranges below refer to PDF file pages.

| Reference | Useful syllabus-aligned coverage | Gaps/boundaries for later writing |
| --- | --- | --- |
| [XML.pdf](../Sources/XML.pdf), 15 pp. | Introduction/HTML comparison pp. 1-5; structure pp. 5-7; namespaces pp. 7-8; DTD pp. 8-10; Schema/validation pp. 10-11; XSL/transformation overview pp. 12-15. | XML DOM is only briefly mentioned (p. 6); worked DOM/XSLT coverage is insufficient. Android/configuration examples do not prescribe Android development. |
| [AJAX.pdf](../Sources/AJAX.pdf), 11 pp. | Introduction/architecture pp. 1-2; XHR/callback/response example pp. 3-4; XML interaction pp. 4-7; database interaction pp. 7-11. | PHP/MySQL are example endpoints, not independent prescribed PHP/JDBC topics. XHR states need fuller treatment than the sample's completion check. |
| [jQuery.pdf](../Sources/jQuery.pdf), 16 pp. | Basics/selectors pp. 4-7, 12; chaining p. 8; styles p. 9; markup pp. 10, 14; DOM overview p. 11. | Events/effects on pp. 13, 15 do not expand the four listed jQuery syllabus topics. Some spellings/examples need checking when writing, including `ccs` on p. 9 and `xss` on p. 14. |
| [JSON.pdf](../Sources/JSON.pdf), 33 pp. | Introduction pp. 2-5; syntax/objects/arrays pp. 7-11; types pp. 13-19; nesting pp. 20-22; XML comparison pp. 24-31. | Does not teach the prescribed JavaScript parsing/stringifying operations. Java/Gson material on p. 32 is not prescribed. |
| [reactjs.pdf](../Sources/reactjs.pdf), 26 pp. | Intro/rendering pp. 2, 4-12; JSX pp. 13-17; components/props pp. 18-21; Babel p. 22. | State, lifecycle, events, forms and React CSS are not developed. The reference's own “Syllabus” on p. 3 is not the official course scope; do not import Router, virtualized lists, webpack or fetch-hook topics from it. |
| [nodejs.pdf](../Sources/nodejs.pdf), 42 pp. | Intro/running/REPL pp. 1-5; npm/modules pp. 6-9; callbacks pp. 10-12; event loop/events pp. 13-24; HTTP server pp. 29-33; file system pp. 34-42. | Installation detail is limited; debugging, Express, static serving and database connectivity are missing. Streams pp. 25-29 may support file/server examples but are not a separate syllabus unit. |

The supplied references do not cover most Module I material or most advanced JavaScript. The completed foundations use the supplementary sources listed in Appendix D where needed. Any support added for planned sections must remain within the official syllabus.

## Appendix C - Past-paper scope audit

The register below accounts for every visible question, including excluded material. **I** items are described in the notes or planned outline; the boundary tables explain every **P/O/U** decision. Group labels and page numbers distinguish identically numbered questions in the mixed 2023 file.

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

| File, locator, verifiable marks | Retain for this outline | Exclude or hold for review |
| --- | --- | --- |
| `CS201_Internet_and_Web_Technology_April_2019.pdf`, Q3.A(i), p. 1, 2+1 | GET vs POST (1 mark), I.5. | JSP tags and examples (2 marks). JSP is not prescribed. |
| Same file, Q3.B, p. 2, 1+4 overall | Explicit HTML registration-form portion, I.13. No HTML-only mark split given. | Servlet lifecycle, servlet code, deployment descriptor and database-table implementation. Node database connectivity does not prescribe this Java stack. |
| Same file, Q6.A(i), p. 2, 1+1 | JavaScript introductory characteristics (from the comparison) and `script` attributes, I.8/II.1. Script-attributes portion is 1 mark; do not claim a retained-only total for the comparison. | Detailed Java-language study from the Java-vs-JavaScript comparison. |
| `IWT 2021 Endsem (2019-23 batch).pdf`, Q1(ii), p. 1, marks not visible | CSS purpose, box model, colors, alignment/layout, iframe and inline styles, I.12/I.14/I.17/I.18/I.20. | The diagram's `marquee` instruction. Frames and CSS animation do not explicitly prescribe this old HTML tag. |
| Same file, Q5(ii), p. 4, marks not visible | Explicit HTML login page (`index.html`), I.13. | Servlet authentication/code and `web.xml` mapping. Do not infer the cut-off final instruction. |
| `IWT_Question_Papers_2023.pdf`, Q4(b), p. 1, 2.5+2.5 for any two options | JSON and AJAX short notes, III.6/III.12. | Spring framework and Struts options. Original choice rule does not make them prescribed. |
| Same file, Group B Q2, p. 3, 10 overall | JSON in AJAX and client-server architecture diagram/explanation, III.6/III.12. No marks assigned to retained clauses separately. | “Types of post backs in AJAX” is U: intended taxonomy/technology is unspecified. Do not add ASP.NET postback material without clarification. |
| Same file, Group B Q4, p. 3, 10 overall | Built-in jQuery functions for selectors, HTML content, CSS styles and HTML DOM; requested background-color getter, III.10/III.11. | Unbounded coverage of all jQuery built-ins, including effects/plugins and library-specific event APIs not explicitly prescribed. No separate getter marks are printed. |

### Out-of-scope questions and options

| File and locator | Actual asked material | Why excluded |
| --- | --- | --- |
| `CS201_Internet_and_Web_Technology_April_2019.pdf`, Q3.A(ii), p. 2, 1+1 marks | JSP vs servlet; use of a JDBC driver. | Neither Java server technology nor JDBC is prescribed. |
| Same file, Q4.B, p. 2, 2+3 marks | Five steps connecting Java to a database and a JDBC program. | Node database connectivity is a different prescribed context. |
| Same file, Q5.A(i), p. 2, 1+2 marks | Class vs interface and a class with multiple constructors. | Java context, not a verified JavaScript-class task. |
| Same file, Q5.B(i), p. 2, 1+1+1 marks | JavaBean example, serializable interface and EJB types. | JavaBeans/EJB/Java serialization have no module-level topic. The general outcome's Java Beans mention does not prescribe this detailed Java stack; flag the wording discrepancy for review below. |
| Same file, Q6.B(i), p. 2, 2.5 marks | EJB vs RMI. | Neither is a prescribed module topic. |
| Same file, Q6.B(iii), p. 2, 2.5 marks | VBScript short note. | VBScript is not prescribed. The second listed short-note label is printed “iii”; do not renumber it to “ii”. |
| `IWT 2021 Endsem (2018-22 batch).pdf`, Q3, p. 2, marks not visible | Java Person -> StudentIIIT -> MTechStudent/BTechStudent/PhDStudent classes; accessors/mutators, constructors, `this`/`super`. | Explicit Java program, not JavaScript inheritance. |
| Same file, Q4, p. 2, marks not visible | Health-camp servlet that processes height/weight/health data, displays BMI/status and stores data in a database. | Explicit servlet implementation; there is no separately requested HTML-file subtask to retain. Do not transform it into a new JavaScript/Node question. |
| `IWT 2021 Endsem (2019-23 batch).pdf`, Q4(i), p. 3, marks not visible | Java command-line arithmetic program handling arithmetic exceptions. | Explicit Java, not the prescribed JavaScript errors topic. |
| Same file, Q4(ii), p. 3, marks not visible | Implement Java Item/MP3/DVD/Book inheritance diagram and create objects/attributes. | Explicit Java, not JavaScript classes. |
| Same file, Q5(i), p. 4, marks not visible | Java/JDBC connection; create a students table, insert two rows, display contents. | Java/JDBC stack is not prescribed; do not count as Node connectivity. |
| `IWT_Question_Papers_2023.pdf`, Q1(c), p. 1, 2 marks | J2EE concepts/types. | J2EE is not prescribed. |
| Same file, Q3(a), p. 1, 2+1+2 marks | EJB definition, types and differences. | EJB is not prescribed. |
| Same file, Q3(b), p. 1, 2+2+1 marks | Hibernate architecture, components and object states. | Hibernate is not prescribed. |
| Same file, Q4(a), p. 1, 1+2+2 marks | Microservices, advantages and design best practices with examples. | Microservices-specific architecture/design is not a named module topic; broad “web architecture” does not justify importing this full unit. |
| Same file, Q4(b)(i-ii), p. 1, 2.5 per selected note | Spring framework and Struts. | These are excluded options in the partially retained short-note question. |
| Same file, p. 2, checkbox prompt, label obscured, marks not visible | XML UI checkboxes for chocolate syrup, sprinkles and crushed nuts. | Android layout task in the Android fragment, not web XML/DTD. |
| Same file, p. 2, contextual-menu prompt, label appears (j), marks not visible | Define a contextual menu and steps to create it. | Android context established by adjacent UI and Activity/manifest tasks; not a CSS navigation-menu question. |
| Same file, Q2(a), p. 2, 5 marks | Android layout/Java/manifest for one Activity opening a website/map and sharing text, using editable default-valued fields. | Android Activity/intents/manifest development is not prescribed. Opening a website does not make it an IWT web-development question. |
| Same file, Q2(b), p. 2, 5 marks | Android Hello Constraint app using ConstraintLayout, with layout/Java/manifest files. | Android ConstraintLayout is not CSS layout. |

### Uncertain classifications and source issues to review

| Item | Uncertainty | Current treatment |
| --- | --- | --- |
| `CS201_Internet_and_Web_Technology_April_2019.pdf`, Q5.A(ii), p. 2, 2 marks | “Exception handling” does not name its language; surrounding questions are Java-oriented. | U; held out of required question frequency. Retain only if confirmed to ask JavaScript error handling. |
| `IWT_Question_Papers_2023.pdf`, Q1(d), p. 1, 2 marks | MVC's relation to generic prescribed web architecture versus an older framework-specific unit. | U; retained in this audit for review, with no MVC/framework expansion. |
| Same file, Q1(e), p. 1, 2 marks | jQuery readiness/event/effect methods exceed the four explicitly listed jQuery topics; intended DOM-topic depth is unclear. | U; listed in III.10 for review, excluded from confirmed frequency. |
| Same file, Group B Q2, p. 3, part of 10 marks | “Types of post backs” may refer to a technology-specific taxonomy absent from the syllabus. | Parent question P; this clause U. Study JSON/AJAX architecture only until clarified. |
| Official syllabus, p. 1, course-outcome reference to Java Beans | Module lists on pp. 2-3 prescribe Node.js server-side programming, with no JavaBeans/JSP/servlet/JDBC unit. | Do not revive old Java-stack questions. Treat the outcome/module discrepancy as review-worthy; the explicit module topic list controls this outline. |
| 2023 PDF composition/date | P. 1 lacks its coherent second page; p. 2 is Android; p. 3 is a different undated IWT sheet. | Keep page-specific attribution. Do not invent the missing 10 marks, merge sheets into one exam, or treat the undated sheet as an independently verified exam year. |
| 2021 screenshot provenance/marks | Dates come from filenames; travel number is absent; vaccination marks are clipped; second file has no visible marks and a truncated Q5(ii) ending. | Use visible locators and “not visible/not verifiable”; do not invent totals, question numbers or mark allocations. |

## Appendix D - Writing standard and completion record

### Completion record

Module I and the JavaScript fundamentals, DOM, forms and BOM topics through II.14 contain teaching material and model answers. Advanced JavaScript from II.15 onward and Module III remain planned. Four original practice questions supplement gaps in the papers: connections/caching, the box model, classes, and DOM/BOM/timing.

The completed material covers all prescribed Module I subtopics and the introductory JavaScript, HTML DOM and BOM lists, including the cookie continuation on syllabus p. 3. Shared questions have one complete answer and references from related topics. Code examples and hypothetical filenames belong to the written answers; the document does not require extra repository files.

### Standard for subsequent sections

Begin with the idea and its purpose, develop it in connected paragraphs, and use a short example, comparison or diagram where it makes the explanation clearer. Divide substantial topics with meaningful subheadings. Reserve blockquotes for a particularly important distinction rather than adding a summary label after every paragraph.

Group examination questions after the corresponding concepts. Keep each model answer complete and proportionate to its marks, preserve the original source and any scope restriction, and clearly separate generated practice from actual questions. Use source notes unobtrusively; retain the detailed audit here.

Continue one numbered topic at a time within the official syllabus. Fill documented reference gaps without importing another course's outline, and mark a topic complete only when all its prescribed coverage and relevant questions have been addressed.


### Supplementary source notes

The following links support details already used in the completed notes; they do not enlarge the syllabus.

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
