---
layout: post
title:  "Workflow Complements"
date:   2020-11-03
categories: workflow
---

Diagrams. Notes. Checklists. Templates. Snippets. Todolists. Timeboxing. Smaller commits. Macros. The list goes on and on. These help you provide more value. Do you get the best value from them?

Hi!

> Even the smallest changes in our daily routine can create incredible ripple effects that expand our vision of what is possible.
>
> &mdash; <cite>Charles F. Glassman</cite>

&nbsp;


I am a very visual person. I like displaying information under the shape of a diagram, typically.

Also, I like struggling on something the first time, then wing them starting with the second time.

For these purposes, I have equipped myself accordingly.

## Diagrams
A lot of people I know don't like drawing diagrams: it requires a tool they don't use daily, hours of time thinking in a way they're not used to, producing value they don't always like to produce. In other words: producing a diagram is an _Event_.

However, I find that diagrams help me _understand_, they help me _think_, they help me _focus_. It's a visual trace for a certain structuration of pieces of information, which allows me to write it down and safely forget about it - until I read it next time.

But if I was to fire up a new window or create a new tab in my web browser in order to use them, it wouldn't feel cost-efficient in terms of focus.

So how do I do?

The answer:
* a text file
* plantuml's cli interface
* a keyboard mapping to trigger the diagram generation in the background
* my web browser to display the diagram after it's generated.

Tadaa!

Diagram generation on-the-go from my text editor:

![unittestplan]({{ site.baseurl }}/assets/img/unittestplan.png)

That image was generated from the following text file:
```
@startmindmap
title ConvertTwoIntsToString: (int, int) => string
* Unit Tests

** happy_path
*** (0,0) => "zero"
**** (0,0) => zero


** supported edge cases
*** (-1, -1) => unsupported
**** behavior

** specified as out of scope
*** some_value
**** do not throw

** not mentioned in specifications
*** some_value
**** can throw - we don't care

@endmindmap
'https://plantuml.com/fr/mindmap-diagram
```

As you can see, I'm using it to generate a sort of checklist that helps me think more rigorously.

That being said, that text file looks long to write. I must have lost a lot of focus on the syntax!

Or have I?

## Snippets
Snippets are a common way of generating text with placeholders for the parts you want to customize.

A gif is worth a thousand words.

![unittestplantuml]({{ site.baseurl }}/assets/img/unittestplantuml.gif)


However, how easy is it to create your own snippets?

On Visual Studio, each snippet is a complete xml file with a heavy syntax, and getting to their location is quite painful:

```xml
<Snippet>
  <Code Language="Plantuml">
    <![CDATA[@startmindmap
title $Method$: ($Parameters$) => $Return$
* Unit Tests

** happy_path
*** $HappyPathInput$
**** $HappyPathInput1$
$OtherHappyPaths$

** supported edge cases
*** $SupportedEdgeCaseInput$
**** $SupportedEdgeCaseBehavior$

** specified as out of scope
*** $OutOfScopeInput$
**** $OutOfScopeBehavior$

** not mentioned in specifications
*** $UnspecifiedInput$
**** $UnspecifiedBehavior$

@endmindmap
'https://plantuml.com/fr/mindmap-diagram]]>
  </Code>
  <Declarations>
    <Literal>
      <ID>Method</ID>
      <Default>MyMethod</Default>
    </Literal>
    <Literal>
      <ID>Parameters</ID>
      <Default>string</Default>
    </Literal>
    <Literal>
      <ID>Return</ID>
      <Default>string</Default>
    </Literal>
    <Literal>
      <ID>HappyPathInput</ID>
      <Default>acceptance_test</Default>
    </Literal>
    <Literal>
      <ID>HappyPathInput1</ID>
      <Default>first_increment</Default>
    </Literal>
    <Literal>
      <ID>OtherHappyPaths</ID>
      <Default>first_increment</Default>
    </Literal>
    <Literal>
      <ID>SupportedEdgeCaseInput</ID>
      <Default>some_value</Default>
    </Literal>
    <Literal>
      <ID>SupportedEdgeCaseBehavior</ID>
      <Default>behavior</Default>
    </Literal>
    <Literal>
      <ID>OutOfScopeInput</ID>
      <Default>some_value</Default>
    </Literal>
    <Literal>
      <ID>OutOfScopeBehavior</ID>
      <Default>behavior</Default>
    </Literal>
    <Literal>
      <ID>UnspecifiedInput</ID>
      <Default>some_value</Default>
    </Literal>
    <Literal>
      <ID>UnspecifiedBehavior</ID>
      <Default>can throw - we don't care</Default>
    </Literal>
  </Declarations>
</Snippet>
```

That doesn't make you want to create snippets on Visual Studio, does it?

