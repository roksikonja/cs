# Literature Review

## Matrix Approximation

1. ***Local Low-Rank Matrix Approximation by Lee, J., Kim, S., Lebanon, G., Singer, Y.***   

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

1. ***The Power of Convex Relaxation: Near-Optimal Matrix Completion by E. J. Candes and T. Tao.***

    - https://arxiv.org/pdf/0903.1476.pdf
    
    - The Matrix completion problem: Given a matrix $M$ of dimensions $n_1 \times n_2$ and an observation set $\Omega$ with
    $|\Omega| = m << n_1 n_2$, is it possible to reconstruct the matrix only from a small set of observations given that the
    matrix $M$ is of low rank or has an approximately low rank.
    
        - In Collaborative Filtering this makes sense, since often only a few factors (aspects of the movie) contribute to an
        individuals taste.
    
    - Paper presents optimality results on the minimum number of entries $m$ needed to recover a matrix of rank exactly $r$
    by any method whatsoever.
    
    - Rank minimization problem w.r.t. of $X$, $\min rank(X)$, with the constraint of for every $(a, b) \in \Omega$ it 
    holds $X_{a, b} = M_{a, b}$ is NP-hard. However, if minimization of the nuclear norm of $X$ is tractable and results
    in a semidefinite program (c.f. with convex relaxation of the sparsest solution to an minimum $l_1$ norm solution).
        
        - If M obeys low coherence condition and $m$ entries are sampled u.a.r, then w.h.p. $M$ can be reconstructed from samples
        $\Omega$ as long as $m > C n^{6/5} r \log n$.
        
    - Main results are the lower bounds on $m$.

## Applications in MRI

1. ***MR Image Reconstruction From Highly Undersampled k-Space Data by Dictionary Learning by S. Y. Bresler.***

	- Focus on:
		- Upgrade Compressed Sensing notion for MR image reconstruction from undersampled k-space data.
		- Learn dictionary - base in which the signal is sparse - from data.
		- Enforce sparsity in local patches with overlapping. 
		- Iterative two-phase optimization technique.
