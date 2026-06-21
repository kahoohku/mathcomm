# Inserting Figures

## Pgfplots package

### Introduction

The `pgfplots` package, which is based on [TikZ](https://www.overleaf.com/learn/latex/TikZ_package), is a powerful visualization tool and ideal for creating scientific/technical graphics. The basic idea is that you provide the input data/formula and `pgfplots` does the rest.

#### The document preamble

To use the `pgfplots` package in your document add following line to your preamble:

```latex
\usepackage{pgfplots}
```

You also can configure the behaviour of `pgfplots` in the document preamble. For example, to change the size of each plot and guarantee backwards compatibility (recommended) add the next line:

```latex
\pgfplotsset{width=10cm,compat=1.9}
```

This changes the size of each `pgfplot` figure to 10 centimeters, which is huge; you may use different units (pt, mm, in). The `compat` parameter is for the code to work on the package version 1.9 or later.

#### Compilation time (brief background)

When the original TeX engine was conceived/written, more than 40 years ago, it was not designed for direct production of graphics—those were to be files created by external programs (e.g., MetaPost) and imported into the typeset document. The advent of pdfTeX—which is closely based on the original TeX software—brought the ability to create graphics directly by using pdfTeX's new built-in TeX language commands (called primitives) which can output the PDF operators/data required to produce graphics.

The creation of pdfTeX led to the development of sophisticated LaTeX graphics packages, such as `TikZ`, `pgfplots` etc, capable of producing graphics coded using high-level LaTeX commands. However, behind the scenes, and deep inside the pdfTeX engine (and other engines), those high-level LaTeX graphics commands need to be processed by "converting" them back into low-level pdfTeX engine (primitive) commands which actually generate (output) the PDF operators required to produce the resultant figure(s).

That processing of graphical LaTeX commands—expansion and execution of primitives—can take a non-negligible amount of time. Even a single high-level LaTeX graphics command, together with its corresponding data, might require repeated execution of many low-level TeX engine (primitive) commands. From an end-user's perspective, documents containing multiple `pgfplots` figures, and/or very complex graphics, can take a considerable amount of time to render (compile).

#### Reducing compilation time

To increase speed of document-compilation you can configure the `pgfplots` package to export the figures to separate PDF files and then import them into the document: compile once, then re-use the figures. To do that, add the code shown below to the preamble:

```latex
\usepgfplotslibrary{external}
\tikzexternalize
```

See [this help article](https://www.overleaf.com/learn/latex/Questions/I_have_a_lot_of_tikz%2C_matlab2tikz_or_pgfplots_figures%2C_so_I%27m_getting_a_compilation_timeout._Can_I_externalise_my_figures%3F) for further details on how to set up tikz-externalization in your Overleaf project.

### Basic example (also externalizing the figures)

```latex
\documentclass{article}
\usepackage[margin=0.25in]{geometry}
\usepackage{pgfplots}
\pgfplotsset{width=10cm,compat=1.9}
% We will externalize the figures
\usepgfplotslibrary{external}
\tikzexternalize
\begin{document}
First example is 2D and 3D math expressions plotted side-by-side.
%Here begins the 2D plot
\begin{tikzpicture}
\begin{axis}
\addplot[color=red]{exp(x)};
\end{axis}
\end{tikzpicture}
%Here ends the 2D plot
\hskip 5pt
%Here begins the 3D plot
\begin{tikzpicture}
\begin{axis}
\addplot3[
surf,
]{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}
%Here ends the 3D plot
\end{document}
```

The following image shows the result produced by the code above:

#### Explanation of the code

Because `pgfplots` is based on `tikz` the plot must be inside a `tikzpicture` environment. Then the environment declaration `\begin{axis}`, `\end{axis}` will set the correct scaling for the plot—check the [Reference guide](#Reference-guide) for other axis environments.

To add an actual plot, the command `\addplot[color=red]{log(x)};` is used. Inside the square brackets, `[...]`, some options can be passed in; here, we set the color of the plot to red. The square brackets are mandatory, if no options are passed leave a blank space between them. Inside the curly brackets you put the function to plot. Is important to remember that this command must end with a semicolon (`;`).

To put a second plot next to the first one declare a new `tikzpicture` environment. Do not insert a new line, but a small blank gap, in this case `\hskip 10pt` will insert a 10pt-wide blank space.

The rest of the syntax is the same, except for the `\addplot3 [surf,]{exp(-x^2-y^2)*x};`. This will add a 3d plot, and the option `surf` inside squared brackets declares that it's a surface plot. The function to plot must be placed inside curly brackets. Again, don't forget to put a semicolon (`;`) at the end of the command.

Note: It's recommended as a good practice to indent the code—see the second plot in the example above—and to add a comma (`,`) at the end of each option passed to `\addplot`. This way the code is more readable and is easier to add further options if needed.

### 2D plots

`pgfplots`' 2D plotting functionalities are vast—and you can personalize your plots to suit your requirements. Nevertheless, the default options usually give very good results, so all you need to do is feed the data and LaTeX will do the rest.

#### Plotting mathematical expressions

Here is an example:

```latex
\begin{tikzpicture}
\begin{axis}[
axis lines = left,
xlabel = \(x\),
ylabel = {\(f(x)\)},
]
%Below the red parabola is defined
\addplot [
domain=-10:10,
samples=100,
color=red,
]
{x^2 - 2*x - 1};
\addlegendentry{\(x^2 - 2x - 1\)}
%Here the blue parabola is defined
\addplot [
domain=-10:10,
samples=100,
color=blue,
]
{x^2 + 2*x + 1};
\addlegendentry{\(x^2 + 2x + 1\)}
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the code

Let's analyse the new commands line-by-line:

- `axis lines = left`. This will set the axis only on the left and bottom sides of the plot, instead of the default `box`. Further customisation options at the [reference guide](#Reference-guide).
- `xlabel = \(x\)` and `ylabel = {\(f(x)\)}`. Self-explanatory parameter names, these will let you put a label on the horizontal and vertical axis. Notice the `ylabel` value in between curly brackets, this brackets tell `pgfplots` how to group the text. The `xlabel` could have had brackets too. This is useful for complicated labels that may confuse `pgfplots`.
- `\addplot`. This will add a plot to the axis, general usage was described at the [introduction](#Introduction). There are two new parameters in this example.
  - `domain=-10:10`. This establishes the range of values of `x`.
  - `samples=100`. Determines the number of points in the interval defined by `domain`. The greater the value of `samples` the sharper the graph you get, but it will take longer to render.
- `\addlegendentry{\(x^2 - 2x - 1\)}`. This adds the legend to identify the function.

To add another graph to the plot just write a new `\addplot` entry.

#### Plotting from data

Scientific research often yields data that has to be analysed. The next example shows how to plot data with `pgfplots`:

Plotting from data:

```latex
\begin{tikzpicture}
\begin{axis}[
title={Temperature dependence of CuSO\(_4\cdot\)5H\(_2\)O solubility},
xlabel={Temperature [\textcelsius]},
ylabel={Solubility [g per 100 g water]},
xmin=0, xmax=100,
ymin=0, ymax=120,
xtick={0,20,40,60,80,100},
ytick={0,20,40,60,80,100,120},
legend pos=north west,
ymajorgrids=true,
grid style=dashed,
]
\addplot[
color=blue,
mark=square,
]
coordinates {
(0,23.1)(10,27.5)(20,32)(30,37.8)(40,44.6)(60,61.8)(80,83.8)(100,114)
};
\legend{CuSO\(_4\cdot\)5H\(_2\)O}
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the code

There are some new commands and parameters here:

- `title={Temperature dependence of CuSO\(_4\cdot\)5H\(_2\)O solubility}`. As you might expect, assigns a title to the figure. The title will be displayed above the plot.
- `xmin=0, xmax=100, ymin=0, ymax=120`. Minimum and maximum bounds of the x and y axes.
- `xtick={0,20,40,60,80,100}, ytick={0,20,40,60,80,100,120}`. Points where the marks are placed. If empty the ticks are set automatically.
- `legend pos=north west`. Position of the legend box. Check the [reference guide](#Reference-guide) for more options.
- `ymajorgrids=true`. This enables/disables grid lines at the tick positions on the y axis. Use `xmajorgrids` to enable grid lines on the x axis.
- `grid style=dashed`. Self-explanatory. To display dashed grid lines.
- `mark=square`. This draws a squared mark at each point in the `coordinates` array. Each mark will be connected with the next one by a straight line.
- `coordinates {(0,23.1)(10,27.5)(20,32)...}`. Coordinates of the points to be plotted. This is the data you want analyse graphically. If the data is in a file, which is the case most of the time; instead of the commands `\addplot` and `coordinates` you should use `\addplot table {file_with_the_data.dat}`, the rest of the options are valid in this environment.

#### Scatter plots

Scatter plots are used to represent information by using some kind of marks and are commonly used when computing statistical regression. In this example we'll create a scatter plot using data contained in a file called `scattered_example.dat`, in which the data looks like this:

```
GPA ma ve co un
3.45 643 589 3.76 3.52
2.78 558 512 2.87 2.91
2.52 583 503 2.54 2.4
3.67 685 602 3.83 3.47
3.24 592 538 3.29 3.47
2.1 562 486 2.64 2.37
...
```

Our scatter plot uses the first two columns of the data:

```latex
\begin{tikzpicture}
\begin{axis}[
enlargelimits=false,
]
\addplot+[
only marks,
scatter,
mark=halfcircle*,
mark size=2.9pt
] table[meta=ma] {scattered_example.dat};
\end{axis}
\end{tikzpicture}
```

###### Explanation of the code

The parameters passed to the `axis` and `addplot` environments can also be used in a data plot, except for `scatter`. Below the description of the code:

- `enlarge limits=false` - This will shrink the axes so the point with maximum and minimum values lay on the edge of the plot.
- `only marks` - Really explicit, will put a mark on each point.
- `scatter` - When `scatter` is used the points are coloured depending on a value, the colour is given by the `meta` parameter explained below.
- `mark=halfcircle*` - The kind of mark to use on each point, check the [reference guide](#Reference-guide) for a list of possible values.
- `mark size=2.9pt` - The size of each mark, different units can be used.
- `table[meta=ma]{scattered_example.dat};` - Here the `table` command tells latex that the data to be plotted is in a file. The `meta=ma` parameter is passed to choose the column that determines the colour of each point. Inside curly brackets is the name of the data file.

#### Bar graphs

Bar graphs (also known as bar charts and bar plots) are used to display gathered data, mainly statistical data about a population of some sort. Bar plots in `pgfplots` are highly configurable, but here we are going to show a plain example:

```latex
\begin{tikzpicture}
\begin{axis}[
x tick label style={
/pgf/number format/1000 sep=},
ylabel=Year,
enlargelimits=0.05,
legend style={at={(0.5,-0.1)}, anchor=north,legend columns=-1},
ybar interval=0.7,
]
\addplot coordinates {(2012,408184) (2011,408348) (2010,414870) (2009,412156)};
\addplot coordinates {(2012,388950) (2011,393007) (2010,398449) (2009,395972)};
\legend{Men,Women}
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the code

The figure starts with the ([previously explained](#Introduction)) declaration of the `tikzpicture` and `axis` environments, but the `axis` declaration has a number of new parameters:

- `x tick label style={/pgf/number format/1000 sep=}` - This piece of code defines a complete style for the plot. With this style you may include several `\addplot` commands within this `axis` environment, they will fit and look nice together with no further tweaks (the `ybar` parameter described below is mandatory for this to work).
- `enlargelimits=0.05`. Enlarging the limits in a bar plot is necessary because these kind of plots often require some extra space above the bar to look better and/or add a label. Then number 0.05 is relative to the total height of of the plot.
- `legend style={at={(0.5,-0.2)}, anchor=north,legend columns=-1}` - Again, this will work just fine most of the time. If anything, change the value of `-0.2` to locate the legend closer/farther from the x-axis.
- `ybar interval=0.7`, - Thickness of each bar. `1` meaning the bars will be one next to the other with no gaps and `0` meaning there will be no bars, but only vertical lines.

The `coordinates` in this kind of plot determine the base point of the bar and its height. The labels on the y-axis will show up to 4 digits. If the numbers you are working with are greater than 9999 `pgfplots` will use the same notation as in the example.

### 3D Plots

`pgfplots` has the 3D Plotting capabilities that you may expect in a plotting software.

#### Plotting mathematical expressions

There's a simple example about this at the [introduction](#Introduction), let's work on something slightly more complex:

```latex
\begin{tikzpicture}
\begin{axis}[
title=Example using the mesh parameter,
hide axis,
colormap/cool,
]
\addplot3[
mesh,
samples=50,
domain=-8:8,
]
{sin(deg(sqrt(x^2+y^2)))/sqrt(x^2+y^2)};
\addlegendentry{\(\frac{sin(r)}{r}\)}
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the code

Most of the commands here have already been explained, but there are 3 new things:

- `hide axis` - This option in the `axis` environment is self descriptive, the axis won't be shown.
- `colormap/cool` - Is the colour scheme to be used in the plot. Check the [reference guide](#Reference-guide) for more colour schemes.
- `mesh` - This option is self-descriptive too, check also the `surf` parameter in the [introductory example](#Introduction).

Note: When working with trigonometric functions `pgfplots` uses degrees as default units, if the angle is in radians (as in this example) you have to use the `deg` function to convert to degrees.

#### Contour plots

In `pgfplots` it is possible to plot contour plots, but the data has to be pre-calculated by an external program. Let's see an example:

```latex
\begin{tikzpicture}
\begin{axis} [
title={Contour plot, view from top},
view={0}{90}
]
\addplot3[
contour gnuplot={levels={0.8, 0.4, 0.2, -0.2}}
]
{sin(deg(sqrt(x^2+y^2)))/sqrt(x^2+y^2)};
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the code

This is a plot of some contour lines for the same equation used in the previous section. The value of the `title` parameter is inside curly brackets because it contains a comma, so we use the grouping brackets to avoid any confusion with the other parameters passed to the `\begin{axis}` declaration. There are two new commands:

- `view={0}{90}` - This changes the view of the plot. The parameter is passed to the `axis` environment, which means this can be used in any other type of 3D plot. The first value is a rotation, in degrees, around the z-axis; the second value is to rotate the view around the x-axis. In this example when we combine a 0° rotation around the z-axis and a 90° rotation around the x-axis we end up with a view of the plot from top.
- `contour gnuplot={levels={0.8, 0.4, 0.2, -0.2}}` - This line of code does two things: First, it tells LaTeX to use the external software [gnuplot](http://www.gnuplot.info/) to compute the contour lines; this works fine in Overleaf but if you want to use this command in your local LaTeX installation you have to install gnuplot first (matlab will also work, in such case write matlab instead of gnuplot in the command). Second, the sub parameter `levels` is a list of values of elevation levels where the contour lines are to be computed.

#### Plotting a surface from data

To plot a set of data into a 3D surface all we need is the coordinates of each point. These coordinates could be an unordered set or, in this case, a matrix:

```latex
\begin{tikzpicture}
\begin{axis}
\addplot3[
surf,
]
coordinates {
(0,0,0) (0,1,0) (0,2,0)
(1,0,0) (1,1,0.6) (1,2,0.7)
(2,0,0) (2,1,0.7) (2,2,1.8)
};
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the data

The points passed to the `coordinates` parameter are treated as contained in a 3 × 3 matrix, using a blank line as the separator for each matrix row. All the options for 3D plots in this article apply to data surfaces.

#### Parametric plot

The syntax for parametric plots is slightly different. Let's see an example:

```latex
\begin{tikzpicture}
\begin{axis} [
view={60}{30},
]
\addplot3[
domain=0:5*pi,
samples = 60,
samples y=0,
]
({sin(deg(x))}, {cos(deg(x))}, {x});
\end{axis}
\end{tikzpicture}
```

The output from this code is shown in the image below—the LaTeX document preamble is added automatically when you open the link:

###### Explanation of the code

There are only two new things in this example: first, the `samples y=0` to prevent `pgfplots` from joining the extreme points of the spiral and; second, the way the function to plot is passed to the `addplot3` environment. Each parameter function is grouped inside curly brackets and the three parameters are delimited with a parenthesis.

### Reference guide

| Command/Option/Environment | Description | Possible Values |
|---|---|---|
| `axis` | Normal plots with linear scaling | |
| `semilogxaxis` | logarithmic scaling of x and normal scaling for y | |
| `semilogyaxis` | logarithmic scaling for y and normal scaling for x | |
| `loglogaxis` | logarithmic scaling for the x and y axes | |
| `axis lines` | changes the way the axes are drawn. default is 'box' | `box`, `left`, `middle`, `center`, `right`, `none` |
| `legend pos` | position of the legend box | `south west`, `south east`, `north west`, `north east`, `outer north east` |
| `mark` | type of marks used in data plotting. When a single-character is used, the character appearance is very similar to the actual mark. | `*`, `x`, `+`, `|`, `o`, `asterisk`, `star`, `10-pointed star`, `oplus`, `oplus*`, `otimes`, `otimes*`, `square`, `square*`, `triangle`, `triangle*`, `diamond`, `halfdiamond*`, `halfsquare*`, `right*`, `left*`, `Mercedes star`, `Mercedes star flipped`, `halfcircle`, `halfcircle*`, `pentagon`, `pentagon*`, `cubes` (cubes only work on 3d plots). |
| `colormap` | colour scheme to be used in a plot, can be personalized but there are some predefined colormaps | `hot`, `hot2`, `jet`, `blackwhite`, `bluered`, `cool`, `greenyellow`, `redyellow`, `violet`. |

## TikZ package

### Introduction

[TikZ](https://en.wikipedia.org/wiki/PGF/TikZ) is probably the most complex and powerful tool to create graphic elements in LaTeX. Starting with a simple example, this article introduces some basic concepts: drawing lines, dots, curves, circles, rectangles etc.

Firstly, load the `tikz` package by including the line `\usepackage{tikz}` in the preamble of your document, then draw a graphic using the `tikzpicture` environment.

```latex
\documentclass{article}
\usepackage{tikz}
\begin{document}
\begin{tikzpicture}
\draw[gray, thick] (-1,2) -- (2,-4);
\draw[gray, thick] (-1,-1) -- (2,2);
\filldraw[black] (0,0) circle (2pt) node[anchor=west]{Intersection point};
\end{tikzpicture}
\end{document}
```

This example produces the following output:

In this example two lines and one point are drawn. To add a line the command `\draw[gray, thick]` defines a graphic element whose colour is gray and with a thick stroke. The line is actually defined by it's two endpoints, `(-1,2)` and `(2,-4)`, joined by `--`.

The point is actually a circle drawn by `\filldraw[black]`, this command will not only draw the circle but fill it using black. In this command the centre point `(0,0)` and the radius `(2pt)` are declared. Next to the point is a node, which is actually a box containing the text intersection point, and anchored at the west of the point.

It's important to notice the semicolon `;` used at the end of each draw command.

Note: The `tikzfigure` environment can be enclosed inside a `figure` or similar environment. See the [Inserting Images](https://www.overleaf.com/learn/latex/Inserting_Images) article for more information on this topic.

### Basic elements: points, lines and paths

In this section we provide some examples showing how to create some basic graphic elements which can be combined to create more elaborate figures.

```latex
\documentclass{article}
\usepackage{tikz}
\begin{document}
\begin{tikzpicture}
\draw (-2,0) -- (2,0);
\filldraw [gray] (0,0) circle (2pt);
\draw (-2,-2) .. controls (0,0) .. (2,-2);
\draw (-2,2) .. controls (-1,0) and (1,0) .. (2,2);
\end{tikzpicture}
\end{document}
```

This example produces the following output:

There are three basic commands in this example:

- `\draw (-2,0) -- (2,0);`: This defines a line whose endpoint are `(-2,0)` and `(2,0)`.
- `\filldraw [gray] (0,0) circle (2pt);`: The point is created as a very small gray circle centred at `(0,0)` and whose radius is `(2pt)`. The `\filldraw` command is used to draw elements and fill them with a specific colour. See the next section for more examples.
- `\draw (-2,2) .. controls (-1,0) and (1,0) .. (2,2);`: Draws a [Bézier curve](https://en.wikipedia.org/wiki/B%C3%A9zier_curve). There are 4 points defining it: `(-2,2)` and `(2,2)` are its endpoints, `(-1,0)` and `(1,0)` are [control points](https://en.wikipedia.org/wiki/Control_point_(mathematics)) that determine "how curved" it is. You can think of these two points as "attractor points".

### Basic geometric shapes: Circles, ellipses and polygons

Geometric figures can be constructed from simpler elements so let's start with circles, ellipses and arcs.

```latex
\documentclass{article}
\usepackage{tikz}
\begin{document}
\begin{tikzpicture}
\filldraw[color=red!60, fill=red!5, very thick](-1,0) circle (1.5);
\fill[blue!50] (2.5,0) ellipse (1.5 and 0.5);
\draw[ultra thick, ->] (6.5,0) arc (0:220:1);
\end{tikzpicture}
\end{document}
```

This example produces the following output:

- `\filldraw[color=red!60, fill=red!5, very thick](-1,0) circle (1.5);`: This command was used in the previous section to draw a point, but in this instance there are some additional parameters inside the brackets. These are explained below:
  - `color=red!60`: The colour of the ring around the circle is set to 60% red (lighter than "pure" red). See the [reference guide](#Reference-guide) for a list of the default colours available in LaTeX; also, see [Using colours in LaTeX](https://www.overleaf.com/learn/latex/Using_colours_in_LaTeX) to learn how to create your own colours.
  - `fill=red!5`: The circle is filled with an even lighter shade of red.
  - `very thick`: This parameter defines the thickness of the stroke. See the [reference guide](#Reference-guide) for a complete list of values.
- `\fill[blue!50] (2.5,0) ellipse (1.5 and 0.5);`: To create an ellipse you provide a centre point `(2.5,0)`, and two radii: horizontal and vertical (`1.5` and `0.5` respectively). Also notice the command `fill` instead of `draw` or `filldraw`, this is because, in this case, there's no need to control outer and inner colours.
- `\draw[ultra thick, ->] (6.5,0) arc (0:220:1);`: This command will draw an arc starting at `(6.5,0)`. The extra parameter `->` indicates that the arc will have an arrow at the end. In addition to the starting point you must provide three additional values: the starting and ending angles, and the radius; here, these three parameter values are provided in the format `(0:220:1)`.

In addition to curved geometric shapes you can also create elements that use straight lines, using a similar syntax:

```latex
\documentclass{article}
\usepackage{tikz}
\begin{document}
\begin{tikzpicture}
\draw[blue, very thick] (0,0) rectangle (3,2);
\draw[orange, ultra thick] (4,0) -- (6,0) -- (5.7,2) -- cycle;
\end{tikzpicture}
\end{document}
```

This example produces the following output:

- `\draw[blue, very thick] (0,0) rectangle (3,2);`: Rectangles are created by the special command `rectangle`. You have to provide two points, the first one is where the "pencil" begins to draw the rectangle and the second one is the diagonally opposite corner point.
- `\draw[orange, ultra thick] (4,0) -- (6,0) -- (5.7,2) -- cycle;`: To draw a polygon we draw a closed path of straight lines: a line from `(4,0)` to `(6,0)` and a line from `(6,0)` to `(5.7,2)`. The `cycle` instruction means that the start and end points should coincide to create a "closed" path (shape), which results in construction of the final line segment.

### Diagrams

Nodes are probably the most versatile elements in TikZ. We've already used one node in the introduction—to add some text to the figure. The next example uses nodes to create a diagram.

```latex
\documentclass{article}
\usepackage{tikz}
\usetikzlibrary{positioning}
\begin{document}
\begin{tikzpicture}[
roundnode/.style={circle, draw=green!60, fill=green!5, very thick, minimum size=7mm},
squarednode/.style={rectangle, draw=red!60, fill=red!5, very thick, minimum size=5mm},
]
%Nodes
\node[squarednode] (maintopic) {2};
\node[roundnode] (uppercircle) [above=of maintopic] {1};
\node[squarednode] (rightsquare) [right=of maintopic] {3};
\node[roundnode] (lowercircle) [below=of maintopic] {4};
%Lines
\draw[->] (uppercircle.south) -- (maintopic.north);
\draw[->] (maintopic.east) -- (rightsquare.west);
\draw[->] (rightsquare.south) .. controls +(down:7mm) and +(right:7mm) .. (lowercircle.east);
\end{tikzpicture}
\end{document}
```

This example produces the following output:

There are essentially three commands in this figure: A node definition, a node declaration and lines that join two nodes.

- `roundnode/.style={circle, draw=green!60, fill=green!5, very thick, minimum size=7mm}`: Passed as a parameter to the `tikzpicture` environment. It defines a node that will be referenced as `roundnode`: this node will be a circle whose outer ring will be drawn using the colour `green!60` and will be filled using `green!5`. The stroke will be `very thick` and its minimum size is `7mm`. The line below this defines a second rectangle-shaped node called `squarednode`, using similar parameters.
- `\node[squarednode] (maintopic) {2};`: This will create a `squarednode`, as defined in the previous command. This node will have an id of `maintopic` and will contain the number `2`. If you leave an empty space inside the braces no text will be displayed.
- `[above=of maintopic]`: Notice that all but the first node have an additional parameter that determines its position relative to other nodes. For instance, `[above=of maintopic]` means that this node should appear above the node named `maintopic`. For this positioning system to work you have to add `\usetikzlibrary{positioning}` to your preamble. Without the positioning library, you can use the syntax `above of=maintopic` instead, but the positioning syntax is more flexible and powerful: you can extend it to write `above=3cm of maintopic` i.e. control the actual distance from `maintopic`.
- `\draw[->] (uppercircle.south) -- (maintopic.north);`: An arrow-like straight line will be drawn. The syntax has been already explained in the [basic elements](#Basic-elements) section. The only difference is the manner in which we write the endpoints of the line: by referencing a node (this is why we named them) and a position relative to the node.

### Reference Guide

Possible color and thickness parameters in the `tikz` package:

| parameter | values | picture |
|---|---|---|
| color | white, black, red, green, blue, cyan, magenta, yellow | |
| thickness | ultra thin, very thin, thin, thick, very thick, ultra thick | |

More colours may be available in your LaTeX distribution. See [Using colours in LaTeX](https://www.overleaf.com/learn/latex/Using_colours_in_LaTeX).
