<!-- (dl (section-meta Section Id)) -->

Id is an optional block. It allows you to set an id for the section.

These ids can be used to create dynamic links to the section from within the document or from other compiled documents. [Example how to do that here.](<!-- (dl (get-path doc-link)) -->)

<!-- (dl (# Restrictions)) -->

The id block must meet the following restrictions:

* It must be lowercase.
* It must not contain any symbols other then underscore `_` or hyphen `-`.

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