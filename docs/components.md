# Kelp components (themable)

## Button `.k-button`
<a href="" class="k-button">This is an a.button</a>
<button class="k-button">This is a button.button</button>
```html
<div href="" class="k-button">This is an a.button</div>
<button class="k-button">This is a button.button</button>
```

## buttonGroup `.k-buttonGroup`
k-buttonGroup is a way to group multiple buttons together into one bar. These can only be single rows.
<div class="k-buttonGroup">
  <button class="k-button">Left</button>
  <button class="k-button">Middle</button>
  <button class="k-button">Right</button>
</div>

```html
<div class="k-buttonGroup">
  <button class="k-button">Left</button>
  <button class="k-button">Middle</button>
  <button class="k-button">Right</button>
</div>
```

## inputGroup `.k-inputGroup`
k-inputGroup is an wrapping flex row component for laying out form elements and addons. It is often used inside a form but can be used in other places dealing with buttons and addons too.

**Note: this documentation for inputGroup is a bit out of date, especially with regards to flex children. Flex items are to be separate from inputGroup.**

Here are some examples to illustrate how inputGroup works.

### Auto negative margin management to collapse borders (theme starter)
By default all items except for the last have a margin-right of `-1px` to prevent the double borders.
```css
.k-inputGroup {
  padding-right: 1px;
  padding-bottom: 1px;
}
.k-inputGroup__item {
  margin-bottom: -1px;
  margin-right: -1px;
}
```

margin-bottom is not applied to the last item so that in most cases the border won't cover the elements. This "magic" will be helpful for most cases while requiring some manual intervention for a small number of cases.

Disadvantages: if the inputGroup has a border, it will cover the border of the bottom row of elements. It is not common that an inputGroup would have an additional border but if it does, then a workaround would be to wrap it inside another element.

See example 2 for what this helps achieve

### Example 1: main + addon (aka "none")
```html
<div class="k-inputGroup">
  <input class="k-inputGroup__item" placeholder="main (auto)" type="text">
  <select class="k-inputGroup__item K-flexItem-none">
    <option value="addon">addon</option>
  </select>
</div>
```
<div class="k-inputGroup">
  <input class="k-inputGroup__item" placeholder="main (auto)" type="text">
  <select class="k-inputGroup__item K-flexItem-none">
    <option value="addon">addon</option>
  </select>
</div>

### Example 2: mixing different flex sizes
With `kelp-theme-base` (a base theme that currently lives inside `kelp`), the first item is expected to not have a right border because there is usually other elements on the same row. The full should have a border on the right because it is not expected to have something on the right.

Each line should fill up the whole row.
```html
<div class="k-inputGroup"></div>
```
<div class="k-inputGroup">
  <input class="k-inputGroup__item" value="default (K-flexItem-auto)" type="text">
  <input class="k-inputGroup__item K-flexItem-1of3" value="default (K-flexItem-1of3)" type="text">
  <input class="k-inputGroup__item K-flexItem-full" value="k-flexItem-full" type="text">
  <button class="k-button k-inputGroup__item" value="addon">addon</button>
</div>

### Example 3: `<label>`s and vertical alignment (flex align)
Labels aid usability by effectively expanding the click area for the input. By using the label as the parent `k-inputGroup`, we get simpler markup by not needing the `for` attribute.

By default, items in k-inputGroup are aligned to stretch via [flexbox align](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items).

<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item K-flexItem-1of3">.K-flexItem-1of3</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="by default, text is aligned to flex-start" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of3">`.k-inputGroup__item--tag`</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="using a --tag will vertically align the text" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item kelpDocs-inputGroup__label kelpDocs-inputGroup__label--end">align-self: flex-end</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="Label aligned to flex-end" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item kelpDocs-inputGroup__label">The input can be aligned to the end if desired<br />---<br />(align-self: flex-start)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexStart" placeholder="align-self: flex-start" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item kelpDocs-inputGroup__label">Or it could be at the end too<br />---<br />(align-self: flex-end)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexEnd" placeholder="align-self: flex-end" type="text">
</label>

```html
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item K-flexItem-1of3">.K-flexItem-1of3</span>
  <input class="k-inputGroup__item" placeholder="by default, text is aligned to flex-start" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of3">.k-inputGroup_<wbr></wbr>_item--tag</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item" placeholder="using a block will vertically align the text" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item kelpDocs-inputGroup__label kelpDocs-inputGroup__label--end">align-self: flex-end</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="Label aligned to flex-end" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item kelpDocs-inputGroup__label">The input can be aligned to the end if desired<br />---<br />(align-self: flex-start)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexStart" placeholder="align-self: flex-start" type="text">
</label>
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item kelpDocs-inputGroup__label">Or it could be at the end too<br />---<br />(align-self: flex-end)</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--flexEnd" placeholder="align-self: flex-end" type="text">
</label>
```

```css
.kelpDocs-inputGroup--bordered {
  outline: 1px solid pink;
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

### Example 4: k-inputGroup__item modifiers tag, tagFlat, tagMin
The tag modifiers to the inputGroup item.

**Tip**: If the inputGroup__item contains not only a text node, be sure to wrap it with something else like a span. This is because the tag modifiers turn the item into a flex item so that it can vertically center contents.

<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-share">
    <span>`.k-inputGroup__item--tag` (the whole package)</span>
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tagFlat K-flexItem-share">
    <span>`.k-inputGroup__item--tagFlat` (no background/visible border)</span>
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tagMin K-flexItem-share">
    <span>`.k-inputGroup__item--tagMin` (no padding)</span>
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tagMin K-flexItem-share">
    `.k-inputGroup__item--tagMin` This is what <a href="">happens</a> when you don't wrap inner contents with span.
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>

```html
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-share">
    <span>`.k-inputGroup__item--tag` (the whole package)</span>
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tagFlat K-flexItem-share">
    <span>`.k-inputGroup__item--tagFlat` (no background/visible border)</span>
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tagMin K-flexItem-share">
    <span>`.k-inputGroup__item--tagMin` (no padding)</span>
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tagMin K-flexItem-share">
    `.k-inputGroup__item--tagMin` This is what <a href="">happens</a> when you don't wrap inner contents with span.
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of3" placeholder="..." type="text">
</label>
```

<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button">Mix</button>
  <input class="k-inputGroup__item" id="kelpDocs-inputGroup-and" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and" class="k-inputGroup__item k-inputGroup__item--tag">
    match! (remember to use label `for` carefully)
  </label>
</div>

```html
<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button">Mix</button>
  <input class="k-inputGroup__item" id="kelpDocs-inputGroup-and" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and" class="k-inputGroup__item k-inputGroup__item--tag">
    match! (remember to use label `for` carefully)
  </label>
</div>
```

<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-none">
    <input type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>tags can be used with inputs inside them too</span>
  </span>
</label>

```html
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-none">
    <input type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>tags can be used with inputs inside them too</span>
  </span>
</label>
```




### Advanced notes:

k-inputGroup also handles edgecases such as maintaining consistent left/right padding with bigger font size. It pulls sizing from `$k-spacing`.

While one could configure k-inputGroup flex direction to be a column, this is not something that kelp supports out of the box since it is a rare use case.
