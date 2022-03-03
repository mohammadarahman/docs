[index](./ExcelVBA.md)  
---  

# Excel Worksheet specific tutorial  

## set value or style to a cell 
1) setting value to cell using cells. Cells take row column as number 
```vba
Sheets("Sheet1").Cells(i, 2).Value = p
```
2) setting value to cell using range. Range takes address by letter number string like ex- "Q1"
```vba
Range(colstr & i).value = "hello"
```
3) styling is similar. this example here is creating the excel grid which is kind of very thin border. 
```vba
Range(colstr & i).Borders.Weight = xlThin
Range(colstr & i).Borders.ColorIndex = 15
```
4) Clearing cell data

```vba
Range("A1:C10").ClearContents
Sheets("SheetName").Cells.ClearContents
```

5) setting font color
```vba
Columns(1).Font.Color = vbBlack
```


## working with chart  
### inserting chart
[chart docs](https://www.thespreadsheetguru.com/blog/2015/3/1/the-vba-coding-guide-for-excel-charts-graph)  
[chart type](https://bettersolutions.com/excel/charts/vba-chart-types.htm)  

```vba
Sub CreateChart()
'PURPOSE: Create a chart (chart dimensions are not required)

Dim rng As Range
Dim cht As Object

'Your data range for the chart
  Set rng = ActiveSheet.Range("A24:M27")

'Create a chart
  Set cht = ActiveSheet.Shapes.AddChart2

'Give chart some data
  cht.Chart.SetSourceData Source:=rng

'Determine the chart type
  cht.Chart.ChartType = xlXYScatterLines

End Sub
```




## Excel Color picker
Here is the link for color chooser.  
[Colors](http://dmcritchie.mvps.org/excel/colors.htm)  
[color index](https://docs.microsoft.com/en-us/office/vba/api/excel.colorindex)  
---

[index](../ExcelVBA.md)
[index](.\ExcelVBA.md)
[index](..\ExcelVBA.md)