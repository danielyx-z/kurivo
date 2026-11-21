---
weight: 50
title: Math 138
---

### Some Interesting Substitutions

#### 1. Rationalizing Substitutions
When $\sqrt[n]{f(x)}$ appears in an integrand, the substitution $u = \sqrt[n]{f(x)}$ (or $u^n = f(x)$) can convert non-rational functions into rational functions.

try:
- $\int \frac{\sqrt{x+9}}{x} \, dx$
- $\int \frac{\sqrt{1+\sqrt{x}}}{x} \, dx$

---

#### 2. Weierstrass Substitution (Tangent Half-Angle Substitution)
A rational function of $\sin(x)$ and $\cos(x)$ can be converted into a rational function using the substitution $u = \tan\left(\frac{x}{2}\right)$, or $x = 2\arctan(u)$.

**Key Identities:**
- $\cos(x) = \frac{1-u^2}{1+u^2}$
- $\sin(x) = \frac{2u}{1+u^2}$
- $dx = \frac{2}{1+u^2} \, du$

try:
- $\int \frac{1}{1 + \cos(x)} \, dx$
- $\int \frac{dx}{1 - \cos(x) + \sin(x)}$

### Accelerations (i like this name)

Slowly converging series (like $\sum \frac{1}{n^2}$) need a huge number of terms for a few correct digits. An acceleration rewrites the sum so that it converges much faster.

#### 1. Kummer's Acceleration
To compute $\sum a_n$, find a series $\sum b_n$ whose sum $B$ is **known exactly**, with
$$\lim_{n\to\infty} \frac{a_n}{b_n} = \gamma \neq 0.$$
Then
$$\sum a_n = \gamma B + \sum \left(a_n - \gamma b_n\right).$$
Since $a_n$ and $\gamma b_n$ agree to leading order, the terms $a_n - \gamma b_n$ go to $0$ faster than $a_n$, so the new series converges faster.

**Idea:** subtract off the part of the series you can sum exactly. What's left is small.

**Useful known sums (telescoping):**
- $\sum_{n=1}^\infty \frac{1}{n(n+1)} = 1$
- $\sum_{n=1}^\infty \frac{1}{n(n+1)(n+2)} = \frac{1}{4}$

**Example:** $\sum_{n=1}^\infty \frac{1}{n^2}$ with $b_n = \frac{1}{n(n+1)}$, $\gamma = 1$:
$$\frac{1}{n^2} - \frac{1}{n(n+1)} = \frac{1}{n^2(n+1)}$$
$$\implies \sum_{n=1}^\infty \frac{1}{n^2} = 1 + \sum_{n=1}^\infty \frac{1}{n^2(n+1)}$$
The terms went from $\sim \frac{1}{n^2}$ to $\sim \frac{1}{n^3}$. Repeating with $b_n = \frac{1}{n(n+1)(n+2)}$:
$$\sum_{n=1}^\infty \frac{1}{n^2} = 1 + \frac{1}{4} + 2\sum_{n=1}^\infty \frac{1}{n^2(n+1)(n+2)}$$
and now the terms are $\sim \frac{1}{n^4}$.

try:
- $\sum_{n=1}^\infty \frac{1}{n^3}$ using $b_n = \frac{1}{n(n+1)(n+2)}$ (how fast do the new terms decay?)
- $\sum_{n=1}^\infty \frac{1}{n^2+1}$ using $b_n = \frac{1}{n(n+1)}$

---

#### 2. Euler–Maclaurin Acceleration
Sum the first $N-1$ terms directly, then estimate the **tail** with an integral plus corrections. For a smooth, decreasing $f$:
$$\sum_{n=N}^\infty f(n) \approx \int_N^\infty f(x)\,dx + \frac{f(N)}{2} - \frac{f'(N)}{12}$$

**Idea:** the integral test says $\sum f(n) \approx \int f$. The $\frac{f(N)}{2}$ term is the trapezoid-rule correction, and the $\frac{f'(N)}{12}$ term fixes the curvature the trapezoids miss.

**Example:** $\sum \frac{1}{n^2}$, where $f(x) = \frac{1}{x^2}$ and $f'(x) = -\frac{2}{x^3}$:
$$\sum_{n=N}^\infty \frac{1}{n^2} \approx \frac{1}{N} + \frac{1}{2N^2} + \frac{1}{6N^3}$$
With $N = 10$: $\sum_{n=1}^{9}\frac{1}{n^2} \approx 1.5397677$, and the tail is $\approx 0.1051667$, so the total is $1.6449344$. Compare $\frac{\pi^2}{6} = 1.6449341\ldots$: about 6 correct digits from 9 terms. Plain summation needs about $10^6$ terms for that.

try:
- estimate $\sum_{n=1}^\infty \frac{1}{n^3}$ with $N = 5$
- how many terms of plain $\sum \frac{1}{n^2}$ give 3 correct decimals? (use the integral test bound)

### Lagrange error bound proof

**Statement:** Let $P_n$ be the degree-$n$ Taylor polynomial of $f$ centered at $a$, and $R_n = f - P_n$. If $|f^{(n+1)}(t)| \le M$ for all $t$ between $a$ and $x$, then
$$|R_n(x)| \le \frac{M}{(n+1)!}|x-a|^{n+1}.$$

**Idea:** speed limit. If you start at $0$ and your speed is at most $M$, after time $t$ you're at most $Mt$ away. The error $R_n$ starts at $0$ with all its first $n$ derivatives $0$, and its $(n+1)$th derivative is bounded. Integrate $n+1$ times.

**Proof** (for $x > a$; $x < a$ is symmetric):

$P_n$ matches $f$ and its first $n$ derivatives at $a$, and $P_n^{(n+1)} = 0$ (degree $n$). So
- $R_n(a) = R_n'(a) = \cdots = R_n^{(n)}(a) = 0$
- $R_n^{(n+1)} = f^{(n+1)}$, so $|R_n^{(n+1)}(t)| \le M$

Integrate from $a$ to $t$ repeatedly, using that each lower derivative starts at $0$:
$$|R_n^{(n)}(t)| \le M(t-a)$$
$$|R_n^{(n-1)}(t)| \le \frac{M(t-a)^2}{2!}$$
$$\vdots$$
$$|R_n(x)| \le \frac{M(x-a)^{n+1}}{(n+1)!} \qquad \blacksquare$$

**Notes:**
- $n=0$ is just the MVT: $|f(x)-f(a)| \le M|x-a|$.
- $n=1$ is physics: start at rest with acceleration $\le M$, so distance $\le \frac{1}{2}Mt^2$.
- The $(n+1)!$ is bookkeeping from integrating $n+1$ times. It's also why Taylor series work: the factorial beats $|x-a|^{n+1}$.
- **Use:** proving $R_n(x) \to 0$ shows a Taylor series actually equals $f$. E.g. for $e^x$ at $0$: $M = e^{|x|}$ and $\frac{|x|^{n+1}}{(n+1)!} \to 0$, so $e^x = \sum \frac{x^n}{n!}$ for all $x$.