# HTML & CSS

## Introduction:
 > Understanding HTML and CSS
can help anyone who works
with the web; designers can
create more attractive and
usable sites, website editors can
create better content, marketers
can communicate with their
audience more effectively, and
managers can commission
better sites and get the best out
of their teams.

## In order to learn about creating web pages you must know that it is divided into three sections:
* HTML:
  >  HTML is used to
create web pages. You will see
that you start by writing down
the words you want to appear
on your page. You then add tags
or elements to the words so
that the browser knows what is
a heading, where a paragraph
begins and ends, and so on.

* CSS:
  > CSS
uses rules to enable you to
control the styling and layout
of web pages. We then go on to
look at the wide variety of CSS
properties you can use in your
CSS rules. These properties
generally fall into one of two
categories( *Presentation* , *Layout* ).

*  Practical:
  > We look at some new tags that
will be introduced in HTML5 to
help describe the structure of
your pages. HTML5 is the latest
version of HTML (still under
development at the time of
writing). Before learning about
these elements, you need a good
grasp of how CSS is used to
control the design of web pages.
There is a chapter that talks you
through a design process that
you might like to follow when
creating a new website.

# Structure:
## How pages use structure?
### Think about the stories you
read in a newspaper: for each
story, there will be a headline,
some text, and possibly some
images. If the article is a long
piece, there may be subheadings
that split the story into separate
sections or quotes from those
involved. Structure helps readers
understand the stories in the
newspaper.


## HTML Uses Elements to Describe the Structure of Pages:
### There are several different elements. Each element has an opening tag and a closing tag.
### Tags act like containers. They tell you something about the information that lies between their opening and closing tags.


## Attributes Tell Us More About Elements:
### Attributes provide additional information about the contents of an element. They appear on the opening tag of the element and are made up of two parts: a name and a value, separated by an equals sign.
  > The attribute name indicates what kind of extra information you are supplying about the element's content. It should be written in lowercase.
  > The value is the information or setting for the attribute. It should be placed in double quotes. Different attributes can have different values.
  
# Structure summary:
 * HTML pages are text documents.
 * HTML uses tags (characters that sit inside angled
brackets) to give the information they surround special
meaning.
 * Tags are often referred to as elements.
 * Tags usually come in pairs. The opening tag denotes
the start of a piece of content; the closing tag denotes
the end.
 * Opening tags can carry attributes, which tell us more
about the content of that element.
 * Attributes require a name and a value.
 * To learn HTML you need to know what tags are
available for you to use, what they do, and where they
can go.



# Extra Markup:

## The evolution of HTML:
### Since the web was first created, there have been several different versions of HTML:
 | version | date |
 |---------|------|
 | HTML 4 | released 1997 |
 | HTML 1.0 | released 2000|
 | HTML 5 | released 2000|
 
 
 
## Doctypes:
 > Because there have been
several versions of HTML, each
web page should begin with a
DOCTYPE declaration to tell a
browser which version of HTML
the page is using (although
browsers usually display the
page even if it is not included). 

## Comments in HTML :
 > If you want to add a comment
to your code that will not be
visible in the user's browser, you
can add the text between these
characters:
\<!--  -->

## ID attrebute:
 > Every HTML element can carry
the id attribute. It is used to
uniquely identify that element
from other elements on the
page. Its value should start with
a letter or an underscore (not a
number or any other character).
It is important that no two
elements on the same page
have the same value for their id
attributes (otherwise the value is
no longer unique).

## Class attribute:
 > Every HTML element can
also carry a class attribute.
Sometimes, rather than uniquely
identifying one element within
a document, you will want a
way to identify several elements
as being different from the
other elements on the page. 

## Block elements:
 > Some elements will always
appear to start on a new line in
the browser window. These are
known as block level elements. 
 > Examples of block elements are
\<h1>, \<p>, \<ul>, and \<li>.

## Inline elements:
 > Some elements will always
appear to continue on the
same line as their neighbouring
elements. These are known as
inline elements.
 > Examples of inline elements are
\<a>, \<b>, \<em>, and \<img>.



# Grouping Text & Elements In a Block:
* \<div>:
  > The \<div> element allows you to group a set of elements together in one block-level box.
  
* \<span>:
  > The \<span> element acts like an inline equivalent of the \<div> element. It is used to either:
     1. Contain a section of text where there is no other suitable element to differentiate it from its surrounding text.
     2. Contain a number of inline elements.
     
     
## HTML 5 Summary Layout:
 * The new HTML5 elements indicate the purpose of different parts of a web page and help to describe its structure.
 * The new elements provide clearer code (compared with using multiple \<div> elements).
 * Older browsers that do not understand HTML5 elements need to be told which elements are block-level elements.
 * To make HTML5 elements work in Internet Explorer 8 (and older versions of IE), extra JavaScript is needed, which is available free from Google.
 
 
 ## Process & Design:
  1. It's important to understand who your target audience is, why they would come to your site, what information they want to find and when they are likely to return.
  2. Site maps allow you to plan the structure of a site.
  3. Wireframes allow you to organize the information that will need to go on each page.
  4. Design is about communication. Visual hierarchy helps visitors understand what you are trying to tell them.
  5. You can differentiate between pieces of information using size, color, and style.
  6. You can use grouping and similarity to help simplify the information you present.
  

#  JavaScript introduction:
 ##  Learning to program with JavaScript involves: 
  > Understanding some basic programming concepts and the terms that JavaScript programmers use to describe them. 
  > Learning the language itself, and, like all languages, you need to know its vocabulary and how to structure your sentences.
  > Becoming familiar with how it is applied by looking at examples of how JavaScript is commonly used in websites today.
  
  



## A script is a series of instructions that a computer can follow to achieve a goal. 
## Scripts are made up of instructions a computer can follow step-by-step, a browser may use different parts of the script depending on how the user interacts with the web page, scripts can run different sections of the code in response to the situation around them. 



## WRITING A SCRIPT:
### To write a script, you need to first state your goal and then list the tasks that need to be completed in order to achieve it.

## What is a script and how do I create one?
 * A script is a series of instructions that the computer can follow in order to achieve a goal. 
 * Each time the script runs, it might only use a subset of all the instructions. 
 * Computers approach tasks in a different way than humans, so your instructions must let the computer solve the task prggrammatically. 
 * To approach writing a script, break down your goal into a series of tasks and then work out each step needed to complete that task (a flowchart can help). 
 
## How do computers fit in with the world around them?
 * computers creats models of the world using data.
 * the models use objects to represent physical things.
 * programmers can write code to say " when this event occurs, run that code. "
 * to make web pages interactive, you write code that uses the browser's model of the web page.
 
 
 ## How do I write a script for a web page?
  * It is best to keep JavaScript code in its own JavaScript file. JavaScript files are text files (like HTML pages and CSS style sheets), but they have the . js extension.
  * The HTML \<script> element is used in HTML pages to tell the browser to load the JavaScript file (rather like the \<link> element can be used to load a CSS file). 
  * If you view the source code of the page in the browser, the JavaScript will not have changed the HTML, because the script works with the model of the web page that the browser has created.
  