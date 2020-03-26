# Literature Review

***1. Local Low-Rank Matrix Approximation by Lee, J., Kim, S., Lebanon, G., Singer, Y.***   

- http://proceedings.mlr.press/v28/lee13.html and http://jmlr.org/papers/v17/14-301.html (extended)

- Problem: Approximate a matrix $M$ with dimensions $n_1 \times n_2$ by a rank $r$ matrix $\hat{M} = U V^T$, where
$U$ with dimensions $n_1 \times r$ and $V$ with dimensions $n_2 \times r$ from a set $\Omega$ of $m$ observed entries 
$\{M_{a, b} : (a, b) \in \Omega \}$ of $M$.

- Extention of the notion of low-rank, the matrix behaves as a low rank matrix in the vicinity of certain row-column 
combinations.

- Estimator of $M$ is a smoothed convex combination of $q$ low-rank matrices ($T$), each of which approximates $M$ in a local region.

- Low-rank Matrix Approximation can be posed as an incomplete SVD or compressive sensing problem. 

- Each $T$ is solved as a modified (kernel smoothed) optimization problem similar to original LRMA problem.

- Local Low-rank matrix aproximation algorithm (LLORMA) is proposed. For $t = 1, \ldots, q$, $T_t$ is computed in 
parallel with the anchor point $s_t$ selected at random by solving regularized SVD for $U_t$ and $V_t$. 