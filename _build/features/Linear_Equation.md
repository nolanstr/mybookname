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
  url: /OrdinaryDifferentialEquations
  title: 'Ordinary Differential Equations'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
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
interactive(children=(Dropdown(description='function', options=('Gauss Seidel', 'LU Decomposition', 'Naive Gau…
```

</div>
</div>
</div>

