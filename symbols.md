# The Use of Symbols

Equations are essentially made up from symbols -- numbers, equality
sign, variables and so on. There are many other symbols in mathematics
as well. It is important that symbols be used properly, for otherwise
the resulting sentence may deviate from the intended meaning.

## The Symbols '$=$' and '$\neq$'

The symbol '$=$' is probably one of the very first mathematical symbols
one learns. It means the expressions on its two sides are the same. This
symbol is also one of the most misused symbols, as people abuse it in
various situations. The symbol '$\neq$', on the other hand, means the
two sides are not equal, and we have to be careful about its usage too.

### Are they equal?

When using the equal sign, make sure that the expressions on the two
sides are indeed equal.

<table class="demo" cellpadding="8" cellspacing="0" markdown="block">
<thead> <tr> <th>Wrong</th> <th>Correct</th> <th>Comments</th> </tr> </thead>
<tbody> <tr> <td markdown="block">
By first principles, the derivative of $x^2$ is

$$\begin{align*}
    &\lim_{h\to0} \frac{f(x+h)-f(x)}h \\
    \boldsymbol{={}}& \boldsymbol{\frac{(x^2+2xh+h^2) - x^2}h} \\
    ={}& 2x.
\end{align*}$$
{::nomarkdown}</td> <td markdown="block">{:/}
By first principles, the derivative of $x^2$ is

$$\begin{align*}
    &\lim_{h\to0} \frac{f(x+h)-f(x)}h \\
    \boldsymbol{={}}& \boldsymbol{\lim_{h\to0} \frac{(x^2+2xh+h^2) - x^2}h} \\
    ={}& 2x.
\end{align*}$$
{::nomarkdown}</td> <td markdown="block">{:/}
The answer is correct but it is wrong to omit the limits in the working out. As
the argument stands Line 1 and Line 2 in the wrong example are surely not equal
(neither are Lines 2 and 3).
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
To find the third derivative of $xe^x$, we have

$$\begin{align*}
    \boldsymbol{xe^x} &\boldsymbol{= xe^x + e^x} \\
    &\boldsymbol{= xe^x + 2e^x} \\
    &= xe^x + 3e^x.
\end{align*}$$
{::nomarkdown}</td> <td markdown="block">{:/}
To find the third derivative of $xe^x$, we have

$$\begin{align*}
    \boldsymbol{\frac{d^3}{dx^3}(xe^x)} &\boldsymbol{= \frac{d^2}{dx^2}(xe^x + e^x)} \\
    &\boldsymbol{= \frac{d}{dx}(xe^x + 2e^x)} \\
    &= xe^x + 3e^x.
\end{align*}$$
{::nomarkdown}</td> <td markdown="block">{:/}
In the first (wrong) example, the expressions are clearly not equal.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
Since the derivative is $2x$, the slope of the tangent at $(2,5)$ is 4.
Hence the equation of the tangent is

$$\begin{align*}
    \frac{y-5}{x-2}=4 \enspace \boldsymbol= \enspace y=4x-3.
\end{align*}$$
{::nomarkdown}</td> <td markdown="block">{:/}
Since the derivative is $2x$, the slope of the tangent at $(2,5)$ is 4.
Hence the equation of the tangent is

$$\begin{align*}
    \frac{y-5}{x-2}=4,
\end{align*}$$

**which is the same as**

$$\begin{align*}
    y = 4x-3.
\end{align*}$$
{::nomarkdown}</td> <td markdown="block">{:/}
What the wrong example intended to say was that the equation '$\dfrac{y-5}{x-2}=4$' is 'equal' to the equation '$y=4x-3$'. But as it stands it says much more than that --- for example the middle equality reads $4=y$, which does not make sense.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
We row reduce the matrix to find

$$\begin{align*}
    \begin{bmatrix} 1&0 \\ 2&4 \end{bmatrix}
    \boldsymbol=
    \begin{bmatrix} 1&0 \\ 0&1 \end{bmatrix}.
\end{align*}$$

Hence it is invertible.
{::nomarkdown}</td> <td markdown="block">{:/}
We row reduce the matrix to find

