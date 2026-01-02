---
layout: doc
outline: deep
lang: en-US
---

# ROW function
## Overview
The ROW function in IronCalc is a lookup & reference formula that is used to query and return the row number of a referenced row or cell.
## Usage
### Syntax
**ROW(<span title="Reference" style="color:#1E88E5">reference</span>) => <span title="Number" style="color:#1E88E5">row</span>**
### Argument descriptions
* *reference* ([cell](/features/value-types#references), [optional](/features/optional-arguments.md)). The cell, row, range, or [Named Range](/web-application/name-manager.html) for which you wish to find the row number.
### Additional guidance
* When referencing a range of cells, only the row number of the uppermost cell will be returned.
* Entire columns or rows can also be referenced.
* When using a Named Range as a reference, the reference is not case sensitive.
* IronCalc supports the use of both *Absolute* ($A$1) and *Relative* (A1) references.
* Cross-sheet references are also supported.
### Returned value
ROW returns the [number](/features/value-types#numbers) of the specific cell or range which is being referenced. If no reference is included, the row number of the cell where the formula is entered will be returned.
### Error conditions
* A [`#NAME?`](/features/error-types.html#name) error is returned if a Named Range being referenced is deleted.
* A [`#REF!`](/features/error-types.html#ref) error is returned if a single cell being referenced is deleted.
* A [`#VALUE!`](/features/error-types.html#value) error ir returned if a row being referenced is deleted.
* A [`#VALUE!`](/features/error-types.html#value) error is returned if a cell being directly referenced in a range of cells is deleted. For example, when using **=ROW(<span title="Reference" style="color:#1E88E5">A1:A10</span>)**, only if cell **A1** or **A10** are deleted the error will be returned.
## Details
The ROW function can only be used to display the correlating number of a single row within a Sheet. If you wish to show the number of rows used within a specific range, you can use the [ROWS](/functions/lookup_and_reference/rows) function.
## Examples
### No Cell Reference
When no cell reference is made, the formula uses **=ROW()**. This will output the row number of the cell where the formula is entered.<br><br>For example, if the formula is placed in cell A1, then "1" will be displayed.
### With Cell Reference
When a cell reference is made, the formula uses **=ROW(<span title="Reference" style="color:#1E88E5">Referenced Cell</span>)**. This will then output the row number of the referenced cell, regardless of where the formula is placed in the sheet.<br><br>If **B2** is the referenced cell, then "2" will be the output of the formula, regardless of where the formula is placed in the sheet.<br><br>**Note:** references do not have to be specific cells, you can also reference complete rows. For example, **=ROW(<span title="Reference" style="color:#1E88E5">3:3</span>)** would also result in an output of "3".
### Range References
The ROW function can also be used to reference a range of cells or rows. In this case only the uppermost row will be the resulting output.<br><br>For example, **=ROW(<span title="Reference" style="color:#1E88E5">A1:A10</span>)** will result in the output of "1".
### Anchoring References
ROW can also be used to anchor or offset rows from the starting point. This is useful when using the first row of the sheet as headers.<br><br>For Example, **=ROW(<span title="Reference" style="color:#1E88E5">A2</span>)-1** would result in an output of "1".<br><br>In another use, you can also use ROW to anchor a starting point using *absolute* references. Here, **=ROW()-ROW(<span title="Reference" style="color:#1E88E5">$F$2</span>)+1** could be used to always treat sheet row 2 as the starting point for your rows.
## Links
* Visit Microsoft Excel's [Row function](https://support.microsoft.com/en-us/office/row-function-3a63b74a-c4d0-4093-b49a-e76eb49a6d8d) page.
* Both [Google Sheets](https://support.google.com/docs/answer/3093316) and [LibreOffice Calc](https://wiki.documentfoundation.org/Documentation/Calc_Functions/ROW) provide versions of the ROW function.