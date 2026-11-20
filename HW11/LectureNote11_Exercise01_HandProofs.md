# Lecture Note 11 — Exercise 1
## Phần chứng minh viết tay

Bài 1 yêu cầu viết lại các specification và proof score đã dùng trong slides, chạy bằng CafeOBJ, đồng thời **viết tay tất cả các chứng minh xuất hiện trong slides**. Phần dưới đây là nội dung chứng minh viết tay; code CafeOBJ nằm trong file `LectureNote11_Exercise01.cafe`.

## 0. Quy ước và định nghĩa

Số tự nhiên Peano được xây dựng từ:

- `0` là số tự nhiên.
- Nếu `X` là số tự nhiên thì `s(X)` cũng là số tự nhiên.

Do đó: `0`, `s(0)`, `s(s(0))`, ... lần lượt biểu diễn 0, 1, 2, ...

Các phép toán được định nghĩa đệ quy như sau:

**Phép cộng**

(+) `0 + Y = Y`

(++) `s(X) + Y = s(X + Y)`

**Phép nhân**

(*) `0 * Y = 0`

(**) `s(X) * Y = (X * Y) + Y`

**Hai cách cài đặt factorial**

(f1-1) `fact1(0) = s(0)`

(f1-2) `fact1(s(X)) = s(X) * fact1(X)`

(f2) `fact2(X) = sfact2(X, s(0))`

(sf2-1) `sfact2(0,Y) = Y`

(sf2-2) `sfact2(s(X),Y) = sfact2(X, s(X) * Y)`

Trong các chứng minh, `x`, `y`, `z` là các hằng số mới (fresh constants); chữ hoa `X`, `Y`, `Z` biểu diễn biến tổng quát. Mỗi lần chứng minh bằng quy nạp cấu trúc theo `X`, ta cần có **base case** với `X=0` và **induction case** với `X=s(x)`, giả sử induction hypothesis (IH) đúng tại `x`.

---

## 1. Theorem 1 — Associativity of addition (assoc+)

Cần chứng minh:

`(X + Y) + Z = X + (Y + Z)`

Chứng minh bằng quy nạp cấu trúc theo `X`.

### I. Base case: X = 0

Vế trái:

`(0 + y) + z`

`= y + z`  by (+1)

Vế phải:

`0 + (y + z)`

`= y + z`  by (+1)

Hai vế bằng nhau.

### II. Induction case: X = s(x)

Giả sử IH:

`(x + Y) + Z = x + (Y + Z)`

Cần chứng minh:

`(s(x) + y) + z = s(x) + (y + z)`

Vế trái:

`(s(x) + y) + z`

`= s(x + y) + z`  by (+2)

`= s((x + y) + z)`  by (+2)

`= s(x + (y + z))`  by IH

Vế phải:

`s(x) + (y + z)`

`= s(x + (y + z))`  by (+2)

Hai vế cùng rút gọn về `s(x + (y + z))`. Vậy theorem 1 được chứng minh.

---

## 2. Theorem 2 — Commutativity of addition (comm+)

Cần chứng minh:

`X + Y = Y + X`

Chứng minh bằng quy nạp cấu trúc theo `X`. Hai lemma cần dùng được chứng minh trước.

### Lemma 1 — Right zero of addition (rz+)

Cần chứng minh:

`X + 0 = X`

**I. Base case: X = 0**

`0 + 0 = 0`  by (+1)

**II. Induction case: X = s(x)**

Giả sử IH: `x + 0 = x`.

` s(x) + 0`

`= s(x + 0)`  by (+2)

`= s(x)`  by IH

Vậy lemma 1 được chứng minh.

### Lemma 2 — Right successor of addition (rs+)

Cần chứng minh:

`X + s(Y) = s(X + Y)`

Chứng minh bằng quy nạp cấu trúc theo `X`.

**I. Base case: X = 0**

`0 + s(y) = s(y)`  by (+1)

` s(0 + y) = s(y)`  by (+1)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH: `x + s(Y) = s(x + Y)`.

Vế trái:

` s(x) + s(y)`

`= s(x + s(y))`  by (+2)

`= s(s(x + y))`  by IH

Vế phải:

` s(s(x) + y)`

`= s(s(x + y))`  by (+2)

Hai vế bằng nhau. Vậy lemma 2 được chứng minh.

### Chứng minh Theorem 2

**I. Base case: X = 0**

