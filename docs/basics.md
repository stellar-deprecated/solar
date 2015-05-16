# Kelp basics (non-themable)

## K-flex (K-flexItem)[layout]
[Flexbox](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes) is a new powerful layout mode. K-flex is a set of predefined common flex use cases. It assumes the developer using it has at least a basic understand of the flexbox model.

**Warning: examples and usages in code elsewhere may be out of date. The most up to date reference is in the sections labeled `Reference source code (styles/_layout.flex.scss)`**

### What it provides:
- a set of common flex children sizes

### What it is not:
- an auto-prefixer
- a replacement for css flex properties

### flex-grow 12 basis
Flexbox with a default basis of 12. Here is an example of how it would look like with the basis set
```
| 1/2 basis: 12 | 1/2 basis: 12 | (total: 24)
| 1/3 basis: 12 | 1/3 basis: 12 | 1/3 basis: 12 | (total: 36)
| 2/3 basis: 12 | 1/3 basis: 6 | (total: 18)
| 3/4 basis: 12 | 1/4 basis: 4 | (total: 16)
| 60% basis: 12 | 20% basis: 4 | 20% basis: 4 | (total: 20)
| 50% basis: 12 | 16.6% basis: 4 | 16.6% basis: 4 | 16.6% basis: 4 | (total: 24)
```

When adjusting basis, stay at basis 12 or under.

For now, flex-shrink values assume a default of 1 while flex-grow assumes a default of 12.

### flex container reference
There are 4 different types of containers available:
- K-flex-row
- K-flex-rowWrap
- K-flex-col
- K-flex-colWrap

Reference source code (styles/_layout.flex.scss):
```
// flex containers (all of them have display: flex)
.K-flex-row     { @include K-flex-row; } // flex-direction: row;
.K-flex-rowWrap { @include K-flex-rowWrap; } // flex-flow: row wrap;
.K-flex-col     { @include K-flex-col; } // flex-direction: column;
.K-flex-colWrap { @include K-flex-colWrap; } // flex-flow: column wrap;
```

### flex item reference
These classes are not meant to be comprehensive and for complex cases, you may need to write your own.
<!-- csv to markdown table style="white-space: nowrap"
name,class/mixin name,grow,shrink,basis,description
 ,(no `flex` specified),0,1,auto,<small>when no flex explicitly specified it uses `width` info</small>
 ,(shorthand omission default),1,1,auto,t<small>hese are the values filled when items omitted in shorthand</small>
none,`K-flexItem-none`,0,0,auto,<small>no flexing: takes up space it needs or defined. Same as `flex: none`</small>
full,`K-flexItem-full`,12,0,100%,<small>always takes up the main-size (slightly different from theoretical 12of12)</small>
share[N],`K-flexItem-share`,12,0,0%,<small>all space completely distributed (could get crumpled to ~0px); basis of N: 1 2 3 4 6 8 10</small>
auto[N],`K-flexItem-N`,N,0,auto,<small>extra space distributed; basis of N: 1 2 3 4 6 8 10</small>
MofN,`K-flexItem-MofN`,0,0,100%*M/N,<small>non-resizing column sizes. available for M in range 1-11 with N at 12. always reduced</small>
-->

<table>
<tr><td>name</td><td>class/mixin name</td><td>grow</td><td>shrink</td><td>basis</td><td>description</td></tr>
<tr><td> </td><td style="white-space: nowrap">(no `flex` specified)</td><td>0</td><td>1</td><td>auto</td><td><small>when no flex explicitly specified it uses `width` info</small></td></tr>
<tr><td> </td><td style="white-space: nowrap">(shorthand omission default)</td><td>1</td><td>1</td><td>auto</td><td>t<small>hese are the values filled when items omitted in shorthand</small></td></tr>
<tr><td>none</td><td style="white-space: nowrap">`K-flexItem-none`</td><td>0</td><td>0</td><td>auto</td><td><small>no flexing: takes up space it needs or defined. Same as `flex: none`</small></td></tr>
<tr><td>full</td><td style="white-space: nowrap">`K-flexItem-full`</td><td>12</td><td>0</td><td>100%</td><td><small>always takes up the main-size (slightly different from theoretical 12of12)</small></td></tr>
<tr><td>share[N]</td style="white-space: nowrap"><td>`K-flexItem-share`</td><td>12</td><td>0</td><td>0%</td><td><small>all space completely distributed (could get crumpled to ~0px); basis of N: 1 2 3 4 6 8 10</small></td></tr>
<tr><td>auto[N]</td style="white-space: nowrap"><td>`K-flexItem-N`</td><td>N</td><td>0</td><td>auto</td><td><small>extra space distributed; basis of N: 1 2 3 4 6 8 10</small></td></tr>
<tr><td>MofN</td><td style="white-space: nowrap">`K-flexItem-MofN`</td><td>0</td><td>0</td><td>100%*M/N</td><td><small>non-resizing column sizes. available for M in range 1-11 with N at 12. always reduced</small></td></tr>
</table>

Note: CSSWG might (or might not) rename flex-basis of `auto` to `main-size` in future versions of flex

