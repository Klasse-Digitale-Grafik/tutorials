# SASS & SCSS

SASS & SCSS is a pair of programming languages that make it easier to create and generate CSS. While SASS is a different way to notate stylesheets, SCSS keeps the regular CSS syntax.

Both are supersets of CSS, which means that any CSS works as well, but they can not be interpreted by any browser. So `.sass` and `.scss` files have to be compiled (or preprocessed) to CSS before publishing.

- [sass-lang.com](https://sass-lang.com)
- [SASS on Wikipedia](https://de.wikipedia.org/wiki/Sass_(Stylesheet-Sprache))
- [SASS Basics](https://sass-lang.com/guide)
- [SASS Documentation](https://sass-lang.com/documentation)

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
So now you can start working with SASS/SCSS inside your `assets/scss` folder. Make sure that in your HTML, you still reference the `assets/css/styles.css` file.

## SASS basics

1. **Nested syntax** that better represents the nested structure of your HTML
```scss
header {
  h1 {
    font-size: 2rem;
    &:before {
      content: '–';
    }
  }
}
a {
  &:hover {
    color: red;
  }
}
```

2. **Variables** that can store property values
```scss
$color: #f00;
h1 {
  color: $color;
}
```

3. **Mixins** are reusable code blocks, that can also be passed an argument
```scss
@mixin tag {
  padding: 0.3em 0.6em;
  border: 1px solid currentColor;
  border-radius: 3px;
}
@mixin hover( $property: color ) {
  transition: $property 300ms ease;
  &:hover {
    #{$property}: yellow;
  }
}
.tag,
.button {
  @inlcude tag;
}
.link {
  @inlcude hover;
}
.button {
  @inlcude hover( background-color );
}
```

4. **Modules** that let you split up code into seperate files
```bash
scss
  _variables-mixins.scss # module, indicated by leading underscore
  _typography.scss
  style.scss # file
```
```scss
/* _variables-mixins.scss */
$color: red;
/* _typography.scss */
@import 'variables-mixins';
h1 {
  color: $color;
}
/* style.scss */
@import 'variables-mixins';
@import 'typography';
```
E.g. it can be a good convention to outsource all mixins and variables into a seperate file and then include it into all other files.

5. **Loops**
```scss
$steps = ("s": 0.5rem, "m": 1rem, "l": 2rem);
@each $step, $size in $steps {
  .margin-#{$step} {
    margin: $size;
  }
}
```

## Examples

1. Creating a color sheme
```scss
$black: #000;
$white: #fff;
$blue: #00f;
$colors = (
  "black": $black,
  "white": $white,
  "blue": $blue
);
@each $color, $value in $colors {
  .#{$color} {
    background-color: $value;
  }
  .text-#{$color} {
    color: $value;
  }
}
```

2. Creating a grid system
```scss
$breakpoints = (
  "s": 800px,
  "m": 1200px,
  "l": 1600px
);
@mixin grid( $columns ) {
  display: grid;
  grid-template-columns: repeat(#{$columns}, minmax(0, 1fr));
  @include column( $columns );
  @each $name, $width in $breakpoints {
    @media (min-width: $width) {
      @include column( $columns, '-#{name}' );
    }
  }
}
@mixin column( $i, $breakpoint: '' ) {
  @if $i > 0 {
    > .col#{$breakpoint}-#{$i} {
      grid-column-end: span $i;
    }
    @include column( $i - 1, $breakpoint );
  }
}
.grid {
  @include grid( 12 );
}
```
```html
<div class="grid">
  <div class="col-12">12 columns wide</div>
  <div class="col-6 col-s-3">6 columns on mobile, 3 on tablet and desktop</div>
  <div class="col-6 col-s-9">6 columns on mobile, 9 on tablet and desktop</div>
  <div class="col-6 col-s-4 col-m-3">6 columns on mobile, 4 on tablet, 3 on desktop</div>
</div>
```
