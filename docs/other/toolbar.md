# Toolbar

The Peak Tools addon adds a hidden toolbar to the bottom right corner of your screen. It becomes visible when you hover it and it displays the current Tailwind CSS breakpoint (when your env is `local`). It also has an edit button when you're logged in. The toolbar can be permantly fixed to your window by toggling the button.

The view that is being used to render this toolbar is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```
