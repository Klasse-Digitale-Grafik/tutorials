# CSS Cascading Style sheets

CSS is a method to assign styles to HTML elements, which allows you to seperate the appeareance from the actual content.

[Wikipedia](https://en.wikipedia.org/wiki/CSS)

## 🛷 Basic syntax

```css
selector {
    /* comment */
    property: value;
}
```

```
<h1>Headline 1</h1>
<style>
    h1 {
        color: red;
    }
</style>
```

### Selectors

- `*` select all
- `tagname` select elements by tag name
- `.class` select elements by class name
- `#id` select element by id
- `:pseudoclass` select elements that is in a special state, or a pseudo child like `:before`
- `[attr]` select elements that have a given attribute
- `parent descendant` select elements inside some other elements
- `parent > child` select elements that are direct children of given parent elements
- `element1 + element2` select elements that follow some other elements

- [Full list of CSS Selectors](https://www.w3schools.com/cssref/css_selectors.asp)
- [CSS Diner](https://flukeout.github.io) selector training game

### Rules

There are various rules that you can apply to your element to control its appeareance.
- [Full list of CSS Rules](https://www.w3schools.com/cssref/default.asp)
- [Browser support](https://caniuse.com)

### Units
- `px` pixels in non-retina terms (1x1 css px = 2x2 retina pixels)
- `%` relative to parent element
- `vw` % of screen width
- `vh` % of screen height
- `em` relative to current font size
- `rem` [relative to root font size](https://www.w3schools.com/cssref/css_pxtoemconversion.asp)
- `color` as #hex, rgb() or rgba()

- [Full list of CSS Units](https://www.w3schools.com/cssref/css_units.asp)
- [List of all CSS default colors](https://www.w3schools.com/cssref/css_colors.asp)

### Bringing CSS into HTML
Basically, there are 3 standard ways to [attatch CSS to your HTML](https://www.w3schools.com/css/css_howto.asp):

**Inline using `style` attribute**
```html
<h1 style="color: red;">Headline</div>
```

**Within the HTML `head`**
```html
<head>
    <style>
        h1 { color: red; }
    </style>
```

**Inside a seperate `.css` file, referenced from within the HTML `head`**
```
<link rel="stylesheet" href="styles.css">
```

### Cascading and inheritance
One of CSS’ key characteristics is the power of inheritance, which means: A selector always selects all matching elements. And all rules applied to an element will populate down to all it’s children ("cascading"), as long as they’re not overwritten. And with the `inherit` value, child elements can explicitly inherit a rule from its ancestors.

## 🚨 Browser support and default values
Not all rules and features are supported by all browsers. Some rules are even interpreted differently across browsers. Especially for new or fancy features, you should check for browser support:

- [CanIUse Archive of browser support](https://caniuse.com)
- [Supported rules](https://www.w3schools.com/cssref/css3_browsersupport.asp)

All browsers come with a default stylesheet, that provides fallback styles for many HTML elements. These fallback rules can even be edited by the user, so it often makes sense to "reset" or "normalize" them:
- [List of browser default values](https://www.w3schools.com/cssref/css_default_values.asp)
- [Reboot, Resets, Rereasoning by Chris Coyer](https://css-tricks.com/reboot-resets-reasoning/)
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
}
```
which resets (almost) all default css rules, but retains `display`.

## 🧮 Layout

- [w3scools CSS Layout](https://www.w3schools.com/css/css_website_layout.asp)
- [Learn CSS Box Alignment with Ahmad Shadeed](https://ishadeed.com/article/learn-box-alignment/) game

**Position**
- [CSS-Tricks](https://css-tricks.com/almanac/properties/p/position/)
- [Learn CSS Positioning with Ahmad Shadeed](https://ishadeed.com/article/learn-css-positioning/)

**Flex**
- [CSS-Tricks Complete guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexbox froggy](https://flexboxfroggy.com) game

**Grid**
- [CSS-Tricks complete guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid Garden](https://cssgridgarden.com) game

**Tables**
- [CSS-Tricks complete guide](https://css-tricks.com/complete-guide-table-element/)

## 📱 Responsive design

- [Media queries](https://css-tricks.com/a-complete-guide-to-css-media-queries/)
- [Hyphenation]((https://medium.com/clear-left-thinking/all-you-need-to-know-about-hyphenation-in-css-2baee2d89179)) and [word breaks](https://justmarkup.com/articles/2015-07-31-dealing-with-long-words-in-css/)

**Mobile first paradigm**
means that you first define all the rules required for the layout on a mobile device and later add or override the design for larger screens using media queries or a seconds css file. This makes sense because usually dvices with larger screens have more compute power and faster internet than smaller devices.
```css
.grid {
    padding: 0.5rem;
}
.grid .item {
    padding: 0.5rem;
}
@media (min-width: 600px){
    .grid {
        display: flex;
        flex-wrap: wrap;
    }
    .grid .item {
        flex: 1 1 50%;
    }
}
@media (min-width: 900px){
    .grid .item {
        flex-basis: 25%;
    }
}
```

## 🎆 Effects

- [Transform](https://css-tricks.com/almanac/properties/t/transform/)
- [Transition](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
- [Animation](https://css-tricks.com/almanac/properties/a/animation/)

And of course
[Border-radius](https://www.w3schools.com/cssref/css3_pr_border-radius.asp),
[box-shadow](https://www.cssmatic.com/box-shadow),
[text-shadow](https://css-tricks.com/almanac/properties/t/text-shadow/),
[outline](https://developer.mozilla.org/en-US/docs/Web/CSS/outline),
[sticky](https://css-tricks.com/position-sticky-2/),
[gradients](https://www.cssmatic.com/gradient-generator),
[scroll-behaviour](https://css-tricks.com/almanac/properties/s/scroll-behavior/), ...

## 📝 Webfonts

```css
@font-face {
    font-family: 'MyWebFont';
    src: url('/path/to/webfont.woff2') format('woff2'),
        url('/path/to/webfont.woff') format('woff');
}
```
More on [CSS Tricks](https://css-tricks.com/snippets/css/using-font-face/)

## 🛠 Tooling and Preprocessors
There are several tools, that can help you to make your CSS work easier. Preprocessors allow you to write your css in a more readable and reusable way and then compile it to real css that browsers can handle. Common examples are:
- [Sass/SCSS](https://sass-lang.com)
- [PostCSS](https://postcss.org)

## 🧩 Frameworks
When you don’t want to handle every edge case yourself, a CSS framework could help. This is especially helpful for grid systems, forms and user interfaces:

- [Tailwind](https://tailwindcss.com) framework
- [Pure.css](https://purecss.io) framework
- [Bootstrap](https://getbootstrap.com) framework
- [Reflex](https://reflexgrid.com) grid system
- [State of CSS](https://2020.stateofcss.com/en-US/technologies/css-frameworks/) overview

## 🔗 More resources

- [MDN Mozilla Docs](https://developer.mozilla.org/de/docs/Web/CSS)
- [CSS-Tricks Almanac](https://css-tricks.com/almanac/)
- [w3scools](https://www.w3schools.com/css/default.aspcodepen)
- [Can I Use](https://caniuse.com)
- [Codepen](https://codepen.io/pen/) for quick experiments
- [State fo CSS](https://stateofcss.com) annual census
