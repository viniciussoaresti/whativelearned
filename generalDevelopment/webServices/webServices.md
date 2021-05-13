# Web Services:

Web Services are, as the name implies, services, that are developed aiming at communicating with themselves ignoring the code's language, or which software or hardware are involved. Basically an API.

Initially, following the standard: XML requests, under the HTTP protocol, and identified by an URI (Universal Resource Identifier), that is, the URL (like google.com) with added paths (like /search). Later on, via JSON and HTTPS.

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

Simple Object Access Protocol (SOAP) is a XML-based protocol to web services communication, standardized by W3C.

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