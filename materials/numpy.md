
<a href="https://github.com/drshahizan/Python_EDA/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python_EDA" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python_EDA" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python_EDA" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python_EDA" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python_EDA/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python_EDA?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython_EDA&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# NumPy

NumPy is a fundamental library in Python for numerical and array operations. While it's often used in conjunction with pandas for EDA, it can also be directly applied for specific tasks within EDA. Here are some common NumPy syntax and functions suitable for EDA:

1. **Basic NumPy Operations:**
   - Import NumPy:

   ```python
   import numpy as np
   ```

2. **Creating NumPy Arrays:**
   - Create a NumPy array from a Python list:

   ```python
   numpy_array = np.array([1, 2, 3, 4, 5])
   ```

3. **Array Shape and Dimensions:**
   - Get the shape and dimensions of a NumPy array:

   ```python
   numpy_array.shape
   numpy_array.ndim
   ```

4. **Array Indexing and Slicing:**
   - Access elements and slices of a NumPy array:

   ```python
   numpy_array[2]  # Access element at index 2
   numpy_array[1:4]  # Slice from index 1 to 3
   ```

5. **Array Operations:**
   - Perform element-wise operations on arrays:

   ```python
   numpy_array + 2  # Add 2 to each element
   numpy_array * 3  # Multiply each element by 3
   ```

6. **Array Aggregation:**
   - Calculate statistics on arrays:

   ```python
   np.mean(numpy_array)  # Mean
   np.median(numpy_array)  # Median
   np.std(numpy_array)  # Standard deviation
   ```

7. **Array Concatenation and Stacking:**
   - Combine multiple arrays:

   ```python
   np.concatenate([array1, array2])
   np.vstack([array1, array2])  # Vertically stack arrays
   np.hstack([array1, array2])  # Horizontally stack arrays
   ```

8. **Array Filtering:**
   - Filter elements based on a condition:

   ```python
   numpy_array[numpy_array > 3]
   ```

9. **Random Number Generation:**
   - Generate random numbers or arrays:

   ```python
   np.random.rand(3, 3)  # Generate a 3x3 array of random values between 0 and 1
   ```

10. **Reshaping Arrays:**
    - Change the shape of an array:

    ```python
    numpy_array.reshape((2, 3))
    ```

11. **Missing Data Handling:**
    - Handle missing values in arrays:

    ```python
    numpy_array[numpy.isnan(numpy_array)]  # Detect missing values
    numpy_array[~numpy.isnan(numpy_array)]  # Remove missing values
    ```

12. **Statistical Tests:**
    - Conduct statistical tests on arrays for hypothesis testing:

    ```python
    from scipy import stats
    t_stat, p_value = stats.ttest_ind(array1, array2)
    ```

NumPy is a powerful library for numerical operations and array manipulation, making it a valuable tool for various tasks in EDA, especially when dealing with numerical data or conducting statistical tests. It is often used alongside pandas for data analysis and manipulation in EDA workflows.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)