Reference source code (styles/_layout.flex.scss):
```scss
// no flexing
.K-flexItem-none { @include K-flexItem-none; } // flex: 0 0 auto;

// full row
.K-flexItem-full { @include K-flexItem-full; }   // flex: 12 0 100%;

// share sizes (all space distributed)
.K-flexItem-share1  { @include K-flexItem-share1; }  // flex: 1 0 0%;
.K-flexItem-share2  { @include K-flexItem-share2; }  // flex: 2 0 0%;
.K-flexItem-share3  { @include K-flexItem-share3; }  // flex: 3 0 0%;
.K-flexItem-share4  { @include K-flexItem-share4; }  // flex: 4 0 0%;
.K-flexItem-share6  { @include K-flexItem-share6; }  // flex: 6 0 0%;
.K-flexItem-share8  { @include K-flexItem-share8; }  // flex: 8 0 0%;
.K-flexItem-share10 { @include K-flexItem-share10; } // flex: 10 0 0%;
.K-flexItem-share   { @include K-flexItem-share; }   // flex: 12 0 0%;

// auto sizes (extra space distributed)
.K-flexItem-auto1  { @include K-flexItem-auto1; }  // flex: 1 0 auto;
.K-flexItem-auto2  { @include K-flexItem-auto2; }  // flex: 2 0 auto;
.K-flexItem-auto3  { @include K-flexItem-auto3; }  // flex: 3 0 auto;
.K-flexItem-auto4  { @include K-flexItem-auto4; }  // flex: 4 0 auto;
.K-flexItem-auto6  { @include K-flexItem-auto6; }  // flex: 6 0 auto;
.K-flexItem-auto8  { @include K-flexItem-auto8; }  // flex: 8 0 auto;
.K-flexItem-auto10 { @include K-flexItem-auto10; } // flex: 10 0 auto;
.K-flexItem-auto   { @include K-flexItem-auto; }   // flex: 12 0 auto;

// column sizes
.K-flexItem-5of6 { @include K-flexItem-11of12; } // flex: 0 0 91.66666%; // 11of12
.K-flexItem-5of6 { @include K-flexItem-5of6; }   // flex: 0 0 83.33333%; // 10of12
.K-flexItem-3of4 { @include K-flexItem-3of4; }   // flex: 0 0 75%;       // 9of12
.K-flexItem-2of3 { @include K-flexItem-2of3; }   // flex: 0 0 66.66666%; // 8of12
.K-flexItem-1of3 { @include K-flexItem-7of12; }  // flex: 0 0 58.33333%; // 5of12
.K-flexItem-1of2 { @include K-flexItem-1of2; }   // flex: 0 0 50%;       // 6of12
.K-flexItem-1of3 { @include K-flexItem-5of12; }  // flex: 0 0 41.66666%; // 5of12
.K-flexItem-1of3 { @include K-flexItem-1of3; }   // flex: 0 0 33.33333%; // 4of12
.K-flexItem-1of4 { @include K-flexItem-1of4; }   // flex: 0 0 25%;       // 3of12
.K-flexItem-1of6 { @include K-flexItem-1of6; }   // flex: 0 0 16.66666%; // 2of12
.K-flexItem-1of12 { @include K-flexItem-1of12; } // flex: 0 0 8.33333%;  // 1of12
```

### Demos
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-share">.K-flexItem-share</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-full">.K-flexItem-full</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>

Grid proportioned flex items are not a direct replacement for traditional grids since this does not take into account the gutters (and no, adding a bit of margin-right does not make it a true grid column). They do add a quick simple way to proportionally take up space and this is useful for inputGroups.

<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-1of2">.K-flexItem-1of2</div>
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
</div>
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-1of2">.K-flexItem-1of2</div>
  <div class="K-flexItem-1of3">.K-flexItem-1of3</div>
</div>

<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-share">.K-flexItem-share</div>
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-full">.K-flexItem-full</div>
  <div class="K-flexItem-1of2">.K-flexItem-1of2</div>
  <div class="K-flexItem-1of3">.K-flexItem-1of3</div>
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-1of6">.K-flexItem-1of6</div>
  <div class="K-flexItem-1of12">.K-flexItem-1of12</div>
</div>
```html
<div class="K-flex-rowWrap kelpDocs-flexDemo-container">
  <div class="K-flexItem-share">.K-flexItem-share</div>
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-full">.K-flexItem-full</div>
  <div class="K-flexItem-1of2">.K-flexItem-1of2</div>
  <div class="K-flexItem-1of3">.K-flexItem-1of3</div>
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-1of6">.K-flexItem-1of6</div>
  <div class="K-flexItem-1of12">.K-flexItem-1of12</div>
</div>
```


### Example 1: K-flexItem-share vs K-flexItem-auto
With a auto sized flex element and no specified `width`, the flex item will take up its natural size. For text, this means it the width will be one line. **For text, use share instead of auto**.

<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of4">.K-flexItem-1of4</span>
  <input class="k-inputGroup__item K-flexItem-share" placeholder="K-flexItem-share" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of3">.K-flexItem-1of3</span>
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-share">K-flexItem-share doesn't assert any space and gets squeezed in here</span>
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of4">.K-flexItem-1of4</span>
  <input class="k-inputGroup__item K-flexItem-share" placeholder="K-flexItem-share" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of3">.K-flexItem-1of3</span>
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-auto">K-flexItem-auto (default inputGroup item) gets pushed down to new row</span>
</label>
