---
layout: post
title:  "Mind on the Problem"
date:   2020-11-02
categories: workflow
---

The mainstream workflow paradigm doesn't help you **remain focused** - it is filled with context switching and visual noise. Let's take a closer look and see if we can find a more efficient paradigm.

Hi!

> That’s been one of my mantras - focus and simplicity. Simple can be harder than complex…
>
> &mdash; <cite>Plato</cite>

&nbsp;


## Context management
The mainstream paradigm features **windows**.

Windows are very practical. Until you find yourself spamming `Alt`+`Tab` due to their sheer number.

[![toomanywindows]({{ site.baseurl }}/assets/img/toomanywindows.png)]({{ site.baseurl }}/assets/img/toomanywindows.png)

In that situation, you might try to put 2 windows (or more) side by side. It certainly is possible.

Except that by the time you set them the way you like, you already forgot what you wanted to do.

I find that a better option is to use **screen splits**: that way, you get to see exactly what you want on the screen.

Here, you can see three splits (one on the left, one of the right, and one under them):

[![vimsplits]({{ site.baseurl }}/assets/img/vimsplits.png)]({{ site.baseurl }}/assets/img/vimsplits.png)

Vim keeps track of all the previously opened splits so you can _query_ vim to open any of them. Below, the querying menu allowing me to select one of the 15 existing splits:

[![vimbuffers]({{ site.baseurl }}/assets/img/vimbuffers.png)]({{ site.baseurl }}/assets/img/vimbuffers.png)

Screen splits do not overlap each other. You don't _have_ to pick **one** window to work in anymore.

Instead, you have **control** over _how many_ splits you want to work with, as well as their _geometry_ on your screen.

I personally like to have either 2 or 3 splits open at the same time, but other tastes exist:

[![vimsplits](https://i.redd.it/irzw1bqj34h51.png)](https://i.redd.it/irzw1bqj34h51.png)

&nbsp;

## Project structure visualization
The mainstream paradigm features **Project Explorers**.

[![projectexplorer]({{ site.baseurl }}/assets/img/projectexplorer.png)]({{ site.baseurl }}/assets/img/projectexplorer.png)

I'm going to quote [u/romainl](https://www.reddit.com/r/vim/comments/cnh3ut/what_is_your_vim_workflow/ewaje2d?utm_source=share&utm_medium=web2x&context=3) here:
> I don't like to have information on the screen that I don't use: an always-on file explorer, for example, is only ever useful when you actually use it so it's just a waste of pixels most of the time [...]. All that is just noise.

I like much more using the **tree** utility whenever I _need_ it (right split):

[![tree]({{ site.baseurl }}/assets/img/tree.png)]({{ site.baseurl }}/assets/img/tree.png)

&nbsp;

## Mouse & Graphical Interface
The mainstream paradigm provides **searching**, **scrolling** and **browsing links after links after links**, amongst other things.

[![linkafterlink]({{ site.baseurl }}/assets/img/linkafterlink.gif)]({{ site.baseurl }}/assets/img/linkafterlink.gif)

### Keyboard & Muscle memory
I prefer using my **keyboard** and build **muscle memory** because I feel more proactive, rather than merely guided by the GUI. In the example below, I _query_ the same files as above instead of browsing:

[![fuzzybrowsing]({{ site.baseurl }}/assets/img/fuzzybrowsing.gif)]({{ site.baseurl }}/assets/img/fuzzybrowsing.gif)

&nbsp;

## "Focus, and simplicity"

I follow three basic guidelines in order to maximize my focus on problem-solving:
* Remove disruptive elements
* Remove noise
* Make what I use as easily accessible as possible

Hence my **"Focus, and simplicity" paradigm**:

> **Every action should be _instantly_ accessible, from the current context, from my fingers.**  
> **Graphical elements should appear on the screen _exclusively_ when I need them.**  

Ideally, this would mean full functionality using:
* **one** window - the one I'm writing source code from.
* **one** input device - the keyboard.
* **one** type of interaction - running commands.
* **one** graphical interface - text file edition.

> Perfection is achieved, not when there is nothing more to add, but when there is nothing left to take away.
>
> &mdash; <cite>Antoine de Saint-Exupery</cite>

