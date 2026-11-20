# I217 Functional Programming – Lecture Note 12
## Exercises 1 and 2: Manual proofs

This version follows the organization of Lecture Note 12:

- `LIST1`: list constructors, concatenation, `rev1`, and Theorem 1 (`assoc@`).
- `LIST2`: the list operations with associative concatenation, together with `rev2` and `sr2`; this is the context used for Lemma 1 (`p-sr2`) and Theorem 2 (`ctrr`).
- Exercise 2 is proved separately using one additional lemma.

---

# Exercise 1

## 1. List specification

A list is constructed in two ways:

1. `nil` is the empty list.
2. If `E` is an element and `L1` is a list, then `E | L1` is a list whose first element is `E` and whose remaining list is `L1`.

Concatenation is defined recursively on its first argument:

\[
\begin{aligned}
 nil @ L_2 &= L_2 && (@1)\\
 (E|L_1) @ L_2 &= E | (L_1 @ L_2) && (@2)
\end{aligned}
\]

The recursive reverse is:

\[
\begin{aligned}
 rev1(nil) &= nil && (r1\text{-}1)\\
 rev1(E|L_1) &= rev1(L_1) @ (E|nil) && (r1\text{-}2)
\end{aligned}
\]

The tail-recursive reverse is:

\[
\begin{aligned}
 rev2(L_1) &= sr2(L_1,nil) && (r2)\\
 sr2(nil,L_2) &= L_2 && (sr2\text{-}1)\\
 sr2(E|L_1,L_2) &= sr2(L_1,E|L_2) && (sr2\text{-}2)
\end{aligned}
\]

## 2. Theorem 1 – Associativity of concatenation (`assoc@`)

**Theorem.**

\[
(L_1@L_2)@L_3 = L_1@(L_2@L_3)
\]

**Proof.** By structural induction on `L1`.

### I. Base case: \(L_1=nil\)

We need to show:

\[
(nil@l_2)@l_3 = nil@(l_2@l_3).
\]

Left-hand side:

\[
(nil@l_2)@l_3 \xrightarrow{(@1)} l_2@l_3.
\]

Right-hand side:

\[
 nil@(l_2@l_3) \xrightarrow{(@1)} l_2@l_3.
\]

Both sides reduce to the same term. Thus, the base case holds.

### II. Induction case: \(L_1=e|l_1\)

**Induction hypothesis (IH):**

\[
(l_1@L_2)@L_3 = l_1@(L_2@L_3).
\]

We need to show:

\[
((e|l_1)@l_2)@l_3 = (e|l_1)@(l_2@l_3).
\]

Left-hand side:

\[
\begin{aligned}
((e|l_1)@l_2)@l_3
&\xrightarrow{(@2)} (e|(l_1@l_2))@l_3\\
&\xrightarrow{(@2)} e|((l_1@l_2)@l_3)\\
&\xrightarrow{(IH)} e|(l_1@(l_2@l_3)).
\end{aligned}
\]

Right-hand side:

\[
(e|l_1)@(l_2@l_3)
\xrightarrow{(@2)} e|(l_1@(l_2@l_3)).
\]

Both sides reduce to the same term. Thus, the induction case holds, and `assoc@` is proved.

---

## 3. Lemma 1 – A property of `sr2` (`p-sr2`)

**Lemma.**

\[
sr2(L_1,E_2|L_2)=sr2(L_1,nil)@(E_2|L_2).
\]

**Proof.** By structural induction on `L1`. The induction-case proof uses the associativity of `@` established in Theorem 1.

### I. Base case: \(L_1=nil\)

We need to show:

\[
sr2(nil,e_2|l_2)=sr2(nil,nil)@(e_2|l_2).
\]

Left-hand side:

\[
sr2(nil,e_2|l_2)\xrightarrow{(sr2\text{-}1)}e_2|l_2.
\]

Right-hand side:

\[
\begin{aligned}
sr2(nil,nil)@(e_2|l_2)
&\xrightarrow{(sr2\text{-}1)}nil@(e_2|l_2)\\
&\xrightarrow{(@1)}e_2|l_2.
\end{aligned}
\]

Both sides reduce to the same term. Thus, the base case holds.

### II. Induction case: \(L_1=e|l_1\)

**Induction hypothesis (IH):**

\[
sr2(l_1,E_2|L_2)=sr2(l_1,nil)@(E_2|L_2).
\]

We need to show:

\[
sr2(e|l_1,e_2|l_2)=sr2(e|l_1,nil)@(e_2|l_2).
\]

Left-hand side:

\[
\begin{aligned}
sr2(e|l_1,e_2|l_2)
&\xrightarrow{(sr2\text{-}2)}sr2(l_1,e|e_2|l_2)\\
&\xrightarrow{(IH)}sr2(l_1,nil)@(e|e_2|l_2).
\end{aligned}
\]

Right-hand side:

\[
\begin{aligned}
sr2(e|l_1,nil)@(e_2|l_2)
&\xrightarrow{(sr2\text{-}2)}sr2(l_1,e|nil)@(e_2|l_2)\\
&\xrightarrow{(IH)}(sr2(l_1,nil)@(e|nil))@(e_2|l_2)\\
&\xrightarrow{(assoc@)}sr2(l_1,nil)@((e|nil)@(e_2|l_2))\\
&\xrightarrow{(@2)}sr2(l_1,nil)@(e|(nil@(e_2|l_2)))\\
&\xrightarrow{(@1)}sr2(l_1,nil)@(e|e_2|l_2).
\end{aligned}
\]

Both sides reduce to the same term. Thus, the induction case holds, and `p-sr2` is proved.

---

## 4. Theorem 2 – Correctness of tail-recursive reverse (`ctrr`)

**Theorem.**

\[
rev1(L_1)=rev2(L_1).
\]

**Proof.** By structural induction on `L1`. We use Lemma 1 (`p-sr2`).

### I. Base case: \(L_1=nil\)

Left-hand side:

\[
rev1(nil)\xrightarrow{(r1\text{-}1)}nil.
\]

Right-hand side:

\[
\begin{aligned}
rev2(nil)&\xrightarrow{(r2)}sr2(nil,nil)\\
&\xrightarrow{(sr2\text{-}1)}nil.
\end{aligned}
\]

Thus, the base case holds.

### II. Induction case: \(L_1=e|l_1\)

**Induction hypothesis (IH):**

\[
rev1(l_1)=rev2(l_1).
\]

We need to show:

\[
rev1(e|l_1)=rev2(e|l_1).
\]

Left-hand side:

\[
\begin{aligned}
rev1(e|l_1)
&\xrightarrow{(r1\text{-}2)}rev1(l_1)@(e|nil)\\
&\xrightarrow{(IH)}rev2(l_1)@(e|nil)\\
&\xrightarrow{(r2)}sr2(l_1,nil)@(e|nil).
\end{aligned}
\]

Right-hand side:

\[
\begin{aligned}
rev2(e|l_1)
&\xrightarrow{(r2)}sr2(e|l_1,nil)\\
&\xrightarrow{(sr2\text{-}2)}sr2(l_1,e|nil)\\
&\xrightarrow{(p\text{-}sr2)}sr2(l_1,nil)@(e|nil).
\end{aligned}
\]

Both sides reduce to the same term. Thus, the induction case holds, and `ctrr` is proved.

---

# Exercise 2

We must prove:

\[
\boxed{rev1(rev1(L))=L}
\]

for every list `L`.

We first prove an auxiliary lemma. This lemma is not the theorem itself, so it can safely be used in the theorem's proof.

## 1. Lemma 2 – Reverse after appending one element

**Lemma.**

\[
rev1(L_1@(E|nil))=E|rev1(L_1).
\]

**Proof.** By structural induction on `L1`.

### I. Base case: \(L_1=nil\)

We need to show:

\[
rev1(nil@(e|nil))=e|rev1(nil).
\]

Left-hand side:

\[
\begin{aligned}
rev1(nil@(e|nil))
&\xrightarrow{(@1)}rev1(e|nil)\\
&\xrightarrow{(r1\text{-}2)}rev1(nil)@(e|nil)\\
&\xrightarrow{(r1\text{-}1)}nil@(e|nil)\\
&\xrightarrow{(@1)}e|nil.
\end{aligned}
\]

Right-hand side:

\[
e|rev1(nil)\xrightarrow{(r1\text{-}1)}e|nil.
\]

Both sides reduce to `e | nil`. Thus, the base case holds.

### II. Induction case: \(L_1=e_1|l_1\)

**Induction hypothesis (IH):**

\[
rev1(l_1@(E_2|nil))=E_2|rev1(l_1).
\]

We need to show:

\[
rev1((e_1|l_1)@(e_2|nil))=e_2|rev1(e_1|l_1).
\]

Left-hand side:

\[
\begin{aligned}
&rev1((e_1|l_1)@(e_2|nil))\\
&\xrightarrow{(@2)}rev1(e_1|(l_1@(e_2|nil)))\\
&\xrightarrow{(r1\text{-}2)}rev1(l_1@(e_2|nil))@(e_1|nil)\\
&\xrightarrow{(IH)}(e_2|rev1(l_1))@(e_1|nil)\\
&\xrightarrow{(@2)}e_2|(rev1(l_1)@(e_1|nil)).
\end{aligned}
\]

Right-hand side:

\[
\begin{aligned}
e_2|rev1(e_1|l_1)
&\xrightarrow{(r1\text{-}2)}e_2|(rev1(l_1)@(e_1|nil)).
\end{aligned}
\]

Both sides reduce to the same term. Thus, the induction case holds, and Lemma 2 is proved.

---

## 2. Theorem 3 – Reverse of reverse (`rev1(rev1(L)) = L`)

**Theorem.**

\[
rev1(rev1(L))=L.
\]

**Proof.** By structural induction on `L`. We use Lemma 2.

### I. Base case: \(L=nil\)

\[
rev1(rev1(nil))
\xrightarrow{(r1\text{-}1)}rev1(nil)
\xrightarrow{(r1\text{-}1)}nil.
\]

Thus, the base case holds.

### II. Induction case: \(L=e|l\)

**Induction hypothesis (IH):**

\[
rev1(rev1(l))=l.
\]

We need to show:

\[
rev1(rev1(e|l))=e|l.
\]

\[
\begin{aligned}
rev1(rev1(e|l))
&\xrightarrow{(r1\text{-}2)}rev1(rev1(l)@(e|nil))\\
&\xrightarrow{\text{Lemma 2}}e|rev1(rev1(l))\\
&\xrightarrow{(IH)}e|l.
\end{aligned}
\]

Thus, the induction case holds. Therefore,

\[
\boxed{rev1(rev1(L))=L}
\]

for all lists `L`.

---

## 3. CafeOBJ proof-score mapping

The accompanying `.cafe` file contains these proof-score sections in this order:

1. `LIST1` – base and induction cases of `assoc@`.
2. `LIST2` – base and induction cases of `p-sr2`.
3. `LIST2` – base and induction cases of `ctrr`.
4. `LIST2` – base and induction cases of Lemma 2.
5. `LIST2` – base and induction cases of `rev1(rev1(L)) = L`.

For Exercise 1, the `LIST2` specification declares concatenation with the `{assoc}` attribute. This makes the associativity of concatenation available in the `p-sr2` proof, matching the use of `(assoc@)` in the slide's manual derivation. The explicit induction proof of `assoc@` remains in `LIST1`.
