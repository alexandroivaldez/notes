# Optional Lab: Model representation

The lab uses a simple data set with only two data points to represent our training set:

- A house with 1000 square feet sold for $300k
- A house with 2000 square feet sold for $500k

```py
x_train = np.array([1.0, 2.0])
y_train = np.array([300.0, 500.0])
print(f"x_train = {x_train}")
print(f"y_train = {y_train}")
```

np.array([1.0, 2.0]) is NumPy's way of initializing arrays. In Javascript this would look like:

```js
const x_train = [1.0, 2.0]
```

In Python "f-strings" are basically JS template literals. You specify the variable and it's value by "embedding" it in the string. In JS it would look like this:

```js
console.log(`x_train = ${x_train}`);
```

## Number of training example `m`

Remember that `m` denotes the number of training examples. In the example above, `x_train = np.array([1.0, 2.0])` there are 2 training examples, 1.0 and 2.0.

`.shape` - Numpy arrays have a .shape parameter, which returns a python tuple with an entry for each dimension.

In Python, a tuple is an ordered collection of elements, similar to a list. However, tuples are immutable, which means once they are created, their elements cannot be changed or modified.

```py
my_tuple = (1, 2, 3, 4, 5)
```

`.shape[0]` - Returns the length of the array and number of training examples. Alternatively, you could use len(x_train) to get the length of an array/tuple.

## Plotting Data

`scatter()` - Is part of matplotlib and allows you to plot your data.

In the function `plt.scatter(x_train, y_train, marker='x', c='r')`, `marker` and `c` are parameters used to customize the appearance of the scatter plot created by Matplotlib's `scatter()` function.

<details>
  <summary>Here's what each parameter means:</summary>
  <p>
  marker - This parameter specifies the marker style used to represent each data point in the scatter plot. It determines the shape of the marker used at each point. The default marker is a circle. Some common marker styles include:

- `'.'`: point marker
- `'o'`: circle marker
- `'x'`: x marker
- `'^'`: triangle marker
- `'s'`: square marker

   You can explore more marker styles in the Matplotlib documentation.

c - This parameter specifies the color of the markers in the scatter plot. It can accept a variety of formats for specifying colors, including:

- Single letter color codes such as `'r'` for red, `'g'` for green, `'b'` for blue, etc.
- HTML color names like `'red'`, `'green'`, `'blue'`, etc.
- RGB tuples like `(1, 0, 0)` for red, `(0, 1, 0)` for green, etc.
- Hexadecimal color codes like `'#FF0000'` for red, `'#00FF00'` for green, etc.
  </p>

</details>

## Model Function

![Univariate Linear Regression Image](images/univariate-linear-regression.png)
