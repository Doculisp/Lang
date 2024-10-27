<!-- (dl (section-meta Get)) -->

The `get` block is an unusual block as its parameter is an id representing dynamic text that will be put into its place.

<!-- (dl (# The Reference Block)) -->

The id in the get must be one of the ids given in a reference block. It will be replaced with the relative path to the target file.

<!-- (dl (# Example)) -->

```markdown
<!--
(dl
    (section-main
        (title Some title)
        (reference
            (file
                (id contribLink)
                (source ./contrib/_main.dlisp)
                (target ../../contrib.md)
            )
        )
    )
)
-->

How to [contribute](<!-- (dl (get contribLink)) -->)

```