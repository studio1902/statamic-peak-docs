# Forms

Peak renders forms and mail templates dynamically so you can add as many forms as you'd like, just by creating them in the CP. Peak ships with a default basic contact form you can edit using the following files:

* `resources/forms/contact.yaml` The contact form configuration.
* `resources/blueprints/forms/contact.yaml` The forms blueprint defining all the fields.
* `resources/views/page_builder/_form.antlers.html` The forms template file.
* `resources/views/email/form_owner.html` The forms email template that goes out to the site owner. The `_text.html` version contains the text template.
* `resources/views/email/form_sender.html` The forms email template that goes out to the sender of the form. The `_text.html` version contains the text template.
* `resources/lang/en.json`. Strings file containing the the form's localizable field labels.
* `resources/lang/en/strings.php` Strings file containing the e-mail's localizable body contents and logo image location.

The default contact form has a required consent field. The field handle is `consent`. Due to restraints the form template contains a conditional that depends on this specific handle name. Don't use it for other form fields.

The forms sending is done with fetch and uses Alpine to display the various notifications.

> Note: Peak dynamically fetches a CSRF token, so you can use forms with [Static File Caching](https://statamic.dev/static-caching) enabled. You can use this logic by using `window.getToken()` in your (Alpine) JavaScript to fetch your own token.

The form handler view that is included in your form partial is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```

## Conditional logic
The Peak form component and published field views support the AlpineJS driven [conditional fields feature](https://statamic.dev/tags/form-create#conditional-fields) added in Statamic 3.3

## Sections
The Peak form component and published field views support the new sections introduced in Statamic 4.0.
