# Misc kelp things

## Responsiveness
### Breakpoints
Kelp is build in a mobile first way and breakpoints only use `min-width`. Styles in smaller breakpoints cascade to larger breakpoints until overwritten by those larger breakpoints. These breakpoints are shared by both media queries and element queries.

- **x-small** `xs`: `min-width: 240px`
- **small** `s`: `min-width: 360px`
- **medium** `m`: `min-width: 540px`
- **large** `l`: `min-width: 780px`
- **x-large** `xl`: `min-width: 1060px`

Why? There are no such thing as a perfect set of breakpoints but these are fine grained and flexible. Each breakpoint is 60px in growth greater than the previous one (240 + 120 = 360; 360 + 180 = 540; 540 + 240 = 780).

### Media queries
Media queries respond to the screen width. Usage:
```css
.widget-demo__child {
  // Styles here will show up regardless of screen width
  background: pink;
  @include r-media(medium) {
    // These styles will show up when widget demo's width is 540px or greater
    border: 2px solid black;
  }
}
```

### Element queries
Element queries respond to the closest element that has element queries enabled. The breakpoint chose will be based on the parent's width (not including padding or border). Element query parents can not nest.

Warning: Only use element queries on elements that won't change in size due to the element query styles. If this is not followed, an infinite loop of ping-ponging styles can happen.

#### Example
```html
<div element-query class="widget-demo">
  <div class="widget-demo__child">
</div>
```

```css
.widget-demo__child {
  // Styles here will show up regardless of element query width
  background: pink;
  @include r-element(medium) {
    // These styles will show up when widget demo parent elementQuery width is 540px or greater
    border: 2px solid black;
  }
}
```
