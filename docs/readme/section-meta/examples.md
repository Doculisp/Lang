<!-- (dl (section-meta Section-Meta Examples)) -->
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

<!-- (dl (##subtitle-example Subtitle Example)) -->

```doculisp
(section-meta
    (title Section Meta Block)
    (subtitle A Detailed Explanation)
)
```

<!-- (dl (##author-example Author Example)) -->

```doculisp
(section-meta
    (title Section Meta Block)
    (author jason-kerney)
    (author another-author)
)
```

<!-- (dl (##include-example Include Example)) -->

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

<!-- (dl (##id-example ID Example)) -->
(section-meta
    (title Doculisp: A Short Description)
    (id doculisp-short-description)
)

<!-- (dl (##comment-example Comment Example)) -->

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