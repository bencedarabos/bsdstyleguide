# Black Swan HTML Style Guide() {

*A mostly reasonable approach to HTML sitebuild*

## Context

This document describes what to avoid and what to use instead when it comes to development with HTML on Avionics projects.

**Note**: Think of this document as a common knowledge base. This means two things:

  1. This document lays out rules. Even those can't be forced automatically. Keep playing by the rules.
  1. Collaboration: if you can't find a solution for your problem or have any additional suggestions feel free to create a pull request with additional sections, fixes or thoughts. This is a living documentation and should contain ideas we as a team agree on.

## Table of Contents

  1. [Document Type](#markdown-header-protocol)
  1. [HTML Validity](#markdown-header-html-validity)
  1. [Semantics](#markdown-header-semantics)
  1. [Separation of Concerns](#markdown-header-separation-of-concerns)
  1. [Entity References](#markdown-header-entity-references)
  1. [General Formatting](#markdown-header-general-formatting)
  1. [HTML Quotation Marks](#markdown-header-html-quotation-marks)
  1. [Reducing Markup](#markdown-header-html-reducing-markup)
  

## Document Type

- Use HTML5.
- HTML5 (HTML syntax) is preferred for all HTML documents: <!DOCTYPE html>.

- (It’s recommended to use HTML, as text/html. Do not use XHTML. XHTML, as application/xhtml+xml, lacks both browser and infrastructure support and offers less room for optimization than HTML.)

- Although fine with HTML, do not close void elements, i.e. write <br>, not <br />.

## HTML Validity

- Use valid HTML where possible.
- Use valid HTML code unless that is not possible due to otherwise unattainable performance goals regarding file size.

- Use tools such as the W3C HTML validator to test.

## Semantics

- Use HTML according to its purpose.
- Use elements (sometimes incorrectly called “tags”) for what they have been created for. For example, use heading elements for headings, p elements for paragraphs, a elements for anchors, etc.

- Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

```
#!html
<!-- Not recommended -->
<div onclick="goToRecommendations();">All recommendations</div>
<!-- Recommended -->
<a href="recommendations/">All recommendations</a>
```

## Attribute order
- HTML attributes should come in this particular order for easier reading of code.

- class
- id, name
- data-*
- src, for, type, href, value
- title, alt
- role, aria-*
- Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.

```
#!html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```


## Separation of Concerns

- Separate structure from presentation from behavior.
- Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.

- That is, make sure documents and templates contain only HTML and HTML that is solely serving structural purposes. Move everything presentational into style sheets, and everything behavioral into scripts.

- In addition, keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.

## Entity References

- Do not use entity references.
- There is no need to use entity references like &mdash;, &rdquo;, or &#x263a;, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.

- The only exceptions apply to characters with special meaning in HTML (like < and &) as well as control or “invisible” characters (like no-break spaces).

```
#!html
<!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.
<!-- Recommended -->
The currency symbol for the Euro is “€”.
```

## General Formatting

- Use a new line for every block, list, or table element, and indent every such child element.
- Independent of the styling of an element (as CSS allows elements to assume a different role per display property), put every block, list, or table element on a new line.

- Also, indent them if they are child elements of a block, list, or table element.

- (If you run into issues around whitespace between list items it’s acceptable to put all li elements in one line. A linter is encouraged to throw a warning instead of an error.)

```
#!html
<blockquote>
  <p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
  <li>Moe
  <li>Larry
  <li>Curly
</ul>

<table>
  <thead>
    <tr>
      <th scope="col">Income
      <th scope="col">Taxes
  <tbody>
    <tr>
      <td>$ 5.00
      <td>$ 4.50
</table>
```

## HTML Quotation Marks

- When quoting attributes values, use double quotation marks.
- Use double ("") rather than single quotation marks ('') around attribute values.

```
#!html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>
<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```


## Reducing Markup
- Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. Take the following example:

```
#!html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```
