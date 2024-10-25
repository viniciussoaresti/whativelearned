# HTML

HTML, or Hypertext Markup Language, is how the websites structures are defined.
They are defined with tags, which open and close, and have content in it, like:

```html
<h1>content</h1>
```
There are many different tags in HTML, but I'll focus on the most complex ones or
on the ones that I didn't knew.

# Contents:
- [HTML](#html)
- [Contents:](#contents)
  - [Comments:](#comments)
  - [Void Elements:](#void-elements)
  - [Strong vs em vs i:](#strong-vs-em-vs-i)
  - [Global Attributes:](#global-attributes)
    - [Contenteditable:](#contenteditable)
    - [Data-\*:](#data-)
    - [Hidden:](#hidden)
    - [Tabindex:](#tabindex)
    - [Title:](#title)
  - [Reserved characters:](#reserved-characters)
  - [Interesting tags I've not seen before:](#interesting-tags-ive-not-seen-before)
    - [Blockquote and quote (q):](#blockquote-and-quote-q)
    - [Abbreviation:](#abbreviation)
    - [Address:](#address)
    - [DL, DT and DD (lists with key-value pairs usualy):](#dl-dt-and-dd-lists-with-key-value-pairs-usualy)
    - [Pre (preformatted) and code  :](#pre-preformatted-and-code--)
  - [Working with links on the same web page:](#working-with-links-on-the-same-web-page)
  - [Meta tag:](#meta-tag)
    - [Meta SEO:](#meta-seo)
    - [Meta Social Media:](#meta-social-media)
  - [Forms:](#forms)
    - [Input:](#input)
    - [Label:](#label)
    - [Button:](#button)
    - [Datalist](#datalist)
      - [Autocomplete](#autocomplete)
      - [Autofocus](#autofocus)
      - [Other attributes](#other-attributes)
      - [Form and name:](#form-and-name)
      - [Password:](#password)
      - [Email:](#email)
      - [Url:](#url)
      - [File:](#file)
      - [Color:](#color)
      - [Checkbox:](#checkbox)
      - [Hidden:](#hidden-1)
      - [Radio:](#radio)
      - [Textarea:](#textarea)
      - [Search:](#search)
      - [Number:](#number)
      - [Range:](#range)
      - [Input types that don't have a great browser support yet:](#input-types-that-dont-have-a-great-browser-support-yet)
    - [Select:](#select)
      - [Optgroup:](#optgroup)
  - [SEO and Semantics:](#seo-and-semantics)
    - [SEO:](#seo)
    - [Semantics:](#semantics)
      - [Blockquote:](#blockquote)
      - [Header:](#header)
      - [Nav:](#nav)
      - [Main:](#main)
      - [Article:](#article)
      - [Aside:](#aside)
      - [Footer:](#footer)
      - [Section:](#section)
      - [Figure:](#figure)
  - [Visual code shortcuts:](#visual-code-shortcuts)

## Comments:

Comments look like this:

```html
<!-- TODO: Add link to cat photos -->
```

## Void Elements:

Void elements don't have closing tags, like the img tag:

```html
<img>
```
## Strong vs em vs i:

In order, the strong tag represents more urgent parts in a text, em just 
emphasizes a part of the text, and the i tag differentiates a content part.

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

## Working with links on the same web page:

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

## Forms:

A form example:

```html
<form id="contact" action="" method="POST"> 
  <!-- the action attribute specifies to where the data should be sent
  for example a specific path like http://site.com/index/contacts, so the
  action would be /index/contacts !-->
    <fieldset form="contact" name="inputs-contact"> 
    <!-- can have the disabled property which doesn't allow input !-->
        <legend>Contact</legend>
    </fieldset>
    <button></button>
</form>
```

### Input:

One of the most used properties, with a lot of varieties on the type:

```html
<input type='date'>
```

### Label:

Adds accessibility and identifies data:

```html
<label>
  Name:
  <input type="text">
</label>
<!--or, only working with some specific elements like input, meter, output..!-->
<label for="name"> Name: </label>
<input id="name" type="text">
```

### Button:

We can use the type `submit` or `button` for submitting the form, or `reset`
to reset the values written in the form.

```html
<button type="submit">Submit</button>
```

There are other attributes like `autofocus`, `disabled`, `name`, `value` and 
`form`. `Name` describes the name of the value in the value tag, and `form`
links the button to the form:

```html
<form action="" id="my-form"></form>
<button type="submit" form="my-form">Submit</button>
```

### Datalist

It's a list of suggestions for the user to select. Some of the inputs that
support this are `text`, `search`, `url`, `number` and many others, while
`radio`, `checkbox` or other buttons don't.

```html
<input type='text'
    list='fruits-data'
    placeholder='Pick a fruit'>
    <datalist id='fruits-data'>
        <option>apple</option>
        <option>banana</option>
        <option>mango</option>
        <option>orange</option>
        <option>cherry</option>
    </datalist>
```

#### Autocomplete

Attribute that enables the autocomplete feature on the browser, has a lot of
possible values, it's good to check the documentation:

```html
<input type='email' autocomplete='email'>
```

#### Autofocus

The first element found with this attribute gains input focus from the browser:

```html
<input type='email' autocomplete='email' autofocus>
```

#### Other attributes

`Disabled`, `readonly`, `value`, `required`, `placeholder`.

#### Form and name:

Specify the form and the name of the value passed to the form:

```html
<form id="my-form"></form>
<input name="userEmail" form="my-form" type='email' autocomplete='email' autofocus>
```

#### Password:

Accepts `minlength`, `maxlength`, `size` (visual length), `pattern` (regex to validate password),
`title` (message informing of the regex conditions), `placeholder`, `readonly`,
`disabled`, `required`, `inputmode` (input mode for smartphones) and `autocomplete`
(on, off and new-password options) attributes.

#### Email:

Accepts `placeholder`, `readonly`, `disabled`, `value`, `required`,
`multiple` (boolean that informs this field receives multiple emails),
`minlength`, `maxlength`, `size` (visual length), 
`pattern` (regex to validate email) and `list` (receiving emails from a datalist)
attributes.

#### Url:

Accepts `placeholder`, `readonly`, `disabled`, `value`, `required`,
`minlength`, `maxlength`, `size` (visual length), 
`pattern` (regex to validate email), `list` (receiving emails from a datalist)
and spellcheck (enables spell check for the url) attributes.

#### File:

Accepts `value` (contains the file to be sent), `files` (the list of files),
`accept` (specifies the file types to be accepted, like video/*) and 
`multiple` (boolean that enables sending multiple files) attributes.

Careful when using the file input, as the forms need to be configured like this:

```html
<form action="" method='post' enctype='multipart/form-data'>
  <input type="file">
</form>
```

#### Color:

Accepts `value` and `list` (receiving colors from a datalist) attributes.

#### Checkbox:

Accepts `value` and `checked` attributes.

Using checkboxes for multiple values:

```html
<fieldset>
        <legend>Choose your interests:</legend>
        <div>
            <input type="checkbox" id='coding' name='interest' value='coding' checked>
            <label for="coding">Coding</label>
        </div>
        <div>
            <input type="checkbox" id='music' name='interest' value='music' checked>
            <label for="music">Music</label>
        </div>
    </fieldset>
```

#### Hidden:

Field hidden to the user.

#### Radio:

Select an option from many. Main attributes: `checked` and `value`.

```html
<fieldset>
  <legend>Let's have a coffee?</legend>
  <label for="yes">Yes</label>
  <input type="radio" id='yes' name='coffee' value='yes'>
  <label for="no">No</label>
  <input type="radio" id='no' name='coffee' value='no' checked>
</fieldset>
```

#### Textarea:

Accepts `id`, `name`, `rows`, `cols`, `minlength`, `maxlength` and `wrap` attributes,
alongside other input attributes like `autocomplete`, `autofocus`, `placeholder`,
`required`, etc.

#### Search:

Accepts `list` (datalist), `pattern` and `aria-label` (hidden label for screen 
readers) attributes (alongside other input attributes).

#### Number:

Accepts `min`, `max`, `step` and `list` attributes (alongside other input 
attributes).

#### Range:

Number selected with a slider.

Accepts `min`, `max`, `step` and `list` attributes (alongside other input 
attributes).

#### Input types that don't have a great browser support yet:

`Date`, `datetime-local`, `month`, `time`, `week`.

### Select:

Select one or many options.

```html
<label for="carselect">Which car model do you like?</label>
  <select name="carmodel" id="carselect" multiple size="2">
  <option value="">Select the model</option>
  <option value="fiat">Uno</option>
  <option value="audi">A3</option>
  <option value="bmw">X6</option>
</select>
```

#### Optgroup:

Grouping of options on select:

```html
<label for="petsselect">Please choose one or more pets:</label>
<select name="pets" id="petsselect" multiple size='4'>
  <optgroup label='4-legged pets'>
    <option value="dog">Dog</option>
    <option value="cat">Cat</option>
    <option value="hamster" disabled>Hamster</option>
  </optgroup>
  <optgroup label='Flying pets'>
    <option value="parrot">Parrot</option>
    <option value="macaw">Macaw</option>
    <option value="albatross">Albatross</option>
  </optgroup>
</select>
```

## SEO and Semantics:

Writing a semantic HTML page can drastically improve SEO. Check [this](https://developer.mozilla.org/en-US/docs/Glossary/Semantics) link for further explanation, and [this](https://www.w3schools.com/TAgs/default.asp) one for the full elements reference.

### SEO:

Utilizing proper techniques to define the page content an help on the SEO, like
always having an alt attribute defined within images, and describing them in the
best way possible, dividing the page content with main and section tags, and so on.

### Semantics:

#### Blockquote:

Nice for citations:

```html
<blockquote>
Nós (programadores) somos pagos para resolver problemas,
não para memorizar soluções.
												 <cite>─ Mayk Brito</cite>
</blockquote>
```

#### Header:

Top of the page generally with some logo or information. Can be used inside
other semantic elements like article, section.

#### Nav:

Navigation part, such as the main navigation menu. Can be used on other parts,
but it is highly indicated to keep nav as an important navigation section.

#### Main:

Main content, used only once per page, inside the body tag.

#### Article:

Independent content that can be grouped with other articles if they make sense.

#### Aside:

Lateral content, generally related to the main content, such as explanations,
glossaries, extra links, author biography, profile information.

#### Footer:

Foot of the page, generally having page author information, copyright, contacts,
sitemap and a back to top button. Can be put on other locations such as inside 
an article.

#### Section:

Section which generally has a title inside. Use case example:

```html
<main>
    <article>
        <h1>Recipe 1</h1>
        <p>Recipe description</p>
        <section>
            <h2>How to:</h2>
            <p>How to</p>
        </section>
    </article>
</main>
```

#### Figure:

Holds self-contained content, that are related to each other. This can help in
SEO for faster image, video, code or other information localization.

```html
<figure>
  <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/lasagna.jpg" alt="A slice of lasagna on a plate.">
  <figcaption>Cats love lasagna.</figcaption>
</figure>
```

## Visual code shortcuts:

- div#id generates a div with the "id" id;
- div.class generates a div with the "class" class;
- element*n generates n times an element.