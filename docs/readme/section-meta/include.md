<!-- (dl (section-meta Include)) -->

The `include` block allows you to break each section into sub-sections that are composed in separate files. This modular approach makes it easier to manage and edit documentation by limiting the scope of work in each file.

Example

```doculisp
(section-meta
    (title Doculisp a short description)
    (include
        (Section ./doculisp.md)
        (Section ./section-meta.md)
    )
)
```


<!-- (dl (# Include's Subsections)) -->

The `include` block is composed of sub-section blocks. These blocks are different then other doculisp blocks. They are custom named blocks. Which means the name of each block is decided by the programmer the same way a variable name is. The format of these blocks is `(` followed by a name followed by whitespace. After the white space is the file path that leads to the document containing the information on how to build the sub-section. Followed again by an optional new line and whitespace. Ending in `)`.

The `include` block is composed of custom named blocks. These blocks are different from other Doculisp blocks as they are named by the programmer, similar to variable names. The biggest difference is these names can be displayed in the table of contents.

The format of these blocks is `(` followed by a name, whitespace, the file path, optional new line and whitespace, and ending with `)`.

You can add a space (` `) to a name by adding a `-` to the name.

Example:

```doculisp
(include
    (Chapter
        ./information/one.md
    )
)
```

This will create a subsection called `Chapter` that is built using the file `./information/one.md`.

Example:

```doculisp
(include
    (Sub-Section ./one.md)
)
```

This will create a subsection called `Sub Section` that is built using the file `./one.md`.

```doculisp
(include (Section ./two.md))
```

This will create a subsection called `Section` that is built using the file `./two.md`.