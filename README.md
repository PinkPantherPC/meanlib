# meanlib

`meanlib` is a Python library designed to facilitate the computation of various types of means, including simple means, rolling means, and weighted means. It provides easy-to-use classes and functions to update, compute, and retrieve means dynamically as new data becomes available.

## Features

- SimpleMean: Calculate and update a simple arithmetic mean with each new value.
- Mean: Calculate a rolling mean with an optional limit on the number of values stored.
- Weighted Mean Function: Calculate the weighted mean of a list of values.

## Usage

Here are some basic examples of how to use the library.

### Simple Mean Calculation

```python
from meanlib import SimpleMean

# Initialize the SimpleMean object
simple_mean = SimpleMean()

# Update the mean with new values
simple_mean.update(5)
simple_mean.update(10)
print(simple_mean.get_mean())  # Output: 7.5
```

### Rolling Mean with a Maximum Limit

```python
from meanlib import Mean

# Initialize the Mean object with a maximum of 3 values
mean = Mean(max_size=3)

# Update the mean with new values
mean.update(10)
mean.update(20)
mean.update(30)
print(mean.get_mean())  # Output: 20.0

# Adding another value, which will remove the oldest value (10)
mean.update(40)
print(mean.get_mean())  # Output: 30.0
```

### Weighted Mean Calculation

```python
from meanlib import weighted_mean

# Define values and their corresponding weights
values = [1, 2, 3, 4]
weights = [1, 2, 1, 1]

# Calculate the weighted mean
wm = weighted_mean(values, weights)
print(wm)  # Output: 2.4
```
## API Reference

### `weighted_mean(values, weights)`

Calculates the weighted mean of a list of values.

#### Parameters

- `values` (list or array-like): The list of values for which the weighted mean is to be calculated.
- `weights` (list or array-like): The list of weights associated with each value.

#### Returns

- `float` or `complex`: The calculated weighted mean.

#### Raises

- `TypeError`: If values or weights are not list or array-like.
- `ValueError`: If values and weights do not have the same length.
- `ZeroDivisionError`: If the total of values is zero.

### `class SimpleMean`

A class for calculating a simple arithmetic mean that can be updated incrementally.

#### `SimpleMean.__init__()`

Initializes a `SimpleMean` object with initial sum and count set to zero.

#### `SimpleMean.update(number)`

Updates the mean with a new value.

#### Parameters:

- `number` (int, float, or complex): The new value to be added to the mean.

#### Returns:

- `float` or `complex`: The updated mean.

#### Raises:

- `TypeError`: If `number` is not of a compatible type.

#### `SimpleMean.get_mean()`

Returns the current mean.

#### Returns:

- `float` or `complex`: The current mean.
- `None`: If the count is zero.

### `class Mean`

A class for calculating a rolling mean with an optional limit on the number of values stored.

#### `Mean.__init__(max_size=None)`

Initializes a `Mean` object.

#### Parameters:

- `max_size` (int or str, optional): The maximum number of values to store in the array. If `None`, there is no limit.

#### Raises:

- `ValueError`: If `max_size` is not an integer or a string of an integer.

#### `Mean.update(number)`

Updates the mean with a new value, maintaining the array size within the maximum limit.

#### Parameters:

- `number` (int, float, or complex): The new value to be added to the mean.

#### Returns:

- `float` or `complex`: The updated mean.

#### Raises:

- `TypeError`: If `number` is not of a compatible type.

#### `Mean.update_list(_list)`

Updates the mean with a list of values, maintaining the array size within the maximum limit.

#### Parameters:

- `_list` (list or tuple): The new value to be added to the mean.

#### Returns:

- `float` or `complex`: The updated mean.
- `None`: If the count is zero.

#### Raises:

- `TypeError`: If an element in `_list` is not of the correct type or if the value is not of a compatible type.

#### `Mean.get_mean()`

Returns the current mean.

#### Returns:

- `float` or `complex`: The current mean.
- `None`: If the count is zero.

## License

This library is licensed under the MIT License.