$$\begin{align*}
    \begin{bmatrix} 1&0 \\ 2&4 \end{bmatrix}
    \boldsymbol\to
    \begin{bmatrix} 1&0 \\ 0&1 \end{bmatrix}.
\end{align*}$$

Hence it is invertible.
{::nomarkdown}</td> <td markdown="block">{:/}
The matrices are row equivalent but not equal (we say two matrices are equal if
and only if all their entries are the same). The proper way is to use an arrow;
usually we also indicate the operations carried out, for example,
$\xrightarrow{-2R_1+R_2}$ means we add $-2$ times row 1 to row 2.
{::nomarkdown}</tr> </tbody> </table>{:/}

### Non-transitivity of $\ne$

The symbols '$=$' and '$\ne$', like many others, are used to describe
the relationship between *two* things. Sometimes more than two things
are involved and we may still use these symbols successively,
e.g. $1<2<3$, but only when the symbol is *transitive* --- in this
example '$<$' is transitive since if $1<2$ and $2<3$, then we must have
$1<3$. Likewise, '$=$' is transitive. However, '$\ne$' is not.

<table class="demo" cellpadding="8" cellspacing="0" markdown="block">
<thead> <tr> <th>Wrong</th> <th>Correct</th> <th>Comments</th> </tr> </thead>
<tbody> <tr> <td markdown="block">
Since $\boldsymbol{a \neq b \neq c}$, we have...
{::nomarkdown}</td> <td markdown="block">{:/}
- Since **$\boldsymbol{a \neq b}$, $\boldsymbol{b \neq c}$, and $\boldsymbol{a \neq c}$**, we have...
- Since **$\boldsymbol{a, b, c}$ are pairwise distinct**, we have...
{::nomarkdown}</td> <td markdown="block">{:/}
The wrong example intended to mean that all three values $a,b$ and $c$ are different but with the way it is written, $a$ and $c$ could be equal (for example consider $1\neq 2\neq1$).
{::nomarkdown}</tr> </tbody> </table>{:/}

### Proper order

As previously mentioned, '$=$' is transitive and so we can equate three
or more expressions in a single chain of equalities. However, we have to
be careful about the order.

<table class="demo" cellpadding="8" cellspacing="0" markdown="block">
<thead> <tr> <th>Wrong</th> <th>Correct</th> <th>Comments</th> </tr> </thead>
<tbody> <tr> <td markdown="block">
Since $\dfrac{x^4y^4}8=2$, we have $\boldsymbol{x^4y^4=(xy)^4}=8\times2=16$ and so $xy=\sqrt[4]{16}=2$.
{::nomarkdown}</td> <td markdown="block">{:/}
Since $\dfrac{x^4y^4}8=2$, we have $\boldsymbol{(xy)^4=x^4y^4}=8\times2=16$ and so $xy=\sqrt[4]{16}=2$.
{::nomarkdown}</td> <td markdown="block">{:/}
When studying a chain of equalities, one naturally tries to figure out why each
equality sign holds. In the wrong example, one can understand why
$x^4y^4=(xy)^4$, but then for the second inequality $(xy)^4=8\times2$, one gets
stuck. In fact it is $x^4y^4$ that is equal to $8\times2$, so switching the
order makes it much easier to follow.
{::nomarkdown}</tr> </tbody> </table>{:/}

## The Symbols '$\Rightarrow$' and '$\Leftrightarrow$'
The first symbol means 'implies' and the second symbol means 'is equivalent to' (or 'if and only if'). They are used to relate different statements and are some of the most frequently used symbols. Yet, they are also some of the most commonly misused symbols.

<table class="demo" cellpadding="8" cellspacing="0" markdown="block">
<thead> <tr> <th>Wrong</th> <th>Correct</th> <th>Comments</th> </tr> </thead>
<tbody> <tr> <td markdown="block">
**If** $\boldsymbol{x=1}$ $\boldsymbol\Rightarrow$ $x+1=2$.
{::nomarkdown}</td> <td markdown="block">{:/}
- If $x=1$**, then** $x+1=2$.
- $\boldsymbol{x=1\Rightarrow}$ $x+1=2$.
{::nomarkdown}</td> <td markdown="block">{:/}
The easiest way to see what is wrong is to convert back to English. The wrong
example reads 'if $x$ equals 1, implies $x+1$ equals 2', which clearly does not
seem correct.
Note that the correct example reads '$x$ equals 1 implies $x+1$ equals 2',
which is perfectly fine.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
Hence we have

