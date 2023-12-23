+++
title = 'Hello World'
date = 2023-12-23T12:58:27-06:00
draft = false
tags = ["blog", "development", "hugo"]
categories = ["meta"]
+++

I've long since wanted to make a blog. This article details the process that I
went through.
<!--more-->

## Finding the Right Blogging Platform

For some years I've wanted some place to share the thoughts that come across my
mind but had found myself unsure of how to proceed. After a quick Google search
I had settled on the notion of using Hugo to develop a blog, or so I thought.
Earlier this year, I did attempt to start a blog, though I ran into issues with
that plan, such as the theme not being applied properly despite following the
guide for the [Binario](https://github.com/Vimux/Binario) theme that I was
using at the time.

Being the ambitious developer that I am, I opted to create my own platform
instead of spending time to preperly debug the issues I was having with Hugo.
After all, I'd figured that creating my own platform would be something I could
be more proud of while gathering experience working with 
[SvelteKit](https://kit.svelte.dev/). While working on this project,
[sk3p7ic/sk3p7ic-blog-svelte](https://github.com/sk3p7ic/sk3p7ic-blog-svelte),
was fun, I ran into issues with the manner in which I was rendering markdown
and \\(\LaTeX\\) code with KaTeX. I forget the exact error that I was
encountering, but I believe it had something to do with some files not being
included in the built website. There were other issues as well--issues for
which I did not have the time to work on. Thus, that project stopped there and
joined the graveyard of dead projects that many devs find themselves building,
internally saying, "I'll get back to finishing you some day."

Perhaps I will, but in the meantime I opted once more to visit Hugo and attempt
to spin up a blog that I could at least be happy is deployed and working.

## Building a Blog with Hugo

### Settling on a Theme

I'd started by looking through the list of themes that may be found on
[themes.gohugo.io](https://themes.gohugo.io/tags/blog/) with the "Blog" filter
enabled. Here, I found many themes that appeared to fit my needs, such as the
Binario theme I had previously tried, Congo, and a few others. These themes
did seem nice and aesthetically attractive to me (admittedly Binario makes the
cut because it reminds me of [Zig](https://ziglang.org/) for some reason), but
most seemed to be too feature-rich for my needs, did not have legible tables,
or did not seem to favor support for LaTeX, which is something that I value in
a blog since I believe I will be covering some mathematical expressions in the
future.

In the end, I chose [TeXify2](https://texify2.io/) as my theme, adoring its
simplicity and resemblance to \\(\LaTeX\\) documents (which is how I do my
academic notes, assignments, and presentiations--something I may cover some day
in another post). Additionally, altering the styles of this theme appeared to
be easy, and I therefore set off to start working on my new blog.

### Setting up and Styling the Blog

The initial setup process was extremely simple, with there being only a handful
of commands to execute to initialize a git repository, add the theme as a
submodule, and then enable the theme in the `hugo.toml` file.

Next, I started working on setting up the site variables, such as the title,
author, and description. I initially could not get the title to change in the
heading, but inspecting the code for the partial that was rendering the
heading showed that I needed to put this code under the `[params]` tag. The
same bit of digging needed to be done to find how to set the author, which was
not that hard to do.

I also started working on overriding the theme. I wanted a dark theme, and thus
I looked into which elements and classes would need to have their styles
overridden in css, coming up with this file under `static/css/darken.css`:
```css
body, #wrapper {
    background-color: #27272a;
    color: #d4d4d8;
}

.link, .content a {
    color: #67e8f9!important;
}

.footnote-ref {
    margin-left: 0.2rem;
}

.content pre, .content code {
    background-color: #18181b!important;
    color: #fef3c7!important;
}
```
All that was left was to add this file as `customCSS` in my `hugo.toml` file,
and I was now all set.

## Deployment

The site is not yet deployed. I will update once it is.
