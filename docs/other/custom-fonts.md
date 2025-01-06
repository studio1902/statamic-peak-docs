# Custom fonts

Custom fonts don't really have much to do with Peak, but you often need them setup. This is how.

## Convert your font files
If you don't have `.woff` and `.woff2` font files you can convert your licensed or free fonts easily on [fontsquirrel.com](https://www.fontsquirrel.com/tools/webfont-generator). For modern browsers (those that support grid) you really only need `.woff2` files. Including both won't hurt though. The browser only downloads the files it uses.

## Include your fonts
You can place your font files somewhere in your resources folder. For example in `resources/fonts`. This directory doesn't exist by default.

Now it's time to add the `@font-face` rules to your CSS build. You can put it the Tailwind CSS base layer in `resources/css/custom.css`. Let's say we have one font family with two weights, both in italics.

```css
@layer base {
    @font-face {
        font-family: 'awesome';
        src: url('/resources/fonts/awesome-regular.woff2') format('woff2'),
            url('/resources/fonts/awesome-regular.woff') format('woff');
        font-weight: 400;
        font-style: normal;
        font-display: swap;
    }

    @font-face {
        font-family: 'awesome';
        src: url('/resources/fonts/awesome-regular-italic.woff2') format('woff2'),
            url('/resources/fonts/awesome-regular-italic.woff') format('woff');
        font-weight: 400;
        font-style: italic;
        font-display: swap;
    }

    @font-face {
        font-family: 'awesome';
        src: url('/resources/fonts/awesome-bold.woff2') format('woff2'),
            url('/resources/fonts/awesome-bold.woff') format('woff');
        font-weight: 700;
        font-style: normal;
        font-display: swap;
    }

    @font-face {
        font-family: 'awesome';
        src: url('/resources/fonts/awesome-bold-italic.woff2') format('woff2'),
            url('/resources/fonts/awesome-bold-italic.woff') format('woff');
        font-weight: 700;
        font-style: italic;
        font-display: swap;
    }
}
```

Vite will serve those fonts when running `npm run dev`. When you run `npm run build` it will copy them over to the build folder and version them.

> Note that all font-family share the same name. It's just the properties (weight and style) that change according to the font file being used.

## Configure Tailwind CSS
The default Peak Tailwind CSS configuration assumes you might want to use custom fonts so it's easier to implement them. Let's say our font `awesome` is a sans-serif font and it's the only font we're currently using. The relevant part of the configuration in `resources/css/site.css` would look like this:

```css
--font-sans: Awesome, ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
```

## Using the fonts
In your templates you can now use `font-sans` (with a fallback stack), `font-normal`, `font-bold`, `italic` and `not-italic`.
