<!-- (dl
(section-meta
    (title Dynamic Document Linking)
    (id doc-link)
)
) -->

You can convert ids to link text that will link to the file and appropriate header if used from outside of the file, and become a header link only when used within in the file.

```doculisp
(get-path id)
```

This will return the path needed to get to the document / header combination. This would best be used in a link as follows:

```md
[Main Document](<!-- (dl (get-path main)) -->)
```

In the above example you will have link to correct document and the correct heading.