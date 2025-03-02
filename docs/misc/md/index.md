---
title: Markdown
description: Brief presentation of the markdown language and its benefits
---

## What is markdown and why should you care ?

Markdown is a ==lightweight== markup language used to format text.
Why is it better than more conventional writing applications ?

We have 4 main apps to write text.

<div class="grid" markdown>

**:material-note-text: notepad.exe** allows you to write fast, but is unreadeable afterwards 

**:material-file-word: Word** is slower (you need to use your mouse), and a bit prettier to look at

**:material-language-html5: HTML** is excruciatingly painful to write, but has a good rendering

**:material-language-markdown: Markdown** is as fast as notepad, and renders like HTML
{ .card }

</div>

Want more ? Here are some addittional arguments from the Markdown Guide.

!!! quote "[Markdown Guide](https://www.markdownguide.org)"
    You might be wondering why people use Markdown instead of a WYSIWYG editor. Why write with Markdown when you can press buttons in an interface to format your text? As it turns out, there are several reasons why people use Markdown instead of WYSIWYG editors.

    - Markdown can be used for everything. People use it to create websites, documents, notes, books, presentations, email messages, and technical documentation.

    - Markdown is portable. Files containing Markdown-formatted text can be opened using virtually any application. If you decide you don’t like the Markdown application you’re currently using, you can import your Markdown files into another Markdown application. That’s in stark contrast to word processing applications like Microsoft Word that lock your content into a proprietary file format.

    - Markdown is platform independent. You can create Markdown-formatted text on any device running any operating system.

    - Markdown is future proof. Even if the application you’re using stops working at some point in the future, you’ll still be able to read your Markdown-formatted text using a text editing application. This is an important consideration when it comes to books, university theses, and other milestone documents that need to be preserved indefinitely.

    - Markdown is everywhere. Websites like Reddit and GitHub support Markdown, and lots of desktop and web-based applications support it.

    <figure markdown=span>
        [:simple-markdown: Read more on the markdown guide](https://www.markdownguide.org/){ .md-button .md-button--primary align=center}
    </figure>


## How easy is Markdown, actually ?

Here is an example of some source code.  

<div class="grid" markdown>

```html title="hello.html"
<!DOCTYPE html>
<html>
    <head>
        <title>
            Hello !
        </title>
    </head>
    <body>
        <h1>
            Hello !
        </h1>
        <p>This is some text</p>
    </body>
</html>
```

```md title="hello.md"
---
title: Hello!
---

# Hello !

This is some text
```

Without hunderds of lines of CSS, the render of the HTML would be quite ugly.

Markdown would render just like the page you're reading now.<br> In fact, it was written in markdown. You can read its source code by clicking the :material-file-eye: icon at the top of the page, near the table of contents. 

</div>

*[WYSIWYG]: What You See Is What You Get

## How to write with markdown ?

Read my cheat sheet to learn virtually everything you need to know about writing in markdown in **one (1) minute**.

[Read the cheat sheet](https://flaghunter01.github.io/mkdocs-yml/en/guide/setup.html#using-markdown){ .md-button }

## Where to write with markdown ?

MkDocs. If you want to publish your docs, it's MkDocs. Otherwise, you can use it literally everywhere. 

Go to the next page to learn more about MkDocs.
