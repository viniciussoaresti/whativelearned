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

### WSDL:

"Web Services Description Language (WSDL) is an XML-based interface description language that is used for describing the functionality offered by a web service", [Wikipedia](https://en.wikipedia.org/wiki/Web_Services_Description_Language). There's some tools to make it easier to read, like SoapUI.

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
            wsoap:mepDefault="http://www.w3.org/2003/05/soap/mep/request-response">
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

### XSD:

"XSD (XML Schema Definition), a recommendation of the World Wide Web Consortium (W3C), specifies how to formally describe the elements in an Extensible Markup Language (XML) document. It can be used by programmers to verify each piece of item content in a document, to assure it adheres to the description of the element it is placed in", [Wikipedia](https://en.wikipedia.org/wiki/XML_Schema_(W3C)).

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