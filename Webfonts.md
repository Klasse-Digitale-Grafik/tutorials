# Webfonts

## Embedding a custom webfont in CSS

```css
@font-face {
    font-family: 'MyWebFont';
    src: url('/path/to/webfont.woff2') format('woff2'),
        url('/path/to/webfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}
```
More on [CSS Tricks](https://css-tricks.com/snippets/css/using-font-face/)

## Applying a typeface

```css
html {
    /* Custom font */
    font-family: 'MyWebFont';
    /* Websafe fallback */
    font-family: 'MyWebFont', Arial;
    /* Select type like 'serif', 'sans-serif', 'monospace', 'cursive' */
    font-family: monospace;
    /* Full control */
    font-family: 'MyWebFont', Arial, sans-serif;
}
```

## Finding webfonts

### Websafe fonts
There is a group of typefaces that are most likely installed on every computer that uses a latin alphabet. These fonts are called web safe, because you can use them without worrying that the browser replaces it with another typeface. These include:
- Arial
- Times New Roman
- Courier New
- [and more](https://www.w3schools.com/cssref/css_websafe_fonts.asp)

### Webfont services
There are also services that let you directly embed fonts into your websites

- [Google Fonts](https://font.google.com)
- [Adobe Fonts](https://fonts.adobe.com)

### Custom webfonts
Of course you can also provide custom font files. The modern way would be to have it in `woff2` or `woff` format, but `otf` and `ttf` often works as well.

All modern type foundaries will offer their typefaces in these formats. You can also export webfonts from typedesign software like Glyphs or Robofont. And then you can convert your regular desktop fonts to webfonts with tools like [Transfonter](https://transfonter.org).

- [Open Source Webfonts](https://www.are.na/laurel-schwulst/open-source-web-fonts) curated by Laurel Schwulst

## Typesetting

### Font size & spacing
```css
html {
    /* fixed font size */
    font-size: 16px;
    /* relative font size with min, max value */
    font-size: clamp(14px, 2vw, 24px);
}
p {
    font-size: 1rem;
    line-height: 1.2;
    letter-spacing: -0.05em;
}
p + p {
    text-indent: 3em;
}
```

> Use `rem` for values that you want to make relative to the root font size. Use `em` for values relative to the current font-size.

- [All CSS font rules](https://css-tricks.com/almanac/properties/f/font/)
- [type.js](http://typejs.org/)
- [Kerning](https://css-tricks.com/almanac/properties/f/font-kerning/)
- [Scale font-sizes with clamp()](https://css-tricks.com/linearly-scale-font-size-with-css-clamp-based-on-the-viewport/)

### Hyphanation

```html
<html lang="de">
```
```css
p {
    -webkit-hyphens: auto;
    -ms-hyphens: auto;
    hyphens: auto;
    /* min word length, min length pre-split, min-length after-split */
    hyphenate-limit-chars: 8 4 4;
    /* max consecutive lines with hyphened words */
    -ms-hyphenate-limit-lines: 2;
    -webkit-hyphenate-limit-lines: 2;
    hyphenate-limit-lines: 2;
}
```

[Read more](https://medium.com/clear-left-thinking/all-you-need-to-know-about-hyphenation-in-css-2baee2d89179)

## Further reading

- [More on CSS](CSS.md)
- [Using @font-face](https://css-tricks.com/snippets/css/using-font-face/) by CSS-Tricks
- [Using webfonts](https://github.com/grillitype/web-fonts-guide) by Grilli Type
