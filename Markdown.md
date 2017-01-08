Markdown
================
Markdown was created in 2004 by John Gruber.  It allows for plain-text formatting with little to no markup and easy conversion to HTML.  Its focus is on readability.  It's syntax is simple and deliberately limited - not intended for comprehensive conversion.  

Markdown Flavors
----------------
Since its inception, there have been numerous adjustments and additions to Markdown.  Markdown's popularity along with it's lack of an evolving standard has spawned myriad pop-up flavors, most serving a specific niche.  These are the three major flavors supported by Brett Terpstra's _MarkdownEditing_ package for **_Sublime Text_**.

### Standard Markdown (MD)
This is the original Markdown specification as stated by John Gruber.  Gurber considers it complete and has not adjusted it - or even commented on it - in years.  Standard Markdown is deliberately minimalistic.

* Complete Syntax listed at [Daring Fireball](http://daringfireball.net/projects/markdown/syntax) : v1.0.1 - 17Dec2004

### GitHub Flavored Markdown (GFM)
This is a well-known flavor as it's utilized throughout the GitHub website.  It has various tweaks and additions, primarily to enhance the display and readability of code.  Since it's designed to be used by coders on the GitHub site, it's processing takes into account inevitable poor practices by users or even possible malicious intent.

* Syntax listed at [Writing on GitHub](https://help.github.com/categories/writing-on-github/)   
* The latest build of [GFM](https://github.com/github/markup)  

### MultiMarkdown (MMD)
Multi-Markdown, by Fletcher T. Penny, extends the original specification to accommodate many more typography and publishing related tasks (footnotes, citations, captions, etc.) as well as more conversion types than just HTML - namely LaTeX.  It also allows for the incorporation of metadata.  

* Multi-Markdown Syntax [Cheat-Sheet](https://rawgit.com/fletcher/human-markdown-reference/master/index.html)  
* Latest build of [MultiMarkdown](http://fletcherpenney.net/multimarkdown/)

# Markdown Syntax
Starting with the standard specification, Markdown syntax is comprised entirely of punctuation chosen specifically to support readability.

**Note:** This is intended to be a somewhat comprehensive, but not exhaustive, listing of specific Markdown syntaxes.  For complete reference, consult original sources (the links above.)  

## Block Level Elements

### Headers
Headers can be defined _Setext_ style:

>Heading (h1)  
 \\=================

by placing equals signs `=` under the heading

>Subheading (h2)  
 \----------------  

by placing dashes `-` under the subheading

Headers can also be defined _atx_ style (h1-h6) by using the number-sign `#`
>  
 \# Heading 1  
 \## Heading 2  
 \### Heading 3  
 \#### Heading 4  
 \##### Heading 5  
 \###### Heading 6  

### Paragraphs and line breaks
Paragraphs are defined whenever text is preceded by a blank line.  Lines are hard-wrapped so the next line with be appended to the previous unless separated by a blank line.  To enforce a new-line without adding a blank line, insert **two spaces** after the last character in a line before the carriage-return.

### Blockquotes
Blockquotes are defined by preceding a block with the right angle-bracket.  The '>' is only necessary at the beginning of the block, but one per line helps readability.  Blockquotes can be nested.

>\> Quote
>>\> \> Those who believe in telekinesis, raise my hand.  \> \> ~ Kurt Vonnegut

### Lists
Unordered Lists are defined using th `*`, `+`, or `-`

>\* Item 1  
 \* Item 2  
 \* Item 3  

Ordered Lists are defined using numbers (the actual number doesn't matter.)

>_1. First_  
 _2. Second_  
 _3. Third_  

### Code Blocks
Code blocks are defined by indenting four spaces (notionally one full tab.)

    function (){
        return;
    }

### Horizontal Rules
A Horizontal Rules is placed by using three or more `***`, `---` or `___` with or without spaces.

\*\*\*  
or  
\* \* \*  
will make  

***

## Inline Elements

### Links
Links are defined using brackets as follows:
>
This is an \[example link\](http:www.example.com "Optional Title") for demonstration.

Links can also be passed a reference with an ID that can be placed anywhere in the document:
>
This is another \[example link\]\[id\]  
>  
\[id\]: http:www.example.com "Optional Title"

The ID can also be implicit, and the optional title can also appear in parenthesis instead of quotes, and on the next line if necessary or desired:
>
Search at \[Google\] \[ \]
>  
\[Google\]: http:www.google.com  
   (Google)

### Emphasis
Emphasis (typically italics) and Strong (bold) can be achieved using single or double of either `_` or `*`.

Single: \__emphasis_\_ or \**emphasis*\*

Double: \_\___Strong__\_\_ or \*\***Strong**\*\*

## Syntax for GitHub Flavored Markdown
GitHub changes and adds to standard Markdown in a number of ways.  It is designed specifically to be utilized by coders on the GitHub site itself.

### An End to Intra-word Emphasis
In standard Markdown emphasis can exist in the middle of a word: 'un\_frigging\_believable', becomes 'un<em>frigging</em>believable!'

This has undesirable effect within code such as: `user_last_name`, so the intra-word emphasis ability has been disabled.

### Strikethrough
Strike through text is designated with double `~`:  
'~~Mistake~~' becomes <del>Mistake</del>  

### Fenced Code Blocks
Code Blocks can be declared using a triple-tick ` ``` ``, alleviating the need for selective indenting of each line.  

    '''
    Code Block
    '''

### Tables
Tables can be constructed using pipes `|` and dashes `-`

```
    First Name | Last Name
    -----------|----------
      John     |   Doe
      Jane     |   Moe
```
makes:  

First Name | Last Name
-----------|----------
  John     |   Doe
  Jane     |   Moe

Tables don't *have* to line up neatly to render properly in HTML. A colon `:` can also be used to designate if a column is right or left aligned:

```
    left aligned| right aligned
    :--|--:
    John | Doe
    Jan | Moe
```

  left aligned| right aligned
  :--|--:
  John | Doe
  Jan | Moe

### Syntax Highlighting
The GitHub website also provides syntax highlighting for Markdown and various programming languages as well.

## MultiMarkdown Syntax
MultiMarkdown syntax is the most comprehensive in this listing.  This is because while Markdown was intended for plain-text to HTML, MultiMarkdown extends the concept to publishing formats as well.

### Metadata
Metadata must be a the beginning of the file, each item at beginning of the line, and specified as a `name: value` pair.  The metadata block should be followed by a blank line.

### Tables
As in GFM tables are also supported in MultiMarkdown.   MMD allows for table names too - placed in square brackets at bottom of the table.

### Definition Lists
The term is immediately followed by a carriage return, and then a colon `:` on the newline followed by the definition:
>
Word  
&#58; definition goes here

Looks like:

Word
: definition goes here

### Red Ink
MultiMarkdown has its own syntax for strikethrough plus syntax for underlining and highlighting.
>
Delete {--this--} word.

>
Underline {++this++} word.

>
Highlight {==this==} word.

### Footnotes, Endnotes, Citations and Glossary
MultiMarkdown supports footnotes, but apparently HTML doesn't differentiate between footnotes and endnotes, so they always end up at the end of the document.

>
Here is a footnote.\[^name]  This is the next sentence.
>
\[^name]: Here is the footnote itself.
>
More text. And more and more. Another footnote.\[^second] And more and more.
>
\[^second]: The second footnote.
>
Last paragraph.
>
(footnotes would appear at the end of the document)

**Note:** It'd be nice if there was a way to declare the placement of footnotes in a HTML document.  Using MMD's [page breaks] syntax seems intuitive, but doesn't work.

Since all are essentially endnotes they can also serve as citations or with [definition lists] to create glossary terms.

### Cross References
Links can also be used to create cross-references.  Inspecting the HTML in Marked preview (CMD+u) reveals every header is tagged with an ID equal to its text (I'm wincing inside now too.)  Headings can be given a custom ID as well.

>
Head up to the top of this section \[MultiMarkdown Syntax\]\[\].

becomes:  

Head up to the top of this section [MultiMarkdown Syntax][].

> ###### Sample Heading \[customID\]

### Math
Here are samples of how to incorporate math formulas:

>\\[ {e}^{i\pi }+1=0 \\]   
>$${e}^{i\pi }+1=0$$   
>A formula, \\( {e}^{i\pi }+1=0 \\), inside a paragraph.   
>A formula, ${e}^{i\pi }+1=0$ , inside a paragraph. (Note space after the '$') >x^2,y     
>x^2,y^    
>x~z,y     
>x~z,y~  

**Note:** This doesn't seem to render properly in HTML, but is presumably very powerful in LaTeX.

## Marked app Syntax  
These are special commands specific to the Marked.app program itself.  They serve as preprocessor commands to influence the conversion process.  As in MultiMarkdown some commands are specific to publishing conventions rather than HTML.  

## Page Breaks
Page breaks are inserted through the use of the command `BREAK` within an HTML comment:

>
<!-\-BREAK-\->

### File Inclusion
To include the contents of additional files:

>
<<\[folder/filename\]

To include external files as code, i.e. &#60;pre&#62;&#60;code&#62;, use parenthesis instead:

>
<<\(folder/filename\)

To include external files that remain untouched, i.e. not processed, use brackets:

>
< <\{folder/filename\}

Naturally, this last option should already be well formatted.
