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


## Lecture Schedule

| No. | Date | Time (JST) | Topic | Materials |
|---:|---|---|---|---|
| 1 | Tue, Oct 13 | 10:50–12:30 | Sorts, Operators, Terms and Equations | Lecture Note 1 |
| 2 | Thu, Oct 15 | 09:00–10:40 | Modules, Order Sorts and Lists of Natural Numbers | Lecture Note 2 |
| 3 | Thu, Oct 15 | 13:30–15:10 | Term Rewriting | Lecture Note 3 |
| — | Tue, Oct 20 | 10:50–12:30 | Tutorial Hour (Lecture Note 3) | — |
| 4 | Thu, Oct 22 | 09:00–10:40 | Parametrized Modules | Lecture Note 4 |
| 5 | Thu, Oct 22 | 13:30–15:10 | Tables | Lecture Note 5 |
| 6 | Tue, Oct 27 | 10:50–12:30 | Infinite Lists | Lecture Note 6 |
| 7 | Thu, Nov 5 | 09:00–10:40 | Multisets | Lecture Note 7 |
| 8 | Tue, Nov 10 | 10:50–12:30 | A Programming Language Processor – Interpreter | Lecture Note 8 |
| 9 | Thu, Nov 12 | 09:00–10:40 | A Programming Language Processor – Virtual Machine | Lecture Note 9 |
| 10 | Thu, Nov 12 | 13:30–15:10 | A Programming Language Processor – Compiler | Lecture Note 10 |
| 11 | Tue, Nov 17 | 10:50–12:30 | Program Verification – Natural Numbers | Lecture Note 11 |
| 12 | Thu, Nov 19 | 09:00–10:40 | Program Verification – Lists | Lecture Note 12 |
| 13 | Tue, Nov 24 | 10:50–12:30 | Verification of Arithmetic Calculator Compiler | Lecture Note 13 |
| 14 | Thu, Nov 26 | 09:00–10:40 | Proof Assistant | Lecture Note 14 |
| — | Thu, Nov 26 | 13:30–15:10 | Tutorial Hour (Exam Preparation) | — |
| — | Tue, Dec 1 | 10:50–12:30 | **Exam** | — |

## Homework Submission Deadlines

All deadlines are at **18:00 JST**.

| Homework | Related Lecture(s) | Submission Deadline |
|---|---|---|
| HW1 | Lecture 1 | Tue, Oct 20 |
| HW2 | Lecture 2 | Thu, Oct 22 |
| HW3 | Lecture 3 | Tue, Oct 27 |
| HW4 | Lecture 4 | Thu, Oct 29 |
| HW5 | Lecture 5 | Wed, Nov 4 |
| HW6 | Lecture 6 | Fri, Nov 6 |
| HW7 | Lecture 7 | Thu, Nov 12 |
| HW8, HW9, HW10 | Lectures 8–10 | Thu, Nov 19 |
| HW11 | Lecture 11 | Tue, Nov 24 |
| HW12 | Lecture 12 | Thu, Nov 26 |
| HW13 | Lecture 13 | Fri, Dec 4 |
| HW14 | Lecture 14 | Fri, Dec 4 |

## Important Notes

- All dates and times are in Japan Standard Time (JST).
- Check the corresponding lecture notes and homework instructions before each deadline.
- HW8, HW9, and HW10 share the same submission deadline.
- HW13 and HW14 share the same submission deadline.
- The tutorial on November 26 is intended for exam preparation.

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
