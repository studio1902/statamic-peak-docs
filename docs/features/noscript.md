# Noscript

The noscript partial disables the hiding of x-cloak elements when a user doesn't have Javascript enabled so content is still accessible.

It also adds text to inform the user that Javascript is required to make parts of the website function properly.

> Note: the strings used in the partial are translatable and can be edited in `resources/lang/en/site.php`.

The view that is being used to render this is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
