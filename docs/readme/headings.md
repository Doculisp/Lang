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
            (Section ./add.md)
            (Section ./subtract.md)
            (Section ./muliply.md)
            (Section ./divide.md)
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

<!-- (dl (#head-max Max Heading Depth)) -->

Currently, the maximum heading depth recognized by Markdown is H6. However Doculisp will not restrict you to that depth. If the total depth is more then H6 you may get unexpected results.