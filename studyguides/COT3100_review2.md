# COT 3100 Discrete Structures - Exam 1 Review

<p style="text-align:center">
    <a href="../textbooks/COT3100_textbook.pdf">textbook</a> |
    <a href="../flashcards/COT3100_flashcards2.csv">flashcards</a> |
    <a href="https://quizlet.com/957758773/cot-3100-set-laws-identities-flash-cards">quizlet</a>
</p>

**Disclaimer:** This review is a stub. You can help by contributing to the repository.

# 1. Set Logic

- The following can be used in place of identities in formal logic
    - "By definition of ..."

### Set Operators & Constants
| Form                  | Name                  | Set-Builder Notation                                                              |
|-----------------------|-----------------------|-----------------------------------------------------------------------------------|
| $A^C$                 | complement            | { x \| x $\notin$ A }                                                             |
| A $\cup$ B            | union                 | { x \| x $\in$ A $\lor$ x $\in$ B }                                               |
| A $\cap$ B            | intersection          | { x \| x $\in$ A $\land$ x $\in$ B }                                              |
| A - B                 | difference            | { x \| x $\in$ A $\land$ x $\notin$ B }                                           |
| A $\times$ B          | cartesian product     | { (x,y) \| x $\in$ A, y $\in$ B }                                                 |
| A $\Delta$ B          | symmetric difference  | { x \| (x $\in$ A $\land$ x $\notin$ B) $\lor$ (x $\in$ B $\land$ x $\notin$ A) } |
| $\emptyset$           | empty set             | { x \| *false* }                                                                  |
| $\textbf{\textbf{U}}$ | universal set         | { x \| *true* }                                                                   |

- Recall order-of-operations for sets is undefined
- Cartesian product can be found using a table

>**Example:** Perform the Cartesian product $\{x,y,z\} \times \{1,2,3\}$.
>
>| *x* \ *y*    | 1     | 2     | 3     |
>|:------------:|:-----:|:-----:|:-----:|
>| x            | (x,1) | (x,2) | (x,3) |
>| y            | (y,1) | (y,2) | (y,3) |
>| z            | (z,1) | (z,2) | (z,3) |
>
> $= \{(x,1), (x,2), \dots, (z,3)\} \checkmark$

### Set Identities
| Name                  | Intersection Form                                         | Union Form                                                         |
|-----------------------|-----------------------------------------------------------|--------------------------------------------------------------------|
| Identity Law          | A $\cap$ $\textbf{U}$ = A                                 | A $\cup$ $\emptyset$ = A                                           |
| Universal Bound Law   | A $\cap$ $\emptyset$ = $\emptyset$                        | A $\cup$ $\textbf{U}$ = $\textbf{U}$                               |
| Idempotent Law        | A $\cap$ A = A                                            | A $\cup$ A = A                                                     |
| Inverse Law           | A $\cap A^C$ = $\emptyset$                                | A $\cup A^C$ = $\textbf{U}$                                        |
| Commutative Law       | A $\cap$ B = B $\cap$ A                                   | A $\cup$ B = B $\cup$ A                                            |
| Associative Law       | (A $\cap$ B) $\cap$ C = A $\cap$ (B $\cap$ C)             | (A $\cup$ B) $\cup$ C = A $\cup$ (B $\cup$ C)                      |
| Distributive Law      | A $\cup$ (B $\cap$ C) = (A $\cup$ B) $\cap$ (A $\cup$ C)  | A $\cap$ (B $\cup$ C) = (A $\cap$ B) $\cup$ (A $\cap$ C)           |
| Absorption Law        | A $\cap$ (A $\cup$ B) = A                                 | A $\cup$ (A $\cap$ B) = A                                          |
| De Morgan's Law       | $(A \cap B)^C$ = $A^C$ $\cup$ $B^C$                       | $(A \cup B)^C$ = $A^C \cap B^C$                                    |

| Name                          | Form                                  |
|-------------------------------|---------------------------------------|
| Double Complement Law         | $(A^C)^C$ = C                         |
| Set Difference Law            | A - B = A $\cup$ $B^C$                |
| Symmetric Difference Law      | A $\Delta$ B = (A - B) $\cup$ (B - A) |
| Reflexive Law                 | A $\subseteq$ A                       |

- Sets are *mutually disjoint* if all are disjoint from all others
    - $A \cap B \cap C \cap ... \equiv \emptyset$
- The *cardinality* of a set is its size
    - $|A|=$ # of elements in $A$
- A set can be *partitioned* into multiple sets:
    - That are mutually disjoint
    - Whose union is the original set

>**Example:** List two possible partitions of \( \{1,2,3,4,5\} \).
>
>$\{\{1,2\},\{3,5\},\{4\}\}$<br>
>$\{\{2\},\{1\},\{3,4,5\}\}\checkmark$

- Power set, $\mathcal{P}(A)$, is set of all subsets of $A$
    - $\mathcal{P}(\emptyset) = \{ \emptyset \}$
    - $|\mathcal{P}(A)| = 2^{|A|}$

>**Example:** Derive the power set of $\{0,1,2\}$.
>
>$\{\emptyset,\{0\},\{1\},\{2\},\{0,1\},\{0,2\},\{1,2\},\{0,1,2\}\} \checkmark$

- The cardinality of some arbitrary Cartesian product, $|A \times B \times C \times \dots|$, is $|A| \times |B| \times |C| \times \dots$

### Common Set Identities
| Name                          | Identity                                                          | Alternate Form                                                    |
|-------------------------------|-------------------------------------------------------------------|-------------------------------------------------------------------|
| Definition of union           | A $\cup$ B = { x \| x $\in$ A $\lor$ x $\in$ B }                  | $x \in A \cup B \leftrightarrow x \in A \lor x \in B$             |
| Definition of intersection    | A $\cap$ B = { x \| x $\in$ A $\land$ x $\in$ B }                 | $x \in A \cap B \leftrightarrow x \in A \land x \in B$            |
| Definition of set difference  | A - B = { x \| x $\in$ A $\land$ x $\notin$ B }                   | $x \in A - B \leftrightarrow x \in A \land x \notin B$            |
| Definition of set equality    | $A = B \leftrightarrow A \subseteq B \land B \subseteq A$         |                                                                   |

# 2. Relations over Sets

- A *relation* is a subset of the cartesian product of two sets
    - Each pair of elements satisfies some condition (if true, a *relationship*)
    - First set is domain, second is codomain
- For some relation *R*
    - If x $\in$ A is related to y $\in$ B, expressed as x *R* y $\leftrightarrow$ (x,y) $\in$ R
    - If x is not related to y, expressed as x ~~*R*~~ y $\leftrightarrow$ (x,y) $\notin$ R
    - x *R* y does not necessarily imply y *R* x
- Relation from A to A itself is relation *on* A
    - **Ex:** The operator $<$ is a relation on $\textbf{R}$, a subset of $\textbf{R} \times \textbf{R} = \textbf{R}^2$
- *Divides to* is a relationship that states "$x$ divides $y$ if $y$ is divisible by $x$"
    - Represented as $x | y$ or $\frac{x}{y} \in \textbf{Z}$
### Properties of Relations on a Set
| Property              | Definition                                                                        |
|-----------------------|-----------------------------------------------------------------------------------|
| reflexive             | $\forall a \in A,(a,a) \in R$                                                     |
| symmetric             | $\forall a,b \in A, (a,b) \in R \rightarrow (b,a) \in R$                          |
| transitive            | $\forall a,b,c \in A, ((a,b) \in R \land (b,c) \in R) \rightarrow (a,c) \in R$    |
| equivalence           | <small>*symmetric, reflexive, and transitive*</small>                             |

- The *inverse* of a relation is relation with flipped ordered pairs
    - $R^{-1} = \{ (b,a) | (a,b) \in R \}$
    - Same properties apply
- Symmetric relations are equal to their inverse

# 3. Modular Arithmetic

- Used to evaluate operations of the form $a^m \space mod \space n$
    1. Partition *m* into its equivalent powers of 2 (its `1` bits when converted to binary)
    2. For every power of 2, *p*, perform $a^p \space mod \space n$ using the identity $a^m \space mod \space n = (a^\frac{m}{2} \space mod \space n)^2 \space mod \space n$
    3. For every intermediate modulo result, *p'*, multiply them and modulo their product by *n*
- Becomes more efficient the larger the exponent is
- First modulo must always be done by hand

>**Example:** Evaluate $38^{47} \space mod \space 41$.
>
>Partition the exponent into its powers of 2. 
>
>$47 = 32 + 8 + 4 + 2 + 1$
>
>For each power, find the modulo.
>
>$38^1 \space mod \space 41 = 38 \space mod \space 41 = 38$<br>
>$38^2 \space mod \space 41 = (38^1 \space mod \space 41)^2 \space mod \space 41 = 38^2 \space mod \space 41 = 9$<br>
>$38^4 \space mod \space 41 = (38^2 \space mod \space 41)^2 \space mod \space 41 = 9^2 \space mod \space 41 = 40$
>$38^8 \space mod \space 41 = (38^4 \space mod \space 41)^2 \space mod \space 41 = 1^2 \space mod \space 41 = 1$
>$38^16 \space mod \space 41 = (38^8 \space mod \space 41)^2 \space mod \space 41 = 9^2 \space mod \space 41 = 1$
>$38^32 \space mod \space 41 = (38^{16} \space mod \space 41)^2 \space mod \space 41 = 9^2 \space mod \space 41 = 1$
>
>Multiply the intermediate modulo's, taking the remainder of the result.
>
>$(38 \bullet 9 \bullet 40 \bullet 1 \bullet 1 \bullet 1) \space mod \space 41 = 27$
>
>Therefore, $38^{47} \space mod \space 41 = 27 \checkmark$