<!-- (dl
(section-meta
    (title Comment Block)
    (id comment)
)
) -->

The comment block is the only block that can be present at all levels within the Doculisp Main Block. The comment is created by adding an astrics `*` just after an open parenthesis and end when the block and all its sub-blocks are closed.

Example:

```markdown
<!--
(dl
    (*section-meta
        (title Doculisp)
        (include
            (Section ./doculisp.md)
            (Section ./section-meta.md)
            (Section ./content.md)
            (Section ./comment.md)
        )
    )
)
-->
```

In this example the `section-meta` block and all of its sub-blocks are commented out. Comments can also be nested. This allows you to uncomment in pieces.

Example:

```markdown
<!--
(dl
    (*section-meta
        (title Doculisp)
        (*include
            (Section ./doculisp.md)
            (Section ./section-meta.md)
            (Section ./content.md)
            (*section ./comment.md)
        )
    )
)
-->
```

<!-- (dl (#comment-nested Nested Comments)) -->

In this example the `section-meta` and all its sub-blocks are commented out. However when you uncomment `section-meta` then the `include` block will be commented out. When you uncomment that block, then the `section ./comment.md` block will be commented out.
