<!--
(dl
    (section-meta 
        (title Default Target File)
    )
)
-->

You can set a default target or output file name (with path) from within the `section-meta` block. This is done with the `target` command.

Example:

```markdown
<!--
(dl
    (section-meta
        (title An example)
        (target ../README.md)
    )
)
-->
```