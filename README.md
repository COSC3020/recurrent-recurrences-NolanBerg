[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/8KYthzwp)
# Recurrent Recurrences

Sources: Used ai to help with expressions

Give big $\Theta$ bounds for the following recurrence relations.

1.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

Input decreases by 13 every time we recurse. Input size is $n = 13^k$, $k$ = number of recursions. Then $k = \log_{13}(n)$. 

Substitute $n = 13^k$:

$T(13^k) = T(13^{k-1}) + 5$

Expand recursively:

$T(13^k) = T(13^{k-2}) + 10 = T(13^{k-3}) + 15 = \ldots = T(1) + 5k$

$T(1)$ is the base case, $T(n) = 1$ for $( n \leq 1 \)$

$T(n) = 1 + 5k$

Substitute: $k = \log_{13}(n)$:

$T(n) = 1 + 5\log_{13}(n)$

Drop low order terms and constants:

$T(n)$ is $\Theta(\log_{13}(n))$



2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

Input decreases by 13 every time we recurse. Input size is $n = 13^k$, $k$ = number of recursions. Then $k = \log_{13}(n)$.

Substitute $n = 13^k$:

$T(13^k) = 13 T(13^{k-1}) + 5$

Expand recursively:

$T(13^k) = 13^2 T(13^{k-2}) + 13 \cdot 5 + 5 = 13^3 T(13^{k-3}) + 13^2 \cdot 5 + 13 \cdot 5 + 5 = \ldots$

After $i$ iterations:

$T(13^k) = 13^i T(13^{k-i}) + 5 \left(13^0 + 13^1 + \ldots + 13^{i-1}\right)$

Use the sum of geometric series with ratio $r$ from $0$ to $n - 1$:

$13^0 + 13^1 + \ldots + 13^{i-1} = \frac{{13^i - 1}}{{13 - 1}} = \frac{{13^i - 1}}{12}$

Substitute back into $T(13^k)$ expression:

$T(13^k) = 13^i T(13^{k-i}) + \frac{{5(13^i - 1)}}{12}$

Continue until $i = k$. Then $k - i = 0$ and $T(13^{k-i}) = T(1) = 1 \$.

$T(13^k) = 13^k + \frac{{5(13^k - 1)}}{12}$

Drop low order terms and constants:

$T(n)$ is $\Theta(n)$.

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$

$T(n) = 13T\left(\frac{n}{13}\right) + 2n$

Expand Recursively:

$T(n) = 13^2T\left(\frac{n}{13^2}\right) + 13 \times 2\left(\frac{n}{13}\right) + 2n = 13^3T\left(\frac{n}{13^3}\right) + 13^2 \times 2\left(\frac{n}{13^2}\right) + 13 \times 2\left(\frac{n}{13}\right) + 2n = \ldots$

After $i$ iterations:

$T(n) = 13^iT\left(\frac{n}{13^i}\right) + 2n \times \sum_{k=0}^{i-1}13^k$

When $i$ $\frac{n}{13^i} = 1$: 

$\frac{n}{13^i} = 1 \Rightarrow n = 13^i \Rightarrow i = \log_{13}(n)$

Substitute $i = \log_{13}(n)$ into $T(n)$:

$T(n) = 13^{\log_{13}(n)}T(1) + 2n \times \sum_{k=0}^{\log_{13}(n)-1}13^k$

$T(n) = nT(1) + 2n \times \sum_{k=0}^{\log_{13}(n)-1}13^k$

$T(n) = n + 2n \times \frac{13^{\log_{13}(n)} - 1}{13 - 1}$

Drop low order terms and constants:

$T(n)$ is $\Theta(n \log_{13}(n))$

