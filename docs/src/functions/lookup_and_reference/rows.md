---
layout: doc
outline: deep
lang: en-US
---

# ROWS function
## Overview
The ROWS function in IronCalc is a lookup & reference formula that is used to query and return the number of rows referenced in a particular range or array.
## Usage
### Syntax
**ROWS(<span title="Reference" style="color:#1E88E5">reference</span>) => <span title="Number" style="color:#1E88E5">rows</span>**
### Argument descriptions
* *reference* ([cell](/features/value-types#references)). The cells, rows, array, range, or [Named Range](/web-application/name-manager.html) which you wish to evaluate.
### Additional guidance
* When using ROWS a reference must be included.
* You are able to reference either complete rows, columns, or individual cells.
* When referencing [Named Ranges](/web-application/name-manager.html), the complete row must have the label. Referencing individual cells using Named Ranges in ROWS is not supported.
* When using a Named Range as a reference, the reference is not case sensitive.
* IronCalc supports the use of both *Absolute* ($A$1) and *Relative* (A1) references.
* Cross-sheet references are also supported.
* When referencing a range of rows or cells, if a cell or row within the range is deleted the count will automatically adjust. However, if the cell or row that is explicitly referenced is deleted an error will be thrown.
* Using array formulas, for example **=ROWS(<span title="Reference" style="color:#1E88E5">{1, 23; 4, 56}</span>)**, is not supported.
### Returned value
ROWS returns the [number](/features/value-types#numbers) of rows which are being referenced.
### Error conditions
* [`#ERROR!`](/features/error-types.html#error) is returned if no reference is included.
* [`#NAME?`](/features/error-types.html#name) is returned if a Named Range being referenced is deleted.
* [`#REF!`](/features/error-types.html#ref) is returned if a single cell being referenced is deleted.
* [`#VALUE!`](/features/error-types.html#value) is returned if a row or cell being referenced is deleted.
* [`#VALUE!`](/features/error-types.html#value) is returned if a cell name is being referenced.
* [`#VALUE!`](/features/error-types.html#value) is returned when referencing a Named Range in combination with an additional cell or row.
* [`#VALUE!`](/features/error-types.html#value) is returned when using array formulas.
## Details
The ROWS function can only be used to display the correlating number of rows being referenced. If you wish to show the number of a single row within a Sheet, you can use the [ROW](/functions/lookup_and_reference/row) function.
## Examples
### Basic Range
When a range of cells or rows is referenced, only the number of rows will display.<br><br>For example, **=ROWS(<span title="Reference" style="color:#1E88E5">A1:A3</span>)** and **=ROWS(<span title="Reference" style="color:#1E88E5">4:6</span>)** will both output a value of "3".
### Named Ranges
When using ROWS, Named Ranges can only be referenced individually and not in combination with other cells or rows.<br><br>For example, **=ROWS(<span title="Reference" style="color:#1E88E5">Range1</span>)** will output the amount of rows contained within your Named Range. An error will be returned if you try to reference anything else within the paranthesis.
### Single Cell & Single Row References
When a single cell is referenced, such as **=ROWS(<span title="Reference" style="color:#1E88E5">G1</span>)**, an Output of "1" will always be the result. This result will also return when referencing single rows, for instance **=ROWS(<span title="Reference" style="color:#1E88E5">3:3</span>)**.
### Multiple Column References
References can also be spread across multiple columns. For Example, **=ROWS(<span title="Reference" style="color:#1E88E5">C4:E7</span>)** will result in an output of "4" because the formula spreads across four rows.
### Using ROWS for Dynamic Lookup Formulas
ROWS is often combined with other functions, such as [INDEX](/functions/lookup_and_reference/index).<br><br>**=INDEX(<span title="Reference" style="color:#1E88E5">A1:A10</span>,ROWS(<span title="Reference" style="color:#1E88E5">A1:A10</span>))** will dynamically return the value from the last cell of the specified range.
## Links
* Visit Microsoft Excel's [Rows function](https://support.microsoft.com/en-us/office/rows-function-b592593e-3fc2-47f2-bec1-bda493811597) page.
* Both [Google Sheets](https://support.google.com/docs/answer/3093382) and [LibreOffice Calc](https://wiki.documentfoundation.org/Documentation/Calc_Functions/ROWS) provide versions of the ROWS function.