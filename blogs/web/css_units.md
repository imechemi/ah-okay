# What is the difference between px, em and percent

In CSS, there are two types of units for specifying length values

1. Absolute Units (px, cm, in, pt)
2. Relative Units (em, rem, %, vw, vh, vmin, vmax)

Absolute units will render the element with same size no matter where you put the element in html. 

For example: if you make `<p>` font-size to be `24px`. It will be 24px on mobile, desktop, tablet, when you resize your browser window or when you move the 
element to a different location in the DOM. 

But if you make it a relative unit, now the value is dependent upon parent element or the viewport. 

For example: if you make `<li>` font-size to be 1.5em. Now the font-size of content of `<li>` element depends on it's parent element's font-size.


```html
<ul>
  <li class="one">Alice</li>
  <li class="two">Bob</li>
  <li class="three">Tenzin</li>
  <li class="four">Jordan</li>
</ul>
```

```css
// Different ways to express the same value. 
:root {
  font-size: 48px;
}

body {
  font-size: 16px; // default is 16px. 
}

// Relative
li.one {
  font-size: 1.5em; // 1.5 times the font-size of the <ul> or <body> tag's font-size. (16px * 1.5 = 24px)
}

// Absolute
li.two {
  font-size: 24px;  // Always be 24px 
}

// Relative
li.three {
  font-size: 150%;  // 50% larger than the parent element i.e <ul> or <body> tag's font-size (16px * 1.5 = 24px)
}

li.four {
  font-size: 0.5rem; // 50% of the font-size of the :root element which is 48 * 0.5 = 24px
}
```

You can play around with code here: https://codepen.io/imechemi/pen/ZEQJPqE . Try changing the font-size of the body to 8px and see what happens.

