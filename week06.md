# Week 06
In this session, the key discussion was centered about the **Singular Value Decomposition** (SVD) of an arbitary $m\times n$ real matrix $A$. The important points covered during the discussion:
* For any real $m\times n$ matrix $A$, the matrices $A^TA$ and $AA^T$ have the **same non-zero** eigenvalues.
* The eigenvalues of $A^TA$ (or those of $AA^T$) are **non-negative**. In particular, the non-zero eigenvalues must be **strictly positive**.
* Let these positive eigenvalues be $\lambda_1$, $\lambda_2$, $\ldots$, $\lambda_r$ (where $r$ is the rank of matrix $A$). Then, the **singular values** of the matrix $A$ are the numbers 
    $$
     \sigma_1 = \sqrt{\lambda_1} \\
     \sigma_2 = \sqrt{\lambda_2} \\
    \vdots \\
    \sigma_r = \sqrt{\lambda_r}
    $$
* Work out the eigenvectors of $A^TA$ associated with the eigenvalues $\lambda_1$, $\lambda_2$, $\ldots$, $\lambda_r$. Let them be $v_1$, $v_2$, $\ldots$, $v_r$. These are referred to as the **right singular vectors** of the matrix $A$. Now extend this set, using Gram-Schimdt to an orthonormal set 
   $$
    \{ v_1, v_2, \ldots, v_r, v_{r+1}, \ldots, v_n\}
  $$
  Construct the matrix $Q_2$ with these vectors as columns:
  $$
   Q_2 = \begin{bmatrix} \vert   & \vert & & \vert \\
           v_1 & v_2 & \ldots & v_n \\
         \vert   & \vert & & \vert 
       \end{bmatrix} 
$$            
*  Work out the eigenvectors of $AA^T$ associated with the eigenvalues $\lambda_1$, $\lambda_2$, $\ldots$, $\lambda_r$. Let them be $u_1$, $u_2$, $\ldots$, $u_r$. These are referred to as the **left singular vectors** of the matrix $A$. Now extend this set, using Gram-Schimdt to an orthonormal set 
   $$
    \{ u_1, u_2, \ldots, u_r, u_{r+1}, \ldots, u_m\}
  $$
   Construct the matrix $Q_1$ with these vectors as columns:
  $$
   Q_1 = \begin{bmatrix} \vert   & \vert & & \vert \\
           u_1 & u_2 & \ldots & u_m \\
         \vert   & \vert & & \vert 
       \end{bmatrix} 
$$    
* The SVD of $A$ is then 
  $$
  A = Q_1 \Sigma \ Q_2^T
  $$
   where ${\displaystyle \Sigma}$ is an $m \times n $ having the structure:
$$
\Sigma = \begin{bmatrix}
\sigma_1 &  & & & \\
& \sigma_2 & & & \\
& & \ddots && \\
& & & \sigma_r & \\
& & & & 0  
\end{bmatrix}_{m\times n}
$$
 
* In practice, however, we needn't workout the eigenvectors for both $A^TA$ and $AA^T$. It is useful to do it only for one them. If $m < n$, then the size of $AA^T$ is smaller. Work out the left singular vectors $u_i$'s and then obtain $r$ of the right singular vectors $v_i$'s using 
   $$
     v_i = \dfrac{1}{\sigma_i} A^T u_i
  $$
  Then extend the set $\{ v_1, v_2, \ldots, v_r\}$ to have $n$ orthonormal vectors using Gram Schimdt orthogonalization. 

* If $n < m$, then the size of $A^TA$ is smaller. Work out the right singular vectors $v_i$'s and then obtain $r$ of the left singular vectors $u_i$'s using 
   $$
     u_i = \dfrac{1}{\sigma_i} A u_i
  $$
  Then extend the set $\{ u_1, u_2, \ldots, u_r\}$ to have $m$ orthonormal vectors using Gram Schimdt orthogonalization. 

* It is instructive to note that the columns of $Q_1$ and $Q_2$ give the orthonormal bases for all four fundamental subspaces:
   
   | | | | |
   | -------- | :-----------:| --------- | -------- |
   | first |   $r$ | columns of $Q_1$ : | **column space** of $A$ |
   | last | $m-r$ | columns of $Q_1$: | **left nullspace** of $A$ | 
   | first |  $r$ |  columns of $Q_2$ : | **row space** of $A$ |
   | last | $n-r$ | columns of $Q_2$: | **nullspace** of $A$ | 

* We can write $A$ as the sum of rank 1 matrices in the following way:
   $$
     A = \sigma_1 u_1v_1^T + \sigma_2 u_2v_2^T + \ldots + \sigma_r u_rv_r^T
   $$
