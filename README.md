# Computer Math versus Human Math
---
Name: Andrew Marcou  
Topic: Floating Point Arithmetic  
Title: Computer Math versus Human Math
---- 

## Introduction
  If I were to give you a simple math problem, say "What is 0.1 + 0.2?", you would be able to solve it with no issues, responding with "0.3, of course". Clearly, that is the correct answer, right? This follows the basic math principles that we humans have learned and followed for our entire existence. To avoid existential crisis, yes, 0.3 is the correct answer, but arriving at that conclusion is often taken for granted, especially when we are referring to computers, which operate in an entirely different mathematical manner than we do. 

### Let's start with what we are used to - Human Numbers

Humans operate on base-10, or the decimal system. This means that numbers can have integer values ranging from 1-9, and the position of that number is based on powers of 10. Each number position moving from right to left is 10 times the position to its right. Digits to the left of the decimal are representative of values greater than or equal to 1, while values to the right are representative of values less than 1. This gives us the system that we use every day. 
<div align="center">
  
![](decimalvisualization.png)

</div>

In this system, adding is done exactly how we are used to. If we were given an addition problem such as:
<div align="center">

|   | +1|   |   |
|---|---|---|---|
|   | 2 | 5 | 1 |
| + | 4 | 6 | 3 |
|---|---|---|---|
|   | 7 | 1 | 4 |
</div>
we are always taught to "carry the one". This refers to the fact that the addition taking place in a specific column runs out of integers 1-9, and must pass a value of 1 to the next column to the left, meaning a "movement up" in order of magnitude. The process for subtraction is also very similar in base-10.

Multiplication also operates in a simple manner. Multiplication is carried out column by column, and multiplying values in more left-ward columns will cause a shift in the magnitude of the product by a power of 10. Numbers are still "carried" and added to their respective columns similar to addition. For example:
<div align="center">
  
|   |   |   |   |   |   |
|---|---|---|---|---|---|
|   |   |   | 2 | 5 | 1 |
|   |   | x | 4 | 6 | 3 |
|   |   |---|---|---|---|
|   |   |   | 7 | 5 | 3 |
|   | 1 | 5 | 0 | 6 | 0 |
| 1 | 0 | 0 | 4 | 0 | 0 |
|---|---|---|---|---|---|
| 1 | 1 | 6 | 2 | 1 | 3 |
</div>

### Why computer numbers are different
Though many take it for granted, the human mind is incredibly complex and is seemingly impossible to replicate. Consequently, it is very hard for a computer to operate in base-10. Luckily, due to the way its transistors operate, a computer operates very efficiently in base-2 arithmetic. Base-2 means the computer only has 2 digits to work with, unlike the 10 digits that base-10 utilizes. Each position value is determined by the integer 1 or 0, and the position location is determined by powers of 2. For example, the number 5 in base-2 arithmetic is expressed as 101.
<div align="center">
  
![](binarytodecimal.png)

</div>

In regards to adding binary numbers, there are 3 simple rules:  
* 0 + 0 = 1
* 0 + 1 = 1
* 1 + 1 = 10 (and the 1 is "carried" to the next left column)

For Example:

<div align="center">
  
|   | +1| +1| +1|   |
|---|---|---|---|---|
|   |   | 1 | 0 | 1 |
|   | + | 1 | 1 | 1 |
|---|---|---|---|---|
|   | 1 | 1 | 0 | 0 | 

</div>

Fortunately, binary multiplication works in the same manner as decimal where
* 0 x 0 = 0
* 0 x 1 = 0
* 1 x 1 = 1

## Floating Point Numbers

Now that we understand the basics of base-10 versus base-2, we can now look at how a computer stores and uses its base-2 data. Firstly, we must look at a case in which a human is asked to write the number 8 billion. They may write:

$$
\begin{align*}
8,000,000,000 
\end{align*}
$$

<div align="center">
or   
</div>

$$
\begin{align*}
8.0 * 10^9
\end{align*}
$$

The first option takes up a lot of space, and though it is a very intuitive solution, it is very inefficient for very large and very small numbers. This way of writing numbers is referred to as a fixed-point system. The second option, also known as scientific notation, follows a floating point system in which the decimal position is determined by the power of 10 multiplier to the far right. Here, the numbers to the right of the decimal are not necessarily smaller than 1 due to the multiplier. Because of its efficiency in storing very large and very small values, computers use the floating point system for their binary numbers. 

### The Basics of Floating-Point Numbers

Floating point numbers are represented in a computer with three main parts:
* The sign of the number
* The mantissa - the number itself
* The exponent - the multiplier for the number to move the decimal 

A floating-point number is said to be normalized if the leading integer of the mantissa contains a number that satisfies 1 ≤ m < β where β is the base that we are operating in (modern computers use β = 2).

### Computers Use Floating Point Number Systems 
Because of its efficiency in being able to store a wide range of values, computers utilize the IEEE 754 Floating-Point Standard

 
## Floating-Point Arithmetic
### Addition and Subtraction
### Multiplication and Division
