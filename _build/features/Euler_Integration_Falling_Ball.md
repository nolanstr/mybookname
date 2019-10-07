---
redirect_from:
  - "/features/euler-integration-falling-ball"
interact_link: content/features/Euler_Integration_Falling_Ball.ipynb
kernel_name: python3
has_widgets: false
title: 'Euler's Method JN'
prev_page:
  url: /OrdinaryDifferentialEquations
  title: 'Ordinary Differential Equations'
next_page:
  url: /features/Euler_Integration_Falling_Ball_fHandles
  title: 'Euler's Method w/ special functions JN'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


















<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Define the variables that can be interacted with
w = interact(plot_v, m=(1, 10, 1), c=(0.0, 1, 0.1), h=(0.05, 2, 0.05), v_o = (-5,5,1), ODE={'vacuum','viscous'})

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_data_text}
```
interactive(children=(IntSlider(value=5, description='m', max=10, min=1), FloatSlider(value=0.5, description='…
```

</div>
</div>
</div>

