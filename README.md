### Into to XML

* XML stands for EXtensible Markup Language
* XML is a markup language much like HTML
* XML was designed to store and transport data
* XML was designed to be self-descriptive

# Syntax: 

The simplest XML elements contain an opening tag, a closing tag, and some content. The opening tag begins with a left angle bracket (<), 
followed by an element name that contains letters and numbers (but no spaces), and finishes with a right angle bracket (>). In XML, 
content is usually parsed character data. It could consist of plain text, other XML elements, and more exotic things like XML entities, 
comments, and processing instructions (all of which we’ll see later). Following the content is the closing tag, which exhibits the same
spelling and capitalization as your opening tag, but with one tiny change: a / appears right before the element name.

#Example:
<myElement>some content here</myElement> 
 <elements> 
  <myelement>one</myelement> 
  <myelement>two</myelement> 
 </elements>
 
In XML, an element consists of an opening tag, its attributes, any content, and a closing tag. A tag – either opening or closing – 
is used to mark the start or end of an element. Any element can have an attribute. Attribute values must be single- or double-quoted. 
