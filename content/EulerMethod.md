# Euler's Method Intro:

  **Mathamatical explanation** : Euler's Method is a numerical method used to solve first order deifferential equations. 

  **General Definition**: To put it simply, Euler's method sets up a very simple y = mx + b equation that one would have seen many times in their academic career. The importance of Euler's method is the recursive nature in which each new point or solution to the equation is then lent to the following subsequent equation. 

  This can be understood more by looking at the y = mx + b equation. In this equation m is equivalent to the first order differential equation, or dydt, and b is equivalent to the initial condition of the equation or to the previous value of y. Finally the x in this equation is replaced with h, or the step size of which is chosen, which will have implications affecting the accuracy of this numerical method(discussed later). So with this understanding of the equation we can easily rewrite the equation as y_1 = (dydt * h) + y_0.

**Step Size**: As stated in the previous paragraph, the step size, or h, is extremely important to the accuracy of euler's method. In many cases when using a large step size, meaning the amount of points that approximations are made at is relatively small, you can often get values that are far off the desired goal due to overshooting or undershooting, which falls on the first order derivative, which may change drastically between two seperate points for approximations. These errors don't only occur at the end of approximations and often will be seen early on, thus propigating through all iterations and ultimately leaving you with a sub par analysis.

On the other hand when using a small step size, which gives many points of approximation, and thus will typically give a much more accurate solution. Unfortunately using extremely small step sizes is not feasible in certain situiations. If you've ever done Euler's method by hand, which you should have done in an ODE's course, you'll notice how much time each step of euler's equation takes just to pass on information to the next step, this is the same with computers. In instances where the step size is extremely small it can be quite evident to the student that the code they have written may be taking longer to complete where as with a large step size the code may run quickly. 

**Summary (sparknotes)**: Euler's method is a straight forward numerical method that takes advantage of the general equation of a line along with recursive iterations in order to approximate sultions to problems with given intial conditions and a first order differential equation. If the information supplied to the student in this section is not in depth enough or is not effective at explaining key points of Euler's Method, check page 27 from the book(Numerical Methods for Engineering vol. 7) or refer to any of the following links, the interactive section using Jupyter notebooks will follow directly after this section.

 1) https://en.wikipedia.org/wiki/Euler_method
 2) http://calculuslab.deltacollege.edu/ODE/7-C-1/7-C-1-h-c.html
 3) https://www.ugrad.math.ubc.ca/coursedoc/math100/notes/mordifeqs/euler.html




 

 