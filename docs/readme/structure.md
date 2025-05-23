<!-- (dl
(section-meta
    (title Basic Structure)
    (id structure)
)
) -->

The basic structure of Doculisp is all code is contained within blocks. A block is constructed within an HTML comment region. It starts with an open parentheses `(` followed by a sting of non-whitespace characters. This is called an atom. It then has 1 of three possibilities. It can have a parameter, a new block, or nothing. All blocks must close with a close parentheses `)`.

Even the Doculisp main block follows this.

Example

```markdown
<!--
(dl
    (section-meta
        (title Basic Structure)
    )
)
-->
```

The first block is the `dl` block. In it `dl` is the atom. It contains the `section-meta` sub-block.  That block has the atom `section-meta` followed by a further sub block. The last sub block is the `title` sub block. In it `title` is the atom and `Basic Structure` is the parameter.

<!-- (dl (#struct-param Parameter)) -->

A parameter is a string of characters that contains no line advancement (`\r` or `\n`) character and no parentheses (unless escaped). A parameter has a max length of 255 characters.

Example:

```doculisp
(atom parameter)
```

To include parentheses within a parameter, escape them with a backslash:

```doculisp
(atom parameter\))
```

<!-- (dl (#struct-visual More Visual Explanations)) -->

```doculisp
(atom)
(atom parameter)
(atom (atom2))
(atom (atom2 second parameter))
```

```mermaid
graph TD
    subgraph Basic Atom
        A(atom)
    end
    subgraph Atom with Parameter
        B(atom) -->|parameter| C
    end
    subgraph Atom contains Atom
        D(atom) --> E(atom2)
    end
    subgraph Nested
        F(atom) --> G(atom2)
        G -->H(Parameter)
    end
```