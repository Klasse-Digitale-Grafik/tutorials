# CSS Cascading Style Sheets

CSS is a method to assign styles to structured content like HTML. This allows you to seperate the appeareance from the actual content.
More on [Wikipedia](https://en.wikipedia.org/wiki/CSS)

## 🛷 Basics

```css
selector {
    /* comment */
    property: value;
}
```

### Selectors
The most important selectors are:
- `*` select all
- `tagname` select elements by tag name
- `.class` select elements by class name
- `#id` select element**s** by id
- `:pseudo` select elements that are in a special state like `:hover`, or pseudo children like `:before`
- `[attr]` select elements that have a given attribute
- `parent descendant` select elements inside some other elements
- `parent > child` select elements that are direct children of given parent elements
- `element1 + element2` select elements that directly follow some other elements
- `element1 ~ element2` select elements that eventually follow some other elements
- `element1, element2` combine multiple selectors
- `element:lang(de)` select elements that have a `lang="de"` attribute

Learn more:
- [Full list of CSS Selectors](https://www.w3schools.com/cssref/css_selectors.asp)
- [CSS Diner](https://flukeout.github.io) selector training game

### Rules
There are various rules that you can apply to an element to control its appeareance.
```css
h1 {
    color: red;
    font-family: monospace;
    text-align: center;
    text-transform: uppercase;
    margin: 0.5rem;
    padding: 0.5em;
    border: 1px solid blue;
    border-radius: 0.5em;
    text-shadow: 0 0 10px blue;
}
```
[Full list of CSS Rules](https://www.w3schools.com/cssref/default.asp)

### Cascading and inheritance
One of CSS’ key characteristics is the power of inheritance, which means:
1. A selector always selects all matching elements
2. All rules applied to an element will populate down to all it’s children ("cascading"), as long as they’re not overwritten
3. With the `inherit` value, child elements can explicitly inherit a rule from its ancestors

This allows you to make even complex designs with a minimum amount of CSS rules, which makes your code more reusable, readable and your website faster.

### Units
Most common CSS units are:
- `px` pixels in non-retina terms (1x1 CSS px = 2x2 retina pixels)
- `%` relative to the **width** of the parent element
- `vw` % of screen width
- `vh` % of screen height (see ["100vh-problem"](https://css-tricks.com/the-trick-to-viewport-units-on-mobile/))
- `em` relative to current font size (`2em` means `200%` of the current or inherited font-size)
- `rem` [relative to root font size](https://www.w3schools.com/cssref/css_pxtoemconversion.asp) (when `html{font-size:10px;}`, then `1rem` = `10px`)

Units can also be calculated by the browser, eg: `width: calc( 50vw + 1px );`

Learn more:
- [Full list of CSS Units](https://www.w3schools.com/cssref/css_units.asp)

### Colors
You can define colors in a few different ways, eg:
- `blue` there are 140 [default colors](https://www.w3schools.com/cssref/css_colors.asp) with names like `azure`, `mintcream` and `springgreen`
- `currentColor` current or inherited text color
- `#00f` 4-bit hex (`0` = `0`, `9` = `127`, `f` = `255`)
- `#0000ff` 8-bit hex (`00` = `0`, `99` = `127`, `ff` = `255`)
- `rgb( 0, 0, 255)`
- `rgba( 0, 0, 255, 0.5)` with opacity between `0` and `1`
- `hsl( 240, 100%, 50%)` (hue, saturation, lightness)
- `cmyk( 100, 100, 0, 0)`

Read more:
- [w3schools](https://www.w3schools.com/colors/default.asp)

### Bringing CSS into HTML
Basically, there are 3 standard ways to [attach CSS to your HTML](https://www.w3schools.com/css/css_howto.asp):

**Inline**, using the `style` attribute (use only for small exceptions of the rule)
```html
<h1 style="color: red;">Headline</div>
```

**Within the `head`** (use for small stylesheets)
```html
<style>
    h1 { color: red; }
</style>
```

**Seperate `.css` file**, referenced from within the `head` (normal usecase)
```html
<link rel="stylesheet" href="styles.css">
```

## 🧮 Layout

**The Box Model**
When working with properties like `width`, `height`, `margin`, `border` and `padding` it is really helpful to understand the box model concept:
- [The box model](https://www.w3schools.com/css/css_boxmodel.asp)
- [Opening the box model](https://learn.shayhowe.com/html-css/opening-the-box-model/) by Shay Howe
- [Box sizing](https://developer.mozilla.org/de/docs/Web/CSS/box-sizing) to control the box model
- [Collapsing margins](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)

**`position:`**
- [CSS-Tricks](https://css-tricks.com/almanac/properties/p/position/)
- [Learn CSS Positioning](https://ishadeed.com/article/learn-css-positioning/) by Ahmad Shadeed

**`display: flex`**
- [CSS-Tricks Complete guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexbox froggy](https://flexboxfroggy.com) game

**`display: grid`**
- [CSS-Tricks complete guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid Garden](https://cssgridgarden.com) game

**`<table>`**
- [CSS-Tricks complete guide](https://css-tricks.com/complete-guide-table-element/)

Learn more:
- [w3scools CSS Layout](https://www.w3schools.com/css/css_website_layout.asp)
- [Learn CSS Box Alignment](https://ishadeed.com/article/learn-box-alignment/) by Ahmad Shadeed

## 📱 Responsive design and media queries
Using media queries, you can control that certain CSS code gets only applied, when the user device matches a specific rule. This is helpful to adjust a website design for small or large screens or e.g. when it’s being printed.

```css
/* on small screens show items as list */
.grid .item {
    margin: 1rem;
    background-color: grey;
}
@media (min-width: 600px){
    /* on medium sized screens, show 2 column grid */
    .grid {
        display: grid;
        gap: 1rem;
        grid-template-columns: 1fr 1fr;
    }
    .grid .item {
        margin: 0;
    }
}
@media (min-width: 900px){
    /* on large screens, show 4 column grid */
    .grid {
        grid-template-columns: 1fr 1fr 1fr 1fr;
    }
}
@media print {
    /* border instead of background-color */
    .grid .item {
        background-color: transparent;
        border: 1px solid grey;
    }
}
```

You can also add seperate stylesheets that only will be loaded, once the media query matches:
```html
<link rel="stylesheet" href="global.css">
<link rel="stylesheet" href="screen.css" media="screen">
<link rel="stylesheet" href="screen-large.css" media="screen and (min-width: 900px)">
<link rel="stylesheet" href="print.css" media="print">
```

- [Media queries](https://css-tricks.com/a-complete-guide-to-css-media-queries/)
- [Hyphenation](https://medium.com/clear-left-thinking/all-you-need-to-know-about-hyphenation-in-css-2baee2d89179) and [word breaks](https://justmarkup.com/articles/2015-07-31-dealing-with-long-words-in-css/)

**Mobile first paradigm**
means that you first define all the rules required for the layout on a mobile device and later add or override the design for larger screens using media queries or a second css file. This makes sense because usually devices with larger screens have more compute power and faster internet than smaller devices.

## 🎨 CSS Variables
With CSS variables you can make your design more modular and changable:
```css
::root {
    /* define */
    --signature-color: #00f;
}
button, a, h1 {
    /* use */
    color: var(--signature-color);
}
```

Learn more:
- [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [Difference of CSS-Vars and Preprocessor-Vars on CSS-Tricks](https://css-tricks.com/difference-between-types-of-css-variables/)

## 🎆 Effects

- [Animation](https://css-tricks.com/almanac/properties/a/animation/)
- [Filter](https://css-tricks.com/almanac/properties/f/filter/)
- [Transform](https://css-tricks.com/almanac/properties/t/transform/)
- [Transition](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)

And of course
[box-shadow](https://www.cssmatic.com/box-shadow),
[border-radius](https://www.w3schools.com/cssref/css3_pr_border-radius.asp),
[text-shadow](https://css-tricks.com/almanac/properties/t/text-shadow/),
[gradients](https://www.cssmatic.com/gradient-generator),
[sticky](https://css-tricks.com/position-sticky-2/),
[outline](https://developer.mozilla.org/en-US/docs/Web/CSS/outline),
[scroll-behaviour](https://css-tricks.com/almanac/properties/s/scroll-behavior/), ...

## 📝 Webfonts

```css
@font-face {
    font-family: 'MyWebFont';
    src: url('/path/to/webfont.woff2') format('woff2'),
        url('/path/to/webfont.woff') format('woff');
}
```
- [More on Webfonts](Website-Typography.md)

## 🚨 Browser support and default values
Not all rules and features are supported by all browsers. Some rules are even interpreted differently across browsers. Especially for new or fancy features, you should check for browser support:

- [CanIUse](https://caniuse.com) Archive of browser support
- [w3schools](https://www.w3schools.com/cssref/css3_browsersupport.asp) list of supported rules

Sometimes browsers (especially older versions) ignore a rule and only apply it when you add a ["vendor-prefix"](https://bitsofco.de/css-vendor-prefixes/):
```css
element {
    -webkit-animation-name: slidein;
    -moz-animation-name: slidein;
    -ms-animation-name: slidein;
    -o-animation-name: slidein;
    animation-name: slidein;
}
```
In 2021, this is less of a problem compared to a few years ago. But to support older browsers, it can still be helpful. There are also tools like [Autoprefixer](https://autoprefixer.github.io) that can do it for you.

All browsers come with a default stylesheet, which provides fallback styles for many HTML elements. As these fallback rules are different accross browsers and even can be edited by the user, it often makes sense to "reset" or "normalize" them before you add your own rules:
- [List of browser default values](https://www.w3schools.com/cssref/css_default_values.asp)
- [Reboot, Resets, Rereasoning](https://css-tricks.com/reboot-resets-reasoning/) by Chris Coyer
- [Eric Meyer CSS Reset](https://meyerweb.com/eric/tools/css/reset/)
- [normalize.css](http://necolas.github.io/normalize.css/)

The most basic CSS reset would be
```css
* {
    margin: 0;
    padding: 0;
    border: none;
    font: inherit;
    list-style: none;
    color: inherit;
    background-color: none;
    vertical-align: baseline;
    /* depending on your taste: */
    box-sizing: border-box;
}
```
which you can add on top of all your css to reset (almost) all default rules that could mess up your design.

## 🛠 Tooling and Preprocessors
There are several tools, that can help you to make your CSS work easier. Preprocessors allow you to write your css in a more readable and reusable way and then compile it to real css that browsers can handle:
- [SASS & SCSS](https://sass-lang.com)
- [PostCSS](https://postcss.org)

[SASS & SCSS Tutorial](SCSS.md)

## 🧩 Frameworks
When you don’t want to handle every edge case yourself, a CSS framework can help. This is especially helpful for grid systems, forms and user interfaces:

- [Tailwind](https://tailwindcss.com) framework
- [Pure.css](https://purecss.io) framework
- [Bootstrap](https://getbootstrap.com) framework
- [Reflex](https://reflexgrid.com) grid system

## 🔗 More resources

- [MDN Mozilla Docs](https://developer.mozilla.org/de/docs/Web/CSS) reference
- [CSS-Tricks Almanac](https://css-tricks.com/almanac/) reference
- [w3scools](https://www.w3schools.com/css/default.aspcodepen) reference
- [CanIUse](https://caniuse.com) for checking browser support
- [Codepen](https://codepen.io/pen/) for quick experiments
- [State fo CSS](https://stateofcss.com) annual census
- [Tutorials by Josh Comeau](https://www.joshwcomeau.com/tutorials/css/)
- [Shapes of CSS](https://css-tricks.com/the-shapes-of-css/)
- [Getting to know CSS](https://learn.shayhowe.com/html-css/getting-to-know-css/) by Shay Howe
