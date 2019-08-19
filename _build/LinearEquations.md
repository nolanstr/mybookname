---
redirect_from:
  - "/linearequations"
title: 'Linear Equations'
prev_page:
  url: /features/Root_Finding_OPen
  title: 'Roots of Equations Open JN'
next_page:
  url: /features/Linear_Equation
  title: 'Linear Equations JN'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# **Linear Equations**:

**Mathematical Definition**: Linear Equations make up a section of numerical methods that strive to solve linear systems of euqations for their respective numerical solutions.

**General Defintion**: Linear equations are methods that work inside the laws of linear algebra to solve for the numerical solutions to linear systems through various ways. These way can seem extremely complex like LU Decomposition that uses numerous complex steps and Naive Gauss to solve for the solution, while on the other hand seemingly simple equations such as Gauss-Seidel that take advantage of the ability to run large numbers of iterations to approximate the true solution via computer programs. Due to there being two seperate method types of which one can use in order to solve systems of linear equations, we will cover both avenues, being that of linear manipulation and iterable formulas.

# **Linear Manipulation**:

The methods covered in Linear Manipulations are Naive Gauss and LU Decomposition. What makes these methods linear manipulations and not iterable formulas is due to them not relying upon iteration to derive a solution, or an approximate solution. They use the general formula of {A}  {x} = {B}. These methods then proceed to use allowable manipulations in order to derive the answers. Ghe difference between the two methods falls down to the ectent of which they use these ideas.

**Naive Gauss**:
Naive Gauss is about as simple as it gets for linear manipulations. It begins by transforming the equation into Row Echelon Form. From there it beck solves to to find the solution to the given equation. These two steps can be memorized by simply remembering that Naive Gauss first executes forward elimination then back solving.

**LU Decomposition**: LU Decomposition takes care of the problems that are found with using methods such as Gauss Elimination such as their inefficiency of solving equations with the same {A} coefficients and different right-hand side coefficients {B}. To see the best visual representation of this method, check the top of page 280 in the class textbook(Numerical Methods for Engineers, 7th edition). 

This method first decomposes the {A} coefficient matrix into lower and upper matrices. The first of these matrices then is used to solve for the intermitent {D} matrix via the for {L} {D} = {B}. From there this new {D} matrix is then used to solve for the solution matrix {x} via the equation {U} {x} = {D}. I recomend writing a functioning Naive Gauss function then using that function to solve both of the aformetioned equations as it will save the space and time when writing a efficient LU Decomposition function. The difficult part to writing a LU Decomposition is successfully writing the Decomposition portion, though you can find functions in many different libraries such as scipy that have decomposition functions in them.



