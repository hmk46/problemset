# problemset
This is my personal LaTeX package for typesetting problemsets, primarily for mathematics courses.

It's fairly simple right now, and is designed to reduce boilerplate typing.
If you use it and have suggestions for improvements, please let me know.

Here's how it looks:

![example screenshot](/example.png)

## usage
The main part of the package is the *questions* environment. Its usage looks like this:

    \begin{questions}
      \qn This is a simple question.
      \qn This question has a solution.
      \sn This is the solution.
      \qn This question asks for a proof.
      \pf This is the proof.
      \qn This question has parts.
        \pt Simple part.
        \pt This part has a solution.
        \sn This is the solution.
        \pt This part asks for a proof.
        \pf This is the proof.
      \qn[11.5] This question has manual numbering.
      \pt[(ii)] And so does this part.
      \qn This question is
          very very long.
          But whitespace doesn't matter.
      \sn \label{special}
          You can label solutions,
          like this very long one.
    \end{questions}

And that's basically it. Note that there is no current support for nested parts, so you have to manually put those in enumerate environments.


The preamble should look like this:

    \documentclass{article}
    \usepackage{problemset}
    \title{Problem Set 1}
    \class{MATH2875}
    \session{Fall 2020}
    \author{John Doe}
    \studentid{\#317206375}
    \school{Quantum State University}
    \problemset

Where unspecified fields default to being empty.
You need to invoke the `\problemset` command to have *maketitle* and headers/footers work properly.
Also note that it takes an optional language code argument which is just used to generate PDF metadata, and which defaults to en-CA.

If you want to manually specify your own title resp. author line, you can prepend the preamble with `\manualtitletrue` resp. `\manualauthortrue`.

## Prerequisites
The following packages are used:
- ifluatex
- colorprofiles
- pdfx
- fontspec (if compiling with lualatex)
- babel
- amsmath
- amssymb
- amsthm
- mathtools
- stix2
- xparse
- fancyhdr

YOu might need to install stix2. The rest should be included in an up-to-date distribution of TeXLive.

## Installation
There is a general [guide for installing LaTeX packages here.](https://en.wikibooks.org/wiki/LaTeX/Installing_Extra_Packages)

On a Linux distro with TeXLive, this should suffice:

    $ cd ~/texmf/tex/latex
    $ git clone https://github.com/hussainjk/problemset.git
    $ texhash

## Disclaimer

This work is licensed under the public domain and is provided as-is.

In particular, it will probably be modified in ways that break backwards-compatibility. The interface is *not stable.*
