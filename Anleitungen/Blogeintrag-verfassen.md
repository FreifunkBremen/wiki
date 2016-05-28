# Blogeintrag verfassen


## Markdown Spezialitäten zu beachten
Im Gegensatz zum Github-Markdown, verhält sich unsere Website leicht anders, deswegen ist die Vorschau beim Website-Editor bei Github, nicht imme korrekt:
- vor Listen muss eine Freizeile gelassen werden
- 

test

#### Code

Code can be inline, `using backticks`. Or it can be in blocks, either with backtick "fences" or with indents of four spaces. (I prefer fences.)

```python
print('You get syntax highlighting...')
print('...if you include the language name')
```

You can also syntax-highlight some other cool stuff, like file diffs:
```diff
- This line got removed
+ This line got added
```

#### Math

Math forumlae use TeX. Some examples:

##### The quadratic equation
$-b \pm \sqrt{b^2 - 4ac} \over 2a$

##### The probability of getting (k) heads when flipping (n) coins
$\[P(E)   = {n \choose k} p^k (1-p)^{ n-k} \]$

##### The Lorenz Equations
$\dot{x} = \sigma(y-x) \\ \dot{y} = \rho x - y - xz \\ \dot{z} = -\beta z + xy$

##### The Cauchy-Schwarz Inequality
$\[ \left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right) \]$

[Math examples are from here](http://www.mathjax.org/demos/tex-samples/)