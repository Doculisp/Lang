<!-- (dl
(section-meta
    (title Section Meta Ids)
    (id section-meta-id)
)
) -->

The first place that a path id can be included is within a `section-meta` block. It is added though the use of an `id` block.

<!-- (dl (# Section Id)) -->

The Id block is an optional block. It allows you to set an id for the section.

<!-- (dl (# Example)) -->

```doculisp
<!--
example.md
(dl
(section-meta
    (title An Example of an ID)
    (id my-id)
)
)
-->
```