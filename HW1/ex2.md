# Explanation of How `fact(5)` Is Computed in CafeOBJ

## 1. Meaning of the Equations

The given CafeOBJ program defines the factorial function using recursion.

```text
open NAT .
op fact : Nat -> Nat .
var NzX : NzNat .

eq fact(0) = 1 .
eq fact(NzX) = NzX * fact(p NzX) .
```

The two equations have the following meanings:

- `fact(0) = 1`: This is the **base case**, which terminates the recursion.
- `fact(NzX) = NzX * fact(p NzX)`: This is the **recursive case**, where `NzX` is a non-zero natural number.
- `p NzX` represents the predecessor of `NzX`. For example, `p 5 = 4`.

Therefore, for every positive natural number \(n\), the factorial function satisfies:

$$
fact(n)=n\times fact(n-1)
$$

## 2. Step-by-Step Computation of `fact(5)`

When the following command is executed:

```text
red fact(5) .
```

CafeOBJ repeatedly applies the equations to reduce the expression.

### Step 1: Expand the recursive calls

Starting with `fact(5)`:

$$

\begin{aligned}
fact(5)&=5\times fact(4)\\
&=5\times4\times fact(3)\\
&=5\times4\times3\times fact(2)\\
&=5\times4\times3\times2\times fact(1)\\
&=5\times4\times3\times2\times1\times fact(0)
\end{aligned}

$$

### Step 2: Apply the base case

Since `fact(0)=1`, substitute this value into the expression:

$$
5\times4\times3\times2\times1\times1
$$

### Step 3: Calculate the result

Evaluating the multiplication gives:

$$
5\times4\times3\times2\times1=120
$$

Therefore,

$$
\boxed{fact(5)=120}
$$

## 3. Visualization of the Recursive Calls

The recursive calls can be represented as follows:

```text
fact(5)
 └── 5 * fact(4)
      └── 4 * fact(3)
           └── 3 * fact(2)
                └── 2 * fact(1)
                     └── 1 * fact(0)
                          └── 1
```

Each function call waits for the next recursive call to return a result before completing its multiplication. Once `fact(0)` is reached, the result propagates back through the previous calls. This process is called **recursive unwinding**.

## 4. Why Can `fact(10000)` Cause a Stack Overflow?

Each recursive call introduces another level of computation. Consequently:

- `fact(5)` requires 5 recursive steps.
- `fact(100)` requires approximately 100 recursive steps.
- `fact(1000)` requires approximately 1,000 recursive steps.
- `fact(10000)` may exceed the available stack capacity of the CafeOBJ environment.

This limitation concerns the recursion depth and execution resources, rather than the mathematical validity of the factorial function.

The time complexity of this implementation is \(O(n)\) in terms of recursive calls. In addition, the number of digits in \(n!\) grows approximately as \(O(nlog n)\), so the cost of arithmetic also increases as \(n\) becomes larger.

## 5. Conclusion

The function `fact(5)` works by repeatedly reducing its argument from 5 to 0. It applies the base case `fact(0) = 1` and then evaluates the multiplications to obtain the final result, 120.

This example demonstrates how recursion and equations are used in CafeOBJ to define and evaluate a mathematical function.