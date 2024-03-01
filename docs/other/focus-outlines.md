# Focus outlines

The default focus styles are defined in `tailwind.config.site.js`. You can change the following custom properties to alter focus appearance:

* --focus-outline-width: 2px
* --focus-outline-offset: 3px
* --focus-outline-color: currentColor
* --focus-outline-style: dotted
* --focus-form-outline-width: 3px
* --focus-form-outline-offset: 0
* --focus-form-outline-color: "theme(colors.primary.DEFAULT / .5)"
* --focus-form-outline-style: solid

If you want to override the outline colour on a per component basis you can set a colour by adding an `outline-*` class.

When your browser supports `focus-visible`, Peak will automatically disable the outlines upon focus and show then upon focus-visible.
