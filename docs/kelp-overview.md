## 5 minute consumer css overview
This is intended as a quick overview to help you get started using kelp. This section is not the last thing you will need though. As you code, you will find that you need some components or guidance. It is likely that it has been thought out before, so please refer to this document while you write css.

### Overview: Kelp framework architecture
Kelp framework includes four concepts of code:
- Base
- Components
- Modules
- Utilities (still under design)

#### Kelp Base
The kelp base is a set of styles baked in to the kelp-core. It includes css normalize and other extremely basic things such as configuring border-box.

#### Kelp Components (non-themable)
Kelp provides components which are **non-themable** reusable tools. They come in the form of sass mixins along with classes for convenience and are namespaced with `K-`. Think of them as the screws and motors in a robot--these are standard parts that aren't painted/themed.

#### Kelp Modules (themable)
Kelp provides modules which are **themable** reusable building blocks of a website. They are only available as classes. Modules should be as generic as possible so that they can be reused in many different places.

When using a kelp module, do it alongside your own defined class. For example, do the following which uses the module class alongside your own class:
```
<ul class="k-webApp-tabBar state-one-tabBar">
```

Do not use the @extend feature.

### Kelp utilities
Still to be designed. The current thought is that utilities will live inside a kelp extension (with namespace `U-`). Consumers can then create their own utilities as needed.

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

### Kelp packet
To use kelp component mixins, a root scss file (not starting with an underscore) must import the kelp packet which includes all of this functionality:
```
@import 'kelp-packet';
```
