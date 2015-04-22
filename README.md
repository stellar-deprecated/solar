# kelp

Kelp is a front-end framework developed specifically for modular apps.

## 2 minute overview
### Goals
- Reusable & cross organizational modularity (adding classes to items not always possible)
- Mobile first

### Conventions
Kelp is more than just a set of sass files. It is also set of conventions. Kelp modules and consumers should follow the kelp conventions. These conventions are designed to enable developers to write css in a unified, clean, and modular way.

These conventions should be keep the css organized while still being easy to understand. Developers new to this framework should be able to write code meaningfully without being bogged down by heavy conventions.

### Library vs styles
In the kelp framework, there is a distinction between two sets of files in a module: a library and styles:
- **library**: a set of sass files that creates sass functions/mixins/variables without generating output css code
- **styles**: a set of sass files that consumes sass functions/mixins/variables and generates output css code

### Kelp core module
The core library defines the sass functions and variables that other modules use and extend. This library is also extensively used by the framework.

The styles contain the basic framework functionality. It lays out the basic styling and classes.

### Modules and themes
By default, kelp is the only module used in the kelp framework. Additional extensions can be brought in to add or change functionality. Themes are a type of module that only changes the look and feel of kelp.

### Packet of libraries
A packet is a convenient way of calling the kelp libraries used in a project.

Consumers may need in include multiple kelp libraries at once. Packets simplify this by wrapping all the includes into one entry point to the kelp library with a one liner:
```css
@import "kelp-packet";
```
In order to use extensions and themes, one must create a custom packet. Projects using gulp can utilize `gulp-kelp-packet` to generate packets.

### Bundle of styles
Each kelp module may add styles and the order of which files come first is sensitive. A kelp bundle manages this by compiling all the styles brought by modules into a single kelp bundle file. The `gulp-kelp-bundle` tool is [soon to be] provided to compile the bundle.

### Compilation process
1. Create the kelp packet.
2. Compile the kelp bundle, and other css. Each file imports the bundle.

## CSS Conventions
### sass function based objects over class based objects

## Design decisions yet to be made
- How to define widgets on the `kelp` level

## File Conventions
- Each library should contain an `_index.scss` file as its entry point.

## css component documentation
This will later be moved out to its own repository. For now, it will remain in here as a draft.

### Layout
#### kelp-flex
Flexbox with a default basis of 12. Here is an example of how it would look like with the basis set
```
| 1/2 basis: 12 | 1/2 basis: 12 | (total: 24)
| 1/3 basis: 12 | 1/3 basis: 12 | 1/3 basis: 12 | (total: 36)
| 2/3 basis: 12 | 1/3 basis: 6 | (total: 18)
| 3/4 basis: 12 | 1/4 basis: 4 | (total: 16)
| 60% basis: 12 | 20% basis: 4 | 20% basis: 4 | (total: 20)
| 50% basis: 12 | 16.6% basis: 4 | 16.6% basis: 4 | 16.6% basis: 4 | (total: 24)
```

Classes:
- kelp-flex-row
- kelp-flex-col
- kelp-flex-box
- kelp-flex-box-[n] (where n is flex-basis; available for evens below 12 and some above 12: 2, 4, 6, 8, 10, 12, 18, 24, 36)
