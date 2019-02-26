## LaTeX-α<sup>2</sup>

LaTeX-α<sup>2</sup> is a LaTeX package that can execute Wolfram Language codes and show the corresponding results inside LaTeX documents.

The package is heavily inspired by [LaTeX-Alpha](https://github.com/Akollek/LaTeX-Alpha). Unfortunately, LaTeX-Alpha has been down for a while. The aim of this package is to replace LaTeX-Alpha, as well as to add various new features.

The codes can be executed either locally (via locally installed Mathematica) or on the cloud (via [Wolfram Cloud](https://www.wolframcloud.com/)) using the [WolframScript](https://www.wolfram.com/wolframscript/) interpreter.

### Usage

- Download `latexalpha2.sty` to the same folder as your `.tex` file:

```
curl -O https://raw.githubusercontent.com/stevenliuyi/latex-alpha2/master/latexalpha2.sty
```

- Add `\usepackage{latexalpha2}` to the preamble of your document. All the codes will be run locally by default. If you'd like to run on the cloud, use `\usepackage[cloud]{latexalpha2}` instead.

- Use `pdflatex --shell-escape example.tex` to compile your `.tex` file.

### Examples
#### `\Wolfram{}`

Input: `$\Wolfram{Series[Exp[x],{x,0,5}]}$`

Output: ![](http://latex.codecogs.com/gif.latex?1+x+\frac{x^2}{2}+\frac{x^3}{6}+\frac{x^4}{24}+\frac{x^5}{120}+O(x^6))

#### `\WolframGraphics{}`

Input:

```
\WolframGraphics[pdf]{Plot3D[Sin[x]Cos[y], {x, -2Pi, 2Pi}, {y, -2Pi, Pi}]}{example}
\begin{figure}
  \centering
  \includegraphics{example.pdf}
\end{figure}
```

Output:

![Example Plot](example.png?raw=true)

#### `\WolframAlpha{}`

Input: `The population of Shanghai is $\WolframAlpha{population of Shanghai}$, which is $\WolframAlpha{ratio of Shanghai populatioin and NYC population}$ times the population of New York City.`

Output: The population of Shanghai is 2.415×10<sup>7</sup> people, which is 2.814 times the population of New York City.

#### `\WolframDSolve{}`

Input: `\WolframDSolve{D[y[x],x]+y[x]==a*Sin[x]}{y[x]}{x}`

Output: ![](http://latex.codecogs.com/gif.latex?y(x)=\frac{1}{2}a(\sin(x)-\cos(x))+c_1e^{-x})