# Kelp components (themable)

## Button `.k-button`
```html
<div href="" class="k-button">This is an a.button</div>
<button class="k-button">This is a button.button</button>
```
<a href="" class="k-button">This is an a.button</a>
<button class="k-button">This is a button.button</button>

## inputGroup `.k-inputGroup`
k-inputGroup is an opinionated flex row component for laying out form elements and addons. It is often used inside a form but can be used in other places dealing with buttons and addons too.
The k-inputGroup parent is a flex row. It can house three types of children items:

| item type | classes                                         | basic css `flex` | description                                                    |
|-----------|-------------------------------------------------|------------------|----------------------------------------------------------------|
| main      | `k-inputGroup__item`                            | flex: 12 0 auto; | flex-grows with a basis of 12; 0 basis (may shrink to nothing) |
| full      | `.k-inputGroup__item.k-inputGroup__item--full`  | flex: 12 0 100%; | fills to the whole row; pushes others to different rows        |
| addon     | `.k-inputGroup__item.k-inputGroup__item--addon` | flex: 0 0 auto;  | takes up the space it needs; doesn't grow or shrink            |

Here are some examples to illustrate how inputGroup works.

### Example 1: main + addon
```html
<div class="k-inputGroup"></div>
```
<div class="k-inputGroup">
  <input class="k-inputGroup__item" value="main" type="text">
  <select class="k-inputGroup__item k-inputGroup__item--addon">
    <option value="addon">addon</option>
  </select>
</div>

### Example 2: main + full + addon
With `kelp-theme-base` (a base theme that currently lives inside `kelp`), the first item is expected to not have a right border because there is usually other elements on the same row. The full should have a border on the right because it is not expected to have something on the right.

Each line should fill up the whole row.
```html
<div class="k-inputGroup"></div>
```
<div class="k-inputGroup">
  <input class="k-inputGroup__item" value="main" type="text">
  <input class="k-inputGroup__item k-inputGroup__item--full" value="full" type="text">
  <button class="k-button k-inputGroup__item k-inputGroup__item--addon" value="addon">addon</button>
</div>

### Example 3: `<label>`s and vertical alignment (flex align)
Labels aid usability by effectively expanding the click area for the input. By using the label as the parent `k-inputGroup`, we get simpler markup by not needing the `for` attribute.

By default, items in k-inputGroup are aligned to the center via [flexbox align](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items).

<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">flex: 0 0 25%</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item" placeholder="I'm just a default" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label kelpDocs-inputGroup__label--end">align-self: flex-end</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="Label aligned to flex-end" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">By default, items in k-inputGroup are aligned to the center.<br /><br />The item on the right would be centered.</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item" placeholder="(default) align-self: center" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">The input can be aligned to the end if desired<br /><br />(align-self: flex-start)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexStart" placeholder="align-self: flex-start" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">Or it could be at the end too<br /><br />(align-self: flex-end)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexEnd" placeholder="align-self: flex-end" type="text">
</label>

```html
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">flex: 0 0 25%</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item" placeholder="I'm just a default" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label kelpDocs-inputGroup__label--end">align-self: flex-end</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="Label aligned to flex-end" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">By default, items in k-inputGroup are aligned to the center.<br /><br />The item on the right would be centered.</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item" placeholder="(default) align-self: center" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">The input can be aligned to the end if desired<br /><br />(align-self: flex-start)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexStart" placeholder="align-self: flex-start" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup__label">Or it could be at the end too<br /><br />(align-self: flex-end)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexEnd" placeholder="align-self: flex-end" type="text">
</label>
```

```css
.kelpDocs-inputGroup--bordered {
  outline: 1px solid pink;
}
.kelpDocs-inputGroup__label--25 {
  flex: 0 0 25%;
}

// modifiers
.kelpDocs-inputGroup__label--end {
  align-self: flex-end;
}
.kelpDocs-inputGroup__item--huge {
  font-size: $k-scale-up2;
}
.kelpDocs-inputGroup__item--flexStart {
  align-self: flex-start;
}
.kelpDocs-inputGroup__item--flexEnd {
  align-self: flex-end;
}
```

### Example 4: inputGroup item--tag (k-inputGroup__item--tag)
Tags are inputGroup items that wrap, vertically center, and pad its contents. A tag will vertically stretch to fill up the row.

<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>`k-inputGroup__item--label > span`</span>
  </span>
  <input class="k-inputGroup__item" placeholder="I'm just a default" type="text">
