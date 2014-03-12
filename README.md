---
title: Style Structure
---

# Style Structure 

* * * 

Resets 
------

Remove all styling for all elements. Will also normalize across browsers. 

Theme
-----

### Variables 

    - Fonts 
    - Colors 
    - Borders 
    - Shadows 

### Sprites / Icons 

### Decorator Classes 

Layouts 
-------

Composed of both SCSS mixins and class definitions. Use this for _common_ layouts. Not to be confused with context/page specific positioning.

Context Specific Styles 
-----------------------

Override base theme and layout. Could include the following: 

* * * 

Guidelines
----------

- Do not style `<h>` elements
- Encourage smart defaults, and expand on them
- Consider that some `<a>` elements might need to look exactly like `<button>` elements. Do not rely on element name for these scenarios.
