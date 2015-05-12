# Kelp basics (non-themable)

## K-flex (K-flexChild)[layout]
[Flexbox](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes) is a new powerful layout mode. K-flex is a set of predefined common flex use cases. It assumes the developer using it has at least a basic understand of the flexbox model.

### What it provides:
- a set of common flex children sizes

### What it is not:
- an auto-prefixer
- a replacement for css flex properties

### 12 basis
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


### Demos
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-share">.K-flexChild-share</div>
  <div class="K-flexChild-share">.K-flexChild-share</div>
</div>
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-addon">.K-flexChild-addon</div>
  <div class="K-flexChild-share">.K-flexChild-share</div>
</div>
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-addon">.K-flexChild-addon</div>
  <div class="K-flexChild-share">.K-flexChild-share</div>
  <div class="K-flexChild-share">.K-flexChild-share</div>
</div>
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-addon">.K-flexChild-addon</div>
  <div class="K-flexChild-full">.K-flexChild-full</div>
  <div class="K-flexChild-share">.K-flexChild-share</div>
</div>

Grid proportioned flex items are not a direct replacement for traditional grids since this does not take into account the gutters (and no, adding a bit of margin-right does not make it a true grid column). They do add a quick simple way to proportionally take up space and this is useful for inputGroups.

<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-1of4">.K-flexChild-1of4</div>
  <div class="K-flexChild-share">.K-flexChild-share</div>
</div>
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-1of4">.K-flexChild-1of4</div>
  <div class="K-flexChild-1of2">.K-flexChild-1of2</div>
  <div class="K-flexChild-1of4">.K-flexChild-1of4</div>
</div>
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-1of4">.K-flexChild-1of4</div>
  <div class="K-flexChild-1of2">.K-flexChild-1of2</div>
  <div class="K-flexChild-1of3">.K-flexChild-1of3</div>
</div>

<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-share">.K-flexChild-share</div>
  <div class="K-flexChild-addon">.K-flexChild-addon</div>
  <div class="K-flexChild-full">.K-flexChild-full</div>
  <div class="K-flexChild-1of2">.K-flexChild-1of2</div>
  <div class="K-flexChild-1of3">.K-flexChild-1of3</div>
  <div class="K-flexChild-1of4">.K-flexChild-1of4</div>
  <div class="K-flexChild-1of5">.K-flexChild-1of5</div>
  <div class="K-flexChild-1of6">.K-flexChild-1of6</div>
  <div class="K-flexChild-1of12">.K-flexChild-1of12</div>
</div>
```html
<div class="kelpDocs-flexDemo-parent">
  <div class="K-flexChild-share">.K-flexChild-share</div>
  <div class="K-flexChild-addon">.K-flexChild-addon</div>
  <div class="K-flexChild-full">.K-flexChild-full</div>
  <div class="K-flexChild-1of2">.K-flexChild-1of2</div>
  <div class="K-flexChild-1of3">.K-flexChild-1of3</div>
  <div class="K-flexChild-1of4">.K-flexChild-1of4</div>
  <div class="K-flexChild-1of5">.K-flexChild-1of5</div>
  <div class="K-flexChild-1of6">.K-flexChild-1of6</div>
  <div class="K-flexChild-1of12">.K-flexChild-1of12</div>
</div>
```

### Usage
