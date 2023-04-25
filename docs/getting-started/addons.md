# Addons

Peak ships with four addons that contain parts of its logic and tooling. The reason for seperating this logic into addons is that you can update them more easily without having to manually edit in changes into your project.

Each addon has fieldsets, views or stubs you can publish to make changes needed for your project. Published files can be found in `resources/fieldsets/vendor`, `resources/stubs/vendor` or `resources/views/vendor`.

The files in those folders take precedence over the files in the addons. So in general it would be wise to only keep files that you need to make changes to and trash published files that don't need edits.

## Browser Appearance
The Browser Apperance addon contains contains the browser appearance fieldsets, partials and listener that are being called in by the Browser Appearance Global. In here you can generate favicons, configure browser behaviour and set browser toolbar colors.

Run the following commands to publish fieldsets and views.
```bash
php artisan vendor:publish --tag="statamic-peak-browser-appearance-fieldsets"
php artisan vendor:publish --tag="statamic-peak-browser-appearance-views"
```

## Commands
The Commands addon contains the various [Peak CLI commands](/getting-started/commands.html) that help speed up development. Make sure to read up on them before starting your project.

Run the following commands to publish the addons stubs.
```bash
php artisan vendor:publish --tag="statamic-peak-commands-stubs"
```

## SEO
The SEO addon contains all SEO fieldsets and partials. It also contains all logic and templates used for generating OG images.

Run the following commands to publish fieldsets and views.
```bash
php artisan vendor:publish --tag="statamic-peak-seo-fieldsets"
php artisan vendor:publish --tag="statamic-peak-seo-views"
```

## Tools
The Tools addon contains various features like the CSRF token logic, picture partial, the noscript partial, the pagination partial, the toolbar and the missing alt text widget.

Run the following commands to publish views.
```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
