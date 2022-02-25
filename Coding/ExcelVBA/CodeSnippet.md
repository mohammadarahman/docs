[index](Index.md)
# Example code

## To get all the env variable in a excel sheet.  
To work with this code create a button and apply this function to the code. 
```vba
Sub Button1_Click()
    Dim Indx As Integer
    Dim arrofenv() As String
    Dim arrofpath() As String
    Dim i As Integer
    i = 1
    Indx = 1
    
    Sheets("Sheet1").Columns(1).ClearContents
    Sheets("Sheet1").Columns(2).ClearContents
    Do
        EnvString = Environ(Indx)
        Indx = Indx + 1
        
        arrofenv = Split(EnvString, "=")
        If EnvString <> "" Then
            Debug.Print arrofenv(1)
            Sheets("Sheet1").Cells(i, 1).Value = arrofenv(0)
            If arrofenv(0) = "Path" Then
                arrofpath = Split(arrofenv(1), ";")
                For Each p In arrofpath
                    Sheets("Sheet1").Cells(i, 2).Value = p
                    i = i + 1
                Next
            
            Else
            
                Sheets("Sheet1").Cells(i, 2).Value = arrofenv(1)
                i = i + 1
            End If
            
            
        End If
    Loop Until EnvString = “”

End Sub
```

## update formating of the cells. 
This portion of the code is to check a matching value and if found update the formatting in another sheet. 
```vba
Public Sub applyformat()
    Dim lRow As Long
    'Dim colstr As String
    Dim i As Integer
    Dim celldata As String
    Dim datret As Boolean
    lRow = Cells(Rows.Count, 1).End(xlUp).Row
    Dim colnames As String
    colnames = "i,j,k,m,n,s,u,v,x"
    Dim cols() As String
    cols = Split(colnames, ",")
    Dim colstr As Variant
    For Each colstr In cols:
        'Debug.Print colstr
        'colstr = "i"
        For i = 24 To lRow:
            celldata = Range(colstr & i)
            If celldata > "" Then
                'Debug.Print "coldata: " & Range(colstr & i)
                datret = False
                datret = findstringval(CStr(Range(colstr & i)))
                'Debug.Print "return res: " & datret
                If datret Then
                    Range(colstr & i).Interior.ColorIndex = 4
                    Range(colstr & i).Borders.Weight = xlThin
                    Range(colstr & i).Borders.ColorIndex = 15
        
                Else
                    Range(colstr & i).Interior.ColorIndex = 0
                    Range(colstr & i).Borders.Weight = xlThin
                    Range(colstr & i).Borders.ColorIndex = 15
                End If
            End If
        Next i
    Next colstr
End Sub
Public Function findstringval(indata As String)
    findstringval = False
    Dim colstr As String
    Dim i As Integer
    Dim celldata As String
    Dim retdata As Boolean
    
    colstr = "A"
    Dim hwcat As Worksheet
    
    Set hwcat = Sheets("HW Catalog")
    'Debug.Print findstringval
    Dim lRow As Long
    lRow = hwcat.Cells(Rows.Count, 1).End(xlUp).Row
    For i = 47 To lRow:
    
    celldata = hwcat.Range(colstr & i)
    If celldata > "" Then
        'Debug.Print hwcat.Range(colstr & i)
        If celldata = indata Then
            'Debug.Print hwcat.Range(colstr & i)
            'Debug.Print hwcat.Range("P" & i)
            findstringval = hwcat.Range("P" & i)
            'Debug.Print "ColP: " & i & " : " & findstringval
            Exit For
            
            'If Not retdata Then
             '   Debug.Print "heelo"
            'End If
        End If
    End If
   Next i
    
End Function
```


[index](Index.md)