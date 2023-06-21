# Social images generation

> You need to manually enable this feature.

Peak can generate your social sharing images (OG and Twitter) and add them to your entries. To use this feature you need to [install Browsershot](https://github.com/spatie/browsershot) and its dependencies. A big thanks to [Spatie](http://spatie.be) and [Puppeteer](https://github.com/puppeteer/puppeteer/)!

## Installation and configuration
On your development machine you can do this by running the following commands:

```bash
composer require spatie/browsershot
npm install puppeteer --global
```

Once you've installed the required software you can enable the functionality in the SEO globals -> Social Sharing. Make sure to flick on the switch and select each collection for which you want to enable auto generated social images.

Publish the Peak SEO addon views:
```bash
php artisan vendor:publish --tag="statamic-peak-seo-views"
```
If you don't plan on making any other changes to the SEO integration you only have to keep `resources/views/vendor/statamic-peak-seo/components/_social_image.antlers.html` and edit that file to determine how the images should look. You can go wild with Antlers and Tailwind CSS and add any field you'd like to use. If you want to preview the images in your browser visit `http://yoursite.test/social-images/{id}`.

## Redis as queue driver
The actual generation of the images is a job, so it's queued when you use Redis. [Read more on how to properly configure Redis](/other/redis-queue.html).

## Generate the images
Once you've opted in the collections you want this available for you can select the entries you want to generate images for in the collection view.

## Listable columns
Note that you could opt to toggle the `Social image` and `Twitter image` fields listable in the collections list view. That way you can or your client an easily scan collections for missing images.
