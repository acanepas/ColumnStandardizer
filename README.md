# ColumnStandardizer
Power Query function that helps standardize column names from a given table and a standard list of columns.

## Arguments

1. **column_names:** List of column names from a given table.
2. **standard_column_names:** List of standard column names set as the target column names.
3. **[Optional] Score:** Numeric value to define the threshold of similarity.
4. **[Optional] symbol_list:** List of symbols to exclude from the comparison between columns.


## Usage
Let's imagine we have a table with three columns: 
1. Date.Month
2. SalesAmount
3. Profit

And we would like to standardize the first two columns to "Date Month" and "Sales Amount".
We don't care about "Profit".

With ColumnStandardizer we would write

```
ColumnStandardizer({"Date.Month","SalesAmount","Profit"},{"Sales Amount", "Date Month"})
```
## Output

```
{{"Date.Month","Date Month"},{"SalesAmount","Sales Amount"}}
```
This output can be used into `Table.RenameColumns` as a second argument. 

With that we are able to standardize our column names to our original list.

Also, this output can be used in `Table.SelectColumns` to drop any columns that don't match the standardize column list.

## Advanced usage

You can also play with the optional parameters. The default symbol list is `{".","/","_","-"," ","\"}`. If you want to override it, or make your own, you can with the following syntax. Let's say you want to exclude only the symbol `|`

```
ColumnStandardizer({"Date.Month","SalesAmount","Profit"},{"Sales Amount", "Date Month"},null, {"|"})
```
Generating the same output above.




