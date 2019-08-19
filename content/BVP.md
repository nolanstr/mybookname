# **Boundary-Value Problems**:

**Mathematical Definition**: A Boundary-Value problem(or BVP) is a problem that contains both a differential equation accompanied by constraints which are known as boundary conditions.

**General Definition**: The general definition of a BVP is a problem that has a differential equation along with boundary conditions that are taken into account and can be used to solve for all other outcomes of the equation.

**Intro**: In order to understand BVP it's good practice to begin by understanding ODE problems first. In the case of ODE problems you typically start off with initial condition problems. These can be problem like a that of a falling ball, where the initial velocity of the ball can dictate the rest of the following values/outcomes. Now taking this knowledge you can apply it to further understanding BVPs, in that they take into account conditions that affect the outcomes, except for BVP, these conditions agree with each other. Examples of these problems are noninsulated rod problems. For this section we will talk about to methods used to solve these problems, the Shooting Method and the Finite Difference Method.

# **The Shooting Method**: 
The Shooting method takes a BVP and converts it into a initial value problem, of which creates an initial value that becomes a geuss and check value that can be found easier by using extrapolation. To find the equation for the form of Runge-Kutta 4th order approximationg that will work for solving a system of ODEs check pages 741-743 of the book(Numerical Method for Engineers, 7th edition). This section also constains pseudocode for this method, though it's not the most helpful of pseudocodes and I would recommend checking the Jupyter notebooks sectino for the Shooting Method.

This method comes easiest after fully understanding Euler's method and Runge-Kutta methods as it is added to the growing list of Numerical Methods used in this class that take or find the slope of an equation, and accompanied by a step size, find the following outputs of an equation. 

To better understand this section I recommend checking the following links:
1) http://people.bu.edu/andasari/courses/Fall2015/LectureNotes/Lecture12_15Oct2015.pdf
2) https://www.webpages.uidaho.edu/~barannyk/Teaching/shooting_linear.pdf
3) https://www.youtube.com/watch?v=ZMgikZ-lcS8

# **Finite Difference Method**:

Finite difference approximation methods are the most common alternatives to the Shooting method for BVPs. What they do different is that they replace the derivatives in the original with the finite-divided-difference approximation's for each respective derivative. Then from rearanging that equation one can put together a matrix equation in the form {A} {x} = {B}. 

This method, just like the shooting method, is also heavily dependent upon step size, and more specifically in the case of the Finite Difference method, the nodes. These nodes are extremely important to this method, as the more nodes one solves for typically the more accurate the solution. Just as in most other methods though, the more accurate the solution the more time and computing power is necessary to solve for these nodal values. 

This method is a better alternative to the Shooting Method when dealing with higher-order equations due to the difficulty to apply approximation formulas in order to achieve a solution. If you would like to see a worked out example(somewhat), check pages 786-788 from the class book(Numerical methods for Engineers, 7th edition).

To better understand this section I recommend checking the following links:

1) https://en.wikipedia.org/wiki/Finite_difference_method

2) https://www.sciencedirect.com/topics/engineering/finite-difference-method

3) http://www.scholarpedia.org/article/Finite_difference_method
