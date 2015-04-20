# kelp

Kelp is a front-end framework developed specifically for modular apps.

## Architecture
### Conventions
Kelp is more than just a framework. It is also set of conventions. Kelp, extensions, and consumers of the kelp system should follow the kelp way of writing css. These conventions are designed to enable developers to write css in a unified, clean, and modular way.

These conventions should be keep the css organized while still being easy to understand. Developers new to this framework should be able to write code meaningfully without being bogged down by heavy conventions.

### Kelp core library/framework
The kelp core has two parts: a sass library and a css framework. A library is defined as a set of scss files that creates mixins and variables but doesn't directly output css code itself. A framework is one that does generate output css code.

The core library contains tools and settings settings that can be extended by extensions and themes. This library is also extensively used by the framework.

The framework is a contains the basic framework functionality. It lays out the basic css selectors and conventions.

### Extensions and themes
Next, extensions extend the kelp core to add or change functionality.

Themes are a type of extension that only changes the look and feel of kelp without adding any functionality.

### Packets
Consumers may need in include multiple kelp libraries at once. Packets simplify this by wrapping all the includes into one entry point to the kelp library with a one liner:
```css
@import "kelp/packet";
```

The default packet only contains the kelp core library. In order to use extensions and themes, one must create a custom packet. The `kelp-packet` module can generate these custom packets.

## File Conventions
- Each library should contain an `_index.scss` file as its entry point.
