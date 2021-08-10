---
layout: post
mathjax: true
title: The Pohlig-Hellman Algorithm for solving a special case of the Discrete Log Problem

---

{% include mathjax.html %}

The *Pohlig-Hellman Algorithm* helps solve the *Discrete Log Problem* for Finite Fields whose order can be factored into prime powers of smaller primes. The algorithm reduces the computation of the discrete log in the Finite Field $G$ to the computation of the discrete log in prime order subgroups of **⟨G⟩**

For e.g. Order of $GF(p)=p−1=p1^{n1}.p2^{n2}.p3^{n3}…$

The PH algorithm allows your solve the DLP in the smaller subgroups of order $p1^{n1}, p2^{n2}, p3^{n3} etc and then combine the solutions using the *Chinese Remainder Theorem* to get the solution for the original DLP.    

---   

**The Algorithm**

Let $g$ be a generator in $GF(p)$

$y \equiv g^x \bmod p$

$y, p and g$ are known. The discrete log problem here is to find $x$

Order of $GF(p)=p−1=p_1^{n_1}.p_2^{n_2}.p_3^{n_3}…$

Let’s take the prime power factors one by one.  

*First consider $p_1^{n_1}$*

Let $x$ be the solution for the subgroup of order $p_1^{n_1}$

First we expand $x$ as a base $p_1$ number.

Note: For e.g. if $p_1=2$, then we have to expand $x$ in base 2 (i.e. do a binary expansion). If x is 13, then in binary (base 2), we can write it as $1101$.

So the binary expansion of $x=13$ will be

$x=13=1101=1 . 2^0 + 0. 2^1 + 1.2^2 + 1.2^3$

If we are solving for $\bmod 2^n$, then the max value of $x$ can only be $2^n −1$. The number $2^n$ in binary representation needs $n+1$ bits. So the number $2^n −1$ will need $n$ bits. Hence when we expand $x$ in base 2, we will have $n$ co-efficients from $0$ to $n−1$

For any base, we do it similarly

$x=\sum_{i=0}^{n−1} a_ip_1^i where $a_i \in {0,…,p−1}$

$x=a_0+ a_1p_1 + a_2{p_1}^2 +…$

$y \equiv g^{a_0+ a_1{p_1}+ a_2{p_1}^2+…} \bmod p$ [substituting x by its expansion]

$y^{\frac{p−1}{p_1} \equiv (g^{a_0+a_1{p_1}+a_2{p_1}^2+…)^{\frac {p−1}{p_1} \bmodp$ [Raise both sides to $\frac {p−1}{p_1}$]

$y^{\frac {p−1}{p_1} \equiv g^(a_0+a_1{p_1}+a_2{p_1}^22+…)(\frac {p−1}{p_1}) \bmod p$

$y^{\frac {p−1}{p_1} \equiv g^{a0 \frac {p−1} {p_1}} . g^{a_1{p_1}\frac{p−1}{p_1}}.g^a_2{p_1}^2 \frac{p−1}{p_1}… \bmod p$


