`format-markdown-epub` is used to convert a Markdown file (which may include other files) into a compliant EPUB file. This will gather up all the source images files, filter out links that aren't appropriate for the specific version, and run the results through `epubcheck` (which is assumed to be on the path).

# Usage

    format-markdown-epub [options] input.markdown [input.markdown ...]

The following options are available:

| Option                | Description |
|---------------------- | ----------- |
| --acknowledgments, -a | Moves the "Acknowledgments" before the table of contents and removes it from the TOC. |
| --cover=`cover.jpg`, -c `cover.jpg` | Uses the given `cover.jpg` for the embedded over image inside the EPUB. If not included, no image will be used. |
| --css=`epub.css`, -s `epub.css` | Uses the given `epub.css` for the CSS file. If missing, then a default one will be used. |
| --debug, -d | Changes the temporary directory to `/tmp/format-markdown-epub` and doesn't delete it once finished running. |
| --dedication | Moves the "Dedication" before the table of contents, removes the title, centers the section, and removes it from the TOC. |
| --epigraphs | Splits blockquotes with a "---" into two lines and assigns a different attribute to the second one. |
| --epub3, -3 | Generates an EPUB3 output file. |
| --filter-links=*selector* | Filters out links inside the source file using the given selector. See [`markdown-filter-links`](Filter Markdown Links) for more information. Can be used more than once. |
| --include, -i | Expands the source file using [`markdown-include`](Expanding Markdown). |
| --metadata=`epub.xml`, -m `epub.xml` | Uses the given `epub.xml` to provide additional metadata to `pandoc`. |
| --output=`output.epub`, -o `output.epub` | Determines the output file for the input. If not present, the name is inferred from the input file. Cannot be used with multiple input files. |
| --verbose, -v | Gives informational messages while running. |
