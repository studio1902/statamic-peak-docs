# Addons

Peak ships with four addons that contain parts of its logic and tooling. The reason for seperating this logic into addons is that you can update them more easily without having to manually edit in changes into your project.

Each addon has fieldsets, views or stubs you can publish to make changes needed for your project. Published files can be found in `resources/fieldsets/vendor`, `resources/stubs/vendor` or `resources/views/vendor`.

The files in those folders take precedence over the files in the addons. So in general it would be wise to only keep files that you need to make changes to and trash published files that don't need edits.

## Browser Appearance
The Browser Apperance addon contains contains the [browser appearance](/features/browser-appearance.html) fieldsets, partials and listener that are being called in by the Browser Appearance Global. In here you can generate favicons, configure browser behaviour and set browser toolbar colors.

Run the following commands to publish fieldsets and views.
```bash
php artisan vendor:publish --tag="statamic-peak-browser-appearance-fieldsets"
php artisan vendor:publish --tag="statamic-peak-browser-appearance-views"
```

> Note: When using the Eloquent Driver make sure you store blueprints and fieldsets as files and not in the database.

## Commands
The Commands addon contains the various [Peak CLI commands](/getting-started/commands.html) that help speed up development. Make sure to read up on them before starting your project.

Run the following commands to publish the addons stubs.

```bash
php artisan vendor:publish --tag="statamic-peak-commands-stubs"
```

## SEO
The SEO addon contains all [SEO fieldsets and partials](/features/seo.html#seo). It also contains all logic and templates used for [generating OG images](/features/social-images-generation.html) and [redirects](/features/redirects.html).

Run the following commands to publish fieldsets and views.

```bash
php artisan vendor:publish --tag="statamic-peak-seo-fieldsets"
php artisan vendor:publish --tag="statamic-peak-seo-views"
```

> Note: When using the Eloquent Driver make sure you store blueprints and fieldsets as files and not in the database.

## Tools
The Tools addon contains the following features: the [form submission logic](/features/forms.html#forms), [picture partial](/features/images.html#images), [the noscript partial](/features/noscript.html), [the skip to content](/features/skip-to-content.html) partial [the pagination](/features/pagination.html#pagination) partial, [the toolbar](/other/toolbar.html#toolbar), [the missing alt text widget](/features/missing-alt-widget.html) and [live Preview](/features/live-preview.html) enhancements.

Run the following commands to publish views.

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
