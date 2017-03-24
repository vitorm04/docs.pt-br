---
title: "Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4347ba0e740419b53a1aa662c43933dead107e9c
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic)
Se você inserir informações de tipo em um aplicativo que faz referência a objetos COM, você pode eliminar a necessidade de um assembly de interoperabilidade primária (PIA). Além disso, as informações de tipo incorporado permite que você atingir a independência de versão para o seu aplicativo. Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca COM sem a necessidade de um PIA específico para cada versão. Esse é um cenário comum para aplicativos que usam objetos de bibliotecas do Microsoft Office. Inserindo informações de tipo permite que a mesma compilação de um programa para trabalhar com diferentes versões do Microsoft Office em computadores diferentes sem precisar reimplantar o programa ou o PIA para cada versão do Microsoft Office.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo requer o seguinte:  
  
-   Um computador em que o Visual Studio e o Microsoft Excel são instalados.  
  
-   Um segundo computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estiverem instalados.  
  
##  <a name="BKMK_createapp"></a>Para criar um aplicativo que funciona com várias versões do Microsoft Office  
  
1.  Inicie o Visual Studio em um computador em que o Excel está instalado.  
  
2.  No menu **Arquivo**, escolha **Novo**, **Projeto**.  
  
3.  No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado. Selecione **aplicativo de Console** no **modelos** painel. No **nome** , digite `CreateExcelWorkbook`e, em seguida, escolha o **Okey** botão. O novo projeto é criado.  
  
4.  Abra o menu de atalho para o projeto CreateExcelWorkbook e, em seguida, escolha **propriedades**. Escolha o **referências** guia. Escolha o botão **Adicionar**.  
  
5.  Sobre o **.NET** guia, escolha a versão mais recente do `Microsoft.Office.Interop.Excel`. Por exemplo, **Interop 14.0.0.0**. Selecione o botão **OK**.  
  
6.  Na lista de referências para o **CreateExcelWorkbook** de projeto, selecione a referência de `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior. No **propriedades** janela, verifique se o `Embed Interop Types` está definida como `True`.  
  
    > [!NOTE]
    >  O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inserido. Se o `Embed Interop Types` está definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office que o aplicativo será executado com.  
  
7.  Abra o arquivo Module1. vb. Substitua o código no arquivo pelo código a seguir:  
  
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
  
9. Pressione CTRL + F5 para compilar e executar o projeto. Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a>Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada  
  
1.  Abra o projeto criado por este passo a passo no Visual Studio.  
  
2.  Sobre o **criar** menu, escolha **CreateExcelWorkbook publicar**. Siga as etapas do Assistente de publicação para criar uma versão instalável do aplicativo. Para obter mais informações, consulte [o Assistente de publicação (desenvolvimento do Office no Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Instale o aplicativo em um computador no qual o .NET Framework 4 ou superior e uma versão diferente do Excel estão instalados.  
  
4.  Quando a instalação for concluída, execute o programa instalado.  
  
5.  Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)   
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)

