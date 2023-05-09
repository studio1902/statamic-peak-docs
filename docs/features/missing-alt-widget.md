# Missing Alt Widget

The Peak Tools addon contains a widget to display images in asset containers that miss alt text. This helps your clients awareness on the importance of a11y. By default this widget will be added to your dashboard. If you want to add widgets for other asset containers, add the following to the `widgets` array in `config/statamic/cp.php`:

```php
[
    'type' => 'images_missing_alt',
    'container' => 'assets', // The handle of your asset container.
    'limit' => 5, // The maximum amount of images without alt text you want displayed at once.
    'width' => 50
],
```

The Blade view that is used to render this widget on your dashboard is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
