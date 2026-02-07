---
title: "Fermat's Little Theorem"
date: 2024-04-25
excerpt: "An introduction to Fermat's Little Theorem with a proof by induction and its application to modular inverse in competitive programming."
tags: ["Number Theory", "Competitive Programming", "Mathematics"]
---

In this article, I will introduce Fermat's Little Theorem and a simple algorithm problem where this theorem can be applied.

<div class="figure">
  <img src="https://upload.wikimedia.org/wikipedia/commons/f/f3/Pierre_de_Fermat.jpg" alt="Portrait of Pierre de Fermat" width="280" />
  <div class="caption">Pierre de Fermat (1607–1665)</div>
</div>

Fermat's Little Theorem states that if $p$ is a prime number, then for all integers $a$, $(a^p - a)$ is an integer multiple of $p$. This is represented in the following modular arithmetic notation:

$$a^p \equiv a \pmod{p}$$

Equivalently, if $a$ is not divisible by $p$:

$$a^{p-1} \equiv 1 \pmod{p}$$

If $p$ is not a prime number, but satisfies the equation above for all integers $a$, then that number is called a **Carmichael number**. Some Carmichael numbers are: 561, 1105, 1729, 2465, 2821...

## Proof of Fermat's Little Theorem

I will prove Fermat's Little Theorem using mathematical induction on $a$.

**Base case:** When $a = 0$,

$$0^p - 0 = 0 \equiv 0 \pmod{p} \quad \checkmark$$

**Inductive step:** Assume the theorem holds for some non-negative integer $a$, i.e., $a^p \equiv a \pmod{p}$. We want to show it holds for $a + 1$.

By the binomial theorem:

$$(a+1)^p = \sum_{k=0}^{p} \binom{p}{k} a^k = a^p + \binom{p}{1}a^{p-1} + \binom{p}{2}a^{p-2} + \cdots + \binom{p}{p-1}a + 1$$

For $1 \leq k \leq p-1$, the binomial coefficient $\binom{p}{k} = \frac{p!}{k!(p-k)!}$ is divisible by $p$ because $p$ is prime and cannot be cancelled by $k!$ or $(p-k)!$. Therefore:

$$\binom{p}{k} \equiv 0 \pmod{p} \quad \text{for } 1 \leq k \leq p-1$$

This gives us:

$$(a+1)^p \equiv a^p + 1 \pmod{p}$$

By the inductive hypothesis, $a^p \equiv a \pmod{p}$, so:

$$(a+1)^p \equiv a + 1 \pmod{p} \quad \blacksquare$$

## Application in Competitive Programming

The key application of Fermat's Little Theorem is computing the **modular multiplicative inverse**. If we need to compute $a^{-1} \pmod{p}$ (where $p$ is prime and $\gcd(a, p) = 1$), we use:

$$a^{-1} \equiv a^{p-2} \pmod{p}$$

This follows directly from $a^{p-1} \equiv 1 \pmod{p}$, which gives us $a \cdot a^{p-2} \equiv 1 \pmod{p}$.

You can easily calculate this using **binary exponentiation** (also known as fast power):

```cpp
long long fastpow(long long base, long long exp, long long mod) {
    long long result = 1;
    base %= mod;
    while (exp > 0) {
        if (exp & 1)
            result = result * base % mod;
        base = base * base % mod;
        exp >>= 1;
    }
    return result;
}

// Modular inverse of a modulo p (p must be prime)
long long mod_inverse(long long a, long long p) {
    return fastpow(a, p - 2, p);
}
```

There are many competitive programming problems that require computations modulo $10^9 + 7$ (1000000007) or $998244353$, which are both prime numbers. Whenever you need to divide under a modulus — for example, computing $\binom{n}{k} \mod p$ — Fermat's Little Theorem gives you the tool to do it:

$$\binom{n}{k} \equiv n! \cdot (k!)^{p-2} \cdot ((n-k)!)^{p-2} \pmod{p}$$

---

**References**

- Long, C. L. (1965). *Elementary introduction to number theory.*
- Singh, N. (2022, August 21). Fermat's little theorem. GeeksforGeeks. [https://www.geeksforgeeks.org/fermats-little-theorem/](https://www.geeksforgeeks.org/fermats-little-theorem/)

*Originally published on [Medium](https://junehahwang.medium.com/fermats-little-theorem-404323a2f0b7).*
