<!--
(dl
    (section-meta
        (title Section Meta Block)
        (author jason-kerney)
        (include
            (Section ./title.md)
            (Section ./ref-link.md)
            (Section ./subtitle.md)
            (Section ./include.md)
            (*Section ./id.md)
            (Section ./authors.md)
            (Section ./comments.md)
        )
        (id section-meta)
    )
)
-->

This block is contained directly within the Doculisp main block. It contains information used to build the current secion. This includes things like title, subtitle, and include.

Example

```doculisp
(section-meta
    (title Doculisp a short description)
    (include
        (section ./doculisp.md)
    )
)
```

<!-- (dl (content)) -->
