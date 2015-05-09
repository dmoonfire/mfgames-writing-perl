# MfGames Writing Perl

This is a collection of scripts written in Perl for purposes of supporting writing using text-based formats, in specific Markdown. It includes tools for querying Markdown files and ones for formatting into various other formats.

## Markdown + YAML

The bulk of the system is intended to work with Markdown that includes a YAML header.

## Query Tools

* `list-unique-words`  
  Used to create a list of words and names that don't appear in the standard dictionaries.
* `markdown-wc`  
  Counts the number of words in one or more Markdown files, excluding the YAML header.
* `markdown-word-breakdown`  
  Counts the occurrences of each word in a Markdown file.
* `sentence-prefix`  
  Gives the beginning of every sentence. (Not YAML aware yet.)
* `summarize-git-differences`  
  A tool for listing the differences between two Git versions and identifying inserts and deletions throughout the document.

## Manipulation Tools

* `markdown-extract`  
  Extracts sections out of a Markdown file based on classes or identifiers.
* `markdown-filter-links`  
  Filters out links that have a specific class, also removes attributes from links.
* `markdown-include`  
  Expands a Markdown file that includes other ones into a single document.
* `markdown-join`  
  Combined one or more Markdown + YAML files into a single formatted one.
* `markdown-split`  
  Splits a Markdown file into its components, mainly used to reverse `markdown-join`.

## Formatting Tools

* [`format-markdown-epub`](Format-EPUB.md)  
   Formats a Markdown file into an EPUB file.
* `format-markdown-odt`  
   Formats a Markdown file into an OpenOffice/Libreoffice document.
* `format-markdown-pdf`  
   Formats a Markdown file into a PDF.

## Conversion

* `creole2markdown`  
  A script for converting a Creole file into Markdown with YAML.

## Spell Checking

The `caspell` is a wrapper around `aspell` that is can be used to create project or world-specific dictionary entries without using LocalWords or other methods.

* `caspell`
* `localwords2cspell`  
  Converts the `LocalWords` attribute in a YAML header into a single `local.words` file for `caspell`.
