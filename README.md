---
title: Style Structure
layout: clean
---

# Style Structure 

[View the example site &raquo;](http://jasonseney.github.io/style-structure/)

Resets 
------

Remove all styling for all elements. Will also normalize across browsers. 

Theme
-----

### Variables 

For most scenarios, SASS variables are set in two levels: 

1. Mapping values to names
    - Example: `$med_blue : #3333FF;`
2. Mapping names to domain specific properties
    - Example: `$link_color: $med_blue;`, `$widget_borders: $med_blue;`

This allows us to keep all values in one place, and avoid side effects in domain properties.

Variable Settings:

- Fonts 
- Color Scheme
- Borders 
- Shadows 

### Sprites / Icons 

### Baseline Styles

For all HTML elements, set base properties such as:

- Typography (font size, family, line-heights)
- Basic theming (create a more sane baseline on top of the reset)

### Decorator Classes 

Style classes you can add to themed elements. Examples:

- Buttons
- Links
- Headings
- Alerts
- Boxes
- Menus
- Form elements

*See twitter bootstrap for examples of this on forms and buttons*

Layouts 
-------

Composed of both SCSS mixins and class definitions. Use this for _common_ layouts. Not to be confused with context/page specific positioning. Examples might be creating columns, basic visual blocks (tables, etc). Use sparingly - most layouts will be context/component specific.

Context & Compontent Specific Styles 
------------------------------------

Override base theme and layout. Example:

    [data-name='followers'] .row {
        height: $med_row_height;
        img.avatar {
            width: $small_avatar;
            float: left;
        }
        a:hover {
            color: $row_highlight;
        }
    }

* * * 

Guidelines
----------

- Encourage smart defaults, and expand on them
- If you're writing the same pattern of CSS multiple times, consider creating a mixin.
- Consider using the SASS `@extend` feature in context specific styles instead of adding many classes to elements.
- Consider that some `<a>` elements might need to look exactly like `<button>` elements. Do not rely on element name for these scenarios.
- Do not style `<h>` elements (used for SEO)

Things that shouldn't be used without serious thought and consideration:

- Grid system (especially with `col-sm-2` type classes).
- Really long, multi-word class names
- Generic styles in _global "scope"_ (`.small {}`, `.important {}`)
