---
redirect_from:
  - "/features/eigenvalueproblem-massspring"
interact_link: content/features/EigenValueProblem_MassSpring.ipynb
kernel_name: python3
has_widgets: false
title: 'Eigenvalue JN'
prev_page:
  url: /EigenValue_LeastSquares
  title: 'Eigenvalue'
next_page:
  url: /LeastSquares_LinearizationInterpolation
  title: 'Least Squares Regression and Linearization with Interpolation'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---




<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
#This example is originally from pages 789 to 792 from the class book

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def DeterminantEigenVals(m1,m2,k):
    a = 1
    
    b = ((-2*k)/m1) + ((-2*k)/m2)

    c = ((3*(k**2))/(m1*m2))

    return a, b, c

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def Quadratic(a,b,c):
    xPos = (-b + m.sqrt((b**2) - (4*a*c))) / (2*a)
    xNeg = (-b - m.sqrt((b**2) - (4*a*c))) / (2*a)
    
    return xPos, xNeg

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def EigenSolver(m1,m2,k):
    StartTime = time.time()
    
    m1,m2,k = float(m1),float(m2),float(k)
    a,b,c = DeterminantEigenVals(m1,m2,k)
    w1,w2 = Quadratic(a,b,c)
    TotalTime = StartTime - time.time()
    
    print('The frequencies for the vibrations of m1 =',m1,'kg and m2 =',m2,'kg')
    print('with a k value of',k,'N/m are w^2 =',w1,'and',w2,'s^-1.')
    print('This calculation took',TotalTime,'seconds.')

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
w = interact(EigenSolver,m1='40',m2='40',k='200')


```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_data_text}
```
interactive(children=(Text(value='40', description='m1'), Text(value='40', description='m2'), Text(value='200'…
```

</div>
</div>
</div>

