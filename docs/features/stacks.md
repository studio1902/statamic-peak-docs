# Stacks

To position page builder blocks Peak uses stacks. These are custom utilities defined in `resources/css/peak.css` that are similar to space-y-* but with a few superpowers. Basically items that are preceded by a sibling get a margin top. You can override this on a child (block) level by using:

* `no-space-t`: removes top margin.
* `no-space-b`: removes top margin from next sibling.
* `no-space-y`: removes top margin and top margin from next sibling.
* `flush`: removes the top or bottom padding in the container when this is the first or last item in the page builder.
* `stack-space-collapse`: if two siblings with this class follow each other, their margins will collapse.
* `stack-space-*`: use these utilities to increase or decrease the top margin on a child level.

Read more on stacks in [this post](https://1902.studio/journal/stack-utilities-to-space-page-builder-blocks).
