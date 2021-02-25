### Entering Commands
- You can execute commands by entering them in the command window after **the Matlab prompt(>>) **and press the Enter key.
- Unless otherwise specified, MATLAB stores calculations in a variable named `ans`
    - You can assign the calculation to a variable
- **The equal sign (=)** in MATLAB is the assignment operator, meaning that the expression on the right of the equals sign is assigned to the variable on the left.
- Notice that **the Workspace window**(on the right) shows all the variables currently in the workspace
- When you enter a command without a **semicolon** at the end, MATLAB displays the result in the command prompt
    - If you add a semicolon to the end of a command, the result will not be displayed. The comannd will still be executed, as you can see in the workspace.
- You can recall previous commands by pressing **the Up arrow key** on your keyboard
    - Note that the Command Window must be the active window for this to work
- When you enter just a variable name at the command prompt, MATLAB returns the current value of that variable
    - If you made a modify on one variable A, and B was caculated using A,
        - B is not gonna to recalculated when A was modified
        - Because MATLAB does not **Rerun** previous commands in the Command Window

### Naming Variables
- You can name your MATLAB variables anything you'd like as long as they **start with a letter and contain only letters, numbers, and underscores(_).**
    - These variables are also **case sensitive**.
- Notice that the variables a and A both exist in the workspace.
    - You can name all you variables a or x, but it is more useful to name your variables something meaningful
- If you use an invalid variable name, Matlab will display a suggested correction.
    - You can use this command, modify it, or press Esc to delete the suggestion

### Saving and Loading Variables
- You can save variables in your **Workspace** to a Matlab specific file format called a MAT-file, using the `save` command
```
save abc
//you will get a MAT-file named abc.mat
```
- When you switch to a new problem in MATLAB, you might want to tidy up your workspace.
    - You can **remove** all variables from your **workspace** with the `clear` function
- That `clear` command removed all the variables, you can load variables from a MAT-file using the `load` command
- Notice that the variable data is listed in the workspace.
    - You can see contents of any variable by entering the name of the variable
- You can use `clc` command to clean up the **Command Window**
- When you close Matlab, the workspace will be cleared
    - If you want to load or save only some of your variables, you can use this
```
//The file myData.mat contains multiple variables
load myData k
save myData k
```
### Using Built-in Functions and Constants
- Matlab contains built-in constants, such as pi to represent Π
    - Also, although only four decimal places are shown for pi, it is represented internally with greater precision
- Matlab contains a wide variety of built-in functions, such as `abs(absolute value)` and `eig(calculate eigenvalues`

### The Live Scripts
** the content mainly based on examples build inside the online Matlab, so that I cannot record it**
- **Click on the Text or Code button will switch your input's attribute**

### Manually Entering Arrays
- In fact, Matlab is an abbreviation for MATrix LABoratory
- All Matlab variables are arrays. This means that each numeric variable can contain multiple numbers.
    - You can use arrays to store related data in one variable
- When you** seperate numbers by spaces** (or commas) as shown in the previous task, Matlab combines the number into a row vector, which is an array with **one row and multiple columns (1 by n)**
- When you **separate numbers by simicolons**, Matlab creates **a column vector (n-by-1)**
- Your can perform calculations within the square brackets
    - `x = [abs(-4) 4^2]`
- For long vectors, entering individual numbers is not pratical.
    - An alternative, shortband method for creating evenly-spaced vectors is to use the operator and specify only the start and end points.
    - `y = 5:8 => y = [5 6 7 8]`
- The `:` operator uses a default spacing of 1, however you can specify your own spacing, as shown below
    - `x = 20:2:26 =>x = [20 22 24 26]`
- If you know the number of elements you want in a vector (instead of the spacing between each element), you could instead use the `linspace` function
    - `x = linspace(0,3,4) => x = [0 1 2 3]`
- You can convert a row vector into a column vector using the transpose operator `'`

### Array Creation Functions
- `size(x)` use this function to get the size of an existing matrix
- `rand(n)` will be an n by n matrix which is fullfilled of random numbers
    - `rand(n,m)` create an n by m matrix
    - `rand(size(x))`create a matrix with the same size as x
- `ones(n,m)` && `zeros(n,m)`
