# Forms

Peak Forms live validate and submit using [Laravel Precognition](https://laravel.com/docs/10.x/precognition). The forms are designed around [Form Design Patterns](https://formdesignpatterns.com) (with a few exceptions) and they support the AlpineJS driven [conditional fields feature](https://statamic.dev/tags/form-create#conditional-fields).

## Rendering

Peak renders forms and mail templates dynamically so you can add as many forms as you'd like, just by creating them in the CP. They also support form sections you can create in the form blueprint builder. Peak ships with a default basic contact form you can edit using the following files:

- `resources/forms/contact.yaml` The contact form configuration.
- `resources/blueprints/forms/contact.yaml` The forms blueprint defining all the fields.
- `resources/views/page_builder/_form.antlers.html` The forms template file.
- `resources/views/email/form_owner.html` The forms email template that goes out to the site owner. The `_text.html` version contains the text template.
- `resources/views/email/form_sender.html` The forms email template that goes out to the sender of the form. The `_text.html` version contains the text template.
- `resources/lang/en.json`. Strings file containing the the form's localizable field labels.
- `resources/lang/en/strings.php` Strings file containing the e-mail's localizable body contents and logo image location.

The default contact form has a consent field with its visibility set to `hidden`. This setting hides it from the publish form of stored submissions as well as from the email. Feel free to apply the same to other fields within your blueprint.

## Error handling

According to Form Design Patterns its best to place error labels below the label and above an input field. This makes sense because error labels could be obscured when the user hasn't scrolled down yet. However in the case of Precognition, errors kick in on blur, so we can assume with most certainty that the user will see the error label. Placing them below the form field prevents jumpyness. To make sure users know when they've made mistakes, after submission they will get focus on an error summary.

## Form handler

The form handler view that is included in your form partial is part of the [Tools Addon](/getting-started/addons.html#tools). If you want to make changes to the views from this addon, you can publish them by running:

```bash
php artisan vendor:publish --tag="statamic-peak-tools-views"
```

## Success Hook

You can pass in an argument to the form handler as a success hook. For example: you could use this to trigger a dataLayer event if your site relies on GTM and your marketer wants to track form events.

```
 {{ partial:statamic-peak-tools::snippets/form_handler success_hook="console.log('Hurray!')" }}
```

By design, there is a default success hook in place, which resets the `success` variable after 4.5 seconds, even if you pass a custom success hook. If you want to skip that or override that behaviour, simply pass a success hook with a `return` statement.

```
 {{ partial:statamic-peak-tools::snippets/form_handler success_hook="console.log('Hurray!'); return" }}
```

This will log "Hurray!" into your browser console and skip the default success hook.

## Submit additional data

If you want to submit additional data besides your form fields you can add an `x-data` attribute to the `form:create` tag that will be merged with the actual Alpine data object:

```
{{ form:create :in="form:handle" js="alpine:form" attr:x-ref="form" x-data='@{"field": "value" }' }}
x-data='@{"product_id": "{ block:product:id }" }
```

## Hidden fields

When you want to populate a hidden field with custom data, you can add the following within your `form:create` tag:

```
 <div x-init="form.hidden_field_handle = 'value', form.validate('hidden_field_handle')"></div>
```

This will make sure that your hidden fields gets populated with the data you want and added to the precognition request. 
