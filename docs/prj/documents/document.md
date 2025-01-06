<!--
(dl
    (section-meta
        (title The Document Block)
        (id document)
    )
)
-->

The `document` block has the information needed to build a single document. This represents the input usually passed to the compiler, plus some optional additional information.

<!-- (dl (#doc-source The Source Block)) -->

The `source` block contains the path to the source file to compile. This can be either have a `.md` extension or the `.dlisp` extension. This is a required block.

<!-- (dl (#doc-output The Output Block)) -->

The `output` block contains the path to the resulting markdown file. This must have the `.md` extension. This is a required block.

<!-- (dl (#doc-example A simple example)) -->

```doculisp
(* myproject.dlprog)
(documents
    (document
        (source ./readme/readme.md)
        (output ../README.md)
    )
    (document
        (output ../contrib.md)
        (source ./contrib/how_to.md)
    )
)
```

<!-- (dl (#doc-id The Document Identifier Block)) -->

The document identifier block is a very different kind of block. It is an optional block that surrounds the `source` and `output` blocks. It can have any character combination, without spaces, as its command name. It works similar to the subsection block in this regard. Its purpose is to give a simple identifier to the document. Every identifier name must be unique within the project file.

If this block is contained within the `document` block then it is the only block that is a child of the `documents` block.

The document identifier block is _**currently is not used.**_ Though it is reserved for future use.

<!-- (dl (##doc-id-restrictions Restrictions)) -->

The document identifier must meet the following restrictions:

* Document identifier must be lowercase.
* Document identifier must not contain any symbols other then underscore `_` or hyphen `-`.

<!-- (dl (##doc-id-example Document Identifier Example)) -->

```doculisp
(* myproject.dlprog)
(documents
    (document
        (readme
            (source ./readme/readme.md)
            (output ../README.md)
        )
    )
    (document
        (contrib
            (output ../contrib.md)
            (source ./contrib/how_to.md)
        )
    )
)
```