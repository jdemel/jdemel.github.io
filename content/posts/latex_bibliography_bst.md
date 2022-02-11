+++
title = "How to tame the BeaST? Customize your Bibliography"
date = "2022-02-11"
author = "Johannes Demel"
draft = true
cover = ""
tags = ["LaTeX", "BibTex"]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
+++

I use [LaTeX](https://en.wikibooks.org/wiki/LaTeX) all the time because it does a superb job at formatting.
Besides, it separates content from presentation, i.e. it is a WYTIWYG system.
I guess many people actually enjoy the amalgamated WYSIWYG text editors but as soon as you write code, you separate the two anyways. 
The LaTeX math system is used in countless cases, e.g. via MathJax in your browser.
[TikZ and PGF](https://en.wikibooks.org/wiki/LaTeX/PGF/TikZ) are very useful and eventually fast and efficient to produce vector graphics.
You can use [matplotlib with PGF](https://matplotlib.org/stable/tutorials/text/pgf.html) to save your figures as PGF files which you can then include in your documents.
I use [QtikZ](http://manpages.ubuntu.com/manpages/trusty/man1/qtikz.1.html) to build figures interactively.
Thus, eventually all documents and presentations end up being done in LaTeX.
The whole automatic reference generator feature via BibTex is also very useful.
However, how does it work? How do I customize it?

## Taming the BeaST

[Taming the BeaST](https://www.ctan.org/pkg/tamethebeast) is a good resource to get started.
I had a look at [this Stackoverflow answer](https://tex.stackexchange.com/a/64695) as well.
It explains the structure of `*.bst` files. Well, if you want to use BibTex.
I guess most LaTeX users still use BibTex, though more modern systems might be available such as BibLaTeX.
I tried [pybtex](https://pypi.org/project/pybtex/) to get a better understanding of my `*.bib` file.
But now, let's have a look at `*.bst` files that you use most likely via:
```
\bibliographystyle{your_bib_style}
\bibliography{library}
```
in case of IEEE publications, you probably use `\bibliographystyle{IEEEtran}`.
How do you modify such a `.bst` file? Let's add a link to a DOI in your references.

```
FUNCTION {format.doi}
{ doi empty$
    { "" }
    {
      new.block
      "DOI:\href{https://doi.org/" doi * "}{" * doi * "}" *
    }
  if$
}
```
In the end, the `format.doi` function takes care of correct DOI formatting.
You can just click on a DOI in a PDF and it takes you directly to the source.
If you print a paper, the link formatting will not clutter your pretty printed PDF.
I prefer acronyms in all caps. Thus, I add `DOI:` in the `format.doi` function.
However, I've seen files with `doi:` before the actual DOI.

The [Reverse Polish Notation (RPN)](https://en.wikipedia.org/wiki/Reverse_Polish_notation) is probably the trickiest part.
I met a few people who enjoy this notation for their calculators.
Apparently, it hasn't fallen out of fashion because [RPN calculators](https://play.google.com/store/apps/details?id=com.ath0.rpn&hl=en) still exists on modern systems.
You probably won't need RPN very often.
However, it might be an interesting concept to learn.
I guess most people don't learn [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language)) but it is an interesting programming language nontheless.

![XKCD on Haskell](https://imgs.xkcd.com/comics/haskell.png)
[Haskell image on XKCD](https://xkcd.com/1312/)


## Generating a library file

Personally, I use [Zotero](https://www.zotero.org/) to collect all the references I need.

- it is an open source system
- I can generate a `library.bib` file that I can use in all my LaTeX projects.
- I can import new PDFs via a browser plug-in.
- It has a merge feature.
- it offers sync features
- if offers premium features that really offer a benefit (more cloud storage).
- There are [Debian Zotero .deb repositories](https://github.com/retorquere/zotero-deb/)

Besides, it does not try to artificially lock you in like competing systems started to after Zotero gained some ground.


## Zenodo, our how to get more DOIs

[Zenodo](https://zenodo.org/) is probably the go-to website to generate [DOIs](https://en.wikipedia.org/wiki/Digital_object_identifier) for your personal data.
It is currently operated by CERN.
This is especially useful for datasets and source code.
I started to use Zenodo for [gr-symbolmapping on Zenodo](https://zenodo.org/record/5997648) which can be found via [DOI: 10.5281/zenodo.5997647](https://doi.org/10.5281/zenodo.5997647).
[Zenodo's GitHub integration](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content) automates the process to publish new versions.
Thus, it makes citing software, and especially open source software, more convenient in your papers.
It helps with references to exact versions.