$$ x+1=5\ \boldsymbol{\Rightarrow}\ x=4. $$
{::nomarkdown}</td> <td markdown="block">{:/}
Hence we have $x+1=5$**, which implies** $x=4$.
{::nomarkdown}</td> <td markdown="block">{:/}
The problem in the wrong example is that the statement '$x+1=5\Rightarrow x=4$'
is true regardless to what happens before, contrary to what we expect by the
use of the connective 'hence'. The intended meaning was that the previous
argument implies that $x+1=5$, which then implies $x=4$.

Note that one
may try to interpret the wrong example as

$$\begin{align*}
	& (\text{Hence we have}\ x+1=5)\\
	\Rightarrow {} & (x=4).
\end{align*}$$

but this is not correct either since 'hence we have $x+1=5$' is not a statement
(while '$x+1=5$' is).
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
The quadratic function has a critical point at $(2,3)$. From this we see that the point $(2,3)$ must be a maximum.

$$ \boldsymbol{\Rightarrow}\ x=2. $$
{::nomarkdown}</td> <td markdown="block">{:/}
The quadratic function has a critical point at $(2,3)$. From this we see that the point $(2,3)$ must be a maximum
**and therefore** $x=2$.
{::nomarkdown}</td> <td markdown="block">{:/}
In general try not to use a symbol in the middle of nowhere. In the wrong
example it is unclear which statement implies $x=2$. Note that '$\Rightarrow
x=2$' is an incomplete sentence and it must be preceded by a statement. While
'the point $(2,3)$ must be a maximum' is a statement, 'from this we see that
the point $(2,3)$ must be a maximum' is not.
{::nomarkdown}</tr> </tbody> </table>{:/}

## The Symbols '$\forall$' and '$\exists$'

The symbol '$\forall$' reads 'for all' and the symbol '$\exists$' reads
'there exists' and that is precisely what they mean. To see whether the
symbols are used correctly, the easiest way to read the sentence to see
if it is a grammatically correct complete sentence and if it makes
sense.

<table class="demo" cellpadding="8" cellspacing="0" markdown="block">
<thead> <tr> <th>Wrong</th> <th>Correct</th> <th>Comments</th> </tr> </thead>
<tbody> <tr> <td markdown="block">
- Let $A$ be the set of positive odd numbers. Then $2 \vert a+1\ \boldsymbol\exists\,a \in A$.
- If $f(0) <0$, $f(1)>0$ and $f$ is continuous, then $\boldsymbol\forall\, c \in [0,1]$ s.t. $f(c)=0.$
{::nomarkdown}</td> <td markdown="block">{:/}
- Let $A$ be the set of positive odd numbers. Then $2 \vert a+1\ \boldsymbol\forall\,a \in A$.
- If $f(0) <0$, $f(1)>0$ and $f$ is continuous, then $\boldsymbol\exists\, c \in [0,1]$ s.t. $f(c)=0.$
{::nomarkdown}</td> <td markdown="block">{:/}
The wrong examples mixed up the meaning of the symbols '$\forall$' and '$\exists$'.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
$f(c)=0\ \boldsymbol\exists\,c\in [0,1]$.
{::nomarkdown}</td> <td markdown="block">{:/}
- $\boldsymbol{\exists\,c \in [0,1]}\textbf{ s.t. } f(c)=0$.
- $f(c)=0$ **for some** $c\in [0,1]$
{::nomarkdown}</td> <td markdown="block">{:/}
'$\exists$' means 'there exists' rather than 'for some'. Note there is no
proper symbol for 'for some'.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
$\exists\,x \in \mathbb R\ \boldsymbol\forall\,x>1000$.
{::nomarkdown}</td> <td markdown="block">{:/}
$\exists\,x \in \mathbb R$ **s.t.** $x>1000$.
{::nomarkdown}</td> <td markdown="block">{:/}
'$\forall$' means 'for all', not 'such that'.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
Since $\max S=1$, we have $x\le1$ **for** $\boldsymbol\forall\,x\in A.$
{::nomarkdown}</td> <td markdown="block">{:/}
Since $\max S=1$, we have $x\le1$ $\boldsymbol\forall\,x\in A.$
{::nomarkdown}</td> <td markdown="block">{:/}
'$\forall$' reads 'for all', so 'for $\forall$' would read 'for for all' which is wrong.
{::nomarkdown}</td> </tr> <tr> <td markdown="block">{:/}
$\boldsymbol\forall\,x \in \mathbb R$ **s.t.** $x^2 \geq 0$.
{::nomarkdown}</td> <td markdown="block">{:/}
$x^2 \geq 0\ \boldsymbol\forall\, x \in \mathbb R$.
{::nomarkdown}</td> <td markdown="block">{:/}
'$\forall\,x\in\mathbb R$ s.t. $x^2\ge0$' is not even a complete sentence (try to read
it). When 'such that' follows 'for all', we do not really mean 'for all', bur
rather 'for those which satisfy the subsequent condition'. For example, 'for
all positive even integers $n$ such that $n>6$, we can write $n$ as the sum of
two odd primes' --- here we do not really mean 'for all positive even integers
$n$', but only those which satisfy the subsequent condition described after
'such that', i.e. $n>6$.
{::nomarkdown}</tr> </tbody> </table>{:/}

