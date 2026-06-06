# Miscellaneous

## Handwriting

It is important to write in a neat and legible manner. The following
lists some frequently confused characters:

- '$t$' vs '$+$'
- '$1$' vs '$l$' vs '$I$'  (in particular the natural logarithm is '$\ln$',
  not '$\mathrm{In}$'!)
- '$x$' vs '$\times$'
- '$p$' vs '$\rho$'
- '$a$' vs '$\alpha$' vs '$2$'
- '$0$' vs '$6$' vs '$\sigma$'

On a side note, Greek letters are extensively used by mathematicians (26
English letters are often insufficient!). One should learn all the Greek
letters in order to master the mathematical language.

## Presentation

Always write in clear order (avoid writing in 'two columns' on the same
page as it usually hinders reading) and cross out unwanted materials
(cross out those and only those words which you don't want; crossing out
one word more or one word fewer can lead to a totally different
meaning). Highlighting the final answer sometimes also helps make the
overall presentation neater.

Also, there are certain expressions such as $\dfrac{1}{2x}$ and
$\dfrac{1}{2}x$ which you need to distinguish carefully. Sometimes it
also helps by writing with proper indentation. For example,

is more readable than

## Avoiding Isolated Equations

We began this writing guide by saying that complete sentences should be
used in mathematical writing. We conclude it by saying that complete
*paragraphs* should be used. In short, this means we should avoid
writing a few isolated equations without explaining the logical
relationship between them. For example, consider the following:

$$\begin{align*}
  5x+1 &=16 \\
  5x &=15\\
  x&=3
\end{align*}$$

This is probably how primary and secondary school
students 'write mathematics'. Indeed these can be considered as complete
sentences. (Try to read them: '5 times $x$ plus 1 is equal to 16. 5
times $x$ is equal to 15. $x$ is equal to 3.' Three complete sentences!)
However when put together this makes no sense --- what are we trying to
say? Are we *assuming* the first equation holds? Or is it true that the
first equation *does* hold because of some reason? Furthermore, what is
the relationship between these equations? These are important issues and
must be clarified by using proper connectives or symbols. For instance,
two possible ways to connect these equations together are as follows:

1.  According to the question, we have $5x+1=16$. Since
    $5x+1=16 \Leftrightarrow 5x=15 \Leftrightarrow x=3$, we conclude
    that the value of $x$ is 3.

2.  It follows from our previous discussion that $5x+1=16$. This is
    equivalent to $5x+1=15$, or $x=3$.

If you are still not convinced of the importance of avoiding isolated
equations, consider the following (wrong) demonstration:

$$\begin{align*}
  \sqrt{x-2} &=x-4 \\
  x-2 &=x^2-8x+16\\
  x^2-9x+18&=0\\
  (x-3)(x-6)&=0\\
  x&=3\text{ or }6
\end{align*}$$

Yet if we plug $x=3$ into the original equation, the two
sides are not equal. Some would argue that *since we have squared both
sides*, it is necessary that we check the 'solutions' obtained at the
end. However this explanation is neither complete nor convincing ---
apart from naturally asking why (squaring both sides would matter), you
can easily find many other examples in which you would end up with such
'wrong solutions' even though you haven't squared both sides in the
process. Ultimately, it is the relationship between different equations
that matters.

The above can be rewritten as follows:

- To solve the equation $\sqrt{x-2}=x-4$, we note that

  $$\begin{align*}
      \sqrt{x-2}=x-4\ &\Longrightarrow\ x-2 =x^2-8x+16 \\
      &\Longrightarrow\ x^2-9x+18=0\\
      &\Longrightarrow\ (x-3)(x-6)=0 \end{align*}$$

  Hence the only possible values of $x$ are 3 and 6. When
  $x=3$, the left hand side of the equation is 1 while the right hand
  side is $-1$; when $x=6$ both sides are equal to 2. Thus we conclude
  that $x=6$ is the only solution.

As the last piece of advice, try to learn mathematical writing by
reading how professional mathematicians write. Pay special attention to
how words and symbols are integrated to form complete sentences, and how
complete sentences are linked together by connectives to form coherent
paragraphs that present rigorous mathematical arguments.
