# Web

"The World Wide Web, commonly known as the Web, is an information system where
documents and other web resources are identified by Uniform Resource Locators
(URL's), which may be interlinked by hyperlinks, and are accessible over the
Internet", [Wikipedia](https://en.wikipedia.org/wiki/World_Wide_Web).

# Contents:
- [Web](#web)
- [Contents:](#contents)
- [Web Basic Concepts:](#web-basic-concepts)
  - [HTTP:](#http)
    - [Communication:](#communication)
      - [HTTP Request Methods:](#http-request-methods)
      - [HTTP Response Status Codes:](#http-response-status-codes)
  - [URL:](#url)
    - [URL vs URN vs URI:](#url-vs-urn-vs-uri)
  - [TCP:](#tcp)
  - [IP:](#ip)
  - [DNS:](#dns)
  - [Proxy:](#proxy)
- [Web Pages:](#web-pages)
  - [Dynamic Web Pages:](#dynamic-web-pages)
- [Web Applications:](#web-applications)
- [Web Services:](#web-services)
  - [Concepts:](#concepts)
    - [XML:](#xml)
    - [SOAP:](#soap)
      - [WSDL:](#wsdl)
      - [XSD:](#xsd)
    - [REST:](#rest)
    - [API:](#api)
    - [JSON:](#json)

# Web Basic Concepts:

## HTTP:

"Hypertext Transfer Protocol (HTTP) is an application-layer protocol for
transmitting hypermedia documents, such as HTML. It was designed for
communication between web browsers and web servers, but it can also be used for
other purposes. HTTP follows a classical client-server model, with a client
opening a connection to make a request, then waiting until it receives a
response. HTTP is a stateless protocol, meaning that the server does not keep
any data (state) between two requests", [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP).

There's a lot of debate around the stateful definition, as found [here](https://stackoverflow.com/questions/13200152/why-is-it-said-that-http-is-a-stateless-protocol),
but as for this time, I'll agree that it's stateless because it's not mandatory
to keep the state, just a possibility.

It is also extensible, which means that many different responses can be obtained
based on different headers and bodies.

### Communication:

A request typically informs the method it's using (described below), together
with its header and body (but they are optional).

The request is sent to a resource URL, for example: 
https://developer.mozilla.org.

A response typically informs a status code (described below), together with its
header and body (but they are optional).

We can observe all of this process using the browser's developer tools, but,
sometimes, some information is omitted. We can use `curl` to see more details.

#### HTTP Request Methods:

- (C) Post: creates something;

- (R) Get: gets something, and is characterized by being a 'safe' method, meaning that
it doesn't change anything in the server, and by being 'idempotent', meaning that
it can be called multiple times without changing the result of the first call.
For example, multiple requests with the same body can sometimes return different
status codes, but if it causes an effect on the first request, the second and 
further ones won't cause any change to the server status;

- (U) Put: creates or updates something entirely (ideally), and is characterized
by being 'idempotent';

- (D) Delete: deletes something, and is characterized by being 'idempotent';

- Options: returns the options available in the called resource URL, on the
response headers (doesn't have a body), and is characterized by being a 'safe'
method;

- Head: returns just the header of what would be the full response, and is
characterized by being a 'safe' and  'idempotent' method;

- Patch: partially modifies a resource, modifying for example just an attribute.

#### HTTP Response Status Codes:

- 1xx - Information;

- 2xx - Success;

- 3xx - Redirecting;

- 4xx - Client Error;

- 5xx - Server Error.

See more at [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

## URL:

"Uniform Resource Locator (URL) is a text string that specifies where a resource
(such as a web page, image, or video) can be found on the Internet.

In the context of HTTP, URLs are called "Web address" or "link". Your browser
displays URLs in its address bar, for example: https://developer.mozilla.org
Some browsers display only the part of a URL after the "//", that is, the Domain
name.

URLs can also be used for file transfer (FTP) , emails (SMTP), and other
applications", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/URL).

### URL vs URN vs URI:

- "A Uniform Resource Identifier (URI) is a string of characters that uniquely
identify a name or a resource on the internet. A URI identifies a resource by
name, location, or both. URIs have two specializations known as Uniform Resource
Locator (URL), and Uniform Resource Name (URN);

- A Uniform Resource Locator (URL) is a type of URI that specifies not only a
resource, but how to reach it on the internet—like http://, ftp://, mailto://;

- A Uniform Resource Name (URN) is a type of URI that uses the specific naming
scheme of urn, like urn:isbn:0-486-27557-4 or urn:isbn:0-395-36341-1.

- So a URI or URN is like your name, and a URL is a specific subtype of URI
that’s like your name combined with your address", [Daniel Miessler](https://danielmiessler.com/p/difference-between-uri-url/).

## TCP:

"TCP (Transmission Control Protocol) is an important network protocol that lets
two hosts connect and exchange data streams.  TCP guarantees the delivery of
data and packets in the same order as they were sent. TCP's role is to ensure
the packets are reliably delivered, error free.  TCP has concurrence control,
which means the initial requests start small, increasing in size to the levels
of bandwidth the computers, servers, and network can support", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Transmission_Control_Protocol_(TCP)).

## IP:

"The Internet Protocol (IP) is a protocol, or set of rules, for routing and
addressing packets of data so that they can travel across networks and arrive
at the correct destination. Data traversing the Internet is divided into smaller
pieces, called packets. IP information is attached to each packet, and this
information helps routers to send packets to the right place. Every device or
domain that connects to the Internet is assigned an IP address, and as packets
are directed to the IP address attached to them, data arrives where it is
needed", [Cloudfare](https://www.cloudflare.com/learning/network-layer/internet-protocol/#:~:text=The%20Internet%20Protocol%20(IP)%20is%20a%20protocol%2C%20or%20set,into%20smaller%20pieces%2C%20called%20packets.&text=The%20most%20common%20transport%20protocols%20are%20TCP%20and%20UDP.).

## DNS:

"DNS (Domain Name System) is a hierarchical and decentralized naming system for
Internet connected resources. DNS maintains a list of domain names along with
the resources, such as IP addresses, that are associated with them.

The most prominent function of DNS is the translation of human-friendly domain
names (such as mozilla.org) to a numeric IP address (such as 151.106.5.172);
this process of mapping a domain name to the appropriate IP address is known as
a DNS lookup. By contrast, a reverse DNS lookup (rDNS) is used to determine the
domain name associated with an IP address", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/DNS).

## Proxy:

"A proxy server, or just proxy for short, is like having another computer that
your internet requests get sent to before going to the real website. It's a
server that takes all of the information you've sent out, like a request to buy
new shirts on H&M, and routes it through a different IP address.

That's what makes a proxy so powerful. They can make all of your internet
activity appear as if it's coming from a completely different location",
[Free Code Camp](https://www.freecodecamp.org/news/what-is-a-proxy-server-in-english-please/).

It can be a router, a 'server' functioning as cache, filter, load balancer, etc.  

# Web Pages:
## Dynamic Web Pages:

Dynamic web pages differ from static pages in that they are modified based on
database connections, for example. Instead of just consulting the server for a
static page through a specified path, the path generated instead generates some
(or all) parts of the page based on dynamic data, thus, making the web page
dynamic.

Real world example: an user page can have the same structure (html+css+js), but
the returned data depends on the path specified
(e.g. https://example.com/user/1). 

# Web Applications:

Web applications are the next step, after web pages. The server actually runs a
software that provides web pages, and the access for the end user is most of the
times the same, but the software actually can communicate with databases and web
services, manages access and such.

# Web Services:

Web Services are, as the name implies, services, that are developed aiming at
communicating with themselves ignoring the code's language, or which software or
hardware are involved. Basically an API.

Initially, following the standard: XML requests, under the HTTP protocol, and
identified by an URI (Universal Resource Identifier), that is, the URL (like
google.com) with added paths (like /search). Later on, via JSON and HTTPS.

## Concepts:

### XML:

Extensible Markup Language.

```XML
<note>
    <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body>Don't forget me this weekend!</body>
</note>
```

### SOAP:

Simple Object Access Protocol (SOAP) is a XML-based protocol to web services
communication, standardized by W3C.

"A SOAP message is an ordinary XML document containing the following elements:

An Envelope element that identifies the XML document as a SOAP message
A Header element that contains header information
A Body element that contains call and response information
A Fault element containing errors and status information", [W3Schools](https://www.w3schools.com/xml/xml_soap.asp).

```XML
HTTP/1.1 200 OK
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">

<soap:Body xmlns:m="http://www.example.org/stock">
  <m:GetStockPriceResponse>
    <m:Price>34.5</m:Price>
  </m:GetStockPriceResponse>
</soap:Body>

</soap:Envelope>
```

#### WSDL:

"Web Services Description Language (WSDL) is an XML-based interface description
language that is used for describing the functionality offered by a web
service", [Wikipedia](https://en.wikipedia.org/wiki/Web_Services_Description_Language).
There's some tools to make it easier to read, like SoapUI.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<description xmlns="http://www.w3.org/ns/wsdl" 
             xmlns:tns="http://www.tmsws.com/wsdl20sample" 
             xmlns:whttp="http://schemas.xmlsoap.org/wsdl/http/"
             xmlns:wsoap="http://schemas.xmlsoap.org/wsdl/soap/"
             targetNamespace="http://www.tmsws.com/wsdl20sample">

<documentation>
    This is a sample WSDL 2.0 document. 
</documentation>

<!-- Abstract type -->
   <types>
      <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
                xmlns="http://www.tmsws.com/wsdl20sample"
                targetNamespace="http://www.example.com/wsdl20sample">
                 
         <xs:element name="request"> ... </xs:element>
         <xs:element name="response"> ... </xs:element>
      </xs:schema>
   </types>

<!-- Abstract interfaces -->
   <interface name="Interface1">
      <fault name="Error1" element="tns:response"/>
      <operation name="Get" pattern="http://www.w3.org/ns/wsdl/in-out">
         <input messageLabel="In" element="tns:request"/>
         <output messageLabel="Out" element="tns:response"/>
      </operation>
   </interface>

<!-- Concrete Binding Over HTTP -->
   <binding name="HttpBinding" interface="tns:Interface1" 
            type="http://www.w3.org/ns/wsdl/http">
      <operation ref="tns:Get" whttp:method="GET"/>
   </binding>
   
<!-- Concrete Binding with SOAP-->
   <binding name="SoapBinding" interface="tns:Interface1" 
            type="http://www.w3.org/ns/wsdl/soap" 
            wsoap:protocol="http://www.w3.org/2003/05/soap/bindings/HTTP/"
            wsoap:mepDefault=
            "http://www.w3.org/2003/05/soap/mep/request-response">
      <operation ref="tns:Get" />
   </binding>

<!-- Web Service offering endpoints for both bindings-->
   <service name="Service1" interface="tns:Interface1">
      <endpoint name="HttpEndpoint" 
                binding="tns:HttpBinding" 
                address="http://www.example.com/rest/"/>
      <endpoint name="SoapEndpoint" 
                binding="tns:SoapBinding" 
                address="http://www.example.com/soap/"/>
   </service>
</description>
```

#### XSD:

"XSD (XML Schema Definition), a recommendation of the World Wide Web Consortium
(W3C), specifies how to formally describe the elements in an Extensible Markup
Language (XML) document. It can be used by programmers to verify each piece of
item content in a document, to assure it adheres to the description of the
element it is placed in", [Wikipedia](https://en.wikipedia.org/wiki/XML_Schema_(W3C)).

```XML
<?xml version="1.0" encoding="UTF-8"?>

<shiporder orderid="889923"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="shiporder.xsd">
  <orderperson>John Smith</orderperson>
  <shipto>
    <name>Ola Nordmann</name>
    <address>Langgt 23</address>
    <city>4000 Stavanger</city>
    <country>Norway</country>
  </shipto>
  <item>
    <title>Empire Burlesque</title>
    <note>Special Edition</note>
    <quantity>1</quantity>
    <price>10.90</price>
  </item>
  <item>
    <title>Hide your heart</title>
    <quantity>1</quantity>
    <price>9.90</price>
  </item>
</shiporder>
```

### REST:

"REST (Representational State Transfer) refers to a group of software
architecture design constraints that bring about efficient, reliable and
scalable distributed systems.

The basic idea of REST is that a resource, e.g. a document, is transferred via
well-recognized, language-agnostic, and reliably standardized client/server
interactions. Services are deemed RESTful when they adhere to these constraints.

HTTP APIs in general are sometimes colloquially referred to as RESTful APIs,
RESTful services, or REST services, although they don't necessarily adhere to
all REST constraints. Beginners can assume a REST API means an HTTP service that
can be called using standard web libraries and tools", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/REST).

It is able to work with both XML and JSON (and other types of response formats),
but it's more common to see it working with JSON. It's easier to learn and
develop, compared with SOAP.

### API:

"An API (Application Programming Interface) is a set of features and rules that
exist inside a software program (the application) enabling interaction with it
through software - as opposed to a human user interface. The API can be seen as
a simple contract (the interface) between the application offering it and other
items, such as third party software or hardware.

In Web development, an API is generally a set of code features (e.g. methods,
properties, events, and URLs) that a developer can use in their apps for
interacting with components of a user's web browser, or other software/hardware
on the user's computer, or third party websites and services", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/API).

### JSON:

"JavaScript Object Notation (JSON) is a data-interchange format.  Although not a
strict subset, JSON closely resembles a subset of JavaScript syntax. Though many
programming languages support JSON, JSON is especially useful for
JavaScript-based apps, including websites and browser extensions.

JSON can represent numbers, booleans, strings, null, arrays (ordered sequences
of values), and objects (string-value mappings) made up of these values (or of
other arrays and objects).  JSON does not natively represent more complex data
types like functions, regular expressions, dates, and so on.  (Date objects by
default serialize to a string containing the date in ISO format, so the 
information isn't completely lost.) If you need JSON to represent additional
data types, transform values as they are serialized or before they are 
deserialized", [MDN](https://developer.mozilla.org/en-US/docs/Glossary/JSON).