# Optional Lab: Cost function

In this lab I learned how to implement the cost function for linear regression with one variable. More specifically, I experimented with a model that predicts housing prices fiven the square foot size of a house.

`cost` - how well a model is predicting the target price ($) of a house.

Cost Function with One Variable Equation:
$$J(w,b) = \frac{1}{2m} \sum\limits_{i = 0}^{m-1} (f_{w,b}(x^{(i)}) - y^{(i)})^2$$
where 
  $$f_{w,b}(x^{(i)}) = wx^{(i)} + b$$

## Computing Cost Function

The code below computes the cost function for linear regression.

```py
def compute_cost(x, y, w, b): 
    
    m = x.shape[0] 
    
    cost_sum = 0 
    for i in range(m): 
        f_wb = w * x[i] + b   
        cost = (f_wb - y[i]) ** 2  
        cost_sum = cost_sum + cost  
    total_cost = (1 / (2 * m)) * cost_sum  

    return total_cost
```

## Summary

The cost equation determines how well your predicitions (w,b) fit your training data.

Minimizing the cost (how well a model is predicting the target price ($) of a house) provides optimal values for w and b.