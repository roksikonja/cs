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

## Sparse Representations

1. ***K-SVD: An Algorithm for Designing OvercompleteDictionaries for Sparse Representation***

    - Article at https://sites.fas.harvard.edu/~cs278/papers/ksvd.pdf.
    
    - Problem: Given a set $Y = {y_i}_{i=1}^N$ of training signals we assume that there exists a dictionary $D$ that gave rise to
    the given training signals via sparse combinations, i.e. we assume that there exists a dictionary $D$, so that solving
    ($P_0$) for each example $y_i$ gives a sparse representation $x_i$, $y_i = \sum_{j = 1}^K x_{i, j} \cdot d_j$. We
    want to find the best dictionary $D$.
    
    - Sparse coding Problem: Given a signal $y$ and a dictionary $D$ compute a sparse representation representation $x$.
        - Tipically requires solving $P_0$ or $P_{0, \varepsilon}$, which is a NP-hard problem.
        - Approximately solved via "pursuit" algorithms
            - Matching pursuit (MP) and Orthogonal matching pursuit (OMP)- greedy algorithms.
            - Basis pursuit (BP) and FOCUSS - convex $l_1$ relaxation of $l_0$ norm, motivated by MAP.
            
    - Prior art of designing dictionaries.
        - Design of a dictionary is a generalization of K-means algorithm, where each signal is assigned exactly one cluster 
        (sparsity) and the dictionary are the cluster centroids.
        - Maximum likelihood methods: $y = Dx + v$, where $v% is a Gaussian white noise, prior is added on the norm of $x$.
        - Method of optimal directions (MOD) is an iterative algorithm for dictionary construction.
        - Maximum a Posteriori methods: Adds a prior on $D$ and follows an iterative procedure.
        
    - K-SVD is an iterative algorithm, a generalization of K-means algorithm.
        - Objective: $\min \norm{Y - DX}_2$ subject to $\forall i$ it holds $\norm{x}_0 \leq T_0$.
        - Iteration between sparse coding step and codebook update step.
        - Sparse coding: Use any pursuit algorithm to find $X$ given current dictionary $D$
        - Codebook update: Each dictionary column is updated by computing SVD on the corresponding error matrix.
        - Guaranteed improvement at each step and convergence to a local minima.

## Applications in MRI

1. ***MR Image Reconstruction From Highly Undersampled k-Space Data by Dictionary Learning by S. Y. Bresler.***

    - Problem: $\min_{x, D, \Gamma} \sum_{i, j} \norm{R_{i, j} x - D \alpha_{i, j}}_2 + \nu \norm{F_u x - y}_2$ subject to
    $\norm{\alpha_{i, j}}_0 \leq T_0$, where $x$ is the reconstructed image, $y$ the measurements in k-space, $D$ the
     dictionary to be learned, and $\alpha$'s sparse codes of the patches.   
    - Learn dictionary - base in which the signal is sparse - from data suited for a particular, specific task.
    - Enforce sparsity in local patches with overlapping through a patch extraction operator $R_{i, j}$.
    - Iterative two-phase optimization technique.
        - Dictionary learning step: Fix $x$, current reconstructed image estimate, and solve for $D$ and $\Gamma$ by 
        utilizing the K-SVD algorithm, where OMP is used for sparse coding.
        - Updating the reconstruction: Fix $D$ and $\Gamma$, and solve for $x$ through a closed form update.

1. ***Image Reconstruction: From Sparity to Data-adaptive Methods and Machine Learning by S. Ravishankar et al.***

    - Types of reconstruction methods:
        - Analytical: filtered back-projection, inverse Fourier transform.
        - Iterative: reduce noise and artifacts.
        - Sparsity and low-rank.
        - Adaptive or data-driven.
   - Paper gives an overview of the progress of the latter two.
   