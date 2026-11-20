# Lecture Note 12 — Exercise 2
## Handwritten proof using the requested general lemma

We want to prove:

\[
\boxed{\forall L,\quad rev1(rev1(L))=L}
\]

**The main lemma is exactly the general lemma requested:**

\[
\boxed{rev1(rev1(L_1)@L_2)=rev1(L_2)@L_1}
\]

We first prove this lemma by structural induction on \(L_1\), then use it to prove the theorem.

### Definitions used

Concatenation:

\[
nil@L=L
\]

\[
(E|L_1)@L_2=E|(L_1@L_2)
\]

Recursive reverse:

\[
rev1(nil)=nil
\]

\[
rev1(E|L)=rev1(L)@(E|nil)
\]

We also reuse the associativity theorem proved in Exercise 1:

\[
\boxed{(L_1@L_2)@L_3=L_1@(L_2@L_3)}
\]

---

## Part A. Supporting property: right identity of concatenation

For the base case of the general lemma, we need:

\[
\boxed{L@nil=L}
\]

This is a supporting property, not a replacement for the requested general lemma.

**Structural induction on \(L\).**

### (I) Base case: \(L=nil\)

\[
nil@nil=nil
\]

This follows directly from the definition of concatenation.

### (II) Induction case: \(L=E|L'\)

**IH:**

\[
L'@nil=L'
\]

Then:

\[
\begin{aligned}
(E|L')@nil
&=E|(L'@nil) &&\text{(definition of } @\text{)}\\
&=E|L' &&\text{(IH).}
\end{aligned}
\]

Therefore:

\[
\boxed{L@nil=L}
\]

---

## Part B. General Lemma

**Lemma 2**

\[
\boxed{rev1(rev1(L_1)@L_2)=rev1(L_2)@L_1}
\]

We prove this by structural induction on \(L_1\).

### (I) Base case: \(L_1=nil\)

We need to prove:

\[
rev1(rev1(nil)@L_2)=rev1(L_2)@nil.
\]

Left-hand side:

\[
\begin{aligned}
rev1(rev1(nil)@L_2)
&=rev1(nil@L_2) &&\text{(definition of } rev1\text{)}\\
&=rev1(L_2) &&\text{(definition of } @\text{).}
\end{aligned}
\]

Right-hand side:

\[
\begin{aligned}
rev1(L_2)@nil
&=rev1(L_2) &&\text{(supporting property }L@nil=L\text{).}
\end{aligned}
\]

Thus both sides are equal, so the base case holds.

### (II) Induction case: \(L_1=E_1|L\)

**Induction hypothesis (IH):**

\[
rev1(rev1(L)@L_2)=rev1(L_2)@L.
\]

We need to prove:

\[
rev1(rev1(E_1|L)@L_2)=rev1(L_2)@(E_1|L).
\]

Proof:

\[
\begin{aligned}
&rev1(rev1(E_1|L)@L_2)\\
={}&rev1((rev1(L)@(E_1|nil))@L_2)
&&\text{(definition of } rev1\text{)}\\
={}&rev1(rev1(L)@((E_1|nil)@L_2))
&&\text{(associativity of } @\text{, Exercise 1)}\\
={}&rev1((E_1|nil)@L_2)@L
&&\text{(IH, with }L_2=(E_1|nil)@L_2\text{)}\\
={}&rev1(E_1|L_2)@L
&&\text{(definition of } @\text{)}\\
={}&(rev1(L_2)@(E_1|nil))@L
&&\text{(definition of } rev1\text{)}\\
={}&rev1(L_2)@((E_1|nil)@L)
&&\text{(associativity of } @\text{, Exercise 1)}\\
={}&rev1(L_2)@(E_1|L)
&&\text{(definition of } @\text{).}
\end{aligned}
\]

Therefore, the induction case holds, and the general lemma is proved.

---

## Part C. Theorem 3 — Reverse twice

**Theorem 3**

\[
\boxed{rev1(rev1(L_1))=L_1}
\]

We prove this by structural induction on \(L_1\), using the general Lemma 2.

### (I) Base case: \(L_1=nil\)

\[
\begin{aligned}
rev1(rev1(nil))
&=rev1(nil) &&\text{(definition of } rev1\text{)}\\
&=nil &&\text{(definition of } rev1\text{).}
\end{aligned}
\]

Hence the base case holds.

### (II) Induction case: \(L_1=E|L\)

**Induction hypothesis (IH):**

\[
rev1(rev1(L))=L.
\]

We need to prove:

\[
rev1(rev1(E|L))=E|L.
\]

Proof:

\[
\begin{aligned}
&rev1(rev1(E|L))\\
={}&rev1(rev1(L)@(E|nil))
&&\text{(definition of } rev1\text{)}\\
={}&rev1(E|nil)@L
&&\text{(general Lemma 2, with }L_1=L,\ L_2=E|nil\text{)}\\
={}&(rev1(nil)@(E|nil))@L
&&\text{(definition of } rev1\text{)}\\
={}&(nil@(E|nil))@L
&&\text{(definition of } rev1\text{)}\\
={}&(E|nil)@L
&&\text{(definition of } @\text{)}\\
={}&E|(nil@L)
&&\text{(definition of } @\text{)}\\
={}&E|L
&&\text{(definition of } @\text{).}
\end{aligned}
\]

Thus the induction case holds.

Therefore, by structural induction:

\[
\boxed{\forall L_1,\quad rev1(rev1(L_1))=L_1.}
\]

---

## What is reused from Exercise 1?

- **Theorem 1 (`assoc@`)** is explicitly reused in the induction case of the general lemma.
- The definitions of concatenation and `rev1` are reused directly from the LIST1 specification.
- The tail-recursive reverse lemma and theorem from Exercise 1 (`p-sr2`, `ctrr`) are not needed here.
- The supporting property \(L@nil=L\) is proved because the base case of the requested general lemma needs it.
- The requested general lemma is proved independently; the target theorem is never assumed.
