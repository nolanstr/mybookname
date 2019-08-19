---
redirect_from:
  - "/features/linear-equation"
interact_link: content/features/Linear_Equation.ipynb
kernel_name: python3
has_widgets: false
title: 'Linear Equations JN'
prev_page:
  url: /LinearEquations
  title: 'Linear Equations'
next_page:
  url: /Optimization
  title: 'Optimization'
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
from scipy.linalg import lu

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
def NaiveGauss(array,b):
    startTime = time.time()
    array = np.array(array , dtype = 'float')
    b = np.array(b , dtype = 'float')
    x = np.zeros(len(b))
    combined = np.zeros([len(b),len(b) + 1])
    
    for i in range(len(b)):
        if array[i,i] == 0:
            print('Naive Gauss only work sif the pivot does not equal 0!(reorganize if neccessary!)')
            return 'Error'
    
    for i in range(len(b)):
        for j in range(len(b)):
            combined[i,j] = array[i,j]
        combined[i,len(b)] = b[i]
    
    
    for i in range(len(b)):
        combined[i] = combined[i]/combined[i,i]
        for j in range(i + 1,len(b)):
            combined[j] -= (combined[i] * combined[j,i])
            
    array = np.delete(combined,len(b),1)
    b = np.delete(combined,np.s_[0:len(b)],1)

    for i in np.arange(len(b)-1,-1,-1):
        vals = array[i] * x
        x[i] = b[i] - sum(vals)
    
    totalTime = time.time() - startTime
    
    return x, totalTime

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def LUDecomp(array,b):
    StartTime = time.time()
    
    array = np.array(array , dtype = 'float')
    b = np.array(b , dtype = 'float')
    _ ,lower,upper = lu(array)
    x = np.zeros(len(b))
    
    
    D, time1 = NaiveGauss(lower,b)
    x, time2 = NaiveGauss(upper,D)
    totalTime = (time.time() - StartTime) + time1 + time2
    return x , totalTime

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def GaussSeidel(array,b,maxItter):
    StartTime = time.time()
    
    array = np.array(array,dtype = 'float')
    b = np.array(b,dtype = 'float')
    x = np.zeros(len(b), dtype = 'float')

    for loop in range(maxItter):
        
        for i in range(len(b)):
            As = np.delete(array[i],i)
            bs = np.delete(x,i)
            sumVals = sum(As * bs)
            
            x[i] = (b[i] - sumVals) / array[i,i]
    TotalTime = time.time() - StartTime
            
    return x , TotalTime

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def FunSelector(function,array,b):
    
    if function == 'Naive Gauss':
        x, totalTime = NaiveGauss(array,b)
        print('x =',x)
        print('Time needed for Naive Gauss Method =',totalTime)
        
    if function == 'LU Decomposition':
        x, TotalTime = LUDecomp(array,b)
        print('x =',x)
        print('LU Decomposition took',TotalTime,'seconds to complete.')
    
    if function == 'Gauss Seidel':
        x , TotalTime = GaussSeidel(array,b,10)  #Tolerance is built in for this example
        print('x =',x)
        print('Gauss-Seidel took',TotalTime,'seconds to complete with 100 iterations.')
    return
    
    

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def runFun(function,row1,row2,row3,b):
    array = np.array([eval(row1),eval(row2),eval(row3)])
    b = np.array(eval(b))
    print(array,'* x = ',b)
    
    FunSelector(function,array,b)
    
    return


```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
array = np.array([[1,0,0],[0,1,0],[0,0,1]])
b = np.array([0,0,0])

print(NaiveGauss(array,b))


```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
(array([0., 0., 0.]), 0.002537965774536133)
```
</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# interacts with runFun which displays interaction with each method
w = interact(runFun , function = {'Naive Gauss','LU Decomposition','Gauss Seidel'} , row1 = '[1,0,0]' , row2 = '[0,1,0]' , row3 = '[0,0,1]' , b = '[0,0,0]')



```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_data_text}
```
interactive(children=(Dropdown(description='function', options=('Naive Gauss', 'LU Decomposition', 'Gauss Seid…
```

</div>
</div>
</div>

