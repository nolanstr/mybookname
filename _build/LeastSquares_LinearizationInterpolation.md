---
redirect_from:
  - "/leastsquares-linearizationinterpolation"
title: 'Least Squares Regression and Linearization with Interpolation'
prev_page:
  url: /features/EigenValueProblem_MassSpring
  title: 'Eigenvalue JN'
next_page:
  url: /features/LeastSquaresRegression_Linear
  title: 'Least Squares Regression JN'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# **Least Squares Regression & Linearization with Interpolation**: 

**Methematical Definitions**: Least Squares Regression is a mathematical attempt to create an equation that in a general sense, follows the trends of a given set of data points, while minimizing the discrepency between the set of data and the equation derived.

Linearization is the mathematical manipulation of an equation in order to linearize its outputs according to its inputs while Interpolation is the attempt to approximate values between given data points via numerous different Numerical Methods.
 
**General Defintion**: The general idea of Least Squared Regression is that it is a method that takes a set of data of which is then converted into an equation that will closely match the trends and positions of the given data.

Linearization is where you make changes to a function in order linearize the outputs to ease the ability of one to see the relationships of characteristics of the function. Interpolation takes advantage of many Numerical Methods to effectively produce new data points between given precise data points.

 # **Least Squares Regression**: 
  Least Squares Regression in a linear sense works by solving for the general equation for a line, y = (m*x) + b, in a way that matches it to a set of data points. these equations are fairly simple, the first of which being a1 = (n * ∑(x_i*y_i) - ∑x_i * ∑y_i) / (n * ∑(x_i^2) - (∑x_i)^2). This equation is then substitued into the equation a0 = mean(y) - (a1 * mean(x)). Finally these two equation are substitued into the linear equation like this, y = (a0 * x) + a1.

  Unfortunately though not all information is linear, and thus when applying a linear Least Squares Regression to a set of data that is parabolic or exponential in growth, the method will fail by giving an equation that does not match the given data.

  Due to this it is good practuce to look at the plotting of data vs the equation derived, if these two seemingly match well then you need not make any changes and you can then use the equation as a relatively accurate approximation for the data. If these two seemingly do not agree you can then use other approximations including the power equation. A helpful alternative to plotting these two would be to look at the error analysis of linear fit that will give you a good idea about the accuracy. To find the equations for the more complez Linearizations, check page 768-769 of the book(Numerical Methods for Engineers, 7th edition).

  To better understand this section I recommend checking the following links:

  1) https://www.statisticshowto.datasciencecentral.com/least-squares-regression-line/

  2) https://www.mathsisfun.com/data/least-squares-regression.html

  3) http://mathworld.wolfram.com/LeastSquaresFitting.html

  # **Linearization & Interpolation**: 
In order to generate more accurate approximations it is necessary to understand the concept of Linearization, which is essentially the attempt of one to take a function and to, through mathematical manipulations, make it into a linear function. Often this can be done through simply "loging" both sides(when you place everything into a log). You'll will see graphs that are manipulated in ways like these in many other classes, including ECE and MSE, both of which you charts whose x and y values may be in the log scale. 

There are many different methods for linearizing equations, from the power equation to the saturation-growth-equation. These can all be seen on pages 468-469 of the book(Numerial Methods for Engineers, 7th edition).

Interpolation is an effective way to derive data from given data points and is arguably one of the most important sections of Numerical Methods, along with Optimizations and solving ODEs through computation. The first of the Interpolations you may see is the Linear Interpolation, of which has a formula very similar to that of the Taylor's series. The formula is **f_1(x) = f(x_0) + ((f(x_1) - f(x_0)) * (x - x_0)) / (x_1 - x_0)**. Breaking down this approximation it can be understood that the equation uses the general equation for a slope between two points, then using that formula it multiplies the slope by the difference in x between the lower x value and the x value of which is being approximated. Finally it adds this value to the output value of the lower bound which gives you a relatively efficient and easily understood approximation for x. Linear Interpolation is obviously a very simple and rudimentary method that has virtually no bells and whistles, especially in comparison to the other two methods I will discuss.

The method is the Quadratic Interpolation method, of which, you geussed it, uses a generalized quadratic equation to derive an approximation for new data points. The equation for this method I will not be writing in here as it would muddy this section up a bit much but all of its equations can be found on page 493 of the book(Numerical Methods for Engineers, 7th edition). As you probably assumed, this method provides more accurate results than general Linear Interpolation but adds a slight bit more difficulty to the creation of the function in code. It also should theoretically take more time for a computer to run the approximation, but in all reality the calculations preformed are relatively minute as far as what a modern cpu can handle, thus meaning in most situations the Quadratic Interpolation method is a better option than Linear Interpolation. 

Final method is the Newton's Interpolating Polynomials Method(or NIPM). This method is by far the most accurate and most used because of this, but also because of its relatively simple and effective philosophy. This method, of which I wont be writing in here for the same reason as Quadratic Interpolation but can be found on pages 495-496 in the class book(Numerical Methods for Engineers, 7th edition), takes advantage of finite divided differences and second finite divided differences. Using these methods NIPM creates what can be described as a layered equation, that generates values of which will be used to generate one less value in each recursion up until you only have one value left, which will be the approximation. 

  To better understand this section I recommend checking the following links:

  1) https://en.wikipedia.org/wiki/Newton_polynomial
  2) https://en.wikipedia.org/wiki/Linear_interpolation
  3) https://en.wikipedia.org/wiki/Polynomial_interpolation
  4) https://en.wikipedia.org/wiki/Linearization

