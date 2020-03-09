%title: Linux Dojo - Linux terminal Hot Tips
%author: Michele Morelli
%date: 15th March 2020

-> # Introduction <-


---------------------------

-> # The command line is full of surprises <-

* More things than one may think can be done efficiently (and for free) from 
the command line:
<br>

    * PDF editing (e.g. [pdftk](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/));
<br>

    * image editing (e.g. [imagemagick](https://imagemagick.org/index.php))
<br>

    * browsing the Internet (e.g. [lynx](https://lynx.browser.org/))
<br>

    * Word processing (e.g. [vim](https://www.vim.org/) + [LaTEX](https://www.latex-project.org/))
<br>

    * testing RESTful API (e.g. [curl](https://curl.haxx.se/))
<br>

    * *writing presentations!* :-) (e.g. [mdp](https://github.com/visit1985/mdp))

-----------------------------------------

-> # The 'Unix Philosophy' <-

This is made possible by the *"Unix philosophy"*: many  little, robust 
programs that do one thing very well

<br>
*TIMTOWTDI (Tim Toady)* - originally from the Perl community, but applies 
well to general Linux scripting in my opinion

<br>

In contrast with Python's Zen: "There should be one — and preferably only 
one — obvious way to do it." 

---------------------------------------------

-> # Linux pipelines and functional programming <-

Linux pipelines and functional programming languages' pipelines are very similar!
We start from an 'immutable' value (usually a string) and we pass it through a 
series of functions, which take a string-argument and return a string value 
(in most cases). 
<br>

    $ String generator => S | S => S | S => S 
    
    $ String generator => S | S => S | S => S >> file.txt
    
    $ $(String generator => S | S => S | S => S >> file.txt)

<br>
*Some important caveats:*

- no guarantee of referential transparency;

- the values are not really immutable!

----------------------------------------------------------

-> # Linux pipelines and functional programming <-

Some typical string generators: 

* $cat (to read from files)
<br>

* $echo (to pass strings)
<br>

*... but really, the sky is the limit!*

-------------------------------------------------------

-> # Example 1: <-
Our manager asked us to make a short report of all the commits that were done 
for the [code-dojo repository](https://github.com/folde01/linux-dojo).

Our manager told us that the report must follow some *specific format requirements*:

- it should contain only the commits' hash codes;
- each hash code should contain only the first 6 characters;
- the output should be all-caps;

We are also told that we need to create a command that sends us back to 
the first commit in the repository.

*How can we do this with a one-liner?*

---------------------------------------------------------

-> # curl and REST API testing <-

* [curl](https://curl.haxx.se/) is a very powerful tool that allow to make 
requests using different protocols (e.g. FTP, HTTP...) and methods (GET, POST, PATCH)

* it is invaluable when testing RESTful APIs!

------------------------------------------------

-> # Example 2: <-

We need to test an endpoint of [a new REST API](https://jsonplaceholder.typicode.com/) that we are evaluating, 
and we want to ensure that the
requests using the GET method return meaningful results.

We need to check that the following endpoint:
**https://jsonplaceholder.typicode.com/todos/**

returns the correct information for items.

For example, to get information about item with ID one, we would make a get call to:
**https://jsonplaceholder.typicode.com/todos/1**

How can we make get the response codes for items *with IDs from 35 to 47 only*?

