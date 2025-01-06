# Tailwind CSS configuration

Peak comes with a `resources/css/site.css` which contains the CSS based configurtion for Tailwind. This file would typically include all custom styles and config for the project you're currently working on. It also imports multiple Tailwind CSS config files each responsible for various parts of your website. Next to the default config, it uses the following configuration files:

1. `resources/css/typography.css`: the Tailwind CSS typography configuration for customizing the `prose` class.
2. `resources/css/typography.css`: all Peak's configuration, utilities and components and importing:
3. `resources/js/tailwind.peak.js`: Peak utilities that currently can't be defined in CSS.

All configuration files are fully documented. Read the Tailwind CSS docs on [theme configuration](https://tailwindcss.com/docs/theme/) for more information.

Read up on the [Tailwind CSS Forms](https://github.com/tailwindlabs/tailwindcss-forms) and [Tailwind CSS Typography](https://github.com/tailwindlabs/tailwindcss-typography) plugins. They're easy to customize and the config file for typography already includes some basic customization so your theme colors are automatically applied. The plugins are easy to remove if you don't want to use them.
