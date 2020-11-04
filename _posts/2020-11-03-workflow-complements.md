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


I am a very visual person. I understand information better when it is presented with a visual structure.

Also, I don't like losing time on something I already solved in the past.

So I acted on that and adapted my workflow accordingly.

## Diagrams
Drawing diagrams. We all admit their values. But. It requires a tool we aren't really used to, hours spent thinking in a way they're not used to either, and all that for producing value they don't always care to produce. In other words: producing a diagram is an _event_.

And like all _events_ (washing dishes, deploying your software to production, writing integration tests... cleaning your fridge?), if we did them more regularly, they would become _non-events_: something easy and quick to do, practical, and valuable.

I personally find that diagrams help me _understand_, they help me _think_, and they help me _focus_. To me, they are a way of taking notes with the whole "A picture is worth a thousand words" added value.

But if I was to fire up a new window or create a new tab in my web browser in order to use them, it would just not be cost-efficient at all in terms of focus.

So how do I do?

The answer:
* [plantuml](https://plantuml.com/)'s cli interface
* a text file representing a diagram
* a keyboard mapping to trigger the diagram generation in the background as a png file
* a web browser to display the diagram after it's generated.

Let me show you.

Diagram generation on-the-go from my text editor:

[![unittestplan]({{ site.baseurl }}/assets/img/unittestplan.png)]({{ site.baseurl }}/assets/img/unittestplan.png)

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

As you can see, I'm using it to generate a sort of checklist that helps me think more rigorously (about unit tests, in this case)

That being said, that text file looks long to write. I must have lost a lot of time/focus writing it!

Or have I?

## Snippets
Snippets are a common way of generating text with placeholders for the parts you want to customize.

A gif is worth a thousand words.

[![unittestplantuml]({{ site.baseurl }}/assets/img/unittestplantuml.gif)]({{ site.baseurl }}/assets/img/unittestplantuml.gif)

I'm designing at the same time as I'm writing. I basically use the snippet as a thinking assistant!

But how easy is it to create your own snippets?

On Visual Studio, each snippet is a complete xml file with a heavy syntax, and getting to their location is quite painful. We are once again poking at the notion of _event_.

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

That doesn't inspire you to create snippets on Visual Studio, does it?

Vim's snippet plugin [UltiSnips](https://github.com/SirVer/ultisnips) lets you edit your snippets _much_ more easily:
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

It suddenly became a _non-event_.

Every time I compare Visual Studio's snippets with vim's (or vscode's) snippets, it reminds me that a **huge** part of the value of a tool is in its ability to go along with my workflow. In fact, had I stayed on Visual Studio, I would _never_ have thought of making my own snippets!

## Todolist & smaller commits
For me, **planning** what I expect to be **done** at the end of the day is an important part it: it gives me a sense of direction, and boundaries to help me chose my trade-offs between thinking and producing.

Additionally, I like to measure my productivity through my commits.

From my perspective, **Commits are value.**

For that reason, I want to commit as soon as I made a change in the code source that compiles and passes the unit tests.

This is my commit workflow:

| #       | Steps                            |
| --      | --------                         |
| **1**   | Edit code                        |
| **2**   | Compile                          |
| **3**   | If Compilation was OK, Run tests |
| **4**   | If Test Runs were OK, Commit     |
| **...** | Rinse and repeat                 |

I used to try tokeep in mind to commit more often. However, oftentimes I would forget, inspired by the incentive to move on.

For that reason, I made it so that every time my solution is building, it automatically runs the tests afterwards and then displays a "commit screen" if everything was green.

That way, my workflow commands my habits and I don't rely on my fallible sense of discipline anymore.

Below, my "dashboard" screen inside vim.
[![dashboard]({{ site.baseurl }}/assets/img/dashboard.png)]({{ site.baseurl }}/assets/img/dashboard.png)

You can see at the top an interactive `git status` split (provided by vim's excellent `vim-fugitive` plugin), some space for displaying file diffs, then three plain files:

| File             | Description                     |
| --               | --------                        |
| **todo**         | my todolist                     |
| **done**         | things I've done recently       |
| **achievements** | things I should feel good about |

I would use that screen to commit my changes, update my todolist, and acknowledge that I made progress.

Moving things on my todo list should always be a moment of celebration. However, celebrating cannot be all black and white. Celebration means colors, joy and wellness! For that precise reason, I build a HTML file from the content of these files and display it in my web browser:

[![dashboardhtml]({{ site.baseurl }}/assets/img/dashboardhtml.png)]({{ site.baseurl }}/assets/img/dashboardhtml.png)

Looking great!

And that's how I turned each commit into a small celebration. Small, but important!

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