On the other hand, Vim's snippet plugin [UltiSnips](https://github.com/SirVer/ultisnips) lets you edit your snippets _much_ more easily:
* one file contains all the snippets for each file type
* you instantly access it from a keyboard mapping of your choice
* the syntax is dead simple:

```
snippet ut "unit test listing" b
@startmindmap
title ${1:MyMethod}: (${2:string}) => ${3:string}
* Unit Tests

** happy_path
*** ${4:acceptance_test}
**** ${5:first_increment}
$6

** supported edge cases
*** ${7:some_value}
**** ${8:behavior}

** specified as out of scope
*** ${9:some_value}
**** ${10:do not throw}

** not mentioned in specifications
*** ${11:some_value}
**** ${0:can throw - we don't care}

@endmindmap
'https://plantuml.com/fr/mindmap-diagram
endsnippet
```

Now, integrating snippet creation into your workflow sounds _manageable_, doesn't it?

Every time I compare Visual Studio's snippets with vim's (or vscode's) snippets, it reminds me that a **huge** part of the value of a tool is in its ability to go along with my workflow. In fact, had I stayed on Visual Studio, I would _never_ have thought of making my own snippets!

## Todolist & smaller commits
Planning what I expect to be done in the current day is an important part of my day: it gives me a sense of direction, and boundaries to help me picking my trade-offs between thinking and producing.

Additionally, I like to measure my productivity through my commits.

**Commits are value.**

For that reason, I want to commit as soon as I made a change in the code source that compiles and passes the unit tests.

This is my commit workflow:

| #       | Steps                            |
| --      | --------                         |
| **1**   | Edit code                        |
| **2**   | Compile                          |
| **3**   | If Compilation was OK, Run tests |
| **4**   | If Test Runs were OK, Commit     |
| **...** | Go back to step 1                |

I used to keep in mind to commit often - but I usually forgot, overwhelmed by the incentive to move on.

For that reason, I made so that every time I build the solution, it automatically runs the tests and displays the commit screen if everything was green. Why bother remembering the procedure when the procedure is in the tool?

![dashboard]({{ site.baseurl }}/assets/img/dashboard.png)

This is my "dashboard" screen inside vim. You can see an interactive `git status` output provided by vim's `vim-fugitive` plugin on the top split, some space for displaying file diffs, and three plain files:

| File             | Description                     |
| --               | --------                        |
| **todo**         | my todolist                     |
| **done**         | things I've done recently       |
| **achievements** | things I should feel good about |

I would then commit my changes, update my todolist, and feel well for making progress in the right direction.

I personally link a dark background to work, but I like a bit more colors for celebration. For that reason, I took the liberty to make an HTML generator from the content of these files:

![dashboardhtml]({{ site.baseurl }}/assets/img/dashboardhtml.png)

And that's how I turned each commit into a small celebration!

```
:smile
                            oooo$$$$$$$$$$$$oooo
                        oo$$$$$$$$$$$$$$$$$$$$$$$$o
                     oo$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$o         o$   $$ o$
     o $ oo        o$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$o       $$ $$ $$o$
  oo $ $ "$      o$$$$$$$$$    $$$$$$$$$$$$$    $$$$$$$$$o       $$$o$$o$
  "$$$$$$o$     o$$$$$$$$$      $$$$$$$$$$$      $$$$$$$$$$o    $$$$$$$$
    $$$$$$$    $$$$$$$$$$$      $$$$$$$$$$$      $$$$$$$$$$$$$$$$$$$$$$$
    $$$$$$$$$$$$$$$$$$$$$$$    $$$$$$$$$$$$$    $$$$$$$$$$$$$$  """$$$
     "$$$""""$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$     "$$$
      $$$   o$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$     "$$$o
     o$$"   $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$       $$$o
     $$$    $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$" "$$$$$$ooooo$$$$o
    o$$$oooo$$$$$  $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$   o$$$$$$$$$$$$$$$$$
    $$$$$$$$"$$$$   $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$     $$$$""""""""
   """"       $$$$    "$$$$$$$$$$$$$$$$$$$$$$$$$$$$"      o$$$
              "$$$o     """$$$$$$$$$$$$$$$$$$"$$"         $$$
                $$$o          "$$""$$$$$$""""           o$$$
                 $$$$o                                o$$$"
                  "$$$$o      o$$$$$$o"$$$$o        o$$$$
                    "$$$$$oo     ""$$$$o$$$$$o   o$$$$""
                       ""$$$$$oooo  "$$$o$$$$$$$$$"""
                          ""$$$$$$$oo $$$$$$$$$$
                                  """"$$$$$$$$$$$
                                      $$$$$$$$$$$$
                                       $$$$$$$$$$"
                                        "$$$""""
```
