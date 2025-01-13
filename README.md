# Ex2 - Object-Oriented Spreadsheet System
### Overview:
This project implements a basic spreadsheet system in Java using object-oriented design principles.
The spreadsheet acts as a 2D grid of cells, where each cell can hold one of the following:

 * Text (e.g., "Hello", "123abc")
 * Numbers (e.g., 42, 3.14, -5)
* Formulas (e.g., =A1+2, =B2/(A3*2))

The spreadsheet evaluates formulas dynamically, identifies errors (e.g., invalid syntax or circular references), and computes the computational depth of each cell.

The project supports various operations, such as evaluating a single cell, computing all cells, and calculating dependencies between cells.

## How It Runs:
### The program workflow is as follows:

### 1 Spreadsheet Initialization:

* The user creates a spreadsheet of specified dimensions (e.g., 10x10 grid).
*  Each cell is initially empty.
 ### 2 User Input:

* Users can update cells with:
* Plain text: e.g., "Hello World"
* Numeric values: e.g., 123, 3.5
* Formulas: e.g., =A1+B2, =2*(B3-1)
* The program automatically identifies the cell type and validates the input.
 ### 3 Formula Evaluation:

*  Formulas reference other cells or numeric values and can include operators +, -, *, and /.
* Dependencies are resolved recursively, ensuring proper order of evaluation.
### 4 Error Detection:

* If a formula contains invalid syntax (e.g., =2**5), it is flagged with ERR_FORM.
* If a formula introduces a circular reference (e.g., A1 → B2 → A1), it is flagged with ERR_CYCLE.
### 5 Cell Evaluation:

* Users can retrieve:
* *A single cell value* using eval(x, y).
* *The entire spreadsheet values* using evalAll().
* *The computational depth of each cell* using depth().
* Errors and dependencies are resolved dynamically during evaluation.


 ## Project Features:
 ### 1. Cell Handling
#### Validation:

 * **isNumber(String text):** Checks if a string is a valid number (e.g., 123, -3.14).
* **isText(String text):** Identifies non-numeric text (e.g., "Hello", "123abc").
* **isForm(String text):** Determines if a string is a valid formula (e.g., =A1+2, =(1+2)/3).
#### Evaluation:

* Numbers and text are stored as-is.
* Formulas are parsed and computed, with support for:
  * Arithmetic operations: +, -, *, /
   * Parentheses for precedence: =(1+2)*(3/4).
    * References to other cells: =A1+B2/2.
#### Error Handling:

 * Invalid formulas are flagged with ERR_FORM.
* Cyclic dependencies are flagged with ERR_CYCLE.
* Errors in referenced cells propagate to dependent cells.

 ### 2. Spreadsheet Functionality
   #### Grid Management:

* The spreadsheet is represented as a 2D array of Cell objects.
* Methods:
  * get(x, y): Retrieves a cell at position (x, y).
  * set(x, y, Cell c): Updates the value of a cell at (x, y).
#### Evaluation Methods:

* eval(x, y): Evaluates a specific cell and returns its value or an error code.
* evalAll(): Evaluates all cells in the grid, resolving dependencies recursively.
#### Depth Calculation:

* depth() computes the computational depth for each cell:
* **Text or Numbers:** Depth is 0.
* **Formulas:** Depth is 1 + max(depth of referenced cells).
Cycles: Depth is -1.


## Synchronization Features:
### 1.Dependency Management:

* The program uses a recursive approach to resolve cell references, ensuring dependencies are processed in the correct order.
### 2.Error Propagation:

* Errors in one cell automatically propagate to all dependent cells, ensuring consistency.
### 3.Circular Reference Detection:

* A recursive check detects cycles in formulas. For example:
* If A1 references B1, and B1 references A1, a cycle is flagged with ERR_CYCLE.
### 4.Incremental Updates:

* Changes to a cell trigger updates only for affected cells, optimizing performance.



## Testing and Validation:
### Extensive tests ensure the program handles all edge cases and scenarios:

##### 1. Validation Tests:

* Correctly identify valid and invalid:
* Text: "abc", "123abc".
* Numbers: 123, -3.14.
* Formulas: =A1+2, =(B2-1)*3.
##### 2.Evaluation Tests:

* Verify arithmetic operations:
* Simple: =1+2 → 3
* Complex: =(1+2)*(3/4) → 2.25
* Test formula dependencies (e.g., A1 → B2 → C3).
 #### 3.Error Handling Tests:

* Detect and handle:
* Invalid syntax (e.g., =2**5).
* Circular references (e.g., A1 → B1 → A1).
* Propagate errors to dependent cells.
##### 4.Depth Calculation Tests:

* Ensure correct depth values:
  * Independent cells: 0
   * Nested formulas: 1 + max(depth of dependencies).
   * Cycles: -1.



## Summary:
This project demonstrates how object-oriented principles can be applied to model a real-world problem like a spreadsheet.
It handles:

* ##### Dynamic formula evaluation
* ##### Error detection and propagation
* ##### Efficient dependency resolution
With its well-tested architecture and robust error handling, this spreadsheet system is a foundational tool for understanding object-oriented programming and recursion.

# Example of use

![screen .png](images/screen%20.png)