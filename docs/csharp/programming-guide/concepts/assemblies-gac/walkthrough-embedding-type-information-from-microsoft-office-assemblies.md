---
title: 'Passo a passo: inserindo informações de tipo de assemblies do Microsoft Office no Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 8e7eb5c797ca87f87950d530112ec64f1327ae0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>Passo a passo: inserindo informações de tipo de assemblies do Microsoft Office no Visual Studio (C#)
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
  
4.  No **Gerenciador de Soluções**, abra o menu de atalho para a pasta **Referências** e escolha **Adicionar Referência**.  
  
5.  Na guia **.NET**, escolha a versão mais recente de `Microsoft.Office.Interop.Excel`. Por exemplo, **Microsoft.Office.Interop.Excel 14.0.0.0**. Escolha o botão **OK**.  
  
6.  Na lista de referências para o projeto **CreateExcelWorkbook**, selecione a referência para `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior. Na janela **Propriedades**, verifique se a propriedade `Embed Interop Types` está definida como `True`.  
  
    > [!NOTE]
    >  O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inseridas. Se a propriedade `Embed Interop Types` estiver definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office com que o aplicativo será executado.  
  
7.  Abra o arquivo **Program.cs**. Substitua o código no arquivo pelo seguinte código:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  Salvar o projeto.  
  
9. Pressione CTRL+F5 para compilar e executar o projeto. Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada  
  
1.  Abra o projeto criado por este passo a passo no Visual Studio.  
  
2.  No menu **Build**, escolha **Publicar CreateExcelWorkbook**. Siga as etapas do Assistente de Publicação para criar uma versão instalável do aplicativo. Para obter mais informações, consulte [Assistente de Publicação (desenvolvimento do Office no Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Instale o aplicativo em um computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estejam instalados.  
  
4.  Quando a instalação for concluída, execute o programa instalado.  
  
5.  Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de amostra: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/link (opções do compilador C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
