---
title: "Euler's Phi Function"
date: 2024-04-25
excerpt: "An introduction to Euler's totient function — how it works, why it works, and a C++ implementation for competitive programming."
tags: ["Number Theory", "Competitive Programming", "C++"]
---

<div class="figure">
  <img src="https://upload.wikimedia.org/wikipedia/commons/6/60/Leonhard_Euler_2.jpg" alt="Portrait of Leonhard Euler" width="280" />
  <div class="caption">Leonhard Euler (1707–1783)</div>
</div>

When given a positive integer $n$, Euler's phi function (EPF), also called Euler's totient function, finds the number of positive integers less than or equal to $n$ that are relatively prime with $n$. EPF is conventionally represented using the Greek letter phi, $\varphi$.

For example, when $n = 16$, there are 8 numbers that are relatively prime with $n$: 1, 3, 5, 7, 9, 11, 13, and 15. Therefore,

$$\varphi(16) = 8$$

## How does the EPF work?

### 1. When $n$ is prime

Because $n$ is only divisible by 1 and itself (note that 1 is relatively prime with any integer),

$$\varphi(n) = n - 1$$

### 2. When $n$ is a prime raised to some power

If $n = p^k$ ($p$ is an arbitrary prime number), the only numbers that divide $n$ are 1 and multiples of $p$. The multiples of $p$ that are less than $p^k$ are: $p, 2p, 3p, \ldots, (p^{k-1}-1)p$. It can be seen that there are $p^{k-1} - 1$ multiples of $p$. Also, since 1 is relatively prime with $p^k$, there is a total of $p^{k-1}$ numbers that are not relatively prime with $p^k$. Thus,

$$\varphi(p^k) = p^k - p^{k-1}$$

### 3. When $n = a \times b$ where $a$ and $b$ are relatively prime

Because $n$ has to be relatively prime to both $a$ and $b$, we can find the number of relatively primes for $a$ and $b$ separately. This is a consequence of the Chinese Remainder Theorem:

$$\varphi(a \times b) = \varphi(a) \cdot \varphi(b) \quad \text{when } \gcd(a, b) = 1$$

## Conclusion

We can prime factorize $n$ like the following:

$$n = p_1^{a_1} \cdot p_2^{a_2} \cdot p_3^{a_3} \cdots p_k^{a_k}$$

By using part 3 (multiplicativity), the EPF for $n$ is:

$$\varphi(n) = \varphi(p_1^{a_1}) \cdot \varphi(p_2^{a_2}) \cdots \varphi(p_k^{a_k})$$

Then, by using part 2,

$$\varphi(n) = (p_1^{a_1} - p_1^{a_1 - 1})(p_2^{a_2} - p_2^{a_2 - 1}) \cdots (p_k^{a_k} - p_k^{a_k - 1})$$

By simplifying, we get:

$$\varphi(n) = n \prod_{p \mid n} \left(1 - \frac{1}{p}\right)$$

<div class="figure">
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/9b/EulerPhi.svg" alt="Plot of Euler's totient function" width="500" />
  <div class="caption">Plot of φ(n) for the first 1000 integers</div>
</div>

## C++ Code for EPF

The following is my C++ code for EPF. The maximum input for $n$ is $10^9$.

```cpp
// Euler's phi function
int EPF(int n) {
    vector<pair<int, int>> factors;
    for (int j: p) { // p is a vector of prime numbers
        int cnt = 0;
        while (n % j == 0) {
            cnt++;
            n /= j;
        }
        if (cnt != 0) factors.push_back({j, cnt});
    }
    // n can have at most one factor greater than sqrt(n).
    if (n != 1) factors.push_back({n, 1});

    ll ret = 1;
    for (auto x: factors) {
        ret *= fastpow(x.first, x.second) - fastpow(x.first, x.second - 1);
    }
    return ret;
}
```

The algorithm works by:
1. Finding the prime factorization of $n$ by trial division
2. Applying the formula $\varphi(p^k) = p^k - p^{k-1}$ for each prime power
3. Multiplying the results together (using the multiplicative property)

The time complexity is $O(\sqrt{n})$, dominated by the prime factorization step.

---

**References**

- 3.8 The Euler Phi Function. [https://www.whitman.edu/mathematics/higher_math_online/section03.08.html](https://www.whitman.edu/mathematics/higher_math_online/section03.08.html)

*Originally published on [Medium](https://junehahwang.medium.com/eulers-phi-function-ba96d34b663a).*
