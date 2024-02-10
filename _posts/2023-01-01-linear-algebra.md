---
layout: post
title: Linear Algebra Foundations
date: 2023-01-01 09:02 +0000
math: true
---

# Linear Algebra

**References**:  
Linear algebra - [lecture notes](https://dylandijk.github.io/assets/pdf/MA106LAnotes.pdf)

## Fields
A **field** is a set $S$ with two binary operations (a map from $S \times S$ to $S$ ): Addition and Multiplication.
These two operations are required to satisfy the **field axioms**. For example there must be an Additive and Multiplicative Identity in $S$.

A **Vector Space** over a field  $F$ is a set $V$ together with two binary operations that satisfy the eight axioms listed [here](https://en.wikipedia.org/wiki/Vector_space#Definition_and_basic_properties). In this context, the elements of $V$ are commonly called _vectors_, and the elements of $F$ are called _scalars_. 
-   The first operation, called  _vector addition_  or simply  _addition_  assigns to any two vectors **v**  and  **w**  in  $V$  a third vector in  $V$  which is commonly written as  **v**  +  **w**, and called the  _sum_  of these two vectors.
-   The second operation, called  _[scalar multiplication](https://en.wikipedia.org/wiki/Scalar_multiplication "Scalar multiplication")_，assigns to any scalar a  in  $F$  and any vector **v**  in  $V$  another vector in  $V$, which is denoted _a_**v**

A consequence of the eight axioms for the binary operations is that a linear map always maps the zero vector to the zero vector.
Because one of the axioms is that there exists an additive inverse($-\mathbf{v}$) of $\mathbf{v} \in U$ s.t $\mathbf{v}-\mathbf{v} = \mathbf{0}$. 
Therefore $T(\mathbf{0}_U) = T(\mathbf{v}-\mathbf{v}) = T(\mathbf{v})-T(\mathbf{v}) = \mathbf{0}_V$

For most cases we can just assume that the field $K$ we are using with the set $V$ is $\mathbb{R}$.

*** 

A **Subspace** is a Vector Space contained within another Vector Space.
As an example the set containing just the zero vector is always a subspace.

The **Kernel** and **image** of a linear transformation are subspaces of the domain and codomain vector spaces respectively.

## Linear independence, spanning and bases of vector spaces

 - A set of vectors are **linearly dependent** if there exists a non-trivial linear combination of them that equals zero
 - A set of vectors are **linearly independent** if there does **not**
 - A subset $U \subset V$ **spans** $V$ if every vector in $v \in V$ is a finite linear combination of vectors in $U$

 - A subset $U \subset V$ is a **basis** of $V$ if $U$ is linearly independent and $U$ spans $V$.

	 - The basis of the vector space containing just the zero vector is $\emptyset$. This has no elements so the vector space containing jus the zero vector is zero.
	 - The vector space  $K^n$  has a  standard basis: $\\{\mathbf{e_1} = (1,0,\dots,0), \dots,\mathbf{e_n} = (0,\dots,0,1)\\}$
where 1 denotes the multiplicative identity in $K$.
	- With respect to a different basis, the same vector $\mathbf{v}$ will have different coordinates. **A basis for a vector space can be thought of as a choice of a system of coordinates.**

 

***
- **Proposition**: The vectors $v_1, . . . , v_n$ form a basis of $V$ if and only if every $v \in V$ can be written uniquely as $v = α_1v_1 + · · · + α_nv_n$; that is, the coefficients $α_1, . . . , α_n$ are uniquely determined by the vector $v$.

- **Basis Theorem** - All finite bases of a vector space $V$ contain the same number of vectors.
	-  We call the number of vectors the **dimension** of $V$.
- **Rank-Nullity Theorem** - Let $T : U → V$ be a linear map with $U$ finite dimensional then
$rank(T) + nullity(T) = dim(U)$

## Linear Transformations
Any matrix leads immediately to a linear transformation and we will see that every linear transformation leads to a matrix

- All vectors are mapped to the column space of the matrix

- Let $U$, $V$ be two vector spaces over the same field $K$. A **linear transformation** or linear map $T$ from $U$ to $V$ is a function
$T : U → V$ such that :

	- $T(u_1 + u_2) = T(u_1) + T(u_2)$ for all $u_1, u_2 ∈ U$
	-  $T(αu) = αT(u)$ for all $α ∈ K$ and $u ∈ U$.

Important to note that linear maps are only defined over the same field

- Linear maps are uniquely determined by their action on a basis. i.e If we define a function that maps elements in a basis $S \subset U$ to $V$ then there exists a unique linear transformation such that the mapping of basis vectors as we defined it holds.

For vector spaces $U$,$V$ over a field $K$ we denote the set of all linear maps from $U$ to $V$ as $Hom_K(U, V )$.  
The operations of scalar multiplication and addition on linear maps in the set $Hom_K(U, V )$ makes $Hom_K(U, V )$ into a vector space over $K$.

### One-to-one correspondence between linear maps and matrices
For two vector spaces $U$ and $V$ over a field $K$, of dimension $n$ and $m$ respectively **then for a given choice of basis for each vector space** there is a one-to-one correspondence between linear maps $U \rightarrow V$ and matrices $K^{m,n}$.

Given a linear map $U \rightarrow V$ and a choice of basis for each, $\\{\mathbf{e_1, \dots, e_n}\\}$ and $\\{\mathbf{f_1, \dots, f_n}\\}$. We can construct a matrix $A$, where the $i$th column is given as the coefficients of $T(e_i)$ with respect to the basis of $V$. 

These coefficients are uniquely determined, and therefore the matrix is uniquely determined once we have a choice of basis for each vector space.

On the otherhand if we are given a matrix $A$ this tells us what each element of the basis $U$ is mapped to. And we know that linear maps are uniquely determined by their action on a basis.

***

- For example the the identity map $I_V : V → V$ with $I_V (v) = v \quad \forall v ∈ V$ when we choose identical basis. Has corresponding matrix $A$, as constructed above, as the identity matrix with size given by the dimension of the vector space $V$. As the columns of $A$ will just be a vector with a 1 in the corresponding position of the basis vector and 0s elsewhere.

- Given $U$ and $V$ and respective basis, let $T$ be a linear map $U \rightarrow V$, and $A$ the matrix which represents $T$ w.r.t the chosen basis. Let the column vectors $\underline{\mathbf{u}} \in K^n$, $\underline{\mathbf{v}} \in$ be the coordinates of vectors $\mathbf{u} \in U$, $\mathbf{v} \in V$ w.r.t the chosen bases.
Then  $\quad T(\mathbf{u}) = \mathbf{v} \iff A\underline{\mathbf{u}} = \underline{\mathbf{v}}$ 

	-	If we use a standard bases for both the domain and codomain then the corrdinate vectors are just the vectors themselves. Therefore  
	$T(\mathbf{u}) = \mathbf{v} \iff A\mathbf{u} = \mathbf{v}$


### Isomorphisms
*For this section on isomorphisms I have used the [book by Jim Hefferon](https://leanpub.com/linalgebra)*

- An **isomorphism** between two vector spaces  $U$ and $V$ over a field $K$, is a **bijective** linear map $T:U \rightarrow V$.

	-	When such a map exists, then $U$ is **isomorphic** to $V$.

***
- **Isomorphism is an equivalence relation between vector spaces.**

- **Vector spaces are isomorphic if and only if they have the same dimension.**
Outline of proof (helps with intuition):

	-	($\Rightarrow$) 
	Let $\\{\mathbf{e_1}, \dots, \mathbf{e_n} \\}$ be a basis for $U$, then $\\{T(\mathbf{e_1}), \dots, T(\mathbf{e_n}) \\}$ forms a basis of $V$.

	-	($\Leftarrow$) 
	The map $\quad e:U \rightarrow K^n \quad$ mapping the vectors of $U$ to their coordinates with respect to a chosen basis of $U$ is an isomorphism. 
	Therefore any space of dimension $n$ is isomorphic to $K^n$, and by transitivity of isomorphisms all vector spaces of the same dimension are isomorphic to each other.

From the outline of the proof can see that every vector space $U$ over $K$ of dimension $n$ is isomorphic to $K^n$.

***



## Rank of a matrix
$T : U → V \quad$
- **image** $\quad im(T) = \\{T(\mathbf{u}) : \mathbf{u} \in U\\}$
- **kernel**  $\quad ker(T) = \\{\mathbf{u} \in U\ : T(\mathbf{u}) = \mathbf{0}_v\\}$

- **rank**   $\quad dim(im(T))$

 If the vector spaces $U$ and $V$ have the same dimension $\, dim(U) = dim(V) = n \,$. Then we have the following statement:

> $T$ is *bijective* $\iff$ $rank(T)=n$
{: .prompt-info }



***

$im(T)$ is *spanned* by the vectors $T(\mathbf{e_1}),\dots,T(\mathbf{e_n})$. And for a set of vectors that spans a vector space there exists a subsequence which forms a basis (can be shown with the *sifting process*).  By definition, this subset has size $rank(T)$. 
Also if a vector space has dimension $n$ then any $n$ linearly independent vectors in that vector space is a basis and no $n+1$ vectors can be *linearly independent*.

Therefore the rank of $T$ is the largest linearly independent subset of $T(\mathbf{e_1}),\dots,T(\mathbf{e_n})$.

***

The **column space** of a matrix is the subspace of $K^{m,1}$(column vectors over field $K$) spanned by the columns $c_1, \dots , c_n$ of $A$. 
The **column rank** of $A$ is equal to the dimension of the column space of $A$.


> Let $U,V$ be vector spaces over the field $K$ with chosen bases $\mathbf{e},\mathbf{f}$, and $T$ a linear map $T:U \rightarrow V$.
Then the $rank(T)$ is equal to the column rank of the the matrix $A$ representing $T$ w.r.t our chosen bases. 
{: .prompt-tip }

**Proof:**

Let $T'$ denote the linear map $T':K^n \rightarrow K^m$, defined by the matrix $A$.  
$im(T'$) is equal to the column space of $A$, and therefore the $rank(T')$ equals the column rank of $A$.

Now will show $rank(T')$ = $rank(T)$. As we will then have:
column rank of A = $rank(T')$ = $rank(T)$

The map $T'$ can be written as $f^{-1} \circ T \circ e^{-1}$, where $f^{-1}, e^{-1}$ are the  **isomorphisms** $f^{-1}: K^m \rightarrow U$, $e^{-1}: K^n \rightarrow U$ that map coordinates back to their vectors. 
Isomorphisms preserve dimension and therefore $rank(T)$ equals $rank(T').$

***
	
- $rank$ of $T$ is the largest linearly independent subset of $T(\mathbf{e_1}),\dots,T(\mathbf{e_n})$.

> The column and row rank of a matrix $A$ are equal. This is called the rank of $A$. A matrix is **full rank** if its rank is the highest possible for a matrix of the same size.
{: .prompt-info }

Other useful results about the rank of matrices:
> Let $A$ be an $m \times n$ matrix and $B$ an $n \times p$ matrix. Then $rank(AB) \leq min(rank(A), rank(B))$
{: .prompt-info }

> Let $A$ be an $m \times n$ matrix, then $rank(A^TA) = rank(AA^T) = rank(A)$
{: .prompt-info }

> Orthogonal matrices are full rank.
{: .prompt-info }


## The inverse of a linear transformation and of a matrix

### Lets first cover a recap of functions and their inverses.

A function $f$, mapping from sets $X$ to $Y$ $f:X \rightarrow Y$ .
- Has a left inverse $g$ if $g \circ f = I_X$, that is the left composition gives the identity map.
- And has a right inverse $h$ if $f \circ h = I_X$

An inverse that is both a left and right inverse (a **two-sided inverse**), if it exists, must be unique. In fact, if a function has a left inverse and a right inverse, they are both the same two-sided inverse, so it can be called the inverse $f ^−$.
- A function has a two-sided inverse if and only if it is bijective


***

### Inverses of linear maps

Let $T$ be a linear map $T:U \rightarrow V$, from the function recap above $T$ is invertible if $T^{-1}T = I_U$ and  $TT^{-1} = I_V$.  Also we can show that if a linear map has a two-sided inverse then that inverse is also linear.

If we select a basis for $U$ and $V$ we can get our corresponding matrix $A \; (n \times m)$  for the linear map $T$. If $T$ is invertible then there exists $A^{-1}$ such that $AA^{-1} = I_n$ and  $A^{-1}A = I_m$. 

***

If we were given a matrix $A$, and a left inverse and right inverse of that matrix they would have to be equal. As the existence of these matrices would imply that the corresponding function of $A$ has a left and right inverse. And if a function has a left inverse and a right inverse, they are both the same two-sided inverse. Therefore, the right and left inverse matrices must be equal.

***

> If $T$ is invertible, then $dim(U) = dim(V ), \,$ so only square matrices can be invertible.
{: .prompt-tip }

**Proof:**

If any function *T* has a left and right inverse, then it must be a bijection.  
Hence $ker(T) = {0}$ and $im(T) = V$ , so $nullity(T) = 0$ and $rank(T) = dim(V ) = m$.  
But by the rank-nullity theorem, we have $n = dim(U) = rank(T) + nullity(T) = m + 0 = m$.

***
So we know that if $T$ is invertible then the dimension of the domain ($U$) and codomain ($V$) is equal, let this be $n.$  
And if $T$ is invertible then the $im(T)$ is equal to $V$ therefore the $rank(T) = dim(V) = n$.  We also know that the rank of a linear map is equal to the rank of the corresponding matrix therefore the column rank of $A$ is equal to $n$.

In summary if $A$ is invertible $\implies$ column rank of $A$ is equal to $n$.

Explicitly using what I we have written above:  
$T$ is invertible $\iff$ $\, T$ is bijective $\iff$ $\, rank(T) = dim(U) = dim(V) = rank(A) \iff A \,$ is full rank.

> $T$ is invertible $\iff$ corresponding matrix $A$ is full rank.
{: .prompt-info }



## Change of basis and equivalent matrices
Let $U$ be a vector space of dimension $n$, and let $e_1, . . . , e_n$ and $e_1' , . . . , e_n'$ be two bases of $U$.
The matrix $P$ of the identity map $I_U : U → U$ using the basis $e_1, . . . , e_n$ in the domain and $e_1' , . . . , e_n'$ in the range is called the **change of basis matrix** from the basis of $e_i$s to the basis of $e'_i$s.

With the matrix $P$  we have that $P\underline{\mathbf{v}} = \underline{\mathbf{v'}}$, where $\underline{\mathbf{v}}$ is the coordinates of $\mathbf{v}$ w.r.t the basis $\mathbf{e}$ and $\underline{\mathbf{v'}}$ is the coordinates of $\mathbf{v}$ w.r.t the basis $\mathbf{e'}$.
Therefore $P$ can be seen as the matrix which turns a vector’s coordinates with respect to the “old” basis into the same vector’s coordinates with respect to the “new” basis.

- The change of basis matrix is invertible with the inverse matrix corresponding to the choice of basis being switched.

In fact:  
> A matrix is a change of basis matrix $\iff$
it is invertible
{: .prompt-info }

***
 If we have a linear map $T:U \rightarrow V$ and two different pairs of basis for the domain and codomain $\mathbf{e},\mathbf{f}$ and $\mathbf{e'},\mathbf{f'}$. Represented by the matrices $A$ and $B$ respectively then we have that $B=QAP^{-1}$.

- Two $m \times n$ matrices $A$ and $B$ are said to be **equivalent** if there exist invertible $P$ and $Q$ with $B = QAP$
	- Every invertible matrix is a change of basis matrix.
- Equivalence between matrices gives an equivalence relation
- The following are equivalent:
	- A and B are equivalent.
	- A and B represent the same linear map with respect to different pairs of bases.
	- A and B have the same rank.

- Any matrix is equivalent to the Smith normal form matrix with the Identity matrix part being of size $s$ where $s$ is the rank of the matrix.
 
***
The definition of **similar** matrices is the same as **equivalent** matrices but now we restrict the domain and codomain vector spaces to be the same.

Two matrices are **similar** if and only if they represent the same linear map $T : V → V$ with respect to different bases of $V$.


## Eigenvectors and eigenvalues

- A Hermitian matrix (includes real symmetric matrices) is positive definite if and only if all its eigenvalues are positive.




## Projections

- A projection is a map from a vector space to itself $P:V \rightarrow V$, often a subspace, such that $P^2 = P$
	- We can write any point in the space $V$ as the sum of an element from $Im(P)$ and $Ker(P)$.

- An **orthogonal projection** is a projection for which the image and the null space are orthogonal subspaces
- A projection is orthogonal if and only if it is **self-adjoint**/**symmetric**
	- A self-adjoint matrix with real entries is called symmetric

> If we have a vector space $V$ with subspace $U$, out of all projections with image $U$. The projection that minimises the distance from a point $v \in V$ to its projected element $u \in U$, is **the** orthogonal projection.
{: .prompt-tip }

**Proof:**  

Let $v \in V$ and $u \in U$ and $\pi()$ be the orthogonal projector. 
By the Pythagorean theorem we have that:
$||v - u||^2 = ||v - \pi(v)||^2 + ||\pi(v) - u||^2 \geq ||v - \pi(v)||^2$  

So $\pi(v) \in Im(\pi)$ and $u \in Im(\pi)$. 
Therefore $\pi(v) - u\in Im(\pi)$.

$\pi(v - \pi(v)) = 0$ therefore $v - \pi(v) \in ker(\pi)$

Therefore $v - \pi(v)$ and  $\pi(v) - u$ are orthogonal, so can use  Pythagorean theorem.

Now can see that the minimum is attained if we let $u = \pi(v)$. I.e the projection to the subspace U that minimises the distance is the orthogonal projection.




- In an inner-product space, the  **Pythagorean theorem**  states that for any two orthogonal vectors  **v**  and  **w**  we have 
$||v + w||^2 = ||v||^2 + ||w||^2$