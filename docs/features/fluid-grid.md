# Fluid grid

The custom `fluid-grid` component is used to layout individual page builder blocks and can be used together with the [Stack](/features/stacks.md) utilities. Stacks take care of vertical spacing and this new fluid grid handles horizontal spacing on a block level. The component is defined in `tailwind.config.peak.js`.

The fluid grid is a horizontal block that spans from browser edge to browser edge to give you the ability to create full bleed containers or something in between. For example an image that has to start somewhere within the middle your content area but extends to the browser edge. The center of the grid is your content area divided into 12 columns.

The CSS behind the fluid grid looks like this:

```css
.fluid-grid {
    --col-gap: clamp(1rem, 3vw, 4rem);
    --content-max-width: theme('screens.xl');

    --padding-left: clamp(calc(env(safe-area-inset-left, 0rem) + 1rem), 2vw, calc(env(safe-area-inset-left, 0rem) + 2rem));
    --padding-right: clamp(calc(env(safe-area-inset-right, 0rem) + 1rem), 2vw, calc(env(safe-area-inset-right, 0rem) + 2rem));
    --col-width: calc((min(calc(100% - var(--padding-left) - var(--padding-right) - 2 * var(--col-gap)), var(--content-max-width)) - 11 * var(--col-gap)) / 12);
    --side-width: minmax(0, 1fr);

    display: grid;
    column-gap: var(--col-gap);
    grid-template-columns:
      [full-start] var(--side-width)
      [content-start col-1] var(--col-width)
      [col-2] var(--col-width)
      [col-3] var(--col-width)
      [col-4] var(--col-width)
      [col-5] var(--col-width)
      [col-6] var(--col-width)
      [col-7] var(--col-width)
      [col-8] var(--col-width)
      [col-9] var(--col-width)
      [col-10] var(--col-width)
      [col-11] var(--col-width)
      [col-12] var(--col-width) [content-end]
      var(--side-width) [full-end];
}
```

This is the grid it creates:
```
| full-start | content-start col-1 | col-2 | col-3 | col-4 | col-5 | col-6 | col-7 | col-8 | col-9 | col-10 | col-11 | col-12 content-end | full-end |
```

You can alter the custom properties `--col-gap` and `--max-width` to adapt the grid to your needs.

## Placing items on the grid
You can use custom utilities or arbitrary values to place items on the grid. E.g: `md:col-start-[col-3] md:col-span-8` to let an item start on column 3 and span for 8 columns.

> Make sure to check the installable page builder blocks from the [Commands Addon](getting-started/commands.html#install-page-builder-block) for inspiration.

The following utilities are also present to use for spanning items on the grid. By default those are used on Bard sets like: text, image, table, video and pull quote and they can be customised on a per-site basis.

```css
.span-content .span-md, .span-lg, .span-xl {
  grid-column: content
}
.span-full {
  grid-column: full
}
@media screen('md') {
  .span-md {
    grid-column: col 3 / span 8
  }
  .span-lg {
    grid-column: col 2 / span 10
  }
  .span-xl {
    grid-column: col 1 / span 12
  }
}
@media screen('lg') {
  .span-md {
    grid-column: col 4 / span 6
  }
  .span-lg {
    grid-column: col 3 / span 8
  }
  .span-xl {
    grid-column: col 2 / span 10
  }
}
```

## Subgrids

The Custom Property `col-gap` is added to the Tailwind spacing scale so you can use the gap size of fluid grid. For example when you want to nest grids but don't want to rely on the subgrid spec yet:

```html
<section class="fluid-grid">
    <div class="span-content grid grid-cols-12 gap-fluid-grid-gap">
        // Children will fall on a new 12 column element that aligns with the parent fluid grid.
    </div>
</section>
```

With subgrid you could use:

```html
<section class="fluid-grid">
    <div class="span-content grid grid-cols-subgrid">
        // Children will fall on a new 12 column element that aligns with the parent fluid grid using subgrid.
    </div>
</section>
```

> You can use the `fluid-grid-gap` everywhere. For example with stacks: `stack-fluid-grid-gap` or margins: `mb-fluid-grid-gap`.
