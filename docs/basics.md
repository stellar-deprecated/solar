# Kelp basics (non-themable)

## K-flex (K-flexItem)[layout]
[Flexbox](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes) is a new powerful layout mode. K-flex is a set of predefined common flex use cases. It assumes the developer using it has at least a basic understand of the flexbox model.

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

### flex item reference
These classes are not meant to be comprehensive and for complex cases, you may need to write your own.
<!-- csv to markdown table style="white-space: nowrap"
name,class/mixin name,grow,shrink,basis,description
 ,(no `flex` specified),0,1,auto,<small>when no flex explicitly specified it uses `width` info</small>
 ,(shorthand omission default),1,1,auto,t<small>hese are the values filled when items omitted in shorthand</small>
none,`K-flexItem-none`,0,0,auto,<small>no flexing: takes up space it needs or defined. Same as `flex: none`</small>
share,`K-flexItem-share`,12,0,0%,<small>all space completely distributed (could get crumpled to ~0px)</small>
auto,`K-flexItem-auto`,12,0,auto,<small>extra space distributed; basis of 12</small>
auto1,`K-flexItem-1`,1,0,auto,<small>extra space distributed; basis of 1</small>
auto2,`K-flexItem-2`,2,0,auto,<small>extra space distributed; basis of 2</small>
autoN,`K-flexItem-N`,N,0,auto,<small>extra space distributed; basis of N: 1 2 3 4 6 8 10</small>
full,`K-flexItem-full`,12,0,100%,<small>always takes up the main size (same as the nonexistent 1of1)</small>
1of2,`K-flexItem-1of2`,0,0,50%,<small>always takes up 1/2th of the main size</small>
1of3,`K-flexItem-1of3`,0,0,33.3%,<small>always takes up 1/3th of the main size</small>
MofN,`K-flexItem-MofN`,0,0,100%*M/N,<small>available MofN sizes: 1of2 1of3 1of4 1of6 1of12 2of3 3of4 5of6</small>
-->

<table>
<tr><td>name</td><td>class/mixin name</td><td>grow</td><td>shrink</td><td>basis</td><td>description</td></tr>
<tr><td> </td><td style="white-space: nowrap">(no `flex` specified)</td><td>0</td><td>1</td><td>auto</td><td><small>when no flex explicitly specified it uses `width` info</small></td></tr>
<tr><td> </td><td style="white-space: nowrap">(shorthand omission default)</td><td>1</td><td>1</td><td>auto</td><td>t<small>hese are the values filled when items omitted in shorthand</small></td></tr>
<tr><td>none</td><td style="white-space: nowrap">`K-flexItem-none`</td><td>0</td><td>0</td><td>auto</td><td><small>no flexing: takes up space it needs or defined. Same as `flex: none`</small></td></tr>
<tr><td>share</td><td style="white-space: nowrap">`K-flexItem-share`</td><td>12</td><td>0</td><td>0%</td><td><small>all space completely distributed (could get crumpled to ~0px)</small></td></tr>
<tr><td>auto</td><td style="white-space: nowrap">`K-flexItem-auto`</td><td>12</td><td>0</td><td>auto</td><td><small>extra space distributed; basis of 12</small></td></tr>
<tr><td>auto1</td><td style="white-space: nowrap">`K-flexItem-1`</td><td>1</td><td>0</td><td>auto</td><td><small>extra space distributed; basis of 1</small></td></tr>
<tr><td>auto2</td><td style="white-space: nowrap">`K-flexItem-2`</td><td>2</td><td>0</td><td>auto</td><td><small>extra space distributed; basis of 2</small></td></tr>
<tr><td>autoN</td><td style="white-space: nowrap">`K-flexItem-N`</td><td>N</td><td>0</td><td>auto</td><td><small>extra space distributed; basis of N: 1 2 3 4 6 8 10</small></td></tr>
<tr><td>full</td><td style="white-space: nowrap">`K-flexItem-full`</td><td>12</td><td>0</td><td>100%</td><td><small>always takes up the main size (same as the nonexistent 1of1)</small></td></tr>
<tr><td>1of2</td><td style="white-space: nowrap">`K-flexItem-1of2`</td><td>0</td><td>0</td><td>50%</td><td><small>always takes up 1/2th of the main size</small></td></tr>
<tr><td>1of3</td><td style="white-space: nowrap">`K-flexItem-1of3`</td><td>0</td><td>0</td><td>33.3%</td><td><small>always takes up 1/3th of the main size</small></td></tr>
<tr><td>MofN</td><td style="white-space: nowrap">`K-flexItem-MofN`</td><td>0</td><td>0</td><td>100%*M/N</td><td><small>available MofN sizes: 1of2 1of3 1of4 1of6 1of12 2of3 3of4 5of6</small></td></tr>
</table>

Note: CSSWG might (or might not) rename flex-basis of `auto` to `main-size` in future versions of flex

Source:
```scss
// special sizes
.K-flexItem-none { @include K-flexItem-none; } // flex: 0 0 auto;
.K-flexItem-share { @include K-flexItem-share; } // flex: 12 0 0%;

// auto sizes
.K-flexItem-auto { @include K-flexItem-auto; } // flex: 12 0 auto;
.K-flexItem-1 { @include K-flexItem-1; } // flex: 1 0 auto;
.K-flexItem-2 { @include K-flexItem-2; } // flex: 2 0 auto;
.K-flexItem-3 { @include K-flexItem-3; } // flex: 3 0 auto;
.K-flexItem-4 { @include K-flexItem-4; } // flex: 4 0 auto;
.K-flexItem-6 { @include K-flexItem-6; } // flex: 6 0 auto;
.K-flexItem-8 { @include K-flexItem-8; } // flex: 8 0 auto;
.K-flexItem-10 { @include K-flexItem-10; } // flex: 10 0 auto;

// main sizes
.K-flexItem-full { @include K-flexItem-full; } // flex: 12 0 100%;
.K-flexItem-1of2 { @include K-flexItem-1of2; } // flex: 0 0 50%;
.K-flexItem-1of3 { @include K-flexItem-1of3; } // flex: 0 0 33.33333%;
.K-flexItem-1of4 { @include K-flexItem-1of4; } // flex: 0 0 25%;
.K-flexItem-1of5 { @include K-flexItem-1of5; } // flex: 0 0 20%;
.K-flexItem-1of6 { @include K-flexItem-1of6; } // flex: 0 0 16.66666%;
.K-flexItem-1of12 { @include K-flexItem-1of12; } // flex: 0 0 8.33333%;
```

### Demos
<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-share">.K-flexItem-share</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-addon">.K-flexItem-addon</div>
  <div class="K-flexItem-full">.K-flexItem-full</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>

Grid proportioned flex items are not a direct replacement for traditional grids since this does not take into account the gutters (and no, adding a bit of margin-right does not make it a true grid column). They do add a quick simple way to proportionally take up space and this is useful for inputGroups.

<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-share">.K-flexItem-share</div>
</div>
<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-1of2">.K-flexItem-1of2</div>
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
</div>
<div class="kelpDocs-flexDemo-container">
  <div class="K-flexItem-1of4">.K-flexItem-1of4</div>
  <div class="K-flexItem-1of2">.K-flexItem-1of2</div>
  <div class="K-flexItem-1of3">.K-flexItem-1of3</div>
</div>

<div class="kelpDocs-flexDemo-container">
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
<div class="kelpDocs-flexDemo-container">
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
