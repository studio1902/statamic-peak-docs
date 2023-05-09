# Pagination

When you're working with the collection tag and want to use [pagination](https://statamic.dev/tags/collection#pagination), just add the pagination partial using `partial:components/pagination` to automagically add pagination buttons. They're easily editable in  `resources/views/components/_pagination.antlers.html`.

The pagination partial automatically adds linktags to your documents head with `rel="next"` and `rel="prev"`.

You can style the pagination view by feeding the partial tag with classes via the following parameters:

* `class`: Classes for the wrapper element.
* `active_classes`: Classes for links that are active.
* `inactive_classes`: Classes for links that are inactive.
* `location_classes`: Classes for the text between links like: `3 of 5`.

> Note: the strings used in the partial are translatable and can be edited in `resources/lang/en/site.php`.

The view that is being used to render your pagination is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
