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
