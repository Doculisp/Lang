<!-- GENERATED DOCUMENT DO NOT EDIT! -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->

<!-- Compiled with doculisp https://www.npmjs.com/package/doculisp -->
<!-- Written By: jason-kerney -->

# Doculisp #

```
___  ____ ____ _  _ _    _ ____ ___
|  \ |  | |    |  | |    | [__  |__]
|__/ |__| |___ |__| |___ | ___] |
```

A language for Readme.

## Table of Contents ##

1. Version: [Language Version](#language-version)
2. Intro: [What Problem Does Doculisp Solve?](#what-problem-does-doculisp-solve)
3. Language: [Basic Structure](#basic-structure)
4. Language: [Doculisp Master Block](#doculisp-master-block)
5. Language: [Section Meta Block](#section-meta-block)
6. Language: [Content Block](#content-block)
7. Language: [Dynamic Headings](#dynamic-headings)
8. Language: [Comment Block](#comment-block)
9. Language: [Key Atoms by Depth](#key-atoms-by-depth)
10. Structure: [".dlisp" files](#dlisp-files)
11. Recognition: [Contributors ✨](#contributors-)

## Language Version ##

Doculisp version 1.1.0

## What Problem Does Doculisp Solve? ##

Doculisp is designed to solve one problem, making readme files easier to edit and maintain. With Doculisp you can break each read me into multiple smaller files. Every time you have a header or subheader that could be a new file. This allows for the task of documentation to be managed in parts. When a part of the documentation needs to be edited, you can open the file that pertains to that part, and only that part. There is a secondary advantage to this. Whe a change to the documentation happens, you can see what that change effected without looking at file diffs just by examining the files that changed.

### A Word of Advice ###

If the text under a subheading is small, I would recommend  not breaking it into a different file. I actually recommend you start with a single readme, and refactor out to different files as the readme grows in size. Remember the point of this is to make updating and managing updates easier.

## Basic Structure ##

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

### Parameter ###

A parameter is a string of characters that contains no line advancement (`\r` or `\n`) character and no parentheses (unless escaped). A parameter has a max length of 255 characters.

### Visual Explanation ###

```doculisp
(atom)
(atom parameter)
(atom (atom2))
(atom (atom2 second parameter))
```

## Doculisp Master Block ##

All doculisp is contained in an outer doculisp block. That block starts with `(dl` followed by a white space. This doculisp block must be contained in an html comment.

Example

```markdown
<!--
(dl
    (section-meta
        (title Doculisp)
        (include
            (section ./doculisp.md)
        )
    )

    (content (toc numbered-labled))
)
-->
```

You will notice that in this example the doculisp contains 2 main blocks, however it is valid for the Doculisp block to contain more or less. Even zero other blocks.

## Section Meta Block ##

This block is contained directly within the Doculisp main block. It contains information used to build the current secion. This includes things like title, subtitle, and include.

Example

```doculisp
(section-meta
    (title Doculisp a short description)
    (include
        (section ./doculisp.md)
    )
)
```

### Title (required) ###

This is required, however it has two ways of being provided. The simple way, as a parameter to `section-meta`, or as a block if other blocks are also provided.

#### Simple Way ####

The simple way is to provide the title as a parameter to the `section-meta` block.

```doculisp
(section-meta Doculisp a Short Description)
```

#### Structured Way ####

If the `section-meta` block has any other sub blocks, then it is required that it also contains a `title` block. The title is followed by a title that ends at a `)`. Every thing following the white space after the word title and until a new line or a close parenthesis is the title.

```doculisp
(section-meta
    (title Doculisp How To)
    (subtitle A Short Description)
    (include
        (Section ./design.md)
    )
)
```

### Ref-Link ###

This is the first optional sub block for the `section-meta` block. The ref-link allows you to take over the link to use in the table of contents. Its main purpose is to handle characters in the title that markdown does not include in its section headers. This does not change the section link, but lets you specify a different link to use instead.

Example

```doculisp
(section-meta
    (title Doculisp is awesome ✨)
    (ref-link doculisp_is_awesome_)
)
```

### Subtitle ###

Subtitle creates a heading that is two levels of heading less then the title directly beneath the title.

### Include ###

This allows you to break each section up into sub-sections that are composed in seperate files. This allows you to limit the scope of work in each file making it easier to find where you need to edit and focus on a single idea.

Example

```doculisp
(section-meta
    (title Doculisp a short description)
    (include
        (section ./doculisp.md)
        (section ./section-meta.md)
    )
)
```

#### Subsections ####

The `include` block is composed of sub-section blocks. These blocks are different then other doculisp blocks. They are custom named blocks. Which means the name of each block is decided by the programmer the same way a variable name is. The format of these blocks is `(` followed by a name followed by whitespace. After the white space is the file path that leads to the document containing the information on how to build the sub-section. Followed again by an optional new line and whitespace. Ending in `)`.

You can add a space (` `) to a name by adding a `-` to the name.

Example

```doculisp
(include
    (chapter
        ./information/one.md
    )
)
```

This will create a sub-section called `chapter` that is built using the file `./information/one.md`.

Example

```doculisp
(include
    (sub-section ./one.md)
)
```

This will create a subsection called `sub section` that is built using the file `./one.md`.

```doculisp
(include (section ./two.md))
```

This will create a subsection called `section` that is built using the file `./two.md`.

### Section Id ###

Id is an optional block. It allows you to set an id for the section.

**NOT CURRENTLY USED** This is for future use.

#### Restrictions ####

The id block must meet the following restrictions:

* It must be lowercase.
* It must not contain any symbols other then underscore `_` or hyphen `-`.

#### Example ####

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

### Author ###

Author is an optional block in the section meta that puts the author's name in the comments at the top and bottom of the document. This block can be included multiple times and each will have a separate comment line.

```doculisp
(section-meta
    (title An example of the Author Block)
    (author Jason Kerney)
    (author Chris Stead)
)
```

### Exception to the Rule ###

Comment block breaks this rule slightly. The astrict character is a special character that cause all atoms that start with to be treated as a comment, and all parameters and sub blocks to be ignored.

## Content Block ##

The content block signifies where to insert the compiled included documents. This block has only one optional subblock.

### Table of Contents ###

The only subblock to the content block is the table of contents. This will cause a linked table of contents to appear for the section at its location.

#### Simple Usage ####

The simple usage of the table of contents is `(toc)` may have an optional bullet style as a parameter. The default style is `labeled`.

```doculisp
(content (toc numbered))
```

#### Complex Usage ####

The complex usage of table of contents allows you to specify an optional `label` that will appear as a heading directly above the table of contents. You can all so specify an optional `style` which will be a bullet style.

```doculisp
(content
    (toc
        (label Table of Contents)
        (style numbered)
    )
)
```

The default label will be not to include a label, and the default style is `labeled`

### Bullet Style ###

The bullet style argument can have one of the following values:

* no-table
* unlabeled
* labeled
* numbered
* numbered-labeled
* bulleted
* bulleted-labeled

Any of the options with `labled` on it will use the name of the subsection.

```doculisp
(dl
    (file-meta
        (title Some Document)
        (include
            (chapter ./first) (*The title of this document is "An introduction")
        )
    )

    (content (toc bulleted-labeled))
)
```

The table of contents would contain a line that looked like:

```markdown
* Chapter: [An Introduction](#an-introduction)
```

## Dynamic Headings ##

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

### Ids ###

You can add an ID to a heading.

**THIS IS NOT USED YET** and is reserved for future use.

the id follows the hash-mark (`#`).

#### Restrictions ####

The id must meet the following restrictions:

* It must be lowercase.
* It must not contain any symbols other then underscore `_` or hyphen `-`.

#### Example ####

```doculisp
<!-- info.md -->
<!-- (dl (#heading-id Information About Heading Ids)) -->

Some text here.
```

### Max Heading Depth ###

Currently, the maximum heading depth recognized by Markdown is H6. However Doculisp will not restrict you to that depth. If the total depth is more then H6 you may get unexpected results.

## Comment Block ##

The comment block is the only block that can be present at all levels within the Doculisp Main Block. The comment is created by adding an astrics `*` just after an open parenthesis and end when the block and all its subblocks are closed.

Example:

```markdown
<!--
(dl
    (*section-meta
        (title Doculisp)
        (include
            (section ./doculisp.md)
            (section ./section-meta.md)
            (section ./content.md)
            (section ./comment.md)
        )
    )
)
-->
```

In this example the `section-meta` block and all of its subblocks are commented out. Comments can also be nested. This allows you to uncomment in pieces.

Example:

```markdown
<!--
(dl
    (*section-meta
        (title Doculisp)
        (*include
            (section ./doculisp.md)
            (section ./section-meta.md)
            (section ./content.md)
            (*section ./comment.md)
        )
    )
)
-->
```

### Nested Comments ###

In this example the `section-meta` and all its subblocks are commented out. However when you uncomment `section-meta` then the `include` block will be commented out. When you uncomment that block, then the `section ./comment.md` block will be commented out.

## Key Atoms by Depth ##

Here is a list of all the key atoms by depth:

* markdown
* `dl`
  * `section-meta`
    * `title` text
      * `*`
    * `subtitle` text
      * `*`
    * `ref-link` text
      * `*`
    * `include`
      * name
      * file path
      * `*`
    * `reference`
      * `file`
        * `id` text
        * `source` file path
        * `target` file path
    * `*`
  * `content`
    * `toc` bullet style
       * `label` label text
       * `style` bullet style
  * `#` text
  * `*`
* `*`

## ".dlisp" files ##

If you have a file that contains only Doculisp code blocks without any markdown you can simplify that file. By changing the extension from `.md` to `.dlisp` you can remove the html comments and the opening `(dl` to contain raw Doculisp code.

### Example ###

```markdown
<!--
(dl
    (section-meta
        (title Doculisp)
        (include
            (Version ./version.md)
            (Intro ./why.md)
            (Language ./structure.md)
            (Recognition ./contributors.md)
        )
    )
)
-->

<!-- (dl (# Table of Contents)) -->

<!-- (dl (content (toc))) -->
```

Can be simplified to:

```doculisp
(section-meta
    (title Doculisp)
    (include
        (Version ./version.md)
        (Intro ./why.md)
        (Language ./structure.md)
        (Recognition ./contributors.md)
    )
)

(# Table of contents)

(content (toc))
```

## Contributors ✨ ##

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

I want to give a special thanks to my friend [Chris Stead](https://github.com/cmstead) who wrote [Book Lisp](https://github.com/cmstead/booklisp) which was a huge insperation for this tool.

<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="http://www.chrisstead.net/"><img src="https://avatars.githubusercontent.com/u/4184510?v=4?s=100" width="100px;" alt="Chris Stead"/><br /><sub><b>Chris Stead</b></sub></a><br /><a href="#ideas-cmstead" title="Ideas, Planning, & Feedback">🤔</a></td>
    </tr>
  </tbody>
</table>

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

<!-- Written By: jason-kerney -->
<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- GENERATED DOCUMENT DO NOT EDIT! -->