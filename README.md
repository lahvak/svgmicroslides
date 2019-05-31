## SVGMicroSlides

simple svg based slideshows with pgf/tikz.

### Why

In the past I have often used LaTeX Beamer class with the pgf/TiKZ package to
create slides with solved example problems to share with my students. The
Beamer class creates slides in pdf format, and I wanted to have something that
I can easily embed in html pages (WeBWorK problems, blog posts, pages on a
"learning management system" _etc._) There are number of html and javascript
based slide systems, but I wanted something that would allow me to easily build
mathematical formulas and graphs incrementally, the way it can be done with
Beamer.  This is a quick solution for this problem.  It does not have all
capabilities of Beamer, but does allow me to build tikz pictures layer by
layer, which is sufficient for many such small slide shows.

### Installation

This is very easy to install.  You will need a reasonably complete and recent
TeX distribution, such as TeXLive, and the bash shell.

- Copy, move or link the `simplesvgpres.sty` file from the `tex` directory
  somewhere where TeX can find it.
- Copy, move or link the `presfromsvg` script from the `script` directory
  somewhere where your shell can find it.

### Usage

Create a LaTeX file, for example `example.tex`, using the `standalone` document class,
following the example in the `example` directory.  Then compile this to a
presentation as follows:

```bash
latex example
dvisvgm --font-format=woff example
presfromsvg "Contents for html title tag" example.svg > example.html
```

That's it, the `example.html` will contain your presentation.  You can open it
with a web browser, or embed in in an iframe inside another html file.

### Bugs

- No IE support.  I cannot figure out how to properly size the svg in IE, and
  some of my javascript apparently is not supported by IE.  I don't have an
  easy way to test this, and don't have time to experiment with it, but someone
  wants to fix it and submit a pr, that would be great!  I tested it with
  reasonably recent versions of chrome, firefox and edge.
- No documentation of the `simplesvgpres` package.  I will include more
  comments in the example tex file, it is really easy, there are only few
  things to document.
- The `\definePages` TeX command is somewhat sensitive to proper spacing,
  sometimes including extra spaces really messes things up.

If you run into anything else, submit an issue.  Thanks!


