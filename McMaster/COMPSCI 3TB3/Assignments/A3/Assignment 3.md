# 01 Explaining Regular Expressions (Lab)

Explain in simple words the languages described by following regular expressions. Avoid paraphrasing the regular expression!

1.  `0(0|1)*0`

The set of strings over $\{0, 1\}$ starting and ending with 0 (and therefore of length $\leq$ 2).

2.  `([0]1)*[0]`

The set of strings over {0,1} such that any two 0's are separated by at least one 1.

# 02 Writing Regular Expressions (Lab)

Assume that the vocabulary is `{a, b}`. Give regular expressions for following languages:

1.  All sequences that contain `aa` and contain `bb` !

`((a|b)*aa(a|b)*bb(a|b)*)|((a|b)*bb(a|b)*aa(a|b)*)`

2.  All sequences that do not begin with `aaa`

`(b|ab|aab)(a|b)*`

3.  All sequences in which `aa` occurs exactly once. Note that in `aaa`, it would occur twice.

`([a]b)*aa(b[a])*`

4.  All sequences in which every `a` is either immediately preceded or immediately followed by a `b`, for example `baab`, `aba`, `b`.

`([a]b[a])*`


# 03 Three Formalizations (Lab)

Consider the language `L` of possibly empty strings over the symbols `{a, b, c}` where the first `a` precedes the first `b`.

1.  Give a regular grammar that generates `L`.

`G = (T, N, S, P)` where `T = {a, b, c}`, `N = {X, Y}`, `S = X`, and the productions `P` are:

```
X → cX | ε | aY 
Y → ε | aY | bY | cY
```

2.  Give a regular expression that describes `L`.

```
c*[a(a|b|c)*]
```

3.  Give a finite state automaton that accepts `L`.

`A = (T, Q, R, q₀, F)` where `T = {a, b, c}`, `Q = {q₀, q₁}`, `F = {q₀, q₁}`, and the transitions `R` are:

-   `q₀ c → q₀`
-   `q₀ a → q₁`
-   `q₁ a → q₁`
-   `q₁ b → q₁`
-   `q₁ c → q₁`

Note how `A` is constructed from `G`: `q₀, q₁` corresponds to `X`, `Y`, for every production there is an equivalent transition, the initial state `q₀` corresponds to the start symbol `X`, the final states corresponds to nonterminals that have a production to `ε`.


# 05 Explaining Regular Expressions
Explain in simple words the languages described by following regular expressions. Avoid paraphrasing the regular expression! 

1.  `(a*b*)*`

A language made up of strings that consist of any number of repetitions of the substring "a" followed by any amount of "b"s or both.

2.  `(a*ba*b)*a*`

A language made up of strings that consist of any amount of "a" followed by a single "b", followed by any amount of "a"s, followed by a single "b" again, and finally ending with zero or multiple "a"s.

3.  `(a*[ba*c])*`

A language comprised of a set of strings which consists of `a`s before any sequence of `bac` where there is any amount of `a`s in the string, or an empty set.

# 06 Writing Regular Expressions

Assume that the vocabulary is `{a, b}`. Give a regular expression that describes all sequences that must contain at least two consecutive occurrences of `a`, like `aa`, `baa`, `aaa`, `abaaaaba`! 

`b*aaa*b*a*`

Now give a regular expression of the complement of above language (without using a complement operator), that is those sequences over `{a, b}` that must not contain two or more consecutive occurrences of `a`, but still may have an arbitrary number of occurrences of `a`! 

`(b*ab)*`

Assume that the vocabulary is `{a, b, c}`. Give a regular expression that describes all sequences in which the number of `a` symbols is divisible by three.

`(b|c)*|((b|c)*a(b|c)*a(b|c)*a(b|c)*)*`

Now give a regular expression for sequences with the total number of `b` and `c` symbols being three. 

`a*(b|c)a*(b|c)a*(b|c)a*`

# 07 Regular Grammar to Regular Expression

Here is a regular grammar in EBNF for fractional numbers:

```
N → '0' N | ... | '9' N | '.' F
F → '0' D | ... | '9' D
D → '0' D | ... | '9' D | ''
```

Transform the grammar into a regular expression. Use equalities to simplify the regular expressions. Give every step of the transformation in detail and state the rule that you are applying. 

`F` equivalent production:

`F → ('0'|...|'9')D`

`D` equivalent production:

`D → ('0'|...|'9')D | ''`

Using Arden's rule:

`D → ('0'|...|'9')* ''.`

`D` elimination by substitution into `F`:

`F → ('0'|...|'9')('0'|...|'9')* ''`

Equivalent production for `N`:

`N → ('0'|...|'9')N |'.' F`

By Arden's rule, we simplify:

`N → ('0'|...|'9')* '.' F`

`F` elimination by substituting into `N`:

`N → ('0'|...|'9')* '.' ('0'|...|'9')('0'|...|'9')* ''`

Final equivalent regular expression:

`('0'|...|'9')* '.' ('0'|...|'9')* ''`

# 08 Testing Regular Expression
Using the notation from the course notes, write a regular expression for identifiers: an identifier is a sequence of letters `abcdefghijklmnopqrstuvwxyz` and digits `0123456789` starting with a letter. You may use abbreviations 

`(a|...|z)((a|...|z)*(0|...|9)*)*`  
`[a-z]+ ([a-z]* | [0-9]*)*`

```python
class FiniteStateAutomaton:
    def __init__(self, T, Q, R, q0, F):
        self.T, self.Q, self.R, self.q0, self.F = T, Q, R, q0, F
    def __repr__(self):
        return str(self.q0) + '\n' + ' '.join(self.F) + '\n' + \
               '\n'.join(r[0] + ' ' + r[1] + ' → ' + r[2] for r in self.R)
```

```python
class Choice:
    def __init__(self, e1, e2): self.e1, self.e2 = e1, e2
class Conc:
    def __init__(self, e1, e2): self.e1, self.e2 = e1, e2
class Star:
    def __init__(self, e): self.e = e

```

```python
def string(s: set) -> str:
    return '{' + ', '.join(e for e in s) + '}'

def deterministicFSA(fsa: FiniteStateAutomaton) -> FiniteStateAutomaton:
    qʹ0 = frozenset({fsa.q0})
    Qʹ, Rʹ, visited = {qʹ0}, set(), set()
    # print(Qʹ, Rʹ, visited)
    while visited != Qʹ:
        qʹ = (Qʹ - visited).pop(); visited |= {qʹ}
        for t in fsa.T:
            rʹ = {r for (q, u, r) in fsa.R if u == t and q in qʹ}
            if rʹ != set(): Qʹ |= {frozenset(rʹ)}; Rʹ |= {(qʹ, t, frozenset(rʹ))}
        # print(Qʹ, Rʹ, visited)
    Fʹ = {qʹ for qʹ in Qʹ for f in fsa.F if f in qʹ}
    return FiniteStateAutomaton(fsa.T, {string(qʹ) for qʹ in Qʹ}, 
        {(string(qʹ), t, string(uʹ)) for (qʹ, t, uʹ) in Rʹ},
        string(qʹ0), {string(fʹ) for fʹ in Fʹ})
```

```python
def accepts(fsa: FiniteStateAutomaton, τ: str) -> bool:
    δ = {(q, a): r for (q, a, r) in fsa.R}
    q = fsa.q0
    for t in τ:
        if (q, t) in δ: q = δ[q, t]
        else: return False
    return q in fsa.F
```