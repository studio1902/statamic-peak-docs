# Tailwind CSS configuration

Peak comes with a `resources/css/theme.css` which contains the CSS based configuration for Tailwind. This file would typically include all custom styles and config for the project you're currently working on. It also imports multiple Tailwind CSS config files each responsible for various parts of your website. Next to the default config, it uses the following configuration files:

1. `resources/css/typography.css`: the site typography and `prose` class configuration.
2. `resources/css/peak.css`: all Peak's configuration, utilities and components and importing:
3. `resources/js/tailwind.peak.js`: Peak utilities that currently can't be defined in CSS.

All configuration files are fully documented. Read the Tailwind CSS docs on [theme configuration](https://tailwindcss.com/docs/theme/) for more information.

Read up on the [Tailwind CSS Forms](https://github.com/tailwindlabs/tailwindcss-forms) plugin. The plugin is easy to remove if you don't want to use it.

## Utilities

There's a `resources/css/utilities.css` file for custom utilities you may need. The file ships with `grid-cols-fluid` and `text-box-trim-*` utilities.

### grid-cols-fluid

Use this utility to create responsive grid columns without having to rely on breakpoints. The minimum column width is `350px` but you can alter this by configuring the custom property on your element: `style="--min-column-width: 250px"`.

### text-box-trim

Use the `text-box-trim-start`, `text-box-trim-end` and `text-box-trim-both` utilities to trim the textboxes if you need pixel perfect vertical typography alignment in browsers that support it.
