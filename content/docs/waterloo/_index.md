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