</label>

```html
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>`k-inputGroup__item--label > span`</span>
  </span>
  <input class="k-inputGroup__item" placeholder="I'm just a default" type="text">
</label>
```

<label class="k-inputGroup kelpDocs-inputGroup">
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="I'm huge" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>Still stretched and centered</span>
  </span>
</label>

```html
<label class="k-inputGroup kelpDocs-inputGroup">
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="I'm huge" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>Still stretched and centered</span>
  </span>
</label>
```

<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button k-inputGroup__item--addon">Mix</button>
  <input class="k-inputGroup__item--addon" id="kelpDocs-inputGroup-and" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and" class="k-inputGroup__item k-inputGroup__item--tag">
    <span>match! (remember to use label `for` carefully)</span>
  </label>
</div>

```html
<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button k-inputGroup__item--addon">Mix</button>
  <input class="k-inputGroup__item--addon" id="kelpDocs-inputGroup-and" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and" class="k-inputGroup__item k-inputGroup__item--tag">
    <span>match! (remember to use label `for` carefully)</span>
  </label>
</div>
```

<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag k-inputGroup__item--addon">
    <input class="k-inputGroup__item--addon" type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--tag k-inputGroup__item--addon">
    <span>Tags can be used with inputs inside them too</span>
  </span>
</label>

```html
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag k-inputGroup__item--addon">
    <input class="k-inputGroup__item--addon" type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--tag k-inputGroup__item--addon">
    <span>Tags can be used with inputs inside them too</span>
  </span>
</label>
```


### Example 5: inputGroup item--tag (k-inputGroup__item--block)
Blocks work like tags in the previous example except that there is no background or border. This is particularly useful for checkboxes. There is still a 1px transparent border to maintain consistent sizing with tags.


<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--block">
    <span>`k-inputGroup__item--label > span`</span>
  </span>
  <input class="k-inputGroup__item" placeholder="I'm just a default" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup">
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="I'm huge" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--block">
    <span>Still stretched and centered</span>
  </span>
</label>
<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button k-inputGroup__item--addon">Mix</button>
  <input class="k-inputGroup__item--addon" id="kelpDocs-inputGroup-and2" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and2" class="k-inputGroup__item k-inputGroup__item--tag">
    <span>match! (remember to use label `for` carefully)</span>
  </label>
</div>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--block k-inputGroup__item--addon">
    <input class="k-inputGroup__item--addon" type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--block k-inputGroup__item--addon">
    <span>Tags can be used with inputs inside them too</span>
  </span>
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--block k-inputGroup__item--addon">
    <input class="k-inputGroup__item--addon" type="checkbox">
  </span>
  <span class="k-inputGroup__item">In some cases (like with checkboxes), you might not want to use blocks for text because of the double margin. Simply use `.k-inputGroup__item` without any modifiers</span>
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--block k-inputGroup__item--addon">
    <input class="k-inputGroup__item--addon" type="checkbox">
  </span>
  <span class="k-inputGroup__item">The above will look like this</span>
</label>

```html
<!-- it is the same as the above example except with
  the word block instead of tag -->

<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button k-inputGroup__item--addon">Mix</button>
  <input class="k-inputGroup__item--addon" id="kelpDocs-inputGroup-and2" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and2" class="k-inputGroup__item k-inputGroup__item--tag">
    <span>match! (remember to use label `for` carefully)</span>
  </label>
</div>
```

### Example 6: inputGroup item--block (k-inputGroup__item--block)
Blocks work like tags in the previous example except that there is no background or border. This is particularly useful for checkboxes. There is still a 1px transparent border to maintain consistent sizing with tags.


### Example 7: Other cases (dealing with flex)
Some times, you would want to do something with custom sizes like this:
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--addon kelpDocs-inputGroup--25">flex: 0 0 25%</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup3__main" placeholder="I'm just a default" type="text">
</label>

You may ask why inputGroup doesn't have something for columns right out of the box instead of having to write your own flex. The answer is that k-inputGroup is just one module doing what it does best: grouping inputs together. For flex positioning and sizing, you will either have to write your own or use flex utilities.

### Advanced notes:

k-inputGroup also handles edgecases such as maintaining consistent left/right padding with bigger font size. It pulls sizing from `$k-spacing`.

While one could configure k-inputGroup flex direction to be a column, this is not something that kelp supports out of the box since it is a rare use case.
