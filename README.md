# i217e --- Functional Programming

Course notes and study workspace for **i217e Functional Programming** at
the Japan Advanced Institute of Science and Technology (JAIST).

> **Official course website:**
> https://www.jaist.ac.jp/\~ogata/lecture/i217e/

## Course information

-   **Course:** i217e --- Functional Programming
-   **Lecturers:** Kazuhiro Ogata and Canh Minh Do
-   **Period:** October 13 -- December 2, 2026
-   **Classroom:** IS Lecture Hall
-   **Main tool:** CafeOBJ System Version 1.5.9
-   **Official website:** [JAIST i217e course
    page](https://www.jaist.ac.jp/~ogata/lecture/i217e/)

Check the official website and announcements for any updates to the
schedule, assignment instructions, or deadlines.

## Overview

The course introduces functional programming through executable
specifications written in CafeOBJ. It develops the foundations needed to
describe programs with sorts, operators, terms, and equations, and then
applies these ideas to data structures, language implementation, and
program verification.

Topics include:

-   Sorts, operators, terms, equations, and order-sorted specifications
-   Lists, parametrized modules, tables, infinite lists, and multisets
-   Term rewriting and equational reasoning
-   Interpreters, virtual machines, and compilers
-   Program verification for natural numbers, lists, and a calculator
    compiler
-   Proof assistants

## Lecture schedule and assignments

The following schedule and deadlines are transcribed from the official
course website. All deadlines are **Japan Standard Time (JST, UTC+9)**.

  -----------------------------------------------------------------------------------------------------------------------------------
  10:50 - 12:30, Oct 13, Tuesday
1. Sorts, Operators, Terms and Equations (lecture note 1)
Submission deadline of HW1: 18:00 of Oct 20 (JST)

9:00 - 10:40, Oct 15, Thursday
2. Modules, Order Sorts and Lists of Natural Numbers (lecture note 2)
Submission deadline of HW2: 18:00 of Oct 22 (JST)

13:30 - 15:10, Oct 15, Thursday
3. Term Rewriting (lecture note 3)
Submission deadline of HW3: 18:00 of Oct 27 (JST)

10:50 - 12:30, Oct 20, Tuesday
Tutorial Hour (for lecture note 3)

9:00 - 10:40, Oct 22, Thursday
4. Parametrized Modules (lecture note 4)
Submission deadline of HW4: 18:00 of Oct 29 (JST)

13:30 - 15:10, Oct 22, Thursday
5. Tables (lecture note 5) 
Submission deadline of HW5: 18:00 of Nov 4 (JST)

10:50 - 12:30, Oct 27, Thursday
6. Infinite Lists (lecture note 6)
Submission deadline of HW6: 18:00 of Nov 6 (JST)

9:00 - 10:40, Nov 5, Thursday
7. Multisets (lecture note 7)
Submission deadline of HW7: 18:00 of Nov 12 (JST)

10:50 - 12:30, Nov 10, Tuesday
8. A Programming Language Processor - Interpreter (lecture note 8)

9:00 - 10:40, Nov 12, Thursday
9. A Programming Language Processor - Virtual Machine (lecture note 9)

13:30 - 15:10, Nov 12, Thursday
10. A Programming Language Processor - Compiler (lecture note 10)
Submission deadline of HW8, 9, and 10: 18:00 of Nov 19 (JST)

10:50 - 12:30, Nov 17, Tuesday
11. Program Verification - Natural Numbers (lecture note 11)
Submission deadline of HW11: 18:00 of Nov 24 (JST)

9:00 - 10:40, Nov 19, Thursday
12. Pregram Verification - Lists (lecture note 12)
Submission deadline of HW12: 18:00 of Nov 26 (JST)

10:50 - 12:30, Nov 24, Tuesday
13. Verification of Arithmetic Caclulator Compiler (lecture note 13)
Submission deadline of HW13: 18:00 of Dec 4 (JST)

9:00 - 10:40, Nov 26, Thursday
14. Proof Assistant (lecture note 14)
Submission deadline of HW14: 18:00 of Dec 4(JST)

13:30 - 15:10, Nov 26, Thursday
Tutorial Hour (for Exam)

10:50 - 12:30, Dec 01, Tuesday
Exam
  -----------------------------------------------------------------------------------------------------------------------------------

**Schedule note:** The official page states that the schedule was
changed on September 29, 2026. Some lecture-note links may be updated or
unavailable; use the official course page as the source of truth.

## Software setup

The course announcement specifies **CafeOBJ System Version 1.5.9** and
asks students to bring their computers to each class.

1.  Visit the [CafeOBJ website](https://cafeobj.org/) and download the
    course-specified version.
2.  Follow the installation instructions for your operating system.
3.  Open a terminal and start CafeOBJ.
4.  Create a plain-text source file with the `.cafe` extension, for
    example `gcd.cafe`.
5.  Load the file in CafeOBJ with `in gcd` (the extension can be
    omitted).

### A small example

``` cafeobj
open NAT .
op gcd : Nat Nat -> Nat .
var X : Nat .
var NzY : NzNat .

eq gcd(X, 0) = X .
eq gcd(X, NzY) = gcd(NzY, X rem NzY) .

red gcd(24, 36) .
close
```

Useful commands:

-   `open NAT .` --- open the built-in natural-number module.
-   `red 3 + 4 .` --- reduce/evaluate a term using available equations.
-   `close` --- close the currently open module.
-   `?` --- display available commands.
-   `full-reset` --- reset the CafeOBJ system.

**Syntax reminder:** CafeOBJ commands and declarations generally end
with a period (`.`). Follow the spacing shown in the lecture notes,
especially around operators.

## Recommended study workflow

The lecturer's recommended approach is:

1.  **Before class:** Read the lecture notes, attempt Exercise 1, and
    write down questions.
2.  **During class:** Ask about unclear concepts and compare your
    reasoning with the explanations.
3.  **After class:** Revisit and correct your Exercise 1 solution.
4.  **For assignments:** Type the programs yourself, run tests, and
    explain the results in your own words.

The course intentionally does **not** provide all program code as
ready-made files; typing and testing the examples is part of the
learning process.

## Assignment and academic-integrity notes

-   Assignment problems are drawn from exercises in the lecture notes.
    Instructors announce detailed submission instructions and deadlines
    during class.
-   For the first assignment, the course website asks students to use
    the email subject **`Ishikawa i217e HW1`** when emailing the report
    and programs to Ogata. Follow the corresponding instructions for
    later assignments.
-   **Plagiarism is strictly prohibited.** Do not copy programs or
    reports written by others, and do not allow others to copy yours.
    Submit work you understand and have produced yourself.
-   Keep source files, test cases, outputs, and explanations organized
    so you can review your work and prepare for the exam.

## Official resources

-   [Course homepage, announcements, and full
    schedule](https://www.jaist.ac.jp/~ogata/lecture/i217e/)
-   [CafeOBJ download and installation
    information](https://cafeobj.org/)
-   [Lecture 1 --- Sorts, Operators, Terms and
    Equations](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote1.pdf)
-   [Lecture 2 --- Modules, Order Sorts and Lists of Natural
    Numbers](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote2.pdf)
-   [Lecture 3 --- Term
    Rewriting](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote3.pdf)


------------------------------------------------------------------------

*This README is a student-maintained course guide based on the official
JAIST i217e website. If any detail conflicts with a newer announcement,
follow the official course website and instructions given in class.*
