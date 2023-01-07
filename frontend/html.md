# HTML

The standard for web pages.

# Contents:
- [HTML](#html)
- [Contents:](#contents)
  - [Global Attributes:](#global-attributes)
    - [Contenteditable:](#contenteditable)
    - [Data-\*:](#data-)
    - [Hidden:](#hidden)
    - [Tabindex:](#tabindex)
    - [Title:](#title)
  - [Reserved characters:](#reserved-characters)
  - [SEO and Semantics:](#seo-and-semantics)
  - [Forms:](#forms)
  - [Interesting tags I've not seen before:](#interesting-tags-ive-not-seen-before)
    - [Blockquote and quote (q):](#blockquote-and-quote-q)
    - [Abbreviation:](#abbreviation)
    - [Address:](#address)
    - [DL, DT and DD (lists with key-value pairs usualy):](#dl-dt-and-dd-lists-with-key-value-pairs-usualy)
    - [Pre (preformatted) and code  :](#pre-preformatted-and-code--)
  - [Working with links:](#working-with-links)
  - [Meta tag:](#meta-tag)
    - [Meta SEO:](#meta-seo)
    - [Meta Social Media:](#meta-social-media)
  - [Visual code shortcuts:](#visual-code-shortcuts)

## Global Attributes:

### Contenteditable:

Makes an content editable.

### Data-*:

We can define custom attributes.

### Hidden:

We can hide an element.

### Tabindex:

We can order the tab button indexes on the page.

### Title:

We can define a title to be shown when hovering over an element.

## Reserved characters:

Characters like (< > & " " ' ') are reserved by HTML, to put them in a 'vanilla' way, we can put them using [this](https://dev.w3.org/html5/html-author/charref) reference, for example.

## SEO and Semantics:

Writing a semantic HTML page can drastically improve SEO. Check [this](https://developer.mozilla.org/en-US/docs/Glossary/Semantics) link for further explanation, and [this](https://www.w3schools.com/TAgs/default.asp) one for the full elements reference.

## Forms:

Initiating:

```html
<form id="contact" action="">
    <fieldset form="contact" name="inputs-contact">
        <legend>Contact</legend>
    </fieldset>
    <button></button>
</form>
```

## Interesting tags I've not seen before:

### Blockquote and quote (q):

```html
<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
    O <strong>Elemento HTML <code> <blockquote> </code> </strong> (ou <em>HTML Block
    Quotation Element</em>) indica que um texto externo foi citado.
</blockquote> <!-- This can also be done on a short way using quote (q), for small texts !--> 
```
### Abbreviation:

```html
<p>We use <abbr title="Hypertext Markup Language">HTML</abbr>  to make web pages.</p>
```

### Address:

```html
<address>
    <p>Mayk Brito <br>
    <strong>Campo Grande, MS</strong>
    </p>
</address>
```

### DL, DT and DD (lists with key-value pairs usualy):

```html
<h2>Glossary</h2>
<dl>
    <dt>Hypertext</dt>
    <dd>It's a hypertext with possibilities...</dd>

    <dt>Markup</dt>
    <dd>Text Markup</dd>

    <dt>Language</dt>
    <dd>Language with its semantics and syntax....</dd>
</dl>
```

### Pre (preformatted) and code  :

```html
<pre>
    <code>
        &lt;
        writing.  code
        like
          this.
    </code>
</pre>
```

## Working with links:

```html
<p>Know more:</p>
    <ul>
        <li><a href="#about">About me</a></li>
        <li><a href="#history">My History</a></li>
        <li><a href="#jobs">Jobs</a></li>
    </ul>
    <h1 id='about'>About me</h1>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempora obcaecati illum magni animi deserunt nesciunt alias
    qui amet voluptatum, doloribus rem nam. Cupiditate ab id dignissimos, voluptatibus velit sit maiores.
    <h2 id='history'>My History</h2>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Quaerat vitae quod perferendis totam corporis perspiciatis
    minima est voluptatum molestiae ullam, quis suscipit consequuntur quas hic, ut maxime sint reprehenderit aspernatur.
    <h2 id='jobs'>Jobs</h2>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur iste quidem in porro! Placeat numquam fugit
    corporis praesentium officia natus! Modi fugiat aperiam quod, soluta aspernatur voluptatum corporis eveniet maiores.
```

## Meta tag:

"The `<meta>` tag defines metadata about an HTML document", [w3schools](https://www.w3schools.com/tags/tag_meta.asp).

### Meta SEO:

We can use some tags for SEO:
`<meta name="author" content="Vinicius Soares">`
`<meta name="description" content="My personal web developer website.">`
`<meta name="robots" content="index, follow"> //default` 

### Meta Social Media:

We can use some configuration for specific social media sharing, like Facebook, for example:
`<meta property="og:image" content="https://image.link.jpeg">`
`<meta name="og:description" content="Searching for a web dev on facebook? Finally found.">`
`<meta name="og:title" content="Vinicius Soares WebDev">`

And for twitter:
`<meta name="twitter:title" content="Vinicius Soares Web Developer">`

## Visual code shortcuts:

- div#id generates a div with the "id" id;
- div.class generates a div with the "class" class;