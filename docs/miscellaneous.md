---
id: unorganized-stuffs
title: Miscellaneous
category: Documents
---

## Designed with the assumptions
- Developer might not have access to html code (unable to add/remove classes)
- Developer either familiar with solar or has time to learn about solar (not for hackathons)
- Bandwidth is somewhat cheap (it's fine to have solar styles mirror lib for styling with classes)
- CSS class namespace is a scarce commodity (careful naming of classes)

## Design decisions and rationale

### Developers will have access to html most of the time
Developers usually have access to html code (chrome of the app). However, there are cases when they will not (cross-organizational widgets). In these cases though, the developers shouldn't really be changing the widget and if they do need to make drastic changes, they can fork them.

### App specific css is necessary?

### One global organizational theme
Pros:
- simple

Cons:
- One massive theme repository to manage changes. one feature change requires changes in two repositories

### Widgets should use both the generic class names

### Mixins vs classes
- There currently is no way to have inheritance of mixins through sass. That would require a custom preprocessor module to be written


## lost grid
Solar also uses lost, a postcss grid system.


### sass function based objects over class based objects

## Design decisions yet to be made
- How to define widgets on the `solar` level
