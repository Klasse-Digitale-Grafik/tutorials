# SASS & SCSS

SASS & SCSS is a pair of programming languages that make it easier to create CSS. While SASS is a different way to notate stylesheets, SCSS keeps the regular CSS syntax.

Both are supersets of CSS, which means that any CSS works as well, but they can not be interpreted by any browser. So `.sass` and `.scss` files have to be compiled (or preprocessed) to CSS before publishing.

[sass-lang.com](https://sass-lang.com)
[SASS on Wikipedia](https://de.wikipedia.org/wiki/Sass_(Stylesheet-Sprache))

## Install

You can install SASS both as standalone software or as npm package.
[Install guide](https://sass-lang.com/install)

To have it running as standalone software, you will need [Homebrew](https://brew.sh) on Mac or [Chocolatey](https://chocolatey.org) on Windows.

```bash
# mac
brew install sass/sass/sass
# windows
choco install sass
# check if it has been installed correctly
sass -v
```

Maybe you have some setup like
```bash
index.html
assets
  css # rename to scss
    styles.css # rename to styles.scss
```
If you now run
```bash
sass --watch assets/scss:assets/css
```
all `.scss` files inside `assets/scss` will be processed to `.css` files inside `assets/css`, everytime you make a change and save that. That results in a structure like
```bash
index.html
assets
  css # compiled files only for the browser
    styles.css
  scss # original files for you to work in
    styles.scss
```

## SASS Basics

- [SASS Basics](https://sass-lang.com/guide)
