% Making slides with pandoc and revealjs
% Miguel Angel Marco Buzunariz
% Zaragoza, June 2019

# Overview

## Advantages

- Faster workflow
  - And reusable (can export to latex/beamer/pdf/html...)
- Don't depend on pdf viewer
- Can include videos, and animations
- Zoomable
- Can use speaker notes, and overview
- Smaller files (plus dependencies)

## Disadvantages

- Some latex-beamer features might be missing
- Bigger files (if self-contained)
- If we use a theme with upper title bars, slides are not vertically centered

## Requirements

You need

- install pandoc
- copy revealjs on your directory
  - copy the beamer.css file into revealjs/css/theme/
- copy katex on your directory (if you want to be able to compile without internet connection)

## Workflow

Write a markdown file. And then execute

```
pandoc example.md -o example.html \\
       -t revealjs \\
       --katex=./katex/  \\
       --standalone \\
       -V theme=beamer \\
       -V transition=none  \\
       -i --slide-level 2 \\
       --self-contained
```

. . .

Thats it!

# Markdown syntax

## Sections and slides

A line like

```
# This section name
```

Will make a slide with a big centered title (for sections)

. . .

A line like

```
## This slide title
```

Will make a slide with an upper title bar.

## Lists

Lists are done like this

``` markdown
- First item
- Second item
  - Subitem inside second item
  - Second subitem
- Thirthd item
```

- First item
- Second item
  - Subitem inside second item
  - Second subitem
- Thirthd item

## Fragments

To make a part of the slide appear with a click, just separate it with a line with three dots separated by spaces. That is, the code:

``` markdown
First paragraph that i see.

. . .

This second paragraph appears as I click
```

Has this effect:

. . .

First paragraph that i see.

. . .

This second paragraph appears as I click

## Latex content

Latex content can be inserted normally, thanks to katex.

So this:

``` markdown
The formula for the volume of a sphere is $\frac{4 \pi r^3}{3}$.
```

Will produce this:

The formula for the volume of a sphere is $\frac{4 \pi r^3}{3}$.

## Latex content

Display math is also possible. For instance like this:

``` markdown
$$
\int_{0}^{+\infty} \frac{1}{x}dx=+\infty
$$
```

$$
\int_{0}^{+\infty} \frac{1}{x}dx=+\infty
$$

## Theorem boxes

The code

``` markdown
::: thm
## **Theorem:**

The ring of polynomials over a field is noetherian.
:::
```

will be seen as

::: thm
## **Theorem:**

The ring of polynomials over a field is noetherian.
:::

# Pandoc options

## Transitions

> - None
> - Fade
> - Slide
> - Convex
> - Concave
> - Zoom

## Themes

::: columns
::: column
> - beige
> - black
> - blood
> - league
> - moon
> - night
:::
::: column
> - serif
> - simple
> - sky
> - solarized
> - white
> - beamer (not by default)
:::
:::

They are stored in the `/reveal.js/css/theme/` directory.
