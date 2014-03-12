# Style Structure 

[View the example site &raquo;](http://jasonseney.github.io/style-structure/)

Styles are broken into 4 parts: **[** [Reset](#resetstyles), [Theme](#themestyles), [Component](#componentstyles), [Context](#contextstyles) **]**.

1. Reset Styles
---------------

Remove all styling for all elements. Will also normalize across browsers. Yahoo YUI resets are a good starting point.

2. Theme Styles
---------------

### Variables 

SASS variables should be set in two levels: 

1. Mapping names to values
    - Example: `$med_blue : #3333FF;`
2. Mapping domain specific properties to names
    - Example: `$link_color: $med_blue;`, `$widget_borders: $med_blue;`

This allows us to keep all values in one place, and avoid side effects in domain properties.

Variable types:

- Fonts 
- Color Scheme
- Borders 
- Shadows 

### Sprites / Icons 

_Coming soon..._

### Baseline Styles

For all HTML elements, set base properties such as:

- Typography (apply font variables for size, typeface, line-heights)
- Basic theming 
    - Create a more sane baseline on top of the reset
    - Apply many of the variable settings from above

### Decorator Classes 

Style classes you can add to themed elements. Examples:

- Buttons
- Links
- Headings
- Menus
- Messages
- Form elements
- Common layout structures

*See twitter bootstrap for good examples of this on forms and buttons*

3. Component Styles
--------------------

Component styles will define specific styles for a component that can be located _anywhere_ on the site.

Example:

    .pop-menu {
        display: inline-block;
    }
    .pop-menu .inner {
        padding: 5px 0;
        background-color: $light_bg;
        @include rounded_shadow_box;
    }
    .pop-menu .item-option {
        cursor: pointer;
        padding: 5px 8px;
        color: $med_text_color;
    }
    .pop-menu .item-option:hover {
        background: $menu_hover_bg;
    }


4. Context Styles
-----------------

Context styles contain both high level styles(layouts, margins, backgrounds, etc) along with lower level specific styles that are not in a component.

Override and extend on the base theme.  Example:

    [data-name='followers'] .row {
        height: $med_row_height;
        img.avatar {
            width: $small_avatar;
            float: left;
        }
        .name {
            @include fade_in();
            @extend .minor;
            &:hover { 
                background-color: $row_highlight_bg;
            }
        }
    }


Consider using the SASS `@extend` feature in context specific styles instead of adding many classes to elements.

It is up to the developer to decide whether a style belongs in the context or a component. If a detailed style is not used in other contexts, a component might not be needed.

* * * 

Guidelines
----------

- Encourage smart defaults, and expand on them
- If you're writing the same pattern of CSS multiple times, consider creating a mixin.
- Consider that some `<a>` elements might need to look exactly like `<button>` elements. Use a decorator class and do not rely on element names for these scenarios.
- Do not style `<h>` elements (used for SEO)

Warnings and areas of caution:

- Avoid Grid systems (especially with `col-sm-2` type classes).
- Don't use really long, multi-word class names.
- Avoid Generic styles in _global "scope"_,
    - Bad: `.minor {}`, `.important {}`
    - Good: `.field.minor { }`, `.message.important {}`
- Do not create stylesheets that apply styles to _multiple_ contexts that are not part of the "theme".

Styleguides
-----------

A styleguide is a basic web page with the following:

- Common HTML elements used on a website
- Markup for common domain specific components
- Site stylesheets (see #2 above)
- Annotations that help developers find and use the appropiate styles
