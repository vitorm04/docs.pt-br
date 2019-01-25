---
title: 'Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: e5b94c190a77f6877c9a3d37f310aa527083a26a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722771"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic)
Se inserir informações de tipo em um aplicativo que faz referência a objetos COM, você poderá eliminar a necessidade de um PIA (assembly de interoperabilidade primário). Além disso, as informações de tipo inseridas permitem que você conquiste a independência de versão para seu aplicativo. Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca COM sem precisar especificar um PIA específico para cada versão. Esse é um cenário comum para aplicativos que usam objetos de bibliotecas do Microsoft Office. Inserir informações de tipo possibilita que a mesma build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores sem precisar reimplantar o programa ou o PIA para cada versão do Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo requer o seguinte:  
  
-   Um computador em que o Visual Studio e o Microsoft Excel estão instalados.  
  
-   Um segundo computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estão instalados.  
  
##  <a name="BKMK_createapp"></a> Para criar um aplicativo que funciona com várias versões do Microsoft Office  
  
1.  Inicie o Visual Studio em um computador em que o Excel está instalado.  
  
2.  No menu **Arquivo**, escolha **Novo**, **Projeto**.  
  
3.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Aplicativo de Console** no painel **Modelos**. Na caixa **Nome** insira `CreateExcelWorkbook` e, em seguida, escolha o botão **OK**. O novo projeto é criado.  
  
4.  Abra o menu de atalho para o projeto de CreateExcelWorkbook e, em seguida, escolha **propriedades**. Escolha o **referências** guia. Escolha o botão **Adicionar**.  
  
5.  Na guia **.NET**, escolha a versão mais recente de `Microsoft.Office.Interop.Excel`. Por exemplo, **Microsoft.Office.Interop.Excel 14.0.0.0**. Escolha o botão **OK**.  
  
6.  Na lista de referências para o projeto **CreateExcelWorkbook**, selecione a referência para `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior. Na janela **Propriedades**, verifique se a propriedade `Embed Interop Types` está definida como `True`.  
  
    > [!NOTE]
    >  O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inseridas. Se a propriedade `Embed Interop Types` estiver definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office com que o aplicativo será executado.  
  
7.  Abra o arquivo Module1.vb. Substitua o código no arquivo pelo seguinte código:  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  Salvar o projeto.  
  
9. Pressione CTRL+F5 para compilar e executar o projeto. Verifique se que uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\samplefolder\sampleworkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada  
  
1.  Abra o projeto criado por este passo a passo no Visual Studio.  
  
2.  No menu **Build**, escolha **Publicar CreateExcelWorkbook**. Siga as etapas do Assistente de Publicação para criar uma versão instalável do aplicativo. Para obter mais informações, consulte [Assistente de Publicação (desenvolvimento do Office no Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).  
  
3.  Instale o aplicativo em um computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estejam instalados.  
  
4.  Quando a instalação for concluída, execute o programa instalado.  
  
5.  Verifique se que uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\samplefolder\sampleworkbook.xls.  
  
## <a name="see-also"></a>Consulte também

- [Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
