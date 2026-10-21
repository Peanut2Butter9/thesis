# Prime-Detecting Quasimodular Forms and Some of Their Congruence Properties

Code for my bachelor's thesis in mathematics at Universitas Gadjah Mada (2026), whose Indonesian title is
*Bentuk Kuasimodular Pendeteksi Prima dan Beberapa Sifat Kongruensinya*.

The thesis studies the quasimodular forms $H_k$ of Craig, van Ittersum and Ono (2024), whose Fourier
coefficients vanish exactly at the primes. It gives complete proofs of the polynomial identities in
MacMahon's partition functions $M_a(n)$ that detect the primes. It also uses a computer search to find
congruences for the coefficients of $H_k$, and then proves them.

## Results

**Prime-detecting forms.** Let $G_k$ be the Eisenstein series of weight $k$ and $D = q \frac{d}{dq}$.
For even $k \ge 6$, define

```math
H_k = \sum_{n \ge 0} b_n(H_k)\, q^n =
\begin{cases}
\frac{1}{6}\left((D^2 - D + 1)G_2 - G_4\right), & k = 6,\\
\frac{1}{24}\left(-D^2 G_{k-6} + (D^2 + 1)G_{k-4} - G_{k-2}\right), & k \ge 8.
\end{cases}
```

For $n \ge 2$, $b_n(H_k) = 0$ if and only if $n$ is prime. Rewriting $H_k$ in terms of the
generating functions of $M_a(n)$ gives identities such as

```math
(n^2 - 3n + 2)\,M_1(n) - 8\,M_2(n) = 0 \iff n \text{ is prime} \qquad (n \ge 2).
```

**Congruences** (Section 4.2). For every even $k \ge 6$:

| Theorem | Statement |
|---|---|
| 4.2.5 | $b_n(H_k)$ is an integer for $n \ge 2$ |
| 4.2.11 | $b_n(H_k) \equiv 0 \pmod 2$ for odd $n$ |
| 4.2.12 | $b_n(H_k) \equiv 0 \pmod 3$ for $n \not\equiv 0 \pmod 3$ |

The congruence notebook checks these for $k \le 40$ and $n \le 10^4$. Its refined search also finds
congruences that hold for every $n \le 10^4$ but are **not proved** in the thesis. Some examples are
$b_n(H_k) \equiv 0 \pmod 8$ for odd $n$ and $b_{3n+2}(H_k) \equiv 0 \pmod 9$. Others depend on the weight,
such as congruences modulo $11$, $19$ and $23$ on the quadratic non-residue classes.

## Notebooks

| Notebook | Kernel | Contents |
|---|---|---|
| [`Congruences_Hk.ipynb`](Congruences_Hk.ipynb) | SageMath | $q$-expansions of $G_k$ and $H_k$, the congruence search of Appendix A, a refined search, and checks of every result in Section 4.2 |
| [`MacMahon_Partitions.ipynb`](MacMahon_Partitions.ipynb) | Python 3 | $M_a(n)$ by enumeration and by generating function, the identities of Theorem 4.1.14, and congruences of $M_2$ and $M_3$ |

Both notebooks are saved with their outputs, so they can be read on GitHub without running them.

### About the search in Appendix A

The search in Appendix A checks the first 100 coefficients of $H_6$ and prints every progression it
finds: 154 congruences of the form $a(tn+b) \equiv 0 \pmod m$. Most of them follow from a few basic
ones. For example, $a(4n+1)$ and $a(6n+5)$ are sub-progressions of $a(2n+1) \equiv 0 \pmod 2$.
Eleven of them stop holding when more coefficients are checked. For example, $a(7n) \equiv 0 \pmod 2$
fails at $a(196) = 1106115$. Section 4 of `Congruences_Hk.ipynb` explains both effects. It then adds a search
that checks $10^4$ coefficients, uses prime-power moduli only and reports only the congruences that
do not follow from shorter ones.

## Running

`Congruences_Hk.ipynb` needs [SageMath](https://www.sagemath.org/) (tested with 10.2) and runs in
about 20 seconds. Start Jupyter with the SageMath kernel and open the notebook:

```bash
sage -n jupyter
```

It also runs on [CoCalc](https://cocalc.com/) with a SageMath kernel.

`MacMahon_Partitions.ipynb` uses plain Python 3 with no packages. Open it in Jupyter, or use the
Colab badge at the top of the notebook.

## References

- W. Craig, J.-W. van Ittersum and K. Ono, *Integer partitions detect the primes*, Proceedings of the
  National Academy of Sciences 121 (39), e2409417121, 2024.
- B. Kane, K. Krishnamoorthy and Y.-K. Lau, *On a conjecture about prime-detecting quasimodular forms*,
  Research in the Mathematical Sciences 12, 60, 2025.
- P. A. MacMahon, *Divisors of numbers and their continuations in the theory of partitions*,
  Proceedings of the London Mathematical Society (2) 19, 1921.
- M. Kaneko and D. Zagier, *A generalized Jacobi theta function and quasimodular forms*,
  Progress in Mathematics 129, 165–172, 1995.

## Citation

```bibtex
@thesis{alfarizi2026prime,
  author      = {Alfarizi, Moh Hasbi},
  title       = {Prime-Detecting Quasimodular Forms and Some of Their Congruence Properties},
  type        = {Bachelor's thesis},
  institution = {Universitas Gadjah Mada},
  address     = {Yogyakarta},
  year        = {2026}
}
```

## License

The code is released under the [MIT License](LICENSE).
