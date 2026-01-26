# Buttons

The files `resources/fieldsets/buttons.yaml` and `resources/views/components/_buttons.antlers.html` go together. The button fieldset is a set in Bard but can also be called from other fieldsets where you want to include buttons. Just call the buttons partial in your template and one or multiple buttons will be rendered.

## Styling

Button styling is extracted to CSS classes `.button` and `.button-inline` and can be found in `resources/css/buttons.css`. The styling extracted to CSS makes it easier to style various variants you might need in your project.

## Rendering a single button

In some cases you don't want to render dynamic buttons but a button to a specific entry or URL. This is possible using any of the following methods.

Link to the index page the collection `news` is mounted on:
```html
{{ partial:components/button label="All news" link_type="url" url="{mount_url:news}" }}
```

Or link to a single entry:
```html
 {{ partial:components/button label="Read more about this entry" link_type="entry" :entry="entry" }}
```

Or to do fancy Alpine stuff:
```html
{{ partial:components/button }}
    {{ slot:attributes }}
        @click="doSomething()"
    {{ /slot:attributes }}
{{ /partial:components/button }}
```

## Tiggering events

The button fieldset has an `event` field that only shows when you use GTM, GTAG or Fathom as a Tracker. You can enter the name of your event in the field and it will automatically trigger and register when a user clicks your button.
