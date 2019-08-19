# **Optimization**: 

**Mathematical Definition**: Optimizers are Numerical Methods that use numerous different philosophies in order to achieve the optimal output of an equation by deriving the values of which give specified outcomes.

**General Definition**: Optimizers look for specific input values to achieve, typically, the minimal output. 

**Optimization**: This is quite possibly the most important section of this course, it's a section that quite litterally should be taught as an entire class due to its shear importance to Engineering in general. The ability to understand the essence of optimization and to be capable of applying it is something that, if you don't manage to take anything else from this course, can give you an edge over many others in the field. 

A great place to start for understanding Optimizations is to start by understanding Root location techniques, as the method and ideas behind these two topics are inherently linked. The philosophy of root location is to use an equation and its inputs/outputs as information that can be used to derive where the equation may have a root, such as is the same way in which optimizers find the optimal parameters to fit an equation. 

This class, in previous semesters, has typically had the main project be an optimization project. The project consisted of a train being propelled by a pneumatic piston. Some of the parameters that had to be optimized were the train length, height, the pressure in the piston from the begining, the piston gear, and the material that it's made of. All of these parameters are interconnected in such a way that the slightest adjustment of one parameter will cause the initial speed to vary.

**Aplication In Code**: The most effective way to set up an optimization problem is to create what is known as an objective function. The objective function is essentially the function that you want to be optimized. This function usually takes a single argument in the form of an array of parameters. These parameters are then passed into other functions that calcluate necessary values such as initial speed, brake(friction) force, time to reach a specified distance, and even distance traveled. These functions are your physics functions. The final necessary portion is to have filter functions. These are functions that make sure that the given parameters are legal, meaning whatever restrictions you are given are not broken. Typically when a given restriction is broken you will want to return a value that could not be the optimized value. From there you pass this objective function to your optimizer of choice along with given parameter ranges. When done correctly, you should recieve optimized parameters. 

  To better understand this section I recommend checking the following links:
  1) https://en.wikipedia.org/wiki/Mathematical_optimization
  2) https://www.viva64.com/en/t/0084/  (This is more for how to write efficient code)
  3) http://tutorial.math.lamar.edu/Classes/CalcI/Optimization.aspx
  
