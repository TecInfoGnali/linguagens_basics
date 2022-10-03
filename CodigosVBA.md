# Códigos VBA
### Proteção
 >ActiveSheet.Unprotect
 
 >    ActiveSheet.Protect DrawingObjects:=True, Contents:=True, Scenarios:=True _
        , AllowFormattingColumns:=True, AllowFormattingRows:=True

### Display
 >Application.DisplayFullScreen = True

 >ActiveWindow.DisplayHeadings = True

 >Application.Displayformula = True

 >Application.DisplayStatusBar = True

### Importantes
 >Sheets("Aba desejada").Visible = True
 
 >Sheets("Aba desejada").Select

 >Range("celula desejada").Select

 >ActiveWindow.Zoom = 100

 >ActiveSheet.Shapes("botão desejado").ZOrder msoSendToBack

 >Sheets("Aba Desejada"). -> função desejada

 >Application.ScreenUpdating = False

 >Application.DisplayAlerts = False

>Application.ScreenUpdating = True

 >Application.DisplayAlerts = True

### Ir para o último registro
 >ActiveSheet.Unprotect
 
 >Range("a1").End(xlDown).Activate

 >ActiveCell.Offset(1, 0).Select
