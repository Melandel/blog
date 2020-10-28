---
layout: post
title:  "Vim: the text edition paradigm"
date:   2020-10-28
categories: vim
---

**Vim**. You may have heard about it - it is, after all, [_ubiquitous_](https://www.vim.org/). Most people scratch the surface, find it too unintuitive, and walk away. Some others stay, but don't dig. _I_ digged for you.

> Practical vim: Edit Text at the Speed of Thought
>
> &mdash; <cite>Drew Neil</cite>

&nbsp;

## Interactions through <u>language</u>

In vim's paradigm, you **command** vim to edit text _via_ a **_composable_ language**.

Vim's language is made from **three elements** : verbs, complements, and counts.

| Vim language           | Vim command | Verb          | Complement    | Count         |
| -------------          | ----------- | ------------- | ------------- | -----------   |
| "Change a word."       | `caw`       | `Change`      | `a word`      | `1` (default) |
| "Delete a paragraph."  | `dap`       | `Delete`      | `a paragraph` | `1` (default) |
| "Yank (copy) 2 words." | `y2w`       | `Yank`        | `a word`      | `2`           |

## A typical text edition workflow in vim

Vim's language paradigm allows for a very special command:

| Vim  language         | Vim command |
| --                    | --          |
| "Repeat last command" | `.`         |

![repeatlastchange]({{ site.baseurl }}/assets/img/repeatlastchange.gif)

Hence a typical **on-the-fly-macro-style workflow** in vim that many view as a productivity boost:

| #       | Steps                                                    |
| --      | --------                                                 |
| **1**   | Move the cursor to a text region to edit                 |
| **2**   | Command vim to edit text                                 |
| **3**   | Move the cursor somewhere else and `Repeat last command` |
| **...** | Repeat last step as many times as needed                 |

## Some of the most commonly used vim language elements

Vim's language itself is very vast, but just like [git](https://git-scm.com/), knowing a few basic elements is enough to power through 90% of your needs in practice.

Here is a _small_ compilation of vim language elements that might address 90% of your needs:

| Verbs                       | Complements                                               | Cursor Motions                                                                         |
| -------                     | -----                                                     | ----                                                                                   |
| `c` Change                  | `^` to the 1st character of the line                      | `^` move to the first character of the line                                            |
| `d` Delete                  | `$` to the end of the line                                | `$` move to the end of the line                                                        |
| `y` Yank                    | `f[c]` to the character `[c]` in the line                 | `f[c]` move to the character `[c]` in the line                                         |
| `>` Increase indent         | `t[c]` till before character `[c]` in the line            | `gg` move to the first line of the file                                                |
| `<` Decrease indent         | on all visually selected characters                       | `G` move to the last line of the file                                                  |
| `r` Replace every character | `:g/regex/[cmd]` on every line matching a given regex     | `w` move to the beginng of next word                                                   |
| `J` Join line with the next | `:v/regex/[cmd]` on every line NOT matching a given regex | `}` move to the end of the current paragraph                                           |
| `A` Append to line          | `aw` on a word                                            | `:cn` move to a position described by the output of a program (_eg_ compilation error) |
| `I` Prepend to line         | `a{` on a block defined by brackets                       | `gd` move to the definition of a function                                              |


## A quick glimpse into the abyss

Because you can also **build your own language elements** fairly easily, _i.e._ add your own words, the language itself is infinite.

For the sake of **curiosity**, here is a bigger sample of vim language elements:

| Verbs                                        | Complements                                                | Cursor Motions                                                                         |
| -------                                      | -----                                                      | ----                                                                                   |
| `c` Change                                   | `^` to the 1st character of the line                       | `^` move to the first character of the line                                            |
| `d` Delete                                   | `$` to the end of the line                                 | `$` move to the end of the line                                                        |
| `y` Yank                                     | `f[c]` to the character `[c]` in the line                  | `f[c]` move to the character `[c]` in the line                                         |
| `~` Swap case                                | `t[c]` till before character `[c]` in the line             | `t[c]` till before character `[c]` in the line                                         |
| `gu` Make lowercase                          | `gg` to the first character of the file                    | `gg` move to the first line of the file                                                |
| `gU` Make uppercase                          | `G` to the last line of the file                           | `G` move to the last line of the file                                                  |
| `!` Filter through an external program       | `aw` on a word                                             | `w` move to the beginng of next word                                                   |
| `gq` Text formatting                         | `ap` on a block delimited by new lines (= paragraph)       | `b` move to the beginning of current/last word                                         |
| `gw` Text formatting with no cursor movement | `a{` on a block delimited by brackets                      | `}` move to the end of the current paragraph                                           |
| `g?` rOT13 encoding                          | `at` on a block delimited by markup tags                   | `{` move to the beginning of the current/previous paragraph                            |
| `>` Increase indent                          | `aa` on a function argument                                | `n` move to the beginning of a searched regex                                          |
| `<` Decrease indent                          | on all visually selected characters                        | `n` move to the end of a searched regex                                                |
| `zf` Define a fold                           | on all visually selected lines                             | `gf` move to the file which path is under the cursor                                   |
| `ga` Vertically align                        | `:g/regex/[cmd]` on every line matching a given regex      | `hjkl` move n'th characters to the left, right, top or down of current position        |
| `r` Replace every character                  | `:v/regex/[cmd]` on every line NOT matchinig a given regex | `<C-FDUB>` move n'th "pages" or "semi-pages" to the top or down of current position    |
| `J` Join line with the next                  | `:%[cmd]` on every line of the file                        | `"[m]` move to a position you have assigned to a marker in the past                    |
| `S` Split line by a given character          | `)` till next sentence                                     | `<C-O>` move to a position you have jumped to in the past                              |
| `@` Repeat a macro                           | `aW` on a Word                                             | `g;` move to a position you have edited in the past                                    |
| `A` Append to line                           | `af` on a function                                         | `:cn` move to a position described by the output of a program (_eg_ compilation error) |
| `I` Prepend to line                          | `ai` on a block defined by its indentation level           | `gd` move to the definition of a function                                              |

## A rewarding learning experience

Like any language, you start with **a few, massively used** words. Then you learn bit by bit with each situation you come across, one word at a time.

Because of the **composability** of the language, each word you learn is going to have a _tremendous_ amount of applications, which makes vim a **fun** and **rewarding** learning _experience_.

I'm ending this post with a video showing how vim can help you power through certain concrete tasks:

<iframe width="560" height="315" src="https://www.youtube.com/embed/futay9NjOac" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
