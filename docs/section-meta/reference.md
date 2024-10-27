<!-- (dl (section-meta Reference)) -->

The `reference` block indicates external documents that are both to be compiled and are linked to from within the section or its subsections. The reference block has at least one `file` sub-block.

<!-- (dl (# File Sub-Block)) -->

The `file` sub-block contains three sub-blocks. An `id` block, a `source` block, and a `target` block.

The `id` block contains the unique name that can be used to insert the output path into this section or its subsections.

The `source` block contains the path of the source files to be compiled. This path is in reference to the current file.

The `target` block indicates the output file and path. This path is in reference to the current file.

<!-- (dl (# Reference Example)) -->

```doculisp
(section-meta
    (title References)
    (reference
        (file 
            (id contribDoc)
            (source ./contrib/_main)
            (target ../../contrib.md)
        )
    )
)
```
