# Core variables

These are the real variables that will stay
```css
$k-color-primary: $k-color-A; // a bright brand color
$k-color-neutralDark: $k-color-E; // a dark "neutral" color like a dark gray
$k-color-neutralLight: $k-color-G; // a light "neutral" color like a dark gray
$k-color-shadow: #aaa; // color for shadows


// Contains variables that control spacing of the app
// May be multiplied
$k-spacing-formPadding: 0.66666em;

// Aligned spacing.
// Some inputs may have bigger font sizes than others and in those cases, it is
// important to use a fixed size.
// This is also useful for when something wants to have consistent padding.
$k-spacing-formPadding-fixed: 12px;


// margins between items like forms
$k-spacing-marginXSmall: 0.33333em;
$k-spacing-marginSmall: 0.66666em;

$k-spacing-marginXSmall-fixed: 6px;
$k-spacing-marginSmall-fixed: 12px;


// padding on the inside of widgets
$k-spacing-widgetPadding: 0.66666em;
// $k-spacing-widgetPadding-large: 1.3333em;


// border radius intentionally big by default to encourage widget developers to
// remember about them

// border radius for small elements
$k-details-borderRadiusSmall: 3px;

// border radius for large elements
$k-details-borderRadiusLarge: 6px;

```
