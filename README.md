# Into to XML

* XML stands for Extensible Markup Language
* XML is a markup language much like HTML
* XML was designed to store and transport data
* XML was designed to be self-descriptive

#### Syntax: 

The simplest XML elements contain an opening tag, a closing tag, and some content. The opening tag begins with a left angle bracket (<), 
followed by an element name that contains letters and numbers (but no spaces), and finishes with a right angle bracket (>). In XML, 
content is usually parsed character data. It could consist of plain text, other XML elements, and more exotic things like XML entities, 
comments, and processing instructions (all of which we’ll see later). Following the content is the closing tag, which exhibits the same
spelling and capitalization as your opening tag, but with one tiny change: a / appears right before the element name.

#### Example:

```
<elements> 
    <myelement>one</myelement> 
    <myelement>two</myelement> 
 </elements>
 ```
 
#####Elements:

In XML, an element consists of an opening tag, its attributes, any content, and a closing tag. A tag – either opening or closing – 
is used to mark the start or end of an element. In the above example we have 3 elements: "elements" and 2 "myelement". Pay attention that the element names are case sensetive and in our example mean different things. 

#####Attributes:

Inside the tag, following the element name, there can be some data (e.g. myElement="Main element"). This is called an attribute.
You can think of attributes as adjectives – they provide additional information about the element that may not make any sense as content.
If we modify our example and add attributes to every element, our example will look like this:

```
<elements="parentElement"> 
    <myelement="childElement1">one</myelement> 
    <myelement"childElement2">two</myelement> 
 </elements>
 ```
 
 #####NameSpacing:
 One of the features of xml is that you can define your own elemnents, which provides flexibility and scope. But it also creates the strong possibility that, when combining XML content from different sources, you’ll experience clashes between code in which the same element names serve very different purposes. For example, if you’re running a bookstore, your use of <element> tags in XML may be used to track books. A mortgage broker would use <element> in a different way – perhaps to track a deed. A dentist or doctor might use <element> to refer to chemical solution. Here is where problems can arise. To solve this ambiguity XML namespaces attempt to keep different semantic usages of the same XML elements separate. In our example, each person could define their own namespace and then prepend the name of their namespace to specific tags: <book:element> is different from <broker:element> and <medrec:element>. A Namespace is a set of unique names. A namespace is declared as follows:
 ```
<elements xmlns:pfx="http://www.example.com" />
 ```
In the attribute xmlns:pfx, xmlns is like a reserved word, which is used only to declare a namespace. In other words, xmlns is used for binding namespaces. A namespace has a prefix, in our example it is "pfx", and URI, "http://www.example.com". Although a namespace usually looks like a URL, that doesn't mean that one must be connected to the Internet to actually declare and use namespaces. Our full example would look like this:
 ```
<?xml version="1.0"?>
<elements xmlns:pfx="http://www.example.com" />
  <pfx:myelement="childElement1">one</pfx:myelement>
  <pfx:myelement="childElement2">two</pfx:myelement>
</elements>
 ```
 
The tags myelement are associated with the namespace "http://www.example.com".




