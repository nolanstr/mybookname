---
redirect_from:
  - "/features/root-finding-open-and-bracketing-methods"
interact_link: content/features/root_finding_open_and_bracketing_methods.ipynb
kernel_name: python3
has_widgets: false
title: 'Roots of Equations Closed JN'
prev_page:
  url: /RootFinding
  title: 'Roots of Equations'
next_page:
  url: /features/Root_Finding_OPen
  title: 'Roots of Equations Open JN'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot
import plotly.graph_objs as go
init_notebook_mode(connected=True)
from __future__ import print_function
from ipywidgets import interact, interactive, fixed, interact_manual
import ipywidgets as widgets
import numpy as np
import time
import numpy as np

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



# **Graphical Method**:
This method needs no function, you just need to be capable of plotting the function where you can then look for the instance, or instances, of which the function is equal to zero.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def bisection(fun, a, b, tol):
    startTime = time.time()
    i = 0.0
    c = (a + b) / 2.0
    
    if fun(a) == 0:
        return a, i, 'guess a was root'
    if fun(b) == 0:
        return b, i, 'guess b was root'
    
    while i < 1000:
        i += 1
        if abs(fun(c)) < tol:
            break
        if fun(c) * fun(a) > 0:
            a = c
        else: 
            b = c
        c = (a + b) / 2
        
    elapseTime = startTime - time.time()
         
    return c, i, elapseTime

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def FalsePosition(fun, a, b, tol):
    startTime = time.time()
    i = 0
    
    if fun(a) == 0:
        return a, i, 'guess a was root'
    if fun(b) == 0:
        return b, i, 'guess b was root'

    c = b - (fun(b) * (a - b)) / (fun(a) - fun(b))
    
    while i < 1000:
        i += 1
        if abs(fun(c)) < tol:
            break
        if fun(c) * fun(a) > 0:
            a = c
        else: 
            b = c
        c = b - (fun(b) * (a - b)) / (fun(a) - fun(b))
            
    elapseTime = startTime - time.time()
    
    return c, i, elapseTime


```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def FunSelector(method, fun, a, b, tol):
    if method == 'bisection':
        root, i, elapseTime = bisection(fun,a, b, tol)
    else:
        root, i, elapseTime = FalsePosition(fun, a, b, tol)
    return root, i, elapseTime

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def KeyFun(fun,root):
    if fun(root) == 0:
        return print('Key = MAGIC')

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def runFun(method, function, a, b, tol):
    
    fun = lambda x: eval(function)
    
    root, i, elapseTime = FunSelector(method, fun, a, b, tol)
    print(i, 'iterations were completed in',abs(elapseTime),'seconds.')
    KeyFun(fun,root)
    
    RangeNearRoot = np.arange(a, b, 0.1)
    funVals = np.zeros(len(RangeNearRoot))
    
    for i in range(len(funVals)):
        funVals[i] = fun(RangeNearRoot[i])
    
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
w = interact(runFun,method = {'FalsePostion','bisection'}, function = {'2 * x','2*(x**2) + 3*x + 1','16*(x**3) - 11 *(x**2) + 14*x - 4'}, a=(-5,1,0.5), b=(2,4,0.5), tol=(1e-4, 5e-1, 1e-2))


```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_data_text}
```
interactive(children=(Dropdown(description='method', options=('FalsePostion', 'bisection'), value='FalsePostio…
```

</div>
</div>
</div>

