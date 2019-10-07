---
redirect_from:
  - "/rootfinding"
title: 'Roots of Equations'
prev_page:
  url: https://github.com/jupyter/jupyter-book
  title: 'Numerical Methods Student Assistance Book'
next_page:
  url: /features/root_finding_open_and_bracketing_methods
  title: 'Roots of Equations Closed JN'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# **Rooting Finding Methods**:

 **Mathematical Definition**: Root finding methods use various different approaches, all of which have their own strengths and weaknesses, to find the roots of functions, typically of which are too difficult or time consuming to solve for algebraically.

**General Defintion**: Fot this section it is quite difficult to pin down the basics of how root finding methods accomplish their tasks in a broad sense, and thus we will cover all of the methods individually, nevertheless the general definttion of a root finding method is a numerical method that tends to take advantage of recursive iterations, methematical theorums, and the functions themselves to find points of which appear to be roots according to pre-determined tolerances.

## **Bracketing Methods**:
In order to better understand root finding methods you must break them into two categories; bracketing and open methods. This section will talk about bracketing methods.

**Basics of Bracketing Methods**:
Bracketing methods are essentially just root finding methods that restrict the scope of the area in which roots can be found. These methods will take arguments that typically consist of upper and lower boundaries and the function itself.

**Graphical Method**: The graphical method is as basic as it gets. Essentially one just creates a plot of a function, then looks to where the function equals zero, f(x) = 0. Nothing more, nothing less. The faults with this method are due to it's simplicity. When one is merely looking at a function it is difficult to precisely mark exaclty where a root is, and thus leaving plenty of room for error.

**Bisection Method**: The bisection method tkaes into acount just three things; the function one is trying to find the root of, an upper geuss, and a lower guess. These two guesses need to be opposite in sign when plugged into the function, fun(upper) < fun(lower) or fun(upper) > fun(lower). This method then uses the midpoint between the upper and lower bounds of which is plugged into the function. The output of the midpoint is then compared to the output of the upper and lower bounds. Whichever of the two bounds has same sign(be it positive or negative) will be replaced by the midpoint. These steps are carried out until the midpoint value reaches a value close enough to zero according to a given tollerance. Where this method fails is if there are more than one root between given upper and lower bounds, since the method has no way of saying that there is more than one root. This method is also relatively brute in it's approach to root finding due to it not taking into consideration the magnitudes of your upper and lower geusses, and thus will typically not be as fast as other more complex methods.

**False-Position Method**: The false-postion method, also known as the regula falsi method. This method is very similar to the aforementioned method in that it still takes an upper and lower geusses, but this method takes advantage of similar triangles in order to take into account the magnitude of the geusses. The two images following should show give a better understanding to this explanation.

## **Open Methods**:
The next group of root finding functions are the open methods, which typically are faster than bracketing methods but they tend to run the risk of not converging on an actual root.

**Open Method Basics**: Open methods are very similar to bracketing methods in the types of arguments you can expect, but they tend to have more intense arguments on top of the expected upper/lower boundaries and the function. You shouldn't be surprised to find open methods that call for more geusses or that even call for the derivatives of functions.

**The Newton Raphson Method**: This method is my personal favorite, as well as the favorite of many other users as it is one of the most widely used root finding methods due to the shear simplicity and beauty of the method. The Method itself takes advantage of the taylor series, in which it cuts of the expansion past the first derivative mark(of which it is assumed that this portion roughly equates to zero), then using what is left as well as making assumptions such as f(x_i+1) = 0, you get the given equation.

**The Secant Method**: The Secant method is another widely used root finding method due to the fact that it shoots to aleviate the main issue with the Newton Raphson Method, of which is finding the derivative of the main function. Though finding the derivative of a simple polynomial is quite simple, in some instances you may have equations that have derivatives that are too difficult to find, which is where this method finds its glory. Instead of a derivative, the Secant Method approximates the derivative by using the backward divided finite difference. The equation for this method can be seen below.

**Brent's Method**: Developed by Richard Brent back in 1973 using the previously developed algorithm create by Theodorus Dekker in 1969, Brent's root location method takes advantage of both open and closed bracket methods, in which it will use open methods when possible, and reverting back to closed bracketing methods when neccessary. This method in fact uses three seperate methods. The first of the open methods it uses is the Secant Method and the second is the Inverse Quadratic interpolation method, but when it reverses back to closed bracketing methods it used the Bisection Method. To get a better understanding for this method I highly recommend reading the section of the book, **Numerical Methods** *for Engineers* (7th edition). The oages for this section are pages 162 through 166. In these pages you can also find pseudocode for this algorithm which may be helpful.
