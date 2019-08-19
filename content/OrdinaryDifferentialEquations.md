# **Ordinary Differential Equations** 

**Mathematical Defintion**:
Ordinary differential equations(or ODE) are functions that are composed of an unknown function and its derivatives. These functions consist of one independent variable(typically time but not restricted to time only). If the function given consist of more than one independent variable then they are considered partial differential equations(or PDE).

 **General Defintion**: In a general sense an ODE is an equation that has the relationship of the derivatives of a variable and it's self. Examplpes of functions that have relations like this could be the equation of a falling parachutists, dV/dt = g - (c/m)*V.

**Intro**:  Through using a multitude of different methods you can use these equations to make real world predictions using generalized and often ideal conditions. These methods are often Euler's method and the variants of Runge-Kutta. 

# **Euler's Method Intro:**

  **Mathamatical explanation** : Euler's Method is a numerical method used to solve first order deifferential equations. 

  **General Definition**: To put it simply, Euler's method sets up a very simple y = mx + b equation that one would have seen many times in their academic career. The importance of Euler's method is the recursive nature in which each new point or solution to the equation is then lent to the following subsequent equation. 

  This can be understood more by looking at the y = mx + b equation. In this equation m is equivalent to the first order differential equation, or dydt, and b is equivalent to the initial condition of the equation or to the previous value of y. Finally the x in this equation is replaced with h, or the step size of which is chosen, which will have implications affecting the accuracy of this numerical method(discussed later). So with this understanding of the equation we can easily rewrite the equation as y_1 = (dydt * h) + y_0.

**Step Size**: As stated in the previous paragraph, the step size, or h, is extremely important to the accuracy of euler's method. In many cases when using a large step size, meaning the amount of points that approximations are made at is relatively small, you can often get values that are far off the desired goal due to overshooting or undershooting, which falls on the first order derivative, which may change drastically between two seperate points for approximations. These errors don't only occur at the end of approximations and often will be seen early on, thus propigating through all iterations and ultimately leaving you with a sub par analysis.

On the other hand when using a small step size, which gives many points of approximation, and thus will typically give a much more accurate solution. Unfortunately using extremely small step sizes is not feasible in certain situiations. If you've ever done Euler's method by hand, which you should have done in an ODE's course, you'll notice how much time each step of euler's equation takes just to pass on information to the next step, this is the same with computers. In instances where the step size is extremely small it can be quite evident to the student that the code they have written may be taking longer to complete where as with a large step size the code may run quickly. 

**Summary (<mark>sparknotes</mark>)**: Euler's method is a straight forward numerical method that takes advantage of the general equation of a line along with recursive iterations in order to approximate sultions to problems with given intial conditions and a first order differential equation. If the information supplied to the student in this section is not in depth enough or is not effective at explaining key points of Euler's Method, check page 27 from the book(Numerical Methods for Engineering vol. 7) or refer to any of the following links, the interactive section using Jupyter notebooks can be found in the next page, *Euler's Method in Jupyter Notebooks*.

 1) https://en.wikipedia.org/wiki/Euler_method
 2) http://calculuslab.deltacollege.edu/ODE/7-C-1/7-C-1-h-c.html
 3) https://www.ugrad.math.ubc.ca/coursedoc/math100/notes/mordifeqs/euler.html


# **Euler's Method Extras:**

**Function Handles**: For those students who would like to create a Euler's method function that is variable it may be best to look into using function handles. Function handles are essentially just regular functions that can be easily written and changed through just one line of code. When writting this variable Euler's method function it's best to treat one of the inputs as a function handle, then using the function handle later in the functino and directly passing values into it, akin to having a function, lets say **function(value,fun)**, where **value** could be your initial position and **fun** is the function you pass through to it. Then in the function you can have the function handle executed easily by doing something similar to **fun(value)**. A Jupyter notebook example for this is locked by your professor or by a key/easter egg that can be unlocked through toying around with the main *Euler's method Jupyter Notebooks*. *Hint*, if you find Euler's weakness, you find the key.

# **Runge-Kutta Intro**: 

**Mathematical Definition**: Like Euler's method, Runge-Kutta is a numerical method used to solve ordinary differential equations in the form **dy/dt = f(x,y)**. Where Runge-Kutta differs from Euler's method is the interpretation of how one sets up the formula **y_i+1 = y_i + (Φ*h)**. Instead of simply using the first derivative of an equation, Runge-Kutta uses selective methods of **extrpolation** to compute this method.

**General Definition**: In a more general sense Runge-Kutta and Euler's method can be viewed as the same(though in many references/sources Euler's Method is grouped up into the group Runge-Kutta) with the primary difference being that of how the slope is found. 

**Step Size Similarities**: Just as in Euler's Method, the ramifications of step size on the accuracy of the numerical method are directly related, as in the smaller the step size h, the higher the accuracy. Yet again the primary draw back with this is that the smaller h is, the more iterations necessary, and thus the longer the method will take and the more intensive on your computer the solution will be. This is a common trend with all of Numerical Methods in that there is no silver bullet, no numerical method that does everything as one would want. Each method has its own draw back, but when understood well it is easy to know when and where to use these numerical methods affectively.

**Runge-Kutta Orders**: Runge-Kutta methods accuracy depend upon the order of the method chosen. one can use any of the numerous versions of Runge-Kutta from the second-order Runge-Kutta method to the fifth-order Runge-Kutta method(all of which are found in the book), and if one wants an even more accurate method they can go higher. Just like step-size though the difficulty to compute also grows as the order gets larger but not in the same sense. A higher oder Runge-Kutta doesn't compute more iterations than a lower order Runge-Kutta but the computation for Φ, the slope, is more intensive. The trade off here isn't as grand as the trade off between step size and accuracy, but it is worth taking into account when approximating a solution. 

**Additional Resources and Equations**: 
1) https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods
2) http://web.mit.edu/10.001/Web/Course_Notes/Differential_Equations_Notes/node5.html

Additionally one can look through part seven of the book(Numerical Methods for Engineers, 7th edition) that start on page 699.


**Summary (<mark>sparknotes</mark>)**: Runge-Kutta approximations are first order approximations that aim to predict outcomes using one what could view as an updated and upgraded version of Euler's Method. 



