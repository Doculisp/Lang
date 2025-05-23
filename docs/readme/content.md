<!-- (dl
(section-meta
    (title Content Block)
    (id content)
)
) -->

The content block signifies where to insert the compiled included documents. This block has only one optional sub-block.

<!-- (dl (#toc Table of Contents)) -->

The only sub-block to the content block is the table of contents. This will cause a linked table of contents to appear for the section at its location.

<!-- (dl (##toc-basic Simple Usage)) -->

The simple usage of the table of contents is `(toc)` may have an optional bullet style as a parameter. The default style is `labeled`.

```doculisp
(content (toc numbered))
```

<!-- (dl (##toc-detailed Complex Usage)) -->

The complex usage of table of contents allows you to specify an optional `label` that will appear as a heading directly above the table of contents. You can all so specify an optional `style` which will be a bullet style.

```doculisp
(content
    (toc
        (label Table of Contents)
        (style numbered)
    )
)
```

The default label will be not to include a label, and the default style is `labeled`

<!-- (dl (#toc-bullet Bullet Style)) -->


The bullet style argument can have one of the following values:

* no-table
* unlabeled
* labeled
* numbered
* numbered-labeled
* bulleted
* bulleted-labeled

Any of the options with `labled` on it will use the name of the subsection. 

```doculisp
(dl
    (file-meta
        (title Some Document)
        (include
            (chapter ./first) (*The title of this document is "An introduction")
        )
    )

    (content (toc bulleted-labeled))
)
```

The table of contents would contain a line that looked like:

```markdown
* Chapter: [An Introduction](#an-introduction)
```
