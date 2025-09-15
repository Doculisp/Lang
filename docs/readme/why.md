<!-- (dl
(section-meta
    (title Why Doculisp?)
)
) -->

<!-- (dl (# The Documentation Maintenance Problem)) -->

As developers, we've all been there: staring at a massive README file that's become unwieldy, outdated, and frankly intimidating to update. Traditional documentation approaches create several pain points:

- **Monolithic files** that are difficult to navigate and edit
- **Merge conflicts** when multiple contributors update different sections
- **Unclear change impact** when reviewing large file diffs
- **Context switching overhead** when editing unrelated documentation sections
- **Inconsistent structure** across different projects and teams

Doculisp solves these problems by bringing **modularity and structure** to markdown documentation.

<!-- (dl (# Why Developers Love Doculisp)) -->

<!-- (dl (## 🎯 **Focused Editing**)) -->
Break your README into logical, manageable chunks. Need to update the installation instructions? Open just the `installation.md` file. Working on API documentation? Focus solely on `api.md`. No more scrolling through hundreds of lines to find the section you need.

<!-- (dl (## 🔍 **Clear Change Tracking**)) -->
Git diffs become meaningful again. Instead of seeing "README.md changed 47 lines," you see exactly which conceptual sections were modified: `installation.md`, `troubleshooting.md`, etc.

<!-- (dl (## 🤝 **Better Collaboration**)) -->
Multiple team members can work on different documentation sections simultaneously without merge conflicts. The documentation author editing the introduction won't conflict with the API maintainer updating endpoint documentation.

<!-- (dl (## 📐 **Consistent Structure**)) -->
The `section-meta` blocks enforce consistent organization across all your documentation, making it easier for new team members to contribute and for users to find information.

<!-- (dl (## ⚡ **Maintainability**)) -->
Small, focused files are easier to review, update, and refactor. When documentation grows, you can easily reorganize by moving files rather than cut-and-paste operations in large documents.

<!-- (dl (## 🔄 **Effortless Restructuring**)) -->
Need to promote a section to its own document? Simply move the file and update the `include` block. What starts as a subsection can easily become a standalone document with its own table of contents and structure. No copy-paste, no broken links, no manual reorganization - just move files and update references.

<!-- (dl (## 🔗 **Resilient Cross-References**)) -->
Every section and header can have a unique ID that enables dynamic linking within and across documents. Reference other sections with `(get-path id)` and Doculisp automatically generates the correct links. Best of all: when you restructure documentation and promote sections to standalone documents, as long as the IDs remain the same, all existing links continue to work seamlessly.

<!-- (dl (# Why Doculisp Over Other Options?)) -->

<!-- (dl (## vs. Traditional Markdown)) -->
**Traditional approach**: One massive README.md file that becomes harder to manage over time.
**Doculisp advantage**: Modular files with structured includes, maintaining the simplicity of markdown while adding organization.

<!-- (dl (## vs. Documentation Generators \(GitBook, Docusaurus, etc.\))) -->
**Documentation generators**: Complex setup, learning curve, often overkill for project READMEs.
**Doculisp advantage**: Zero learning curve if you know markdown. Generates standard markdown files that work everywhere GitHub is supported.

<!-- (dl (## vs. Wiki Systems)) -->
**Wiki systems**: Separate from your codebase, requires context switching, can become disconnected from code changes.
**Doculisp advantage**: Lives in your repository, versioned with your code, integrated into your development workflow.

<!-- (dl (## vs. Raw File Splitting)) -->
**Manual file splitting**: No standard structure, inconsistent organization, manual assembly required.
**Doculisp advantage**: Structured metadata system, automated assembly, consistent patterns across projects.

<!-- (dl (# Getting Started: A Practical Approach)) -->

<!-- (dl (## Start Simple, Grow Naturally)) -->

**Don't over-engineer from day one.** If your current README is manageable, keep it as-is. Doculisp shines when documentation becomes complex enough that modularization provides real value.

**Recommended progression:**
1. **Single file**: Start with a traditional README.md
2. **Natural breaking points**: When sections grow large (>50 lines) or become logically distinct, extract them
3. **Gradual adoption**: Begin with obvious candidates like installation instructions, API documentation, or troubleshooting guides
4. **Full structure**: Eventually organize into a complete Doculisp project when the benefits are clear

**Signs it's time to modularize:**
- Your README is over 200 lines
- Multiple people need to edit different sections
- You find yourself searching within the file to find specific content
- Merge conflicts are happening in documentation
- You're copying documentation patterns between projects

**Pro tip**: The goal is easier maintenance, not complexity. If splitting a small section into its own file makes editing *harder*, don't do it.