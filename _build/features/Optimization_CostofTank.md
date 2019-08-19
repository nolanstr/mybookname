---
redirect_from:
  - "/features/optimization-costoftank"
interact_link: content/features/Optimization_CostofTank.ipynb
kernel_name: python3
has_widgets: false
title: 'Optimization of a tank JN'
prev_page:
  url: /Optimization
  title: 'Optimization'
next_page:
  url: 
  title: ''
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
import math as m
import numpy as np
from scipy.optimize import minimize

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
def Obj(params):
    
    L,D = params[0],params[1]
    
    t = 0.03
    
    p = 8000  #kg/m^3
    
    cw = 20 # $/m
    
    cm = 4.5 # $/kg
    
    Vo = 0.8 #required volume

    LMax = 2
    
    Dmax = 1
    
    VolTank = (np.pi*(D**2)*L) / 4
    
    if (VolumeTank(L,D)/Vo) < .98 or (VolumeTank(L,D)/Vo) > 1.05:
        return 10**10
    
    
    volCyl =  (L*np.pi) * ((((D/2) + t)**2) - ((D/2)**2))
    volPla = (np.pi * (((D/2) + t)**2) * t) * 2
    
    m = (volCyl + volPla) * p    
    
    lw = (4*np.pi) * (D + t)
    
    Cost = (cm * m) + (cw * lw)
    
    return Cost

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def Optimize(params):
    
    bnds = ((0.1,2.0),(0.1,1.0))
    
    OptimalCost = minimize(Obj,(1,1),method = 'TNC', bounds = bnds, tol = 1e-6)
    
    return OptimalCost
    
    

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
L = 1.0
D = 0.75
minimizedCost = Optimize([L,D])
print(minimizedCost)


```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
     fun: 5653.386530727479
     jac: array([3493.25182469, 7236.15466995])
 message: 'Converged (|f_n-f_(n-1)| ~= 0)'
    nfev: 53
     nit: 2
  status: 1
 success: True
       x: array([0.99907701, 0.99957091])
```
</div>
</div>
</div>

