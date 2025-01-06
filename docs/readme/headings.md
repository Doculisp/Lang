<!-- (dl
(section-meta
    (title Dynamic Headings)
    (id headings)
)
) -->

Sometimes you want to create structure aware headings such that only heading of lesser importance are under your title. this is accomplished by the `(#` block, or dynamic heading block.

The dynamic heading block works differently then other blocks. The number of `#` signs determine how far it is beneath the current sub/section heading.

Example

```markdown
<!--
(dl
    (section-meta
        (title Maths an intro)
        (include
            (section ./add.md)
            (section ./subtract.md)
            (section ./muliply.md)
            (section ./divide.md)
        )
    )
)
-->

<!-- (dl (# Summary)) -->

A cool summary of maths.

<!-- (dl (## Reasons For Document)) -->

An explanation why to have the document.


<!-- (dl (content (toc unlabled))) -->
```

If this example was the top level document, then the title of the document, Heading 1, would be "Maths an intro". "Summary" would then be created as a Heading 2, and  "Reasons For Document" as Heading 3.

However if this document represented a subsection directly under the Title, then "Maths an intro" would be Heading 2, "Summary" heading 3, and "Reasons For Document" would be Heading 4.

<!-- (dl (#head-ids Ids)) -->

You can add an ID to a heading.

**THIS IS NOT USED YET** and is reserved for future use.

the id follows the hash-mark (`#`).

<!-- (dl (##head-ids-restrictions Restrictions)) -->

The id must meet the following restrictions:

* It must be lowercase.
* It must not contain any symbols other then underscore `_` or hyphen `-`.

<!-- (dl (##head-ids-example Example)) -->

```doculisp
<!-- info.md -->
<!-- (dl (#heading-id Information About Heading Ids)) -->

Some text here.
```

<!-- (dl (#head-max Max Heading Depth)) -->

Currently, the maximum heading depth recognized by Markdown is H6. However Doculisp will not restrict you to that depth. If the total depth is more then H6 you may get unexpected results.