Cần chứng minh `0 + y = y + 0`.

`0 + y = y`  by (+1)

`y + 0 = y`  by Lemma 1 (rz+)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH: `x + Y = Y + x`.

Cần chứng minh `s(x) + y = y + s(x)`.

Vế trái:

` s(x) + y`

`= s(x + y)`  by (+2)

`= s(y + x)`  by IH

`= y + s(x)`  by Lemma 2 (rs+)

Vậy theorem 2 được chứng minh.

---

## 3. Theorem 3 — Associativity of multiplication (assoc*)

Cần chứng minh:

`(X * Y) * Z = X * (Y * Z)`

Ta cần Lemma 3 (distributive law) trước.

### Lemma 3 — Distributive law of multiplication over addition (d*o+)

Cần chứng minh:

`(X + Y) * Z = (X * Z) + (Y * Z)`

Chứng minh bằng quy nạp cấu trúc theo `X`.

**I. Base case: X = 0**

Vế trái:

`(0 + y) * z = y * z`  by (+1)

Vế phải:

`(0 * z) + (y * z)`

`= 0 + (y * z)`  by (*1)

`= y * z`  by (+1)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH:

`(x + Y) * Z = (x * Z) + (Y * Z)`

Cần chứng minh:

`(s(x) + y) * z = (s(x) * z) + (y * z)`

Vế trái:

`(s(x) + y) * z`

`= s(x + y) * z`  by (+2)

`= ((x + y) * z) + z`  by (*2)

`= ((x * z) + (y * z)) + z`  by IH

`= (x * z) + ((y * z) + z)`  by assoc+

`= (x * z) + (z + (y * z))`  by comm+

Vế phải:

`(s(x) * z) + (y * z)`

`= ((x * z) + z) + (y * z)`  by (*2)

`= (x * z) + (z + (y * z))`  by assoc+

Hai vế bằng nhau. Vậy lemma 3 được chứng minh.

### Chứng minh Theorem 3

**I. Base case: X = 0**

`(0 * y) * z = 0 * z = 0`  by (*1)

`0 * (y * z) = 0`  by (*1)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH:

`(x * Y) * Z = x * (Y * Z)`

Cần chứng minh:

`(s(x) * y) * z = s(x) * (y * z)`

Vế trái:

`(s(x) * y) * z`

`= ((x * y) + y) * z`  by (*2)

`= ((x * y) * z) + (y * z)`  by Lemma 3 (d*o+)

`= (x * (y * z)) + (y * z)`  by IH

Vế phải:

` s(x) * (y * z)`

`= (x * (y * z)) + (y * z)`  by (*2)

Hai vế bằng nhau. Vậy theorem 3 được chứng minh.

---

## 4. Theorem 4 — Commutativity of multiplication (comm*)

Cần chứng minh:

`X * Y = Y * X`

Ta cần Lemma 4 và Lemma 5 trước.

### Lemma 4 — Right zero of multiplication (rz*)

Cần chứng minh:

`X * 0 = 0`

Chứng minh bằng quy nạp cấu trúc theo `X`.

**I. Base case: X = 0**

`0 * 0 = 0`  by (*1)

**II. Induction case: X = s(x)**

Giả sử IH: `x * 0 = 0`.

` s(x) * 0`

`= (x * 0) + 0`  by (*2)

`= 0 + 0`  by IH

`= 0`  by (+1)

Vậy lemma 4 được chứng minh.

### Lemma 5 — Right successor of multiplication (rs*)

Cần chứng minh:

`X * s(Y) = (X * Y) + X`

Chứng minh bằng quy nạp cấu trúc theo `X`.

**I. Base case: X = 0**

Vế trái:

`0 * s(y) = 0`  by (*1)

Vế phải:

`(0 * y) + 0`

`= 0 + 0`  by (*1)

`= 0`  by (+1)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH: `x * s(Y) = (x * Y) + x`.

Vế trái:

` s(x) * s(y)`

`= (x * s(y)) + s(y)`  by (*2)

`= ((x * y) + x) + s(y)`  by IH

`= s(y) + ((x * y) + x)`  by comm+

`= s(y + ((x * y) + x))`  by (+2)

Vế phải:

`(s(x) * y) + s(x)`

`= ((x * y) + y) + s(x)`  by (*2)

`= s(x) + ((x * y) + y)`  by comm+

`= s(x + ((x * y) + y))`  by (+2)

`= s(((x * y) + y) + x)`  by comm+

`= s((y + (x * y)) + x)`  by comm+

`= s(y + ((x * y) + x))`  by assoc+

Hai vế bằng nhau. Vậy lemma 5 được chứng minh.

### Chứng minh Theorem 4

**I. Base case: X = 0**

Cần chứng minh `0 * y = y * 0`.

`0 * y = 0`  by (*1)

`y * 0 = 0`  by Lemma 4 (rz*)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH: `x * Y = Y * x`.

Cần chứng minh `s(x) * y = y * s(x)`.

Vế trái:

` s(x) * y`

`= (x * y) + y`  by (*2)

`= (y * x) + y`  by IH

Vế phải:

`y * s(x)`

`= (y * x) + y`  by Lemma 5 (rs*)

Hai vế bằng nhau. Vậy theorem 4 được chứng minh.

---

## 5. Theorem 5 — Correctness of a tail-recursive factorial (trf)

Cần chứng minh:

`fact1(X) = fact2(X)`

Ta cần Lemma 6.

### Lemma 6 — Property of sfact2 (p-sf2)

Cần chứng minh:

`Y * sfact2(X,Z) = sfact2(X, Y * Z)`

Chứng minh bằng quy nạp cấu trúc theo `X`.

**I. Base case: X = 0**

Vế trái:

`y * sfact2(0,z)`

`= y * z`  by (sf2-1)

Vế phải:

`sfact2(0, y * z)`

`= y * z`  by (sf2-1)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH:

`Y * sfact2(x,Z) = sfact2(x, Y * Z)`

Cần chứng minh:

`y * sfact2(s(x),z) = sfact2(s(x), y * z)`

Vế trái:

`y * sfact2(s(x),z)`

`= y * sfact2(x, s(x) * z)`  by (sf2-2)

`= sfact2(x, y * (s(x) * z))`  by IH

Vế phải:

`sfact2(s(x), y * z)`

`= sfact2(x, s(x) * (y * z))`  by (sf2-2)

`= sfact2(x, (y * z) * s(x))`  by comm*

`= sfact2(x, y * (z * s(x)))`  by assoc*

`= sfact2(x, y * (s(x) * z))`  by comm*

Hai vế bằng nhau. Vậy lemma 6 được chứng minh.

### Chứng minh Theorem 5

**I. Base case: X = 0**

Vế trái:

`fact1(0) = s(0)`  by (f1-1)

Vế phải:

`fact2(0)`

`= sfact2(0, s(0))`  by (f2)

`= s(0)`  by (sf2-1)

Hai vế bằng nhau.

**II. Induction case: X = s(x)**

Giả sử IH:

`fact1(x) = fact2(x)`

Cần chứng minh:

`fact1(s(x)) = fact2(s(x))`

Vế trái:

`fact1(s(x))`

`= s(x) * fact1(x)`  by (f1-2)

`= s(x) * fact2(x)`  by IH

`= s(x) * sfact2(x, s(0))`  by (f2)

Vế phải:

`fact2(s(x))`

`= sfact2(s(x), s(0))`  by (f2)

`= sfact2(x, s(x) * s(0))`  by (sf2-2)

Áp dụng Lemma 6 (p-sf2) với `Y = s(x)`, `X = x`, `Z = s(0)`:

` s(x) * sfact2(x, s(0)) = sfact2(x, s(x) * s(0))`

Do đó hai vế bằng nhau. Vậy theorem 5 được chứng minh.

---

## 6. Những kết quả cần có trong bài nộp

1. **Specifications:** `PNAT1`, `PNAT2`, `PNAT3` trong file CafeOBJ.
2. **Proof scores:** hai nhánh (base case và induction case) cho từng theorem/lemma trong file CafeOBJ.
3. **Hand proofs:** các chứng minh trên, gồm Theorem 1–5 và Lemma 1–6.
4. Khi chạy CafeOBJ, kiểm tra từng lệnh `red ... = ... .`; kết quả cần là `true`.

Lưu ý: các proof score của theorem sử dụng các lemma đã được chứng minh ở phần trước. Trong proof score, các dòng `eq ... .` đặt trong một khối `open ... close` là giả thiết cục bộ để kiểm tra induction hypothesis hoặc lemma; chúng không thay thế việc viết chứng minh riêng cho lemma đó.
