# Human Math vs. Computer Math
---
Name: Andrew Marcou  
Topic: Floating Point Arithmetic  
Title: Human Math vs. Computer Math
---- 
## Table of Contents  
[Introduction](#Introduction)   
- [Human Numbers](#Human-Numbers)  
- [Why computer numbers are different](#Why-computer-numbers-are-different)

[Floating Point Numbers](#Floating-Point-Numbers)  
- [The Basics of Floating-Point Numbers](#The-Basics-of-Floating-Point-Numbers)  
- [Computers Use Floating Point Number Systems](#Computers-Use-Floating-Point-Number-Systems)

[Floating-Point Arithmetic](#Floating-Point-Arithmetic)   
- [Addition and Subtraction](#Addition-and-Subtraction)  
- [Multiplication and Division](#Multiplication-and-Division)

[Errors in Floating-Point: How they grow and how to prevent them](#Errors-in-Floating-Point-How-they-grow-and-how-to-prevent-them)  
- [Addition](#Addition)
- [Subtraction](#Subtraction)
- [Multiplication](#Multiplication)
- [Division](#Division)
- [Preventing Errors](#Preventing-Errors)
- [Catastrophic Cancellation](#Catastrophic-Cancellation)

[Summary/Conclusion](#SummaryConclusion)    
[References](#References)  
## Introduction
  If I were to give you a simple math problem, say "What is 0.1 + 0.2?", you would be able to solve it with no issues, responding with "0.3, of course". Clearly, that is the correct answer, right? This follows the basic math principles that we humans have learned and followed for our entire existence. To avoid existential crisis, yes, 0.3 is the correct answer, but arriving at that conclusion is often taken for granted, especially when we are referring to computers, which operate in an entirely different mathematical manner than we do. 

### Human Numbers

Let's start with what we are used to... Human Numbers. Humans operate on base-10, or the decimal system. This means that numbers can have integer values ranging from 1-9, and the position of that number is based on powers of 10. Each number position moving from right to left is 10 times the position to its right. Digits to the left of the decimal are representative of values greater than or equal to 1, while values to the right are representative of values less than 1. This gives us the system that we use every day. 
<div align="center">
  
![](decimalvisualization.png)  
via: https://mathematicalmysteries.org/decimal-number-system/

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
via: https://www.onlinemathlearning.com/binary-number-system.html

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
Because of its efficiency in being able to store a wide range of values, computers utilize the IEEE 754 Floating-Point Standard. 1 "bit" represents a 0 or a 1, and a "byte" represents eight zeros or ones. It is important to note that due to the limited space of a computer, the values of numbers are limited to a certain number of digits as well. This means that many numbers are approximated by the binary conversion.
<div align="center">
Below is a visualization for IEEE 754 Floating Point Standard for Single Precision
  
![](floatinpointnumberpieces.png)  
via: https://www.geeksforgeeks.org/ieee-standard-754-floating-point-numbers/

Below is a visualization for IEEE 754 Floating Point Standard for Double Precision

![](floatingpointnumberpiecesdouble.png)   
via: https://www.geeksforgeeks.org/ieee-standard-754-floating-point-numbers/

</div>

Again due to the limited capacity of the floating-point system, not all numbers are representable. If such is the case, then the number will be approximated to a nearby floating point number. This process is referred to as rounding and introduces the important topic of rounding error. Two methods of rounding are commonly used.
* Chopping - removing the "extra" bits of a number and leaving the rest as is; also referred to as rounding toward zero
* Round to Nearest - rounds to the closest floating point number, up or down.  
Round to nearest is the most accurate method and is the default within the IEEE system. 

This again raises an important topic, machine epsilon or ε<sub>mach</sub>. Machine epsilon is the accuracy of the floating-point system. In other words, ε<sub>mach</sub> is the smallest possible value that a computer can notice. Any smaller and it will identify that number as 0. For IEEE floating point systems:

* ε<sub>mach</sub> = $2^{-24} \approx 10^{-7}$ in single precision (7 digits of precision in decimal)
* ε<sub>mach</sub> = $2^{-53} \approx 10^{-16}$ in double precision (16 digits of precision in decimal)

To summarize, the floating-point system is utilized to store/represent a much larger range of values than fixed-point systems. Of course, there are many floating-point systems that contain different standards, but for the purpose of simplicity, we deal with the IEEE 754 floating-point system and its utilization with base-2 numbers.

## Floating-Point Arithmetic

With all of the necessary prerequisites out of the way, we can begin discussing how basic math is carried out within computers, and where crazy errors can come from if one is not careful. Recall from the introduction the alluded statement that 0.1 + 0.2 &ne; 0.3 when the calculation is done using a computer. This is due to the binary approximation of 0.1 and 0.2 not being able to fit within the limited space of the floating-point number. To clear things up, we know that in decimal:
$$\frac{1}{3} = 0.\overline{3}$$
The link above the 0.3 represents the fact that we know those 3's continue for infinity. Unfortunately, we cannot write infinite 3's, and therefore, we need an approximation. We can then write
$$\frac{1}{3} \approx 0.333$$
$$\therefore 0.333 + 0.333 + 0.333 = 0.999 < 1$$
It is here where the rounding error is introduced. Of course, we know that 0.999 is incredibly close to 1 and so we consider them to be equivalent. But a computer cannot make that connection, and therefore correctly deems them unequal. 

Now let us consider how 0.1 is approximated in base-2. Because base-2 only recognizes halves, fourths, eighths, and so on, a tenth is very difficult to approximate. 
$$\frac{1}{10} = 0.0\overline{0011} \text{   and   } \frac{2}{10} = 0.\overline{0011}$$
Again, due to limited computer space, these values are approximated
$$\frac{1}{10} \approx 0.000110011001100 \text{   and   } \frac{2}{10} = 0.001100110011001$$
$$\therefore 0.000110011001100 + 0.001100110011001 = 0.299957275390625 < 0.3$$
Again, the rounding error shows up.

<div align="center">
  
![](meme.png)  
via: https://medium.com/@dotcom.software/floating-dangers-in-php-c4a2220bd8dc

</div>

Errors also show up when values are especially small or large and will be discussed later in this section, but for now, let us look at how the floating-point system operates in standard arithmetical operations.

### Addition and Subtraction
Because addition and subtraction follow very similar processes, they will be discussed in one section. When adding and subtracting floating-point numbers, the exponents must match, otherwise, the addition cannot take place. To account for this, the exponent of the smaller number is raised to that of the larger number and the mantissa is adjusted accordingly. After this process occurs, the numbers are added in the standard manner, and the exponent is attached back onto the number. For example:
$$\beta = 10 \text{ (base-10)}, p = 5 \text{ (length of mantissa)}$$
$$x = 3.4352 * 10^4, y = 2.2234 * 10^{2}$$
because we must shift the exponent of the smaller value to that of the larger value, the y value will become  
$$y = 0.022234 * 10^4$$  
and 
$$x + y = 3.457434 * 10^4$$
but due to the mantissa limit of p = 5, we must round off the last 2 digits, giving us
$$x + y = 3.4574 * 10^4$$

Subtraction is carried out in the same manner. The only difference lies in the operation that is carried out with both mantissa (subtraction in place of addition).
### Multiplication and Division
Multiplication and Division are also very similar in their operations. They are also quite simple, as the product/quotient mantissa and exponent can be found independently of each other. Of course, the final answer must abide by the mantissa length and base. For example, let us take the same x and y as before:
$$\beta = 10 \text{ (base-10)}, p = 5 \text{ (length of mantissa)}$$
$$x = 3.4352 * 10^4, y = 2.2234 * 10^{2}$$
Let us look for $x * y$  
We can first find the product exponent value by adding the exponents together. This will give us
$$4 + 2 = 6$$
$$\therefore \text{exponent} = 10^6$$
and now we find the mantissa value by multiplying the mantissa of x and y  
$$3.4352 * 2.2234 = 7.63782368$$
giving us a calculated value of $7.63782368 * 10^6$. When we apply the mantissa constraint, however, we end up with a final value of $7.6378 * 10^6$

Again, division is just as simple. The only difference lies in the operation that is carried out between exponents (subtract them) and mantissa (divide them accordingly).
## Errors in Floating-Point: How they grow and how to prevent them
Errors happen very frequently when dealing with floating-point arithmetic. They can show up for many reasons but can be catastrophic to a code. As an expression continues, many errors can compound on each other, leading to an incredibly inaccurate result. Listed below are common errors found in each operation.
- For any case, the exponent of the result could be too large to be represented, thus failing
- Arbitrarily large values are often harder to represent than arbitrarily small values, as those small values are essentially zero
- Approximation errors in converting decimal to binary will always produce error
### Addition
- Due to floating-point addition being communitive but NOT associative, it is important to note that $(a + b) + c \ne a + (b + c)$
  - This can be witnessed in an equation where n is slightly smaller than ε<sub>mach</sub>: $(1 + n) + n = 1$ but $1 + (n + n) > 1$
  - Due to computer rounding above, the order in which the operations execute will greatly affect the answer
- When adding a very large number to a very small number, a shift in the mantissa may cause the smaller number to be completely lost, effectively adding zero to the number
  - This can be seen in $3.32 * 10^2 + 2.13 * 10^{-3}$ when $2.13 * 10^-3$ becomes $0.0000213 * 10^2$ as it has to follow the exponent, and is then washed out when the sum is rounded
### Subtraction
- Subtraction can introduce cancellation, which will be discussed in a later section
- Similar to addition, when subtracting a very small value from a very large value, oftentimes the very small value will be insignificant, and essentially take on the value 0
- Subtraction is also NOT associative, meaning switching the order in which operations are carried out has the potential to change the final answer
### Multiplication
- Multiplying two very large values can produce a result larger than the maximum exponent
- Multiplying a number with a very small number could result in 0 due to limits on the mantissa length
- Multiplication is also NOT associative
### Division
- Dividing a number by a very small number could return Inf or a special case of NaN
- Dividing a very small number by a very large number could result in 0 due to mantissa limits
- Subtraction is also NOT associative
### Preventing Errors
Sometimes it is possible to work around these errors using specific methods. Whenever possible, it is important to try to mitigate floating-point error to avoid failure of a function.
* Try to add values of similar magnitude (i.e. add very small numbers to other very small numbers)
* Avoid subtracting similar values; algebraically "massage" the equation to avoid this subtraction
* When multiplying and dividing, attempt to multiply and divide by numbers near to 1 (to prevent from getting very large or very small numbers)
* Use built-in functions (where possible) that are better optimized to reduce error
### Catastrophic Cancellation
Catastrophic Cancellation occurs when you have a subtraction of two very similar numbers. Though you get a very precise result, the cancellation of leading digits causes an extreme loss of information. For example
$$6.23145 * 10^1 - 6.23134 * 10^1 = 1.10000 * 10^{-3}$$
Here we see that although the answer is precise and correct, the result is only 2 significant digits, while the previous numbers had 6.

For another example where n is a number slightly smaller than ε<sub>mach</sub>:
$$(1 + n) - (1 - n) = 1 - 1 = 0$$
as represented in floating-point arithmetic. When in reality we know that there is a $2n$ that is larger than ε<sub>mach</sub> but has been completely lost.

Oftentimes, catastrophic cancellation can be resolved through algebraic manipulation of equations, attempting to avoid subtractions of similar values wherever possible. For example, the equation
$$\frac{1}{t*(1-\sqrt{1-t^2})}$$
incurs catastrophic cancellation in subtracting $1 - \sqrt{1-t^2}$, but this can be easily avoided by multiplying by the complex conjugate 
$$\frac{1}{t*(1-\sqrt{1-t^2})} * \frac{1 + \sqrt{1-t^2}}{1 + \sqrt{1-t^2}} = \frac{t}{1 + \sqrt{1-t^2}}$$
which is a much more numerically stable expression.
## Summary/Conclusion
To start, we introduced the topic of base-2 and base-10 number systems. This led right into the introduction of floating-point number systems, which are essentially just a form of scientific notation. Once these topics were introduced, we then moved on to the main topic of the article, floating-point arithmetic. 

Floating-point arithmetic has its trade-offs. The numbers themselves are very efficient to store and make storage very intuitive and efficient. On the other hand, arithmetic with the numbers can potentially lead to extreme error due to rounding. We explored this phenomenon in many cases, namely in floating-point approximations, floating-point addition and subtraction, and floating-point multiplication and division. These rounding errors can easily compound, blowing up a small error into an extreme failure of an equation. Methods for mitigating this error were also discussed. Cases of extreme information loss such as catastrophic cancellation in subtraction were also explored, as well as potential methods for mitigating the risk of its occurrence. 
## References
* Binary number system (video lessons, examples, solutions). www.onlinemathlearning.com. (n.d.). https://www.onlinemathlearning.com/binary-number-system.html 
* Decimal number system. Mathematical Mysteries. (2022, August 9). https://mathematicalmysteries.org/decimal-number-system/ 
* Eswaran, S. (2020, November 2). Floating point arithmetic: Computer architecture. Witspry Witscad. https://witscad.com/course/computer-architecture/chapter/floating-point-arithmetic
* GeeksforGeeks. (2020, March 16). IEEE standard 754 Floating point numbers. GeeksforGeeks. https://www.geeksforgeeks.org/ieee-standard-754-floating-point-numbers/
* Heath, Prof. M. T. (2023, December). CX 4640 - Numerical Analysis, Chapter 1: Scientific Computing. Class. Atlanta, Georgia.
* Losing my precision: Tips for handling tricky floating point arithmetic. SOA. (n.d.). https://www.soa.org/news-and-publications/newsletters/compact/2014/may/com-2014-iss51/losing-my-precision-tips-for-handling-tricky-floating-point-arithmetic/ 
* Software, .com. (2022, October 4). Floating dangers in PHP. Medium. https://medium.com/@dotcom.software/floating-dangers-in-php-c4a2220bd8dc 
* YouTube. (2014). Floating Point Numbers - Computerphile. YouTube. Retrieved December 7, 2023, from https://www.youtube.com/watch?v=PZRI1IfStY0&amp;t=77s&amp;ab_channel=Computerphile. 
* YouTube. (2017). Why Do Computers Use 1s and 0s? Binary and Transistors Explained. YouTube. Retrieved December 7, 2023, from https://www.youtube.com/watch?v=Xpk67YzOn5w&amp;ab_channel=BasicsExplained%2CH3Vtux.

