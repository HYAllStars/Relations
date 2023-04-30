# Notes on Closure Operators 

Let A be any set.  A binary relation on A is any subset of A × A = \{(x, y) : x ∈ A, y ∈ A\}.

Here are some important examples of binary relations on A:

+  1<sub>A</sub> := A × A = the "all" relation
+  0<sub>A</sub> := D = \{(x, x) : x ∈ A\} = the "equality" relation; aka the "identity" or "diagonal" relation
+  ∅ = the empty relation

Here are some less important examples. Let A = \{0, 1, 2\}, then the following are relations on A:

+  R = \{(0, 1)\}
+  S = \{(0, 1), (1, 1)\}
+  T = \{(0, 1), (1, 2), (2, 1)\}
+  < = \{(0, 1), (0, 2), (1, 2)\}
+  ≤ = \{(0, 0), (0, 1), (0, 2), (1, 1), (1, 2), (2, 2)\}

Common notations for the expression (x, y) ∈ R are x R y (infix notation) and R x y (postfix notation).


## Transitive Closure

Recall, a relation R on a set A is called *transitive* provided ∀ x, y, z ∈ A → R x y → R y z → R x z.

The *transitive closure* of a relation R ⊆ A × A is the smallest relation on A that contains R and is transitive.

----------

**Exercise 1**.  Let A = \{0, 1, 2\}.  Find the transitive closures of all the relations mentioned above: 1<sub>A</sub>, 0<sub>A</sub>, ∅, R, S, T, <, ≤.

------------

Let ℙ(A × A) denote the collection of all binary relations on A (i.e., all subsets of A × A).

Let C : ℙ(A × A) → ℙ(A × A) be the *transitive closure operator*.

That is, for each relation R ∈ ℙ(A × A), the transtive closure of R is the relation C R.

-------------

**Exercise 2**.  Prove that C is a closure operator.  That is, C satisfies the following three closure properties:

+ C is **extensive**: ∀ R ∈ ℙ(A × A) → R ⊆ C R.

+ C is **monotone**: ∀ R, S ∈ ℙ(A × A) → R ⊆ S → C R ⊆ C S.

+ C is **idempotent**: ∀ R ∈ ℙ(A × A) → C (C R) = C R.


-------------------

## Solutions

**Solution 1**. 

+  Notice that 1<sub>A</sub>, 0<sub>A</sub>, ∅, R, S, <, and ≤ are all transitive relations so their transitive closures are just themselves: C 1<sub>A</sub> = 1<sub>A</sub>, C 0<sub>A</sub> = 0<sub>A</sub>, C ∅ = ∅, C R = R, C S = S, C < = <, C ≤ = ≤.

   For example, if R x y, then x = 0 and y = 1 and for every z ∈ A, (y , z) ∉ R, so at most one antecedent of the transitive property holds---either R x y or R y z---but not both, so since the premise is false, the consequent is true.  The same argument applies to D.
   
   For S, the only way to fulfill the antecendents of the transitive property is to let x = 0, y = 1, z = 1, in which case the consequent of the transitive property (R 0 1) holds.

+  The transitive closure of T = \{(0, 1), (1, 2), (2, 1)\}:

   First consider the transitive closure of each two-element subset of T.
   
   C \{(0, 1), (1, 2)\} = \{(0, 1), (1, 2), (0, 2)\}

   C \{(0, 1), (2, 1)\} = \{(0, 1), (2, 1)\}

   C \{(1, 2), (2, 1)\} = \{(1, 1), (1, 2), (2, 1), (2, 2)\}
   
   The union of these is U = \{(0, 1), (0, 2), (1, 1), (1, 2), (2, 1), (2, 2)\} and clearly U must be contained in the transitive closure of T.
   
   What else could be in C T?  To find out, notice that we only need to consider each pairs of pairs in U and see what they generate via the transitive property. 
   
   That is, we consider the transitive closure of every two element subset of U (that we haven't already looked at above) and we find that all of these closures are already contained in U, so U is in fact the transitive closure of T. That is,

   C T = \{(0, 1), (0, 2), (1, 1), (1, 2), (2, 1), (2, 2)\}.


**Solution 2**.

+  That C is extensive is obvious from the definition of C R as the smallest relation *that contains R*.  That is, R ⊆ C R is baked right into the definition.

+  C is monotone.  Indeed, let R, S be relations on A and assume R ⊆ S.  By extensivity, S ⊆ C S, therefore R ⊆ C S.  Now, C S is transitive and C R is defined to be the *smallest* transitive relation containing R, therefore C R ⊆ C S. 

+  C (C R) is the smallest transitive relation containing C R, but C R is already transitive, so it C (C R) = C R!


-------------------------


## Reflexive Closure

Recall, a relation R on a set A is called *reflexive* provided ∀ x ∈ A → R x x.

The *reflexive closure* of a relation R ⊆ A × A is the smallest relation on A that contains R and is reflexive.  This is very easy to compute, since it is simply R ∪ 0<sub>A</sub>.  That is, reflexive closure of a relation R ⊆ A × A is simply R ∪ \{(x, x) : x ∈ A\}.


## Symmetric Closure

Recall, a relation R on a set A is called *symmetric* provided ∀ x, y ∈ A → R x y → R y x.

The *symmetric closure* of a relation R ⊆ A × A is the smallest relation on A that contains R and is symmetric.  This is very easy to compute, since it is simply R ∪ R⃖ where R⃖:= \{(x, y) : (y, x) ∈ R\}. 






