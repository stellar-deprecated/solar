# Kelp architecture

The kelp css framework is a modular framework allowing (developer) consumers to use modules that build upon and extend the core kelp functionality.

## Overview
### File architecture
There are multiple layers in the `kelp` ecosystem. In order from general/global to specific:
- Core
- Modules (including themes)
- States
- Widgets

### Kelp core module
The core library defines the sass functions and variables that other modules use and extend. This library is also extensively used by the framework.

The styles contain the basic framework functionality. It lays out the basic styling and classes.

### Modules and themes
At first, kelp core is the only item in the kelp framework. Additional modules can be brought in to add and/or change functionality. Themes are a type of module that only changes the look and feel of kelp.

Each module should contain an `_index.scss` file as its entry point in each of it's folder `lib` and `styles`.

### Module feature types
Each module may have a combination of any of the following:
- **library**: a set of sass files that creates sass functions/mixins/variables without generating output css code
- **styles**: a set of sass files that consumes sass functions/mixins/variables and generates output css code
- **js**: javascript files to be included in the browser

### Entry point
- Each library should contain an `_index.scss` file as its entry point.
- package.json will point to a node module in the root of the folder specifying what feature types they provide.

## Build process overview
The kelp framework build process produces two important files:
- **kelp library bundle** (_kelp-library-bundle.scss)
- **kelp css bundle** (kelp-css-bundle.css)

### Kelp library bundle (_kelp-library-bundle.scss)
A kelp library bundle is a scss file containing all the libraries from kelp modules combined into one scss file. This scss file provides sass functions/mixins/variables but does not directly produce css code.

Each scss can use a one-liner to import the kelp sass library:
```css
@import "kelp-library-bundle";
```

### Kelp css bundle (kelp-css-bundle.css)
A kelp css bundle is a css file compiled from the kelp framework. This css file can then be further postprocessed and then served to the end user's browser.

### Example
Here is an example of a common use case to help illustrate the build process.

Kelp modules:
- **kelp core** (lib and styles): the core required part of kelp
- **kelp-theme-base** (lib and styles): a module that lays out the basics of the ui
- **kelp-theme-allBlue** (only lib): a (fictional) module that configures kelp-theme-base to make everything blue
- **kelp-utilities** (only styles): a set of utility css classes

In order, this is what happens:
```
1. Creating `_kelp-library-bundle.scss`
  a. add `kelp/lib/_index.scss` to `_kelp-library-bundle.scss`
  b. add `kelp-theme-base/lib/_index.scss` to `_kelp-library-bundle.scss`
  c. add `kelp-theme-allBlue/lib/_index.scss` lib to `_kelp-library-bundle.scss`
2. Creating `kelp-css-bundle.css`
  a. add `kelp/styles/_index.scss`
  b. add `kelp-theme-base/styles/_index.scss`
  c. add `kelp-utilities/styles/_index.scss`
  d. sass compilation into one file
```

## Current gulp support
`gulp-kelp` currently exists to build these two files. It currently does not do much and does not have to ability to flatten the scss files into one file nor does it compile the css-bundle. Still, the plugin can makes it much easier to build the kelp bundles.
