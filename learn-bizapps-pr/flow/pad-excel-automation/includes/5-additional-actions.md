To write data to the first available cell in a given column, use the **Get First Free Row on Column from Excel Worksheet** action.

![Screenshot of Get first free row on column Excel worksheet action properties dialog.](..\media\get-first-free-row-on-column-excel-action-properties.png)

The Read and Write actions can use the currently selected cell as a point of reference. Use the **Get Selected Cell Range from Excel Worksheet** action for this purpose by providing the indices of the first and last column and row of the selection.

![Screenshot of Get selected cell range Excel worksheet action properties dialog.](..\media\get-selected-cell-range-excel-action-properties.png)

To change the selected cells, use the **Select Cells in Excel Worksheet** action. Set the **Select** option to **Range of Cells** to select cells by specifying the upper-left and bottom-right corner cells.

![Screenshot of Select cells in Excel worksheet action properties dialog.](..\media\select-cells-in-excel-action-properties.png)

Alternatively, set the **Select** option to **Relatively specified cell** to select a number of cells from the currently selected cell.

To activate a particular cell, use the **Activate Cell in Excel Worksheet** action. In the **Activate** field, you can either choose to specify a cell by its coordinates (**Absolutely specified cell**) or relative to the currently active cell (**Relatively specified cell**).

![Screenshot of Activate Cell in Excel Worksheet action properties dialog.](..\media\activate-cell-in-excel-action-properties.png)

It is also possible to insert and delete columns and rows by using the appropriate actions; however, you are required to specify a column or row index. In case of insertion, the row or column will be added before the one that is specified.

![Screenshot of Insert row to Excel worksheet action properties dialog.](..\media\insert-row-to-excel-action-properties.png)

The **Run Excel macro** action runs any macro saved in the workbook. Specify the name of the macro and any parameters separated by semicolons (;). 

![Screenshot of Properties of 'Run Excel macro' action dialog](..\media\run-excel-macro-action-properties.png)

> [!NOTE] To run a macro named RevenuePerUser with the arguments 778 and Rbotas, the input would have to be > > formatted like so:
> 
> **RevenuePerUser;778;Rbotas**
