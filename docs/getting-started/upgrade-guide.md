# Upgrade Guide

## Tailwind 3.4 to 4.0

If you want to upgrade existing Peak projects to Tailwind 4 and Vite 6, make sure to take care of the following:

* Remove the tailwind config preset files from `tailwind.config.js` to prevent the migrator from running into errors.
* Update vite within your `package.json` to `"vite": "^6.0"`, and the Laravel Vite plugin to `"laravel-vite-plugin": "^1.1"`.
* Run `npx @tailwindcss/upgrade@next` and follow all steps.
* Update your `resources/css/site.css` to [this](https://github.com/studio1902/statamic-peak/blob/main/export/resources/css/site.css) and use your own configuration from your `tailwind.config.site.js`.
* Delete `resources/css/tailwind.css` if you weren't using it before.
* Create `resources/css/peak.css` with [this content](https://github.com/studio1902/statamic-peak/blob/main/export/resources/css/peak.css).
* Create `resources/css/typography.css` with [this content](https://github.com/studio1902/statamic-peak/blob/main/export/resources/css/typography.css) and use your own configuration from your `tailwind.config.typography.js`.
* Create `resources/js/tailwind.peak.js` with [this content](https://github.com/studio1902/statamic-peak/blob/main/export/resources/js/tailwind.peak.js).
* Update your `vite.config.js` to [this](https://github.com/studio1902/statamic-peak/blob/main/export/vite.config.js).
* Delete your `postcss.config.js` file.
* Update your `package.json` by removing unused postcss packages. It should look something like [this](https://github.com/studio1902/statamic-peak/blob/main/export/package.json).
* Delete `tailwind.config.js`, `tailwind.config.peak.js`, `tailwind.config.site.js` and `tailwind.config.typography.js`.

## Statamic 3.4 to 4.0
With the Release of Peak 12 and Statamic 4.0 the Peak addons got updated to the following major versions:

* Commands 2.0
* SEO 2.0
* Browser Appearance 2.0
* Tools 3.0

If you plan to install these, you'll need to manually update your blueprints to support sections and import the appropriate fieldsets from the add-ons. The required changes are outlined in these [Release Notes](https://github.com/studio1902/statamic-peak/releases/tag/v12.0). Only [this PR](https://github.com/studio1902/statamic-peak/pull/314) is necessary; all other updates are optional.
