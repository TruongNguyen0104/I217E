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
  \#                Date and time     Topic                                                                         Assignment
                                                                                                                    deadline
  ----------------- ----------------- ----------------------------------------------------------------------------- -----------------
  1                 Tue, Oct 13,      [Sorts, Operators, Terms and                                                  HW1 --- Oct 20,
                    10:50--12:30      Equations](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote1.pdf)     18:00

  2                 Thu, Oct 15,      [Modules, Order Sorts and Lists of Natural                                    HW2 --- Oct 22,
                    09:00--10:40      Numbers](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote2.pdf)       18:00

  3                 Thu, Oct 15,      [Term                                                                         HW3 --- Oct 27,
                    13:30--15:10      Rewriting](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote3.pdf)     18:00

  ---               Tue, Oct 20,      Tutorial hour for Lecture 3                                                   ---
                    10:50--12:30                                                                                    

  4                 Thu, Oct 22,      Parametrized Modules                                                          HW4 --- Oct 29,
                    09:00--10:40                                                                                    18:00

  5                 Thu, Oct 22,      [Tables](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote5.pdf)       HW5 --- Nov 4,
                    13:30--15:10                                                                                    18:00

  6                 Tue, Oct 27,      [Infinite                                                                     HW6 --- Nov 6,
                    10:50--12:30      Lists](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote6.pdf)         18:00

  7                 Thu, Nov 5,       [Multisets](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote7.pdf)    HW7 --- Nov 12,
                    09:00--10:40                                                                                    18:00

  8                 Tue, Nov 10,      [A Programming Language Processor ---                                         Part of HW8--10
                    10:50--12:30      Interpreter](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote8.pdf)   

  9                 Thu, Nov 12,      [A Programming Language Processor --- Virtual                                 Part of HW8--10
                    09:00--10:40      Machine](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote9.pdf)       

  10                Thu, Nov 12,      [A Programming Language Processor ---                                         HW8--10 --- Nov
                    13:30--15:10      Compiler](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote10.pdf)     19, 18:00

  11                Tue, Nov 17,      [Program Verification --- Natural                                             HW11 --- Nov 24,
                    10:50--12:30      Numbers](https://www.jaist.ac.jp/~ogata/lecture/i217e/lectureNote11.pdf)      18:00

  12                Thu, Nov 19,      Program Verification --- Lists                                                HW12 --- Nov 26,
                    09:00--10:40                                                                                    18:00

  13                Tue, Nov 24,      Verification of Arithmetic Calculator Compiler                                HW13 --- Dec 4,
                    10:50--12:30                                                                                    18:00

  14                Thu, Nov 26,      Proof Assistant                                                               HW14 --- Dec 4,
                    09:00--10:40                                                                                    18:00

  ---               Thu, Nov 26,      Tutorial hour for the exam                                                    ---
                    13:30--15:10                                                                                    

  ---               Tue, Dec 1,       Exam                                                                          ---
                    10:50--12:30                                                                                    
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
