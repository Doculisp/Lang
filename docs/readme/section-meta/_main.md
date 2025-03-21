<!--
(dl
    (section-meta
        (title Section Meta Block)
        (author jason-kerney)
        (id section-meta)
        (include
            (Section ./authors.md)
            (Section ./include.md)
        )
    )
)
-->

The `section-meta` block is a crucial part of the Doculisp DSL. It provides metadata for a section, including the title, author, and included subsections. This block helps organize and structure the documentation by breaking it into manageable parts.

<!-- (dl (#section-meta-components Components of the `section-meta` Block)) -->

1. Title (title):
    * Required
    * Specifies the title of the section.
    * Example: (title Section Meta Block)
2. Ref-Link (ref-link):
    * Optional
    * Allows you to specify a different link to use in the table of contents.
    * Useful for handling characters in the title that markdown does not include in its section headers.
3. Subtitle (subtitle):
    * Optional
    * Creates a heading that is two levels of heading less than the title directly beneath the title.
4. Author (author):
    * Optional
    * Specifies the author(s) of the section.
    * Can be included multiple times for multiple authors.
    * Example: (author jason-kerney)
5. Include (include):
    * If it is used there must be a `content` block.
    * Lists the files to be included in the section.
    * Each file is specified with a custom block name followed by the file path.
6. ID (id):
    * Optional
    * Specifies a unique identifier for the section.
    * Example: (id section-meta)
    * For more information on ids see [Path Ids](<!-- (dl (get-path path-ids)) -->)
    * The `id` block provides a unique identifier for the section, facilitating easy linking and navigation. See [get-path](<!-- (dl (get-path doc-link)) -->) for more details.
7. Comment (*):
    * Optional
    * The comment block breaks the rule slightly. The asterisk character is a special character that causes all atoms that start with it to be treated as a comment, and all parameters and sub-blocks to be ignored.

<!-- (dl (#section-meta-examples Section-Meta Examples)) -->
<!-- (dl (##title-example Title Example)) -->

```doculisp
(section-meta
    (title Section Meta Block)
)
```

<!-- (dl (##section-meta-link-ex Ref-Link Example)) -->

```doculisp
(section-meta
    (title Doculisp is awesome ✨)
    (ref-link doculisp_is_awesome_)
)
```

<!-- (dl (#subtitle-example Subtitle Example)) -->

```doculisp
(section-meta
    (title Section Meta Block)
    (subtitle A Detailed Explanation)
)
```

<!-- (dl (#author-example Author Example)) -->

```doculisp
(section-meta
    (title Section Meta Block)
    (author jason-kerney)
    (author another-author)
)
```

<!-- (dl (#include-example Include Example)) -->

```doculisp
(section-meta
    (title Include Sub-Block)
    (include
        (Section ./title.md)
        (Section ./ref-link.md)
        (Section ./subtitle.md)
        (Section ./include.md)
        (*Section ./id.md) ; Commented out
        (Section ./authors.md)
        (Section ./comments.md)
    )
)
```

<!-- (dl (#id-example ID Example)) -->
(section-meta
    (title Doculisp: A Short Description)
    (id doculisp-short-description)
)

<!-- (dl (#comment-example Comment Example)) -->

```doculisp
(*section-meta
    (title Doculisp)
    (include
        (Section ./doculisp.md)
        (Section ./section-meta.md)
        (Section ./content.md)
        (*section ./comment.md)
    )
)
```

<!-- ((dl (content))) -->

<!-- (dl (#section-meta-summary Section-Meta Summary)) -->

The section-meta block is essential for organizing and structuring documentation in Doculisp. It allows you to define the title, author, included files, and a unique identifier for each section, making it easier to manage and update documentation.