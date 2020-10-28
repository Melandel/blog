---
layout: post
title:  "Fingers on the Home Row"
date:   2020-10-27
categories: workflow
---

We interact with our tools through **typing**, **pointing/clicking** and **shortcuts**. Here's a simple challenge: are you able to imagine what going **keyboard-only** _looks_ like? Let's confront.

> There are things you don't want to know you can do.
>
> &mdash; <cite>Robin McKinley, Sunshine</cite>

&nbsp;

So let's think together: What does going **keyboard-only** look like?

## The Home Row

Your`F` and `J` keys are special. If you look closely at them, you should see some sort of _markers_.

Why?

Well, because if you are using a keyboard, you are [supposed](https://fossbytes.com/keyboard-bumps-keys-f-j-type-faster/) to have your **index fingers placed on `F` and `J`** in order to be able to **reach all keys with the least effort**.

It is the first thing that [touch typists](https://en.wikipedia.org/wiki/Touch_typing#Advantages) (people who can type without looking at their keyboard) learn, followed by learning which finger should go to which key.

![home row]({{ site.baseurl }}/assets/img/homerow2.jpg)

When you use your keyboard that way, you'll notice that your fingers do all the work from muscle memory and your hands should almost not move.

Personally, I find that one key difference between using a mouse and using the keyboard is that:
* Using the **mouse**, I feel in a position where I **have to reach** an element on the screen
* Using the **keyboard**, I feel in a position where I **immediately** press a key

Usually, I feel more **proactive** and **in control** with a **keyboard** whereas I feel more **guided** with a **mouse**.

&nbsp;

## Item selection, but without the mouse
Because our tools are suited to the mouse & keyboard paradigm, trying to select items without a mouse cannot feel natural.

Let me list 4 selection workflows you might find yourself using when going full-keyboard.

### Fuzzy Finding
A fuzzy finder is a program that takes a list of strings as input, and allows you to select one or several of its items through fuzzy search.

What's **fuzzy search** you ask?

Here's a small showcase:
![fuzzyfinder]({{ site.baseurl }}/assets/img/fuzzyfinder.gif)

You'll see:
* queries that I'm typing (`omnilang`, `omnilog`, `bujson` and `endex`)
* elements **"matching"** my query, _i.e._ "the characters in the query appear _at some point_ in the item, _in the same order_
* I'm using file paths in this particular example but it could be **any list of strings**
	* git commits would work
	* file templates would work
	* your own custom list of strings would work
* I can also **customize the action triggered** on the currently selected item when I press `Enter`

There are several fuzzy finders out there - I'm using [fzf](https://github.com/junegunn/fzf). This video goes more into details with how you can use that amazing utility:

<iframe width="560" height="315" src="https://www.youtube.com/embed/qgG5Jhi_Els" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Click-to-shortcut transformation
Sometimes you have to stick with a visual representation of things (web browsers, for instance). In that case you can use something like [vimium - the hacker's browser](https://vimium.github.io/):

![vimium]({{ site.baseurl }}/assets/img/vimium.png)

Pressing one key allows you to display all the links you could otherwise click on, and attach a shortcut that simulates a click.

### More basic things
While the previous examples require some sort of program or script, other ways are out-of-the-box, such as global searching and good old autocompletion:
![globalcommand]({{ site.baseurl }}/assets/img/globalcommand.gif)

&nbsp;

## About the ergonomy of your keyboard...
The truth is, keyboards suffer from some design issues...
* Some keys are placed very close to your fingers but rarely used (I'm looking at you, `Caps Lock` and `AltGr`). 
* Some are going to located at different places depending on the laptop or keyboard you're looking at (`Delete`, `Home`, `End`, `Up`/`Down`/`Left`/`Right`)
* Some even have different shapes from a keyboard to another(`Enter`, anyone?).

For this reason, I created the following **remappings** for myself using [autohotkey](https://www.autohotkey.com/) (Windows only):

| Original key        | Mapped to...            |
| ---------           | --------                |
| `Esc`               | `CapsLock` (pressed)    |
| `Ctrl`              | `CapsLock`(held down)   |
| `Enter`             | `CapsLock`+`m`          |
| `§`                 | "focus my IDE's window" |
| `Tab`               | `CapsLock`+`i`          |
| `Shift`+`Tab`       | `CapsLock`+`o`          |
| `Backspace`         | `CapsLock`+`h`          |
| `Delete`            | `CapsLock`+`l`          |
| `Enter`             | `CapsLock`+`m`          |
| `Up`                | `CapsLock`+`p`          |
| `Down`              | `CapsLock`+`n`          |
| `Left`              | `CapsLock`+`j`          |
| `Right`             | `CapsLock`+`k`          |
| `Home`              | `^`+`j`                 |
| `End`               | `^`+`k`                 |
| `AltGr`+alphanumKey | `^` + consonantLetter   |

I'm using a French azerty keyboard ; here's the gist behind these mappings:
* `Esc` and `Ctrl` are too far from my fingers. I'm using `CapsLock`.
* `Tab` is too far from my left pinky. I'm using `CapsLock`+`i`.
* I have accessible mappings for arrows, `Home`, `End`, `Backspace` and `Delete`.
* I need to move my right hand to reach `Enter`, whereas `CapsLock`+`m` requires zero hand movement.
* I have never used `§` in 28 years. So I remapped it to something useful: putting the focus on my IDE.
* I have never used `^` followed by a consonant letter either. I hate `AltGr` so I remapped all `AltGr` combinations with `^` instead.

You can find my autohotkey script [here](https://raw.githubusercontent.com/Melandel/workflow/master/config/my_keyboard.ahk)!

## Text edition
I'm dedicating next post for this topic, and most likely a series of other ones... The topic is vast, and it has one hell of a big name : [vim - the ubiquitous text editor](https://www.vim.org/)
