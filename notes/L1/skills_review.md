# ECE382 Skills Review

Name:
<br>
<br>
<br>
Section:
<br>
<br>
<br>
Documentation:
<br>
<br>
<br>
Due Date: **Beginning of Class (BOC), Lesson 3**

**Authorized Resources**

This review is **individual effort** and will be counted as a quiz grade.  You may seek help from any instructor and reference any publication in its completion.  You may **not** reference ECE382 skills reviews from previous years.  Normal documentation is required.

## Part 1: Software

Install the Code Composer Studio (CCS) Integrated Development Environment (IDE) using the instructions from [Computer Exercise 1](/labs/compex1/index.html) - the "Installing Code Composer Studio (CCS)" block .  Do not do anything else from the computer exercise.

This will not be checked, but **it must be accomplished by BOC on Lesson 5**.  Failure to accomplish this will result in a **50% penalty** on this assignment.

## Part 2: Introduction to Numbering Systems

Objectives:


- Explain, by means of an example, the idea of positional weighting in numbering systems.
- Convert an arbitrary base Q number to a decimal number.
- Convert a decimal number to a number with base Q.


1. (5pts each) Convert the following numbers to decimal numbers.  **You must show your work for credit**.

    a. D209 (base 16)
<br>
<br>
<br>
<br>
<br>
<br>
    b. 40A7 (base 11)
<br>
<br>
<br>
<br>
<br>
<br>
    c. 672 (base 8)
<br>
<br>
<br>
<br>
<br>
<br>
    d. 10101110 (base 2)
<br>
<br>
<br>
<br>
<br>
<br>
2. (5pts each) Convert the following numbers to the base(s) indicated.

    a. 547 (base 10) to base 2 and base 16
<br>
<br>
<br>
<br>
<br>
<br>
    b. B36D (base 16) to base 2 and base 8
<br>
<br>
<br>
<br>
<br>
<br>
## Part 3: Representation of Negative Numbers

Objectives:


- Understand the concept of a sign bit.
- Understand the concept and uses of two's complement numbers.


3. (5pts each) Find the 8-bit two's complement representation of the following numbers.

    a. 116 (base 10)
<br>
<br>
<br>
<br>
<br>
<br>
    b. -37 (base 10)
<br>
<br>
<br>
<br>
<br>
<br>
    c. -2 (base 10)
<br>
<br>
<br>
<br>
<br>
<br>
4. (5pts) What are the largest (most positive) and the smallest (most negative) 8-bit two's complement numbers in hexadecimal **and** decimal formats?
<br>
<br>
<br>
<br>
<br>
<br>

<br>
<br>
<br>
<br>
<br>
<br>
## Part 4: Binary Addition and Subtraction, Concept of Overflow

Objectives:


- Explain the concept of overflow and when it occurs.
- Know how to add and subtract two binary numbers and note whether an overflow occurs.

5. (5 pts each) All of the numbers below are represented using 8-bit, two's complement notation.  Perform the specified operations and specify whether or not an overflow occurs.

a.  
&nbsp; &nbsp; 1110 1101  
+ 1010 1100  
<br>
<br>
<br>
<br>
<br>
<br>
b.  
&nbsp; &nbsp; 1001 1000  
- 1110 0111  
<br>
<br>
<br>
<br>
<br>
<br>
6. (5pts) When an overflow occurs, a common solution is to expand the number of bits used in the calculation (known as sign extension).  How would  you extend the negative 8-bit two's complement number with a hexadecimal value of BC to 16 bits?
<br>
<br>
<br>
<br>
<br>
<br>
7. (10pts each) Perform the specified operations and specify whether or not an overflow occurs.  Give the answer in unsigned 16-bit hexadecimal format.

a.  
&nbsp; &nbsp; 0xE76D (unsigned 16-bit)  
+ &nbsp; &nbsp; 0x14 (2's comp 8-bit)  
<br>
<br>
<br>
<br>
<br>
<br>
b.  
&nbsp; &nbsp; BD72 (unsigned 16-bit)  
- &nbsp; &nbsp; D6 (2's comp 8-bit)  
<br>
<br>
<br>
<br>
<br>
<br>
## Part 5: Digital Logic

Objectives:

- Know how to use bit masking to change registers. 
- Demonstrate the ability to design a digital logic circuit.
<br>
<ol start="8">
<li> (5 pts)  You are given a 16-bit register called R6 that contains a certain value.  You need to ensure that the 0th and the 6th bits are set (in other words, they have a value of one) in order for your program to function correctly, but you don't want to change any other bits in the register.  Describe what operation needs to be performed and the operands involved in order to set these bits.  Pseudocode will suffice.</li>
<br>
<br>
<br>
<br>
<br>
<li>(5 pts) You forgot you needed to modify one other 16-bit register called R7 to allow your program to work correctly.  In R7, the 0th, 6th, and 15th bits need to be cleared (set to zero) without affecting the other bits in the register.  Describe what operation needs to be performed and the operands involved in order to clear these bits.  Pseudocode will suffice.</li>
<br>
<br>
<br>
<br>
<br>
<li>(5pts) Draw a schematic for a circuit that will generate the following equation.  You may use only the following gates: AND, OR, and NOT.  **No simplification is allowed**.

F = X'Y' + YZ' +X'Y'Z</li>
</ol>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
