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

### Advanced notes:

k-inputGroup also handles edgecases such as maintaining consistent left/right padding with bigger font size and preventing double borders.

While one could configure k-inputGroup flex direction to be a column, this is not something that kelp supports out of the box since it is a rare use case.
