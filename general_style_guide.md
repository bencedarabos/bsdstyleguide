# Black Swan General Style Guide() {

*A mostly reasonable approach to General sitebuild*

## Context

This document describes what to avoid and what to use instead when it comes to development with HTML on Avionics projects.

**Note**: Think of this document as a common knowledge base. This means two things:

  1. This document lays out rules. Even those can't be forced automatically. Keep playing by the rules.
  1. Collaboration: if you can't find a solution for your problem or have any additional suggestions feel free to create a pull request with additional sections, fixes or thoughts. This is a living documentation and should contain ideas we as a team agree on.

## Table of Contents

  1. [Protocol](#markdown-header-protocol)
  1. [Indentation](#markdown-header-indentation)
  1. [Capitalization](#markdown-header-capitalization)
  1. [Encoding](#markdown-header-encoding)
  1. [Comments](#markdown-header-comments)
  1. [Action Items](#markdown-header-action-items)

## Protocol

  - Omit the protocol portion (http:, https:) from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.
  - Omitting the protocol—which makes the URL relative—prevents mixed content issues and results in minor file size savings.

```
#!html
  <!-- Not recommended -->
  <script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>
  <!-- Recommended -->
  <script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

```
#!css
  /* Not recommended */
  .example {
    background: url(https://www.google.com/images/example);
  }
  /* Recommended */
  .example {
    background: url(//www.google.com/images/example);
  }
```

## Indentation

- Indent by 1 tab at a time.
- Don’t mix tabs and spaces for indentation.

```
#!html
<ul>
  <li>Fantastic
  <li>Great
</ul>
```

```
#!css
.example {
  color: blue;
}
```

## Capitalization

- Use only lowercase.
- All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), CSS selectors, properties, and property values (with the exception of strings).
- This not apply to JavaScript

```
#!html
<!-- Not recommended -->
<A HREF="/">Home</A>
<!-- Recommended -->
<img src="google.png" alt="Google">
```

```
#!css
/* Not recommended */
color: #E5E5E5;
/* Recommended */
color: #e5e5e5;
```

## Trailing Whitespace

- Remove trailing white spaces.
- Trailing white spaces are unnecessary and can complicate diffs.

```
#!html
<!-- Not recommended -->
<p>What?_
<!-- Recommended -->
<p>Yes please.
```

## Encoding

- Use UTF-8 (no BOM).
- Make sure your editor uses UTF-8 as character encoding, without a byte order mark.

- Specify the encoding in HTML templates and documents via <meta charset="utf-8">. Do not specify the encoding of style sheets as these assume UTF-8.

- (More on encodings and when and how to specify them can be found in Handling character encodings in HTML and CSS.)

## Comments

- Explain code as needed, where possible.
- Use comments to explain code: What does it cover, what purpose does it serve, why is respective solution used or preferred?

- (This item is optional as it is not deemed a realistic expectation to always demand fully documented code. Mileage may vary heavily for HTML and CSS code and depends on the project’s complexity.)

## Action Items

- Mark todos and action items with TODO.
- Highlight todos by using the keyword TODO only, not other common formats like @@.

- Append a contact (username or mailing list) in parentheses as with the format TODO(contact).

- Append action items after a colon as in TODO: action item.

```
#!html
<!-- TODO: remove optional tags -->
<ul>
  <li>Apples</li>
  <li>Oranges</li>
</ul>
```