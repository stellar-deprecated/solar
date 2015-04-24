### CSS Selectors
Kelp and css should use the following syntax for selectors:
```
namespace-itemName[__descendantName|--modifierName]
```

#### itemName
This consists of the parent item.
#### itemName--modifierName
#### itemName__descendantName
#### itemName.is-stateOfComponent

#### Don't use ID's
Nope. (except for hash anchor points or css `:target`).

#### Don't nest selectors
Media queries and pseudoelements excepted.

#### Kelp Namespaces
You can define your own namespace but make sure that it doesn't clash with these predefined kelp namespaces.

General namespace:
- **`is-`**: States of modules (added and removed )
- **`js-`**: Kelp modules

Kelp framework namespaces:
- **`K-`**: Kelp components
- **`k-`**: Kelp modules
- **`U-`**: General kelp utilities

User defined namespace:
- **`u-`**: User defined utilities
- **`r-`**: Responsive utilities

#### Whitespace
Use two spaces for indentation and don't use tabs.

#### Format
* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Include a single space after the colon of a declaration.
* Use lowercase and shorthand hex values, e.g., `#aaa`.
* Use single or double quotes consistently. Preference is for double quotes,
  e.g., `content: ""`.
* Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
* Include a space after each comma in comma-separated property or function
  values.
* Include a semi-colon at the end of the last declaration in a declaration
  block.
* Place the closing brace of a ruleset in the same column as the first
  character of the ruleset.
* Separate each ruleset by a blank line.

```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
    padding: 10px;
}
```

##### Declaration Order
When declaring selectors, do so in this order:
```css
.selector {
    /* Positioning */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Display & Box Model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Other */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

#### Exceptions and slight deviations

Large blocks of single declarations can use a slightly different, single-line
format. In this case, a space should be included after the opening brace and
before the closing brace.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Long, comma-separated property values - such as collections of gradients or
shadows - can be arranged across multiple lines in an effort to improve
readability and produce more useful diffs. There are various formats that could
be used; one example is shown below.

```css
.selector {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

#### Comments
Do not use block comments (`/* */`). Instead, use the double slash to write comments `//`.

### Specificity
The css selector syntax is designed to keep css specificity low (0,1,0). Use as few selectors as by adding classes to things when necessary.



## Credits & attribution
Shoutouts to a lot of the people who have written and taught about the practices that kelp uses. Specifically but not limited to: @necolas, @mdo, @fat.

- Style guide > CSS selector syntax: @necolas (suit), Yandex (BEM)
- Style guide > format (modified) (CC BY 3.0): @necolas (https://github.com/necolas/idiomatic-css)
