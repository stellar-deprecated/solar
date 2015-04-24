# kelp

Kelp is a front-end framework developed specifically for modular apps with cross organization shared widgets.

## Getting started
Before writing css on the consumer level (widgets and states), please have look through the style guide and have a general understanding of how kelp works.
Before writing css on the framework level (core and extensions) or starting a new `kelp` project, please read the architecture overview.

## Design philosophies/goals
The design decision of `kelp` has been influenced by these main goals:
- **Mobile first**: creating a mobile site THEN scaling up to desktop
- **Unopinionated design core**: including simple unopinionated look and feel for the core
- **Easy to get started**: favoring simplicity for the 90% of use cases over the 10% complex
- **Cross organizational**: enabling easy sharing of widgets to work across multiple organizations

## Conventions
Kelp is more than just a set of sass/js files. It is also set of conventions. Kelp extensions and consumers should follow the kelp conventions. These conventions are designed to enable developers to write css in a unified, clean, and modular way.

These conventions should be keep the css organized while still being easy to understand. Developers new to this framework should be able to write code meaningfully without being bogged down by heavy conventions.

## Architecture

### File architecture
There are multiple layers in the `kelp` ecosystem. In order from general/global to specific:
- Core
- Extensions (including themes)
- States
- Widgets

### Library vs styles
In the kelp framework, there is a distinction between two sets of files in a module: a library and styles:
- **library**: a set of sass files that creates sass functions/mixins/variables without generating output css code
- **styles**: a set of sass files that consumes sass functions/mixins/variables and generates output css code

### Kelp core module
The core library defines the sass functions and variables that other extensions use and extend. This library is also extensively used by the framework.

The styles contain the basic framework functionality. It lays out the basic styling and classes.

### Extensions and themes
By default, kelp core is the only thing needed in the kelp framework. Additional extensions can be brought in to add or change functionality. Themes are a type of module that only changes the look and feel of kelp.

Each extension should contain an `_index.scss` file as its entry point in each of it's folder `lib` and `styles`.

### Packet of libraries
A packet is a convenient way of calling the kelp libraries used in a project.

Consumers may need in include multiple kelp libraries at once. Packets simplify this by wrapping all the includes into one entry point to the kelp library with a one liner:
```css
@import "kelp-packet";
```
In order to use extensions and themes, one must create a custom packet. Projects using gulp can utilize `gulp-kelp-packet` to generate packets.

### Bundle of styles
Each kelp module may add styles and the order of which files come first is sensitive. A kelp bundle manages this by compiling all the styles brought by extensions into a single kelp bundle file. The (soon to be written) `gulp-kelp-bundle` tool is provided to compile the bundle.

### Compilation process
1. Create the kelp packet.
2. Compile the kelp bundle, and other css. Each file imports the bundle.

## CSS Conventions

### Build
kelp uses ruby-sass and postcss for some additional features such as `autoprefixing` for browser compatibility.

## File Conventions
- Each library should contain an `_index.scss` file as its entry point.
