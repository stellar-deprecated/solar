This document contains information on two main sections:
- How the css components are organized
- How the build process and architecture concepts

## Kelp framework css overview
Kelp framework includes four concepts of code:
- Base
- Basics
- Components
- Utilities (still under design)

### Kelp Base
The kelp base is a set of styles baked in to the kelp-core to make the overall css development experience better. It includes css normalize and other extremely basic things such as configuring border-box. It does not come with any mixins or classes that developers can use.

### Kelp Basics (non-themable)
Kelp provides "basics" which are **non-themable** reusable building blocks. They come in the form of sass mixins along with classes for convenience and are namespaced with `K-`. Think of them as the screws and motors in a robot--these are standard parts that aren't painted/themed.

### Kelp Components (themable)
Kelp provides components which are **themable** reusable building blocks of a website. They are only available as classes. Components should be as generic as possible so that they can be reused in many different places.

When using a kelp module, do it alongside your own defined class. For example, do the following which uses the module class alongside your own class:
```
<ul class="k-webApp-tabBar state-one-tabBar">
```

Do not use the @extend feature.

### Kelp utilities
Still to be designed. The current thought is that utilities will live inside a kelp extension (with namespace `U-`). Consumers can then create their own utilities as needed. This is still under design and may be later moved out as an extension.

### Sass
Sass is a css preprocessor that kelp uses. It provides functionality such as mixins and includes.

To use a mixin, do:
```
@include mixinName(arguments);
```

In the kelp framework, only use the following features:
- mixins
- variables
- kelp functions (shade/tint)

Don't use these features:
- @extend
- nesting

### Kelp library bundle
To use kelp component mixins, a root scss file (not starting with an underscore) must import the kelp library bundle which includes all of this functionality:
```
@import 'kelp-library-bundle';
```

## Kelp Ecosystem Architecture

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

### Kelp library bundle
A kelp library bundle is a convenient way of calling the kelp libraries used in a project.

Consumers may need in include multiple kelp libraries at once. Packets simplify this by wrapping all the includes into one entry point to the kelp library with a one liner:
```css
@import "kelp-lib-bundle";
```
In order to use extensions and themes, one must create a custom packet. Projects using gulp can utilize `gulp-kelp` to generate packets.

### Kelp css bundle
A kelp css bundle is a compiled `.css` file containing all the css styles from kelp and extensions used.

Each kelp module may add styles and the order of which files come first is sensitive. A kelp css bundle manages this by compiling all the styles brought by extensions into a single kelp bundle file. The `gulp-kelp` tool can compile the scss files in each of your extensions into css.

### Compilation process
1. Create the kelp library bundle.
2. Compile the kelp css, and other css. Each file imports the bundle.

## File Conventions
- Each library should contain an `_index.scss` file as its entry point.
