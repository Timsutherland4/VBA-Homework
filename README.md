# VBA-Homework
Module 2
Sub VBA_Homework_Easy_2()
'Second version below has line by line notes
    For Each i In ActiveWorkbook.Worksheets
        i.Activate
        LastRow = i.Cells(Rows.Count, 1).End(xlUp).Row
   
    Cells(1, 9).Value = "Ticker"
    Cells(1, 10).Value = "Total Stock Volume"
    
    Dim Tic As String
    Dim Vol As Double
    
    Tic = 2
    Cells(Tic, 9).Value = Cells(Tic, 1).Value
    
        For j = 2 To LastRow
            If Cells(j, 1).Value = Cells(Tic, 9) Then
            Vol = Vol + Cells(j, 7).Value
     
        Else
            Cells(Tic, 10).Value = Vol
            Vol = Cells(j, 7).Value
            Tic = Tic + 1
            Cells(Tic, 9).Value = Cells(j, 1).Value
            
        End If
     
     Next j
     
     Cells(Tic, 10).Value = Vol
        
     Next i
    
End Sub

Sub VBA_Homework_Easy_1()
'FIRST FOR LOOP
    'Open First "For Loop" for Active Sheets- Index Variable i, no conditionals
    For Each i In ActiveWorkbook.Worksheets
        'Activate, or "Select tab" in worksheet
        i.Activate
        'Determine last row in sheet by looking for first empty row, then going up 1
        LastRow = i.Cells(Rows.Count, 1).End(xlUp).Row
    'Add Header for "Ticker" in Worksheet in cell(1, 9)
    Cells(1, 9).Value = "Ticker"
    'Add Header for "Total Stock Volume" in Worksheet in cell(1, 10)
    Cells(1, 10).Value = "Total Stock Volume"
'DECLARE VARIABLES
    'Declare in Memmory "Tic" as Text
    Dim Tic As String
    'Declare in Memmory "Vol" as double (Large number with decimals)
    Dim Vol As Double
'GET FIRST TICKER DATA
    'Start "Tic" in row 2
    Tic = 2
    'Set the value for "Tic" and print in row "Tic" column 9
    Cells(Tic, 9).Value = Cells(Tic, 1).Value
'NESTED FOR LOOP
        'Open the second loop or "Nested Loop" row variable "J" to lastrow
        For j = 2 To LastRow
'NESTED LOOP CONDITIONALS
            'First conditional (If) - Question: is Cell(J, 1) = Cell(Tic, 9)??
            If Cells(j, 1).Value = Cells(Tic, 9) Then
            'If the condition is met, add the the value of(j, 10) to current value of "Vol"
            Vol = Vol + Cells(j, 7).Value
        'Second Conditional (Else) - details what to do if first conditional is not met
        Else
            'Print the value for "Vol" (Total) in cell(Tic, 10)
            Cells(Tic, 10).Value = Vol
            'Resets the Value for "Vol" witht the value in next (j, 7)
            Vol = Cells(j, 7).Value
            'Reset "Tic" to next row
            Tic = Tic + 1
            'Set the value for "Tic" and print in row "Tic" column 9 as above
            Cells(Tic, 9).Value = Cells(j, 1).Value
        'Closing the conditionals
        End If
'CLOSE NESTED FOR LOOP
     Next j
     '
     Cells(Tic, 10).Value = Vol
'CLOSE FIRST FOR LOOP
     Next i
    


End Sub
