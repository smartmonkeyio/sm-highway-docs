# How to split a master worksheet  

**Learn how to split each excel sheet into separate files with help of VBA code**



## 1. Split each worksheet into a separate excel file 

Start with few things before using the above VBA code:
- Create a folder where you want to get all the resulting files.
- Save the main Excel file (which has all the worksheets that you want as separate files) in this folder.

Next, you can put the **following VBA code** in the file and run the code. The below code is written in a way that it picks up the location of the folder using the path of the file (in which the code is run). This is why it’s important to save the file in the folder first and then use this code.

```bash
'Code Created by Sumit Bansal from TrumpExcel.com
Sub SplitEachWorksheet()
Dim FPath As String
FPath = Application.ActiveWorkbook.Path
Application.ScreenUpdating = False
Application.DisplayAlerts = False
For Each ws In ThisWorkbook.Sheets
    ws.Copy
    Application.ActiveWorkbook.SaveAs Filename:=FPath & "\" & ws.Name & ".xlsx"
    Application.ActiveWorkbook.Close False
Next
Application.DisplayAlerts = True
Application.ScreenUpdating = True
End Sub
```


## 2. Split only those worksheets that contain a word/phrase into separate excel files

In case you have a lot of sheets in a workbook and you only want to split only those sheets that have a specific text in it, you can do that as well.

For example, suppose you have an Excel file where you data for multiple years and each sheet in the file has the year number as the prefix. Something as shown below:

Now, let’s say you want to split all the sheets for 2020 and save these as separate Excel files. To do this, you need to somehow check the name of each worksheet and only those sheets that have the number 2020 should be split and saved, and the rest should be left untouched.

This can be done using the **following VBA macro code**:

```bash
'Code Created by Sumit Bansal from TrumpExcel.com
Sub SplitEachWorksheet()
Dim FPath As String
Dim TexttoFind As String
TexttoFind = "2020"
FPath = Application.ActiveWorkbook.Path
Application.ScreenUpdating = False
Application.DisplayAlerts = False

For Each ws In ThisWorkbook.Sheets
    If InStr(1, ws.Name, TexttoFind, vbBinaryCompare) <> 0 Then
        ws.Copy
        Application.ActiveWorkbook.SaveAs Filename:=FPath & "\" & ws.Name & ".xlsx"
        Application.ActiveWorkbook.Close False
    End If
Next

Application.DisplayAlerts = True
Application.ScreenUpdating = True
End Sub
```


## Step-by-step video explanation

You can find more detailed information in this video, a step-by-step guide on how to split each worksheet in Excel into a separate Excel file/workbook:


[!How to Split Each Excel Sheet Into a Separate File](<a href="https://ibb.co/9ZLKyBB"><img src="https://i.ibb.co/nPvdQ44/Screenshot-2020-02-17-at-20-36-35.png" alt="Screenshot-2020-02-17-at-20-36-35" border="0"></a>](https://youtu.be/zcUYP_ZjhWw)

## See also

- [Adding a client]()
- [Uploading a spreadsheet]()
