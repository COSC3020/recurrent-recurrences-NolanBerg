[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/8KYthzwp)
# Recurrent Recurrences

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



3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$
