# Mean Variance Standard Deviation Calculator

The pupose of the project is to create a function named <kbd>calculate()</kbd> in [mean_var_std.py](mean-var-std.py) that uses Numpy to output the **mean**, **variance**, **standard deviation**, **max**, **min**, and **sum of the rows**, **columns**, and **elements in a 3 x 3 matrix**.

## Table of content

1. [Introduction](#intro)
2. [Development](#dev)
3. [Breakdown](#break)
4. [Solution](#sol)


## Introduction<a name="intro"></a>
1. Input of the function should be a list containing 9 digits. The function should convert the list into a **3 x 3 Numpy array**, and then return a dictionary containing the mean, variance, standard deviation, max, min, and sum along both axes and for the flattened matrix.

The returned function will follow the format below:
 ```
 {
  'mean': [axis1, axis2, flattened],
  'variance': [axis1, axis2, flattened],
  'standard deviation': [axis1, axis2, flattened],
  'max': [axis1, axis2, flattened],
  'min': [axis1, axis2, flattened],
  'sum': [axis1, axis2, flattened]
}
 ```

2. If a list containing less than 9 elements is passed into the function, it should raise a <kbd>ValueError</kbd> exception with the message: "List must contain nine numbers." The values in the returned dictionary should be lists and not Numpy arrays.

For example, calculate([0,1,2,3,4,5,6,7,8]) should return:


```
{
  'mean': [[3.0, 4.0, 5.0], [1.0, 4.0, 7.0], 4.0],
  'variance': [[6.0, 6.0, 6.0], [0.6666666666666666, 0.6666666666666666, 0.6666666666666666], 6.666666666666667],
  'standard deviation': [[2.449489742783178, 2.449489742783178, 2.449489742783178], [0.816496580927726, 0.816496580927726, 0.816496580927726], 2.581988897471611],
  'max': [[6, 7, 8], [2, 5, 8], 8],
  'min': [[0, 1, 2], [0, 3, 6], 0],
  'sum': [[9, 12, 15], [3, 12, 21], 36]
}
```
## Development <a name="dev"></a>

For development, you can use [main.py](main.py) to test your <kbd>calculate()</kbd> function. Click the "run" button and [main.py](main.py) will run.

## Solution Breakdown <a name="break"></a>

Here we define the <kbd>calculate()</kbd> funtion, raising the <kbd>ValueError</kbd>, and setting the numpy arrary:

```
def calculate(list):
    if(len(list) != 9):
      raise ValueError("List must contain nine numbers.")

    ls = np.array(list)
    print(ls)
```
Setting up the 3x3 matrix for the mean, varience, standard deviation, max, min, sum:
```
    mean_row = [ls[[0, 1, 2]].mean(), ls[[3, 4, 5]].mean(), ls[[6, 7, 8]].mean()]
    mean_column = [ls[[0, 3, 6]].mean(), ls[[1, 4, 7]].mean(), ls[[2, 5, 8]].mean()]

    var_row = [ls[[0, 1, 2]].var(), ls[[3, 4, 5]].var(), ls[[6, 7, 8]].var()]
    var_column = [ls[[0, 3, 6]].var(), ls[[1, 4, 7]].var(), ls[[2, 5, 8]].var()]

    std_row = [ls[[0, 1, 2]].std(), ls[[3, 4, 5]].std(), ls[[6, 7, 8]].std()]
    std_column = [ls[[0, 3, 6]].std(), ls[[1, 4, 7]].std(), ls[[2, 5, 8]].std()]

    max_row = [ls[[0, 1, 2]].max(), ls[[3, 4, 5]].max(), ls[[6, 7, 8]].max()]
    max_column = [ls[[0, 3, 6]].max(), ls[[1, 4, 7]].max(), ls[[2, 5, 8]].max()]

    min_row = [ls[[0, 1, 2]].min(), ls[[3, 4, 5]].min(), ls[[6, 7, 8]].min()]
    min_column = [ls[[0, 3, 6]].min(), ls[[1, 4, 7]].min(), ls[[2, 5, 8]].min()]

    sum_row = [ls[[0, 1, 2]].sum(), ls[[3, 4, 5]].sum(), ls[[6, 7, 8]].sum()]
    sum_column = [ls[[0, 3, 6]].sum(), ls[[1, 4, 7]].sum(), ls[[2, 5, 8]].sum()]
```
Setting up return statement for the <kbd>calculate()</kbd> function:
```
    return {
      'mean': [mean_column, mean_row, ls.mean()],
      'variance': [var_column, var_row, ls.var()],
      'standard deviation': [std_column, std_row, ls.std()],
      'max': [max_column, max_row, ls.max()],
      'min': [min_column, min_row, ls.min()],
      'sum': [sum_column, sum_row, ls.sum()]
    }
```

## Solution <a name="sol"></a>


Desired format for the return function:

```
{
 'mean': [[3.0, 4.0, 5.0], [1.0, 4.0, 7.0], 4.0],
 'variance': [[6.0, 6.0, 6.0], [0.6666666666666666, 0.6666666666666666, 0.6666666666666666], 6.666666666666667],  'standard deviation': [[2.449489742783178, 2.449489742783178, 2.449489742783178], [0.816496580927726, 0.816496580927726, 0.816496580927726], 2.581988897471611],  'max': [[6, 7, 8], [2, 5, 8], 8],
 'min': [[0, 1, 2], [0, 3, 6], 0], 
 'sum': [[9, 12, 15], [3, 12, 21], 36]
}
```
Organized results in their 3x3 matrices:

<details>
 <summary>
  Mean: 
  
 </summary>
 
 |3.0 | 4.0 | 5.0|
 |---|---|---|
 |1.0| 4.0| 7.0|
 
 => Ans. 4
 
</details>

<details>
 <summary>
  Variance:
 </summary>
 
 |6.0 | 6.0 | 6.0|
 |---|---|---|
 |0.666...| 0.666...| 0.666...|
 
 => Ans. 6.666...
 
</details>

<details>
 <summary>
 Stabard deviation:
  
 </summary>
 
 
 |2.449... | 2.449.. | 2.449...|
 |---|---|---|
 |0.816...| 0.816...| 0.816...|
 
 => Ans. 2.581
 
</details>

<details>
 <summary>
 Max:
  
 </summary>
 
 
 | 6 | 7 | 8 |
 |---|---|---|
 | 2 | 5 | 8 |
 
 => Ans. 8
 
</details>

<details>
 <summary>
Min:
  
 </summary>
 
 
 | 0 | 1 | 2 |
 |---|---|---|
 | 0 | 3 | 6 |
 
 => Ans. 0
 
</details>

<details>
 <summary>
 Sum:
  
 </summary>
 
 
 | 9 | 12 | 15 |
 |---|---|---|
 | 3 | 12 | 21 |
 
 => Ans. 36
 
</details>

