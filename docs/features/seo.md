# SEO

Peak includes full professional SEO support. It's easy to expand on since it's all built with native fields and templating. If you want to make any site particular changes publish the SEO views and/or fieldsets by running:

```bash
php artisan vendor:publish --tag="statamic-peak-seo-fieldsets"
php artisan vendor:publish --tag="statamic-peak-seo-views"
```

And edit the files you want to make changes to in `resources/views/vendor/statamic-peak-seo/` or `resources/fieldsets/vendor/statamic-peak-seo/`. You can trash all the files you won't make changes to and have them automatically updated in the future.

## SEO features
* Page title.
* Website title and seperator.
* Meta description (and set global fallback options).
* Canonical URL.
* Open Graph data and image.
* Default Open Graph image.
* Twitter card and image.
* Default Twitter card image.
* Auto generated sitemaps.xml for a listing of multisitemaps.
* Auto generated /{locale}/sitemap.xml for per site sitemaps.
* Customize the sitemap: which collections are included and per entry frequency and priority settings.
* No-index for entries, also excludes from sitemap.
* JSON-ld schema objects.
* Hreflang tags automatically generated (for selected site locales).
* Knowledge graph data (organization, person or custom).
* JSON-ld breadcrumbs.
* Trackers: Google Analytics, Google Tag Manager, Site Verification, Fathom or Cloudflare Web Analytics.
* Consent Banner.

> Note: by default only `superusers` and the `marketeer` role get access to the SEO global configuration.

## GDPR Compliant Consent Banner

When you use Google Analytics or Google Tag Manager you can enable the consent banner to (somewhat) comply with GPDR. The consent banner uses Google's Consent API v2 so you might need to properly set this up in your GTM/Analytics settings. Users can specify the type of consent they give. When consent is given, gtag/gtm will be updated with the new consent configuration.

The consent banner only blocks Google scripts since it uses the consent API, so if you really want to be a marketing-script-abuser and bug your users with a Facebook pixel or Hotjar, you can be (somewhat) GDPR compliant by running all those scripts through GTM.

When consent has been given, a link will be added to the footer for users to reset their consent.

> Note: tracking and consent by default only work on the `production` environment. However you can tweak this from the `SEO` global.

## Revoking consent

Users can revoke/change their consent by clicking on the link in the footer. The Consent Banner will reappear and consent will be automatically revoked.

You can also configure a revoke consent date in the Consent Banner configuration which will revoke all users consent before this date and time. Use this when you changed consent settings, added scripts or changed trackers, or when your privacy policy has changed. The Consent Banner will reappear. This setting expects a time in the timezone configured for your application.

## Scripts and consent

If you don't use any form of Google tracking: great job! You can still load in scripts. Set the `Tracker type` to `Scripts` and add your scripts by adding script fragments. The scripts will be loaded in the document head on page load.

When you turn on the consent banner they will be injected using Javascript only when the user has given consent. They will be removed from the DOM as soon as a user revokes their consent.

## Embeds and consent

If you enable embeds in the Consent Banner configuration, any YouTube video embeds added via the Video set in the Article (Bard) partial, will automatically be disabled until users give consent. You can add any partial behind a consent gate by wrapping your partials content into the `partial:components/consent_gate` partial. See `resources/views/components/_video.antlers.html` and `resources/views/components/_consent_gate.antlers.html` for an example.

## Local store

All consent types and script are saved in the visitors localStorage. In order for any changes you make to be seen by folks who already visited your site and possibly have given consent, you have to revoke the users consent by setting a revoke date in the banner configuration panel. This make sure the localStorage for users gets cleared and the banner reappears.
