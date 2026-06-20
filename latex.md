# Using LaTeX

LaTeX's features for typesetting mathematics make it a compelling choice for writing technical documents. This article shows the most basic commands needed to get started with writing maths using LaTeX.

Writing basic equations in LaTeX is straightforward, for example:

```latex
\documentclass{article}

\begin{document}

The well known Pythagorean theorem \(x^2 + y^2 = z^2\) was proved to be invalid for other exponents. Meaning the next equation has no integer solutions:
\[ x^n + y^n = z^n \]

\end{document}
```

As you see, the way the equations are displayed depends on the delimiter, in this case `\[...\]` and `\(...\)`.

## Mathematical Modes

LaTeX allows two writing modes for mathematical expressions: the inline math mode and display math mode:

- inline math mode is used to write formulas that are part of a paragraph
- display math mode is used to write expressions that are not part of a paragraph, and are therefore put on separate lines

### Inline Math Modes

You can use any of these "delimiters" to typeset your math in inline mode:

- `\(...\)`
- `$...$`
- `\begin{math}...\end{math}`

They all work and the choice is a matter of taste, so let's see some examples.

```latex
\documentclass{article}

\begin{document}

Standard \LaTeX{} practice is to write inline math by enclosing it between \verb|\(...\)|:
\begin{quote}
In physics, the mass-energy equivalence is stated by the equation \(E=mc^2\), discovered in 1905 by Albert Einstein.
\end{quote}

Instead if writing (enclosing) inline math between \verb|\(...\)| you can use \texttt{\$...\$} to achieve the same result:
\begin{quote}
In physics, the mass-energy equivalence is stated by the equation $E=mc^2$, discovered in 1905 by Albert Einstein.
\end{quote}

Or, you can use \verb|\begin{math}...\end{math}|:
\begin{quote}
In physics, the mass-energy equivalence is stated by the equation \begin{math}E=mc^2\end{math}, discovered in 1905 by Albert Einstein.
\end{quote}

\end{document}
```

### Display Math Modes

Use one of these constructions to typeset maths in display mode:

- `\[...\]`
- `\begin{displaymath}...\end{displaymath}`
- `\begin{equation}...\end{equation}`

Display math mode has two versions which produce numbered or unnumbered equations. Let's look at a basic example:

```latex
\documentclass{article}

\begin{document}

The mass-energy equivalence is described by the famous equation
\[ E=mc^2, \]
discovered in 1905 by Albert Einstein.

In natural units ($c$ = 1), the formula expresses the identity
\begin{equation}
    E=m.
\end{equation}

\end{document}
```

### 2.1.3 Another example

The following example uses the `equation*` environment which is provided by the `amsmath` package—see the [amsmath article](https://www.overleaf.com/learn/latex/Aligning_equations) for more information.

```latex
\documentclass{article}
\usepackage{amsmath} % for the equation* environment
\begin{document}
This is a simple math expression \(\sqrt{x^2+1}\) inside text.
And this is also the same: \begin{math} \sqrt{x^2+1} \end{math} but by using another command.
This is a simple math expression without numbering \[\sqrt{x^2+1}\] separated from text.
This is also the same: \begin{displaymath} \sqrt{x^2+1} \end{displaymath}
\ldots and this: \begin{equation*} \sqrt{x^2+1} \end{equation*}
\end{document}
```

### 2.1.4 Reference guide

Below is a table with some common maths symbols. For a more complete list see the [List of Greek letters and math symbols](https://www.overleaf.com/learn/latex/List_of_Greek_letters_and_math_symbols):

| description | code | examples |
|---|---|---|
| Greek letters | `\alpha \beta \gamma \rho \sigma \delta \epsilon` | α β γ ρ σ δ ϵ |
| Binary operators | `\times \otimes \oplus \cup \cap` | |
| Relation operators | `< > \subset \supset \subseteq \supseteq` | |
| Others | `\int \oint \sum \prod` | |

Different classes of mathematical symbols are characterized by different formatting (for example, variables are italicized, but [operators](https://www.overleaf.com/learn/latex/Operators) are not) and different [spacing](https://www.overleaf.com/learn/latex/Spacing_in_math_mode).
