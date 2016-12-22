---
title: "Passo a passo: Inserindo informa&#231;&#245;es de tipo de Assemblies do Microsoft Office no Visual Studio (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passo a passo: Inserindo informa&#231;&#245;es de tipo de Assemblies do Microsoft Office no Visual Studio (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se você inserir informações de tipo em um aplicativo que faz referência a objetos COM, você pode eliminar a necessidade de um assembly de interoperabilidade primária \(PIA\). Além disso, as informações de tipo incorporado permite que você atingir a independência de versão para o seu aplicativo. Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca COM sem a necessidade de um PIA específico para cada versão. Esse é um cenário comum para aplicativos que usam objetos de bibliotecas do Microsoft Office. Inserindo informações de tipo permite que a mesma compilação de um programa para trabalhar com diferentes versões do Microsoft Office em computadores diferentes sem precisar reimplantar o programa ou o PIA para cada versão do Microsoft Office.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## Pré-requisitos  
 Este passo a passo requer o seguinte:  
  
-   Um computador em que o Visual Studio e o Microsoft Excel são instalados.  
  
-   Um segundo computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estiverem instalados.  
  
##  <a name="BKMK_createapp"></a> Para criar um aplicativo que funciona com várias versões do Microsoft Office  
  
1.  Inicie o Visual Studio em um computador em que o Excel está instalado.  
  
2.  Sobre o **arquivo** menu, escolha **novo**, **projeto**.  
  
3.  No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado. Selecione **aplicativo de Console** no **modelos** painel. No **nome** digite `CreateExcelWorkbook`, e, em seguida, escolha o **OK** botão. O novo projeto é criado.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **referências** pasta e, em seguida, escolha **Adicionar referência**.  
  
5.  Sobre o **.NET** guia, escolha a versão mais recente do `Microsoft.Office.Interop.Excel`. Por exemplo, **Interop 14.0.0.0**. Escolha o botão **OK**.  
  
6.  Na lista de referências para o **CreateExcelWorkbook** de projeto, selecione a referência de `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior. No **propriedades** janela, verifique se o `Embed Interop Types` está definida como `True`.  
  
    > [!NOTE]
    >  O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inserido. Se o `Embed Interop Types` está definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office que o aplicativo será executado com.  
  
7.  Abra o **Program.cs** arquivo. Substitua o código no arquivo pelo código a seguir:  
  
    ```c#  
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
  
8.  Salve o projeto.  
  
9. Pressione CTRL \+ F5 para compilar e executar o projeto. Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\\SampleFolder\\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada  
  
1.  Abra o projeto criado por este passo a passo no Visual Studio.  
  
2.  Sobre o **criar** menu, escolha **CreateExcelWorkbook publicar**. Siga as etapas do Assistente de publicação para criar uma versão instalável do aplicativo. Para obter mais informações, consulte [Assistente de Publicação \(desenvolvimento do Office no Visual Studio\)](/office-dev/office-dev/publish-wizard-office-development-in-visual-studio).  
  
3.  Instale o aplicativo em um computador no qual o .NET Framework 4 ou superior e uma versão diferente do Excel estão instalados.  
  
4.  Quando a instalação for concluída, execute o programa instalado.  
  
5.  Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\\SampleFolder\\SampleWorkbook.xls.  
  
## Consulte também  
 [Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)   
 [\/link \(Link to COM Assembly\)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)