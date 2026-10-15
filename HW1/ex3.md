# 3. Explanation of How `oedc-fact(5)` Is Computed in CafeOBJ

## 1. Understanding the Program

The given CafeOBJ program computes the factorial using the **odd-even divide-and-conquer (OEDC)** approach.

```text
open NAT .
op cond : Bool Nat Nat -> Nat .
op g : Nat Nat -> Nat .
op oedc-fact : Nat -> Nat .
vars X Y : Nat .
var NzX : NzNat .

-- cond
eq cond(true,X,Y) = X .
eq cond(false,X,Y) = Y .

-- g
eq g(X,Y) =
  cond(X > Y,
       g(X,2 * Y) * g(sd(X,Y),2 * Y),
       X) .

-- oedc-fact
eq oedc-fact(0) = 1 .
eq oedc-fact(NzX) = g(NzX,1) .

red oedc-fact(5) .
close
```

The program consists of three functions:

- **`cond(B,X,Y)`**: returns `X` if `B` is true; otherwise, it returns `Y`.
- **`g(X,Y)`**: recursively divides the factorial computation into smaller subproblems.
- **`oedc-fact(N)`**: computes the factorial by calling `g(N,1)`, except when \(N=0\), where the result is 1.

Here, `sd(X,Y)` denotes the symmetric difference operation on natural numbers. In the branch where \(X>Y\), it computes \(X-Y\).

## 2. Understanding the Recursive Rule

The central equation is:

$$
g(x,y)=
\begin{cases}
g(x,2y)\times g(x-y,2y),&x>y\\
x,&x\le y
\end{cases}
$$

This means:

1. If `x>y`, the function makes two recursive calls and multiplies their results.
2. The first call is `g(x,2y)`.
3. The second call is `g(x-y,2y)`.
4. If `x <= y`, the recursion stops and returns `x`.

The function `oedc-fact` starts the computation with `y=1`.

## 3. Step-by-Step Computation of `oedc-fact(5)`

We begin with:

$$
oedc\text{-}fact(5)=g(5,1)
$$

Since `5>1`, apply the recursive rule:

$$
g(5,1)=g(5,2)\times g(4,2)
$$

### Step 1: Compute \(g(5,2)\)

Because `5>2`:

$$
g(5,2)=g(5,4)\times g(3,4)
$$

For \(g(5,4)\), since \(5>4\):

$$
g(5,4)=g(5,8)\times g(1,8)
$$

Both recursive calls satisfy the stopping condition because `5<8` and `1<8`. Therefore:

$$
g(5,8)=5,\qquad g(1,8)=1
$$

Hence:

$$
g(5,4)=5\times1=5
$$

For the other branch, `3<=4`, so:

$$
g(3,4)=3
$$

Thus:

$$
g(5,2)=5\times3=15
$$

### Step 2: Compute `g(4,2)`

Since `4>2`:

$$
g(4,2)=g(4,4)\times g(2,4)
$$

Both calls satisfy the stopping condition:

$$
g(4,4)=4,\qquad g(2,4)=2
$$

Therefore:

$$
g(4,2)=4\times2=8
$$

### Step 3: Compute the final result

Substitute the two results into the original expression:

$$
\begin{aligned}
g(5,1)&=g(5,2)\times g(4,2)\\
&=15\times8\\
&=120
\end{aligned}
$$

Therefore:

$$
\boxed{oedc\text{-}fact(5)=120}
$$

## 4. Comparison with Ordinary Factorial Recursion

| Feature | `fact(5)` | `oedc-fact(5)` |
|---|---|---|
| Strategy | Ordinary recursion | Divide and conquer |
| Recursive calls | One recursive call per step | Two recursive calls in the recursive branch |
| Computation | \(5\times4\times3\times2\times1\) | Products of smaller subproblems |
| Result | 120 | 120 |

Both programs compute the same mathematical function, but they organize the computation differently.

## 5. Why Can `oedc-fact(10000)` Be Computed?

The lecture example indicates that `oedc-fact(10000)` can be computed, even though ordinary recursive factorial may encounter a stack overflow for sufficiently large inputs.

The divide-and-conquer structure changes the shape of the recursive computation. Instead of following only a single chain of recursive calls, the function divides the work into branches whose second arguments grow by doubling.

However, this does not mean the algorithm is automatically faster for every input or that it has no resource limitations. Its performance depends on the interpreter, arithmetic implementation, and recursion behavior.

## Conclusion

The function `oedc-fact(5)` starts by evaluating \(g(5,1)\). The function recursively divides the computation into smaller products until each branch reaches the stopping condition \(x\le y\). The intermediate results are then multiplied to obtain \(15\times8=120\).

This illustrates how divide-and-conquer recursion can compute factorials using a different recursive structure from the ordinary factorial function.