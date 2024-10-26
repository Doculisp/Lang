<!--
(dl
    (section-meta
        (title Title \(required\))
    )
)
-->

This is required, however it has two ways of being provided. The simple way, as a parameter to `section-meta`, or as a block if other blocks are also provided.

<!-- (dl (# Simple Way)) -->

The simple way is to provide the title as a parameter to the `section-meta` block.

```doculisp
(section-meta Doculisp a Short Description)
```

<!-- (dl (# Structured Way)) -->

If the `section-meta` block has any other sub blocks, then it is required that it also contains a `title` block. The title is followed by a title that ends at a `)`. Every thing following the white space after the word title and until a new line or a close parenthesis is the title.

```doculisp
(section-meta
    (title Doculisp How To)
    (subtitle A Short Description)
    (include
        (Section ./design.md)
    )
)
```