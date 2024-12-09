# Upgrade Guide

## Tailwind 3.4 to 4.0

Together with the Tailwind migration in Peak, Statamic got a major update in how it handles starter kits. Because of this, but mostly because of my horrible Git hygienem, the PR got a bit messy.

If you want to upgrade existing Peak projects to Tailwind 4 and Vite 6, make sure to take care of the following:

* Run `npm install tailwindcss@next @tailwindcss/vite@next`
* Remove the packages: `autoprefixer`, and `postcss-import`. Similar functionality is now ships with Tailwind.
* Update your `postcss.config.js` to replace `postcss-import`, `tailwindcss` and `autoprefixer` with just: `'@tailwindcss/postcss'`.
* Update your `resources/css/site.css` to [this](https://github.com/studio1902/statamic-peak/blob/main/export/resources/css/site.css) and use your own configuration from your `tailwind.config.site.js`.
* Move over any CSS you've added from `resources/css/tailwind.css` to `resources/css.site.css` and trash the original file.
* Create `resources/css/peak.css` with [this content](https://github.com/studio1902/statamic-peak/blob/main/export/resources/css/peak.css).
* Create `resources/css/typography.css` with [this content](https://github.com/studio1902/statamic-peak/blob/main/export/resources/css/typography.css) and use your own configuration from your `tailwind.config.typography.js`.
* Create `resources/js/tailwind.peak.js` with [this content](https://github.com/studio1902/statamic-peak/blob/main/export/resources/js/tailwind.peak.js).
* Delete `tailwind.config.js`, `tailwind.config.peak.js`, `tailwind.config.site.js` and `tailwind.config.typography.js`.
* Delete `resources/css/tailwind.css`.
* Rename any of the following utilities you might have used in your project: https://tailwindcss.com/docs/v4-beta#default-shadow-scale-changes


## Statamic 3.4 to 4.0
With the Release of Peak 12 and Statamic 4.0 the Peak addons got updated to the following major versions:

* Commands 2.0
* SEO 2.0
* Browser Appearance 2.0
* Tools 3.0

If you intent to install these you're going to have to do some manual changes to your blueprints to support sections and import the correct fieldsets from the addons. The changes are listed in these [Release Notes](https://github.com/studio1902/statamic-peak/releases/tag/v12.0). Only [this PR](https://github.com/studio1902/statamic-peak/pull/314) is required. Other updates are optional.
