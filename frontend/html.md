# HTML

The standard for web pages.

# Contents:
- [HTML](#html)
- [Contents:](#contents)
  - [Global Attributes:](#global-attributes)
    - [Contenteditable:](#contenteditable)
    - [Data-*:](#data-)
    - [Hidden:](#hidden)
    - [Tabindex:](#tabindex)
    - [Title:](#title)
  - [Reserved characters:](#reserved-characters)
  - [SEO and Semantics:](#seo-and-semantics)
    - [Interesting tags I've not seen before:](#interesting-tags-ive-not-seen-before)
      - [Blockquote and quote (q):](#blockquote-and-quote-q)
      - [Abbreviation:](#abbreviation)
      - [Address:](#address)
      - [DL, DT and DD (lists with key-value pairs usualy):](#dl-dt-and-dd-lists-with-key-value-pairs-usualy)
      - [Pre (preformatted) and code  :](#pre-preformatted-and-code--)
  - [Tips:](#tips)

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

### Interesting tags I've not seen before:

#### Blockquote and quote (q):

```html
<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
    O <strong>Elemento HTML <code> <blockquote> </code> </strong> (ou <em>HTML Block
    Quotation Element</em>) indica que um texto externo foi citado.
</blockquote> <!-- This can also be done on a short way using quote (q), for small texts !--> 
```
#### Abbreviation:

```html
<p>We use <abbr title="Hypertext Markup Language">HTML</abbr>  to make web pages.</p>
```

#### Address:

```html
<address>
    <p>Mayk Brito <br>
    <strong>Campo Grande, MS</strong>
    </p>
</address>
```

#### DL, DT and DD (lists with key-value pairs usualy):

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

#### Pre (preformatted) and code  :

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

## Tips:

- Always try to specify elements, not throw it all around with some divs. This helps with SEO and accessibility.