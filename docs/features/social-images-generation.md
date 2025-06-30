# Social images generation

> You need to manually enable this feature.

Peak can generate your social sharing images (OG) and add them to your entries. This feature uses [Browsershot](https://github.com/spatie/browsershot) and its dependencies. A big thanks to [Spatie](http://spatie.be) and [Puppeteer](https://github.com/puppeteer/puppeteer/)!

## Installation and configuration
Run the following commands (or let the Peak installer handle this for you):

```bash
composer require spatie/browsershot
npm install puppeteer
```

Once you've installed the required software you can enable the functionality in the SEO globals -> Social Sharing. Make sure to flick on the switch and select each collection for which you want to enable auto generated social images.

Publish the Peak SEO addon views:
```bash
php artisan vendor:publish --tag="statamic-peak-seo-views"
```
If you don't plan on making any other changes to the SEO integration you only have to keep `resources/views/vendor/statamic-peak-seo/components/_social_image.antlers.html` and edit that file to determine how the images should look. You can go wild with Antlers and Tailwind CSS and add any field you'd like to use. If you want to preview the images in your browser visit `http://yoursite.test/social-images/{id}`.

### Custom node, npm binaries and Chrome Path

> You can locate your specific paths by running `which node` and `which npm` in your terminal.

Depending on your setup, node or npm might be not directly available to Browsershot. If you need to manually set these binary paths, you can do this by setting `SOCIAL_IMAGE_NODE_BINARY` and `SOCIAL_IMAGE_NPM_BINARY` in your `.env` file.

If you want to use a custom Chrome path you can configure this with the `SOCIAL_IMAGE_CHROME_PATH` variable in your `.env`.

## Customize images

You can customize images using the following environmental variables:
* `SOCIAL_IMAGE_FORMAT`: `jpg` or `png` (default).
* `SOCIAL_IMAGE_RESOLUTION`: `1200x630` (default).
* `SOCIAL_IMAGE_SELECTOR_ID`: `og` (default), the ID referenced in your OG templates. 

## Redis as queue driver

> You can set the queue name by defining `SOCIAL_IMAGE_QUEUE_NAME` in your `.env` file.

The actual generation of the images is a job, so it's queued when you use Redis. [Read more on how to properly configure Redis](/other/redis-queue.html).

## Generate the images
Once you've opted in the collections you want this available for you can select the entries you want to generate images for in the collection view.

## Listable columns
Note that you could opt to toggle the `Social image` fields listable in the collections list view. That way you or your client can  easily scan collections for missing images.
