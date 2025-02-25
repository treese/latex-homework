# The `homework` class

Provides the LaTeX class [homework.cls](homework.cls) for typesetting homework
in a straightforward problem-solution format.
Designed to avoid [this mistake](http://tex.stackexchange.com/a/139878/23505).

This version is slightly modified from the original version by Artem Mavrin.

Read on for a description of the `homework` class.

----

## Table of Contents

* [**Introduction**](#introduction)
  * [**Features**](#features)
  * [**Example**](#example)
* [**Getting Started**](#getting-started)
  * [**Template**](#template)
  * [**Usage**](#usage)
* [**Documentation**](#documentation)
  * [**Commands**](#commands)
  * [**Environments**](#environments)
  * [**Class Options**](#class-options)
* [**License**](#license)

## Introduction

### Features

* Simple interface for specifying homework information (e.g., name and course).
* Environments for writing problem statements, problem parts, and solutions.
* Automatic title creation (but, unlike the original, it is necessary to include `\maketitle` after `\begin{document}`.
* Compatible with `article` class options.
* Loads the AMS math packages.
* Automatic PDF author/title/bookmark metadata creation.

### Example

For an examples of homework solutions created using the `homework` class,
see [example.tex](example.tex) and the resulting [PDF](example.pdf).

## Getting Started

### Template

[template.tex](template.tex) is a ready-to-use homework template that uses the
`homework` class.

### Usage

* Download `homework.cls` and save it in the same directory as your homework
  `.tex` file (*alternatively*, see
  [this question](http://tex.stackexchange.com/questions/1137/) to learn where
  to put `.cls` files to be globally available to TeX)
* At the top of the homework `.tex` file, put `\documentclass{homework}`.
* In the preamble, specify the homework information using the commands listed in
  the [Commands](#commands) section.
* In the document, begin writing problems in `problem` environments and
  solutions in `solution` environments (see [Environments](#environments)).

## Documentation

### Commands

The following commands should be used in the preamble of the homework `.tex`
file.
If these are not used, you will get an error.

* `\name{<name>}`:
  Replace `<name>` with your name.
* `\course{<course>}`:
  Replace `<course>` with the name of the course.
* `\term{<term>}`:
  Replace `<term>` with the term when the course is held.
* `\hwnum{<number>}`:
  Replace `<number>` with the number of the homework.
* `\shorttitle{<short-title>}`:
  Replace `<short-title>` with the running title for pages after the first one. The homework number is automatically appended to the short title.

The value of `\date` is printed with the title as in the article class. It can be set to a string like "Due on Friday".

Thus, at a *minimum*, your preamble must contain

```tex
\documentclass{homework}

\name{<name>}
\course{<course>}
\term{<term>}
\hwnum{<hwnum>}
\shorttitle{<short-title>}
```

You can also change the default text of various labels that appear on the
document by using the following commands.

* `\hwname{<name>}`:
  Replace `<name>` with the desired label for the type of homework (e.g.,
  *Assignment* or *Problem Set*).
  The default is *Homework*.
* `\problemname{<name>}`:
  Replace `<name>` with the desired label for problems created with the
  `problem` environment (e.g., *Exercise* or *Question*).
  The default is *Problem*.
* `\solutionname{<name>}`:
  Replace `<name>` with the desired label for solutions created with the
  `solution` environment (e.g., *Proof*, *Answer*, or a label in another
  language).
  The default is *Solution*.

### Environments

The following environments are provided to typeset the homework.

* `problem`:
  wraps individual problem statements.
  By default, problems are numbered beginning at `1`.
  To change the number of a given problem to `n`, use the command
  `\problemnumber{n}` before the `problem` environment.
* `solution`:
  wraps the solution to a problem.
* `parts`:
  enumerates parts of a multiple-part problem.
  If multiple `parts` environments are used in a single `problem` environment,
  labels will resume unless you use the `\unresume` command right after the
  beginning of each `parts` environment.
  New parts are declared using the `\part` command.
  The part labels can be customized by providing one of the following options to
  the `parts` environment:
    * `a`:
      (default) Lowercase letters.
    * `A`:
      Uppercase letters.
    * `r`:
      Lowercase Roman numerals.
    * `R`:
      Uppercase Roman numerals.
    * `n`:
      Numbers.
  
  To specify your own labels to `parts` (for example,
  to only list parts `b`, `d` and `e`) use the custom label as parameter as in `\part[b)]`.

* `claim`, `lemma`, `propostion`, `theorem`, `corollary`, `proof`:
  organize claims made in a solution (and prove these claims).
  The 'claim' environment takes an optional argument that labels the claim
  (e.g., `\begin{claim}[Conjecture]` will make the claim be labelled
  "Conjecture").
  The other listed environments are derived from the 'claim' environment.

### Class Options

To use a class option, write

```tex
\documentclass[<options>]{homework}
```

at the beginning of your homework file, where `<options>` is a comma-separated
list of the options that you wish to use.

All the options of the `article` class may be used.
In addition, the `homework` class provides the following options.

* `boxes`:
  Use this option if you want the `problem` environment to enclose problem
  statements in boxes.
* `hidesolutions`:
  Use this option to hide solutions in the output.
  With this option enabled, you can still write solutions in the `solution`
  environment, but these solutions will not show up in the final document.
* `qed`:
  Use this option if you want an end-of-proof symbol printed at the end of
  solutions.

## License

This code is distributed under the MIT license. For more info, read the
[LICENSE](LICENSE.txt) file.
