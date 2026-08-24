# Typography

Peak uses fluid typography based on [Utopia](https://utopia.fyi). They are mapped to Tailwind text sizing utilities in `resources/css/theme.css`. Your typography configuration can be configured in `resources/css/typography.css`. This file contains the the styling for all base typography elements and the `prose` class for long form content.

## Prose content
You can add the `prose` class to any element to treat it's children as prose content for vertical flow, rhythm and specific styling. This especially useful on content coming from Bard fields.

You can use `prose-invert`, `prose-sm`, `prose-lg` and `prose-xl` as modifiers to respectively invert the styling, make content smaller and to make content bigger.