## The Symbols '$\in$' and '$\subseteq$'

The first symbol is set membership and simply reads 'in' or 'belongs to'
and we use it to denote that a certain element lies in a set, for
example $2\in \mathbb{N}$ or $\pi \in \mathbb{R}$. The second one means
'subset' and we use it to denote that a collection of elements all lie
in a certain set, for example
$\mathbb{Z}\subseteq \mathbb{Q}\subseteq \mathbb{R}$.

<table class="demo" cellpadding="8" cellspacing="0" markdown="block">
<thead> <tr> <th>Wrong</th> <th>Correct</th> <th>Comments</th> </tr> </thead>
<tbody> <tr> <td markdown="block">
- $(0,1) \boldsymbol\in \mathbb R$
- If $x=5$, then $x \boldsymbol\subseteq \mathbb R$.
{::nomarkdown}</td> <td markdown="block">{:/}
- $(0,1) \boldsymbol\subseteq \mathbb R$
- If $x=5$, then $x \boldsymbol\in \mathbb R$.
{::nomarkdown}</td> <td markdown="block">{:/}
An interval is a subset of $\mathbb R$, and so the subset symbol '$\subseteq$' should
be used. In the second example $x$ is a real number, so the set membership
symbol '$\in$' should be used.
{::nomarkdown}</tr> </tbody> </table>{:/}

## Overusing Symbols

We conclude this section with a warning on using symbols. While using
symbols correctly is essential for presenting mathematics accurately and
concisely as we have shown throughout this section, there is always a
danger of overusing them. For example, consider the following definition
of a function $f(x)$ being continuous at the point $a$:

- $\forall \varepsilon>0\ \exists \delta>0 \text{ s.t. }
  \left|x-a \right|<\delta
  \Rightarrow \left|f(x)-f(a)\right|<\varepsilon$.

While it is perfectly sound and correct, it is a bit difficult to read.
Reducing the use of symbols would give

- For all $\varepsilon>0$, there exists $\delta >0$ such that
  $\left|f(x)-f(a)\right|<\varepsilon$ whenever
  $\left|x-a\right|<\delta$.

In fact, in professional mathematical writing, symbols are usually kept
to a minimum except when discussing logic. Of course sometimes we may
want to use symbols to save time (e.g. in exam situations). The bottom
line is that they are used correctly and form part of complete
sentences, and that the whole argument is reasonably readable.

- - -

Next: **[The Use of Terminology](terminology.md)**
