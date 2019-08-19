---
redirect_from:
  - "/features/root-finding-open"
interact_link: content/features/Root_Finding_OPen.ipynb
kernel_name: python3
has_widgets: false
title: 'Roots of Equations Open JN'
prev_page:
  url: /features/root_finding_open_and_bracketing_methods
  title: 'Roots of Equations Closed JN'
next_page:
  url: /LinearEquations
  title: 'Linear Equations'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
from __future__ import print_function
from ipywidgets import interact, interactive, fixed, interact_manual
import ipywidgets as widgets
from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot
import plotly.graph_objs as go
init_notebook_mode(connected=True)

import time
import numpy as np
import math


```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

<div markdown="0" class="output output_html">
        <script type="text/javascript">
        window.PlotlyConfig = {MathJaxConfig: 'local'};
        if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}
        if (typeof require !== 'undefined') {
        require.undef("plotly");
        requirejs.config({
            paths: {
                'plotly': ['https://cdn.plot.ly/plotly-latest.min']
            }
        });
        require(['plotly'], function(Plotly) {
            window._Plotly = Plotly;
        });
        }
        </script>
        
</div>

</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def derivative(fun):
    if fun == '2 * (x**2)':
        funD = '4 * x'
    if fun == '(2*(x**2)) + (3*x) + 1':
        funD = '(4 * x) + 3'
    if fun == '(x**3) + 4 *(x)  - 16': 
        funD = '(3 * (x**2) + 4)'
    return funD

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def FunSelector(method):
    if method == 'Newton-Raphson Method':
        w = interact(NewtonRaphson , Fun = {'2 * (x**2)','(2*(x**2)) + (3*x) + 1','(x**3) + 4 *(x)  - 16'}, x0=(-15,15,1) , tol=(1e-4, 5e-1, 1e-2))
        return w
    if method == 'Secant Method':
        w = interact(SecantMethod , Fun = {'2 * (x**2)','(2*(x**2)) + (3*x) + 1','(x**3) + 4 *(x)  - 16'}, x0=(-15,14,1) , x1=(-15,14,1), tol=(1e-4, 5e-1, 1e-2))
        return w       
    if method == 'Brents Method':
        w = interact(BrentsMethod , Fun = {'2 * (x**2)','(2*(x**2)) + (3*x) + 1','(x**3) + 4 *(x)  - 16'}, x0=(-15,14,1) , x1=(-15,14,1), tol=(1e-4, 5e-1, 1e-2))
        return w   

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def printFun(fun, root, totalTime, iterations):
    RangeNearRoot = np.arange(root - 2, root + 2, 0.1)
    funVals = np.zeros(len(RangeNearRoot))
    
    for i in range(len(funVals)):
        funVals[i] = fun(RangeNearRoot[i])
    
    print(iterations, 'iterations were completed in',totalTime,'seconds!')
    #plot both datasets
    plot_vals = go.Scatter(name='Equation Near Root', x=RangeNearRoot, y=funVals)
    plot_approx = go.Scatter(name='Root Approximation.', x=np.array([root]), y=np.array([fun(root)]))
        
    iplot([plot_vals, plot_approx])
    

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def KeyFun():
    print('Key = COMPLEX')

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def NewtonRaphson(Fun, x0, tol):
    #write function to determine funD
    fun = lambda x: eval(Fun)
    funD = lambda x: eval(derivative(Fun))
    i = 0
    startTime = time.time()
    if abs(fun(x0)) < tol:
        print('Given intital x value is a root')
        return x0
    
    while i < 2000:
        xi = x0 - (fun(x0)/funD(x0))
        x0 = xi
        i += 1
        
        if fun(x0) < tol:
            totalTime = time.time() - startTime
            printFun(fun,x0,totalTime,i)
            return x0 , totalTime, i
        
    totalTime = time.time() - startTime
    printFun(fun, x0, totalTime, i)
    
    return x0 , totalTime , i

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def SecantMethod(Fun,x0,x1,tol):
    i = 0
    fun = lambda x: eval(Fun)
    startTime = time.time()
    if x0 == x1:
        print('Given x0 and x1 are not roots but are equal to each other, choose different values!')
        return
    
    if abs(fun(x1)) < tol:
        print('Given intital x value is a root')
        return x1
    if abs(fun(x0)) < tol:
        print('Given intital x value is a root')
        return x0
    
    while abs(fun(x1)) > tol and i < 1000:
        x2 = x1 - (fun(x1) * (x0 - x1)) / (fun(x0) - fun(x1))
        x0 = x1
        x1 = x2
        
        i += 1
        
    totalTime = time.time() - startTime
    printFun(fun, x0, totalTime, i)
    
    return x1 , totalTime , i

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
#Method was found online!!

def BrentsMethod(Fun, x0, x1, tol):
    startTime = time.time()
    max_iter = 50
    fun = lambda x: eval(Fun)
    
    fx0 = fun(x0)
    fx1 = fun(x1)
    assert (fx0 * fx1) <= 0, "Root not bracketed" 
 
    if abs(fx0) < abs(fx1):
        x0, x1 = x1, x0
        fx0, fx1 = fx1, fx0
 
    x2, fx2 = x0, fx0
 
    mflag = True
    steps_taken = 0
 
    while steps_taken < max_iter and abs(x1-x0) > tol:
        fx0 = fun(x0)
        fx1 = fun(x1)
        fx2 = fun(x2)
 
        if fx0 != fx2 and fx1 != fx2:
            L0 = (x0 * fx1 * fx2) / ((fx0 - fx1) * (fx0 - fx2))
            L1 = (x1 * fx0 * fx2) / ((fx1 - fx0) * (fx1 - fx2))
            L2 = (x2 * fx1 * fx0) / ((fx2 - fx0) * (fx2 - fx1))
            new = L0 + L1 + L2
 
        else:
            new = x1 - ( (fx1 * (x1 - x0)) / (fx1 - fx0) )
 
        if ((new < ((3 * x0 + x1) / 4) or new > x1) or
            (mflag == True and (abs(new - x1)) >= (abs(x1 - x2) / 2)) or
            (mflag == False and (abs(new - x1)) >= (abs(x2 - d) / 2)) or
            (mflag == True and (abs(x1 - x2)) < tol) or
            (mflag == False and (abs(x2 - d)) < tol)):
            new = (x0 + x1) / 2
            mflag = True
 
        else:
            mflag = False
 
        fnew = fun(new)
        d, x2 = x2, x1
 
        if (fx0 * fnew) < 0:
            x1 = new
        else:
            x0 = new
 
        if abs(fx0) < abs(fx1):
            x0, x1 = x1, x0
 
        steps_taken += 1
    totalTime = time.time() - startTime
    KeyFun()
    printFun(fun, x0, totalTime, steps_taken)
    
    
    return x1 , totalTime , steps_taken

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def runFun(method):
    w = FunSelector(method)
    

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# interacts with runFun which displays interaction with each method
w = interact(runFun,method = {'Newton-Raphson Method','Secant Method','Brents Method'})



```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_data_text}
```
interactive(children=(Dropdown(description='method', options=('Brents Method', 'Secant Method', 'Newton-Raphso…
```

</div>
</div>
</div>

