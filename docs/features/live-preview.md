# Live Preview

Statamic can broadcast an event to your frontend when the client makes edits in Live Preview. Instead of refreshing the browser we can pick up these events. By default, when in Live Preview, Peak adds a bit Javascript that uses Alpine's Morph plugin to intelligently morph changes in the Live Preview window whilst preservering all of Alpine's state. This makes the experience of using Live Preview a lot more user friendly.

Thanks to [Jack Sleight](https://jacksleight.dev/posts/hot-reloading-statamic-s-live-preview-in-a-traditonal-mpa) for sharing this technique.

The view that is included in your layout is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
