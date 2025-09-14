<!-- (dl (section-meta Components of the `section-meta` Block)) -->

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