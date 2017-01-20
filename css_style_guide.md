# Black Swan CSS Style Guide() {

*A mostly reasonable approach to CSS*

## Context

This document describes what to avoid and what to use instead when it comes to development with CSS/SCSS on Avionics projects.

**Note**: Think of this document as a common knowledge base. This means two things:

  1. This document lays out rules. Even those can't be forced automatically. Keep playing by the rules.
  1. Collaboration: if you can't find a solution for your problem or have any additional suggestions feel free to create a pull request with additional sections, fixes or thoughts. This is a living documentation and should contain ideas we as a team agree on.

## Table of Contents

* CSS

1. [CSS Specificity](#markdown-header-css-specificity)
1. [CSS Validity](#markdown-header-css-validity)
1. [Class Naming](#markdown-header-class-naming)
1. [Class Name Delimiters](#markdown-header-class-name-delimiters)
1. [Class Name Style](#markdown-header-class-name-style)
1. [Type Selectors](#markdown-header-type-selectors)
1. [Shorthand notation](#markdown-header-shorthand-notation)
1. [0 and Units](#markdown-header-0-and-units)
1. [Leading 0s](#markdown-header-leading-0s)
1. [Hexadecimal Notation](#markdown-header-hexadecimal-notation)
1. [Declaration Order](#markdown-header-declaration-order)
1. [Declaration Stops](#markdown-header-declaration-stops)
1. [Selector and Declaration Separation](#markdown-header-selector-and-declaration-separation)
1. [Single declarations](#markdown-header-single-declarations)
1. [Rule Separation](#markdown-header-rule-separation)
1. [Section Comments](#markdown-header-section-comments)
1. [Comments](#markdown-header-comments)

* SCSS

1. [Nesting in Sass](#markdown-header-nesting-in-sass)
1. [Nested selectors](#markdown-header-nested-selectors)
1. [Maximum Nesting](#markdown-header-maximum-nesting)
1. [Extend directive](#markdown-header-extend-directive)
1. [Shame](#markdown-header-shame)


## CSS Specificity

- Remember how to calculate css selector specificity and use it when you are in 

- If the element has inline styling, that automatically wins (1,0,0,0 points)
- For each ID value, apply 0,1,0,0 points
- For each class value (or pseudo-class or attribute selector), apply 0,0,1,0 points
- For each element reference, apply 0,0,0,1 point
- You can generally read the values as if they were just a number, like 1,0,0,0 is "1000", and so clearly wins over a specificity of 0,1,0,0 or "100". The commas are there to remind us that this isn't really a "base 10" system, in that you could technically have a specificity value of like 0,1,13,4 - and that "13" doesn't spill over like a base 10 system would.

- More info on CSS specificity:
- https://css-tricks.com/specifics-on-css-specificity/

## CSS Validity

- Use valid CSS where possible.
Unless dealing with CSS validator bugs or requiring proprietary syntax, use valid CSS code.

- Use tools such as the W3C CSS validator to test.

- Using valid CSS is a measurable baseline quality attribute that allows to spot CSS code that may not have any effect and can be removed, and that ensures proper CSS usage.

## Class Naming

- Use meaningful or generic class names.
- Instead of presentational or cryptic names, always use class names that reflect the purpose of the element in question, or that are otherwise generic.

- Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change.

- Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as “helpers.”

- Using functional or generic names reduces the probability of unnecessary document or template changes.

```
#!css
/* Not recommended: meaningless */
.yee-1901 {}

/* Not recommended: presentational */
.button-green {}
.clear {}
/* Recommended: specific */
.gallery {}
.login {}
.video {}

/* Recommended: generic */
.aux {}
.alt {}
```


## Class Name Delimiters

- Separate words in class names by a hyphen.
- Do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.

```
#!css
/* Not recommended: does not separate the words “demo” and “image” */
.demoimage {}

/* Not recommended: uses underscore instead of hyphen */
.error_status {}
/* Recommended */
.video-id {}
.ads-sample {}
```

## Class Name Style

- Use class names that are as short as possible but as long as necessary.
Try to convey what a class is about while being as brief as possible.

- Using class names this way contributes to acceptable levels of understandability and code efficiency.

```
#!css
/* Not recommended */
.navigation {}
.atr {}

/* Recommended */
.nav {}
.author {}
```

## Type Selectors

- Avoid qualifying ID and class names with type selectors.
- Unless necessary (for example with helper classes), do not use element names in conjunction with IDs or classes.

- Avoiding unnecessary ancestor selectors is useful for performance reasons.

```
#!css
	/* Not recommended */
	ul.example {}
	div.error {}
	/* Recommended */
	.example {}
	.error {}
```

## Shorthand notation
- Strive to limit use of shorthand declarations to instances where you must explicitly set all the available values. Common overused shorthand properties include:

- padding, margin, font, background, border, border-radius
- Often times we don't need to set all the values a shorthand property represents. For example, HTML headings only set top and bottom margin, so when necessary, only override those two values. Excessive use of shorthand properties often leads to sloppier code with unnecessary overrides and unintended side effects.


## 0 and Units

- Omit unit specification after “0” values.
- Do not use units after 0 values unless they are required.

```
#!css
	margin: 0;
	padding: 0;
```

## Leading 0s

- Omit leading “0”s in values.
- Do not use put 0s in front of values or lengths between -1 and 1.

```
#!css
font-size: .8em;
```

## Colors

- Do not use hex colors in the stylesheets, use the rgb everywhere, or rgba if translucency needed.
- Use "transparent" when you need completely transparent color.

```
#!css
/* Not recommended */
color: #eebbcc;
color: #ebc;
color: rgba(10,40,20, .0);

/* Recommended */
color: rgb(0,0,0);
color: rgba(0,0,0,.4);
color: transparent;
```


## Declaration Order

- Alphabetize declarations.
- Put declarations in alphabetical order in order to achieve consistent code in a way that is easy to remember and maintain.

```
#!css
background: fuchsia;
border: 1px solid;
border-radius: 4px;
color: black;
text-align: center;
text-indent: 2em;
```


# Block Content Indentation

- Indent all block content.
- Indent all block content, that is rules within rules as well as declarations, so to reflect hierarchy and improve understanding.

```
#!css
@media screen, projection {
  html {
    background: #fff;
    color: #444;
  }
}
```

## Declaration Stops

- Use a semicolon after every declaration.
- End every declaration with a semicolon for consistency and extensibility reasons.

```
#!css
/* Not recommended */
.test {
  display: block;
  height: 100px
}
/* Recommended */
.test {
  display: block;
  height: 100px;
}
```

# Property Name Stops

- Use a space after a property name’s colon.
- Always use a single space between property and value (but no space between property and colon) for consistency reasons.

```
#!css
/* Not recommended */
h3 {
  font-weight:bold;
}
/* Recommended */
h3 {
  font-weight: bold;
}
```

# Declaration Block Separation

- Use a space between the last selector and the declaration block.
- Always use a single space between the last selector and the opening brace that begins the declaration block.

- The opening brace should be on the same line as the last selector in a given rule.

```
#!css
/* Not recommended: missing space */
#video{
  margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
  margin-top: 1em;
}
/* Recommended */
#video {
  margin-top: 1em;
}
```

## Selector and Declaration Separation

- Separate selectors and declarations by new lines.
- Always start a new line for each selector and declaration.

```
#!css
/* Not recommended */
a:focus, a:active {
  position: relative; top: 1px;
}
/* Recommended */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```

## Single declarations
- Single line declarations are not prefered, any rule should be split to separate lines.

```
#!css
	/*  */
	.span1 { width: 60px; }
	.span2 { width: 140px; }
	.span3 { width: 220px; }

	.sprite {
	  display: inline-block;
	  width: 16px;
	  height: 15px;
	  background-image: url(../img/sprite.png);
	}

	.icon {
    background-position: 0 0;
  }
	
  .icon-home {
    background-position: 0 -20px;
  }
```

## Rule Separation

- Separate rules by new lines.
- Always put a blank line (two line breaks) between rules.

```
#!css
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```

## Section Comments

- Group sections by a section comment (optional).
- If possible, group style sheet sections together by using comments. Separate sections with new lines.

```
#!css
/* Header */

.adw-header {}

/* Footer */

.adw-footer {}

/* Gallery */

.adw-gallery {}
```

## Comments
- Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others. Great code comments convey context or purpose. Do not simply reiterate a component or class name.

- Be sure to write in complete sentences for larger comments and succinct phrases for general notes.

```
#!css
/* Bad example */
/* Modal header */
.modal-header {
  ...
}

/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

# SCSS
*Use Your Regular CSS Formatting Rules / Style Guide

- Be consistant with indentation
- Be consistant about where spaces before/after colons/braces go
- One selector per line, One rule per line
- Have a plan for class name naming
- Don't use ID's #hotdrama

## Nesting in Sass
- Avoid unnecessary nesting. Just because you can nest, doesn't mean you always should. Consider nesting only if you must scope styles to a parent and if there are multiple elements to be nested.
- Suggestion: Write pure css and simplify with scss nesting, never follow the markup structure, try to create the simplest selectors possible.

```
#!css
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}
```

## Nested selectors
- Nested selectors, if necessary, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.

```
#!css
.btn {
  background: green;
  font-weight: bold;
  @include transition(background 0.5s ease);

  .icon {
    margin-right: 10px;
  }
}
```

- Do not nest selectors more than three levels deep!

```
#!css
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```

- When selectors become this long, you're likely writing CSS that is:
- Strongly coupled to the HTML (fragile) —OR—
- Overly specific (powerful) —OR—
- Not reusable

## Maximum Nesting
- Maximum 50 line, If a nested block of Sass is longer than that, there is a good chance it doesn't fit on one code editor screen, and starts becoming difficult to understand. The whole point of nesting is convenience and to assist in mental grouping. Don't use it if it hurts that.


- Three Levels Deep

```
#!css
.weather {
  .cities {
    li {
      // no more!
    }
  }
}
```

- Chances are, if you're deeper than that, you're writing a crappy selector. Crappy in that it's too reliant on HTML structure (fragile), overly specific (too powerful), and not very reusable (not useful). It's also on the edge of being difficult to understand.



## Extend directive

- @extend should be avoided because it has unintuitive and potentially dangerous behavior, especially when used with nested selectors. Even extending top-level placeholder selectors can cause problems if the order of selectors ends up changing later (e.g. if they are in other files and the order the files are loaded shifts).

## Media Queries
- To achieve shorter and better readibility, use nested mediaqueries.

```
#!css

.example {
  font-size: 12pt;
  
  @media screen and (min-width: 768px) {
    font-size: 20px;
  }
}
```

## Shame

- In your global stylesheet, @import a _shame.scss file last.

```
#!css
@import "compass"

...

@import "shame"
```

- If you need to make a quick fix, you can do it here. Later when you have proper time, you can move the fix into the proper structure/organization.

- http://csswizardry.com/2013/04/shame-css/