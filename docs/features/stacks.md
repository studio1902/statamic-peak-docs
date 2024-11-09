# Stacks

To position page builder blocks Peak uses stacks. These are custom utilities defined in `tailwind.config.peak.js` that are similar to space-y-* but with a few superpowers. Basically items that are preceded by a sibling get a margin top. You can override this on a child (block) level by using:

* `no-space-t`: removes top margin.
* `no-space-b`: removes top margin from next sibling.
* `no-space-y`: removes top margin and top margin from next sibling.

In addition to that you can also use `stack-space-*` utilities to increase or decrease the top margin on a child level.

This is how you use them.

```html
<main class="stack-16">
  <section></section>
  <section class="no-space-y"></section>
  <section></section>
  <section class="stack-space-8"></section>
</main>
```
It would compile to the following CSS.

```css
.stack-16 > * {
    --stack-space: 4rem/* 64px */;
}
.stack-16 > *:not(.no-space-y, .no-space-b) + *:not(.no-space-y, .no-space-t) {
    margin-block-start: var(--stack-space, 4rem/* 64px */);
}
.stack-space-8 {
    --stack-space: 2rem/* 32px */;
}
```

You can also use arbitrary values and modifiers like `stack-[5px] md:stack-16`. These utilities can of course also be used outside of page builder blocks.

Read more on stacks in [this post](https://1902.studio/journal/stack-utilities-to-space-page-builder-blocks).

## Collapse
If two siblings with the class `stack-space-collapse` follow each other in a stack, their margins will collapse.
