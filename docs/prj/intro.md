<!--
(dl
    (section-meta
        (title What is a Doculisp Project File)
    )
)
-->

The Doculisp project file is a way to compile multiple Doculisp documents with a single command. It is intended to allow related documents to be compiled together and at once easily. This could be the readme and contrib documents, or any other collection of similar documents.

The project file _**MUST**_ have the extension of `.dlproj`. It also cannot be used in the `include` block as it does not represent a single document but instead a collection of related documents.

The contents of the the project file is structured using lisp, similar to any other part of Doculisp.