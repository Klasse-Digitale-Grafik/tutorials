# Markdown.md

Markdown is a way of formatting text in a very simple fashion. It is an opponent to the WYSISYG approach (What You See Is What You Get) of text editors, where you only use blank text to format it.
Through that, there is a strong separation between the design and the content.

Common use cases are: readme files of all sorts, GitHub, Kirbytext editor, ... In fact, this very document is written in Markdown. Please go ahead and open it in a text editor and improve it, to gain a look inside.

The Markdown format can be stored in `.md` files and later be parsed, e.g. to create html.

## Cheatsheet

**Headings** → `<h1>`, ..., `<h6>`
```md
# H1 Heading 1
## H2 Heading 2
### H3 Heading 3
...
###### H6 Heading 6
```

**Italic** → `<em>`
```md
*Italic text*
```

**Bold** → `<strong>`
```md
**Bold text**
```

**Links** → `<a>`
```md
[Link text](https://www.web.site)
```

**Image** → `<img>`
```md
![Image alt text](https://www.web.site/to/image.jpg)
```

**Ordered list** → `<ol>`
```md
1. Firstly
2. Secondly
```

**Unordered list** → `<ul>`
```md
- This
- That
```

**Checklists** (e.g. on GitHub or iCloud Notes)
```md
- [x] Done
- [ ] Left to do
```

**Blockquote** → `<blockquote>`
```md
> The internet is only a hype
```

**Horizontal line** → `<hr>`
```md
----
```

**Preformatted text or code blocks** → `<pre>`
```md
```html
<html>
  <head></head>
  <body></body>
<html>
```

**Inline code** → `<code>`
```md
`code`
```

You can even do tables, but that’s really hard. A more comprehensive documentation can be found [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Markdown and HTML

As you may noticed, some elements are quite similar to HTML. It is a fairly common usecase, to store formatted text as md and then later convert that to HTML.
Also, MarkDown is an extension to HTML, building on top of it. That means that all HTML is also valid inside Markdown text. This gives you way more option, e.g. for images sizes, media embeds, ...

## Further reading

- Live Markdown Editor [Markdown-It](https://markdown-it.github.io)
- Parse Md with JS [Markdown-It](https://github.com/markdown-it/markdown-it)
- Parse Md with PHP [Parsedown](https://parsedown.org)
