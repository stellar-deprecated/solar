---
id: variables
title: Core variables
category: Documents
---

These are the real variables that will stay
```css
$s-color-primary: $s-color-A; // a bright brand color
$s-color-neutralDark: $s-color-E; // a dark "neutral" color like a dark gray
$s-color-neutralLight: $s-color-G; // a light "neutral" color like a dark gray
$s-color-shadow: #aaa; // color for shadows


// Contains variables that control spacing of the app
// May be multiplied
$s-spacing-formPadding: 0.66666em;

// Aligned spacing.
// Some inputs may have bigger font sizes than others and in those cases, it is
// important to use a fixed size.
// This is also useful for when something wants to have consistent padding.
$s-spacing-formPadding-fixed: 12px;


// margins between items like forms
$s-spacing-marginXSmall: 0.33333em;
$s-spacing-marginSmall: 0.66666em;

$s-spacing-marginXSmall-fixed: 6px;
$s-spacing-marginSmall-fixed: 12px;


// padding on the inside of widgets
$s-spacing-widgetPadding: 0.66666em;
// $s-spacing-widgetPadding-large: 1.3333em;


// border radius intentionally big by default to encourage widget developers to
// remember about them

// border radius for small elements
$s-details-borderRadiusSmall: 3px;

// border radius for large elements
$s-details-borderRadiusLarge: 6px;

```
