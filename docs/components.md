# Kelp components (themable)

## Button `.k-button`
```html
<div href="" class="k-button">This is an a.button</div>
<button class="k-button">This is a button.button</button>
```
<a href="" class="k-button">This is an a.button</a>
<button class="k-button">This is a button.button</button>

## inputGroup `.k-inputGroup`
k-inputGroup is an wrapping flex row component for laying out form elements and addons. It is often used inside a form but can be used in other places dealing with buttons and addons too.

**Note: this documentation for inputGroup is a bit out of date, especially with regards to flex children. Flex items are to be separate from inputGroup.**

Here are some examples to illustrate how inputGroup works.

### Auto negative margin management to collapse borders
By default all items except for the last have a margin-right of `-1px` to prevent the double borders.
```css
.k-inputGroup__item {
  margin-bottom: -1px;
}
.k-inputGroup__item:not(:last-child) {
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
  <span class="k-inputGroup__item k-inputGroup__item--block K-flexItem-1of3">`.k-inputGroup__item--block`</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item kelpDocs-inputGroup__item--huge" placeholder="using a --block will vertically align the text" type="text">
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
  <span class="k-inputGroup__item k-inputGroup__item--block K-flexItem-1of3">.k-inputGroup_<wbr></wbr>_item--block</span>
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

### Example 4: k-inputGroup__item--tag and k-inputGroup__item--block
Tags and blocks are inputGroup items that wrap vertically center contents.

A block is functionally the same as a tag except that blocks are flat and don't have a background. Blocks still have a 1px transparent border to maintain consistent sizing with tags.

<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    `.k-inputGroup__item--tag`
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of4" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--block">
    `.k-inputGroup__item--block`
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of4" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of4" placeholder="..." type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    `.k-inputGroup__item--tag`
  </span>
</label>

```html
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    `.k-inputGroup__item--tag`
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of4" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--block">
    `.k-inputGroup__item--block`
  </span>
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of4" placeholder="..." type="text">
</label>
<label class="k-inputGroup">
  <input class="k-inputGroup__item kelpDocs-inputGroup__item--huge K-flexItem-1of4" placeholder="..." type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    `.k-inputGroup__item--tag`
  </span>
</label>
```

<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button">Mix</button>
  <input class="k-inputGroup__item" id="kelpDocs-inputGroup-and" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and" class="k-inputGroup__item k-inputGroup__item--tag">
    <span>match! (remember to use label `for` carefully)</span>
  </label>
</div>

```html
<div class="k-inputGroup">
  <button class="k-inputGroup__item k-button">Mix</button>
  <input class="k-inputGroup__item" id="kelpDocs-inputGroup-and" type="text" placeholder="and">
  <label for="kelpDocs-inputGroup-and" class="k-inputGroup__item k-inputGroup__item--tag">
    <span>match! (remember to use label `for` carefully)</span>
  </label>
</div>
```

<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-none">
    <input type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>item--tag/block can be used with inputs inside them too</span>
  </span>
</label>

```html
<label class="k-inputGroup">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-none">
    <input type="checkbox">
  </span>
  <span class="k-inputGroup__item k-inputGroup__item--tag">
    <span>item--tag/block can be used with inputs inside them too</span>
  </span>
</label>
```



### Example 7: K-flexItem-share vs K-flexItem-auto
Some times, you would want to do something with custom sizes like this:
<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of4">.K-flexItem-1of4</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup3__main K-flexItem-1of4" placeholder="k-inputGroup__item is K-flexItem-auto" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of3">.K-flexItem-1of3</span>
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-share">.K-flexItem-share doesn't assert any space and gets squeezed in here</span>
</label>

<label class="k-inputGroup kelpDocs-inputGroup--bordered">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of4">.K-flexItem-1of4</span>
  <input class="k-inputGroup__item kelpDocs-inputGroup3__main K-flexItem-1of4" placeholder="k-inputGroup__item is K-flexItem-auto" type="text">
  <span class="k-inputGroup__item k-inputGroup__item--tag K-flexItem-1of3">.K-flexItem-1of3</span>
  <span class="k-inputGroup__item k-inputGroup__item--tag">default (.K-flexItem-auto) gets pushed down to new row</span>
</label>

To learn more about flexItem, take a look at the flexItem documentation.

### Advanced notes:

k-inputGroup also handles edgecases such as maintaining consistent left/right padding with bigger font size. It pulls sizing from `$k-spacing`.

While one could configure k-inputGroup flex direction to be a column, this is not something that kelp supports out of the box since it is a rare use case.
