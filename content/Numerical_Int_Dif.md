# **Numerical  Integration & Differentiation**:
**Mathematical Definition**: Numerical Integration and Differentiation are numerical methods that attempt to approximate the integration and differentiation of functions through mathematical formulas. 

**General Definition**: Numerical Differentiation attempts to approximate the derivative of a function through a various assortment of methods, some of which take inspiration from the limit definition of a derivative. On the other hand Numerical Integration attempts to integrate functions from a to b, these methods follow ideas that students should have seen in calculus with the Riemann Sums. 

**Numerical Integration**: For this section of Numerical Methods there are roughly three different Integration techniques you will need to understand well. Those three are the Trapezoidal Rule, Simpson's Rules, and Gauss Quadrature. To begin, I will cover the easiest, that being the Trapezoidal Rule. The integrative method works especially well with first order linear equations. The formula for the Trapezoidal Rule is I = (b -a) * ((f(a) + f(b) / 2).

The next method, or really set of methods are Simpson's Rules. Simpson's Rules essentially take the Trapezoidal Rule and bring in the creation of polynomials. The idea is that if you have f(a) and f(b), there is a point equally spaced between those to points which will give you three points, which can then be used to create a second order polynomial that will give a more accurate estimation of the total area underneath the curve. This relationship between point and order is constant, being that if you have n points, then the order of the polynomial used to approximate is n-1. The two versions of Simpson's Rule are Simpson's 1/3 Rule, and Simpson's 3/8 Rule. The formulas for these can be found on pages 615-622(Numerical Methods for Engineers, 7th edition) as well as plenty of examples to help.

Finally we have Gauss Quadrature. Instead of useing given fixed points or a set of points between fixed points, Gauss Quadrature aims to reavaulte th eintegral as a whole. Using given constants, c, and the a manipulated version of the function, you are esentially finding the area underneath a straight line that is roughly an average of the trends of the given equation. 

  To better understand this section I recommend checking the following links:
1) https://en.wikipedia.org/wiki/Trapezoidal_rule
2) https://en.wikipedia.org/wiki/Simpson%27s_rule
3) http://mathworld.wolfram.com/Legendre-GaussQuadrature.html
4) https://en.wikipedia.org/wiki/Gaussian_quadrature

**Numerical Differentiation**: Numerical Differentiation methods are ruled by finite divided difference(FDD) for all of the methods covered in the Jupyter notebooks and this class. FDD is built off of the general equation for a slope, that being slope = (f(x1) - f(x0)) / (x1 - x0). This equation is maipulated into a few different versions, those being forward, backward, and central versions of FDD.

First the forward version of FDD does exactly as assumed, it takes your given point, x0, then using a step size, it evaluates the function at x0+h. this formula looks something like this, f'(x0) = ((f(x0+h) - f(x0)) / h). 

Next we have the backward FDD, which does the exact same as forward but reversed. Instead of evaluating f(x0) and f(x0+h), your evaluating f(x0) and f(x0-h). Thus the formula becomes f'(x0) = (f(x0) - f(x0-h)) / h.

Finally we have the centered methods. Now if you look into the book the way that they go about explaining how to create this formula is by stating that the Taylor series for backward FDD minus the Taylor series formula for forward FDD, then subrtracting out values with a order of 2 or higher, you are left with this equation, f'(x0) = (f(x+h) - f(x-h)) / (2 * h). Now if you'd prefer to think of the derivation of this equation in a more general sense, you can think about the general form for slope, and that if you were to find slope at a midpoint of two points seperated 2h from each other, then you would just simply take the difference in height divided by the distance between thee points, and voila, you have the same exact formula(technically, the formula is missing the error).

  To better understand this section I recommend checking the following links:
  1) https://en.wikipedia.org/wiki/Finite_difference
  2) http://www.mathematik.uni-dortmund.de/~kuzmin/cfdintro/lecture4.pdf
  3) http://mathworld.wolfram.com/FiniteDifference.html
  