### Indexing into Arrays
- Vector
    - `A(m) = k` change the value at the nth index to m
    - `A(m:n) = k`You can also extract a range of values by using a colon with the first and last indices of the range
- Matrix
    - `A(m,n)` extract one value from the matrix
    - `A(m,:) / A(:,n)` extract a whole row or a whole column from a matrix
    - `A(end;3)`use the end keyword to obtain the value in the last row
        - `A(end-1;3)`you can use arithmetic with the keyword end
- How to contract non-consecutive numbers from a matrix?
```
index = [1,3,6]
p = density(index)
```

### Performing Array Operations on Vectors
```
v1 = data(:,3);
v2 = data(:,4)

// Add a scalar value to all the elements of an array
r = v1 + 1

// Add togehter any two arrays of the same size
vs = v1 + v2

// Multiply or divide all of the elements of an array by a scalar
va = vs / 2

// Use basic statistical functions
vm = max(va)

// Use mathmatical operations
vr = round(va)
```
- Matrix multiplication
    - Do not use `*` and use `.*` instead
    - `mass = density .* va`

### Obtaining Multiple Outputs from Function Calls
```
// The size function can be applied to a matrix to produce either a single output variable or two output variables.
[dr, dc] = size(data)

// 
```