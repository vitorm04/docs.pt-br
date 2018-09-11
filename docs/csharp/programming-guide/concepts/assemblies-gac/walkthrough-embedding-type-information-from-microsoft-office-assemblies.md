---
title: 'Passo a passo: inserindo informações de tipo de assemblies do Microsoft Office no Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 381173eedc209930e011dfa7f1711167f16d5ef6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187962"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="3f7d2-102">Passo a passo: inserindo informações de tipo de assemblies do Microsoft Office no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="3f7d2-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="3f7d2-103">Se inserir informações de tipo em um aplicativo que faz referência a objetos COM, você poderá eliminar a necessidade de um PIA (assembly de interoperabilidade primário).</span><span class="sxs-lookup"><span data-stu-id="3f7d2-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="3f7d2-104">Além disso, as informações de tipo inseridas permitem que você conquiste a independência de versão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="3f7d2-105">Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca COM sem precisar especificar um PIA específico para cada versão.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="3f7d2-106">Esse é um cenário comum para aplicativos que usam objetos de bibliotecas do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="3f7d2-107">Inserir informações de tipo possibilita que a mesma build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores sem precisar reimplantar o programa ou o PIA para cada versão do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="3f7d2-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3f7d2-108">Prerequisites</span></span>  
 <span data-ttu-id="3f7d2-109">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3f7d2-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="3f7d2-110">Um computador em que o Visual Studio e o Microsoft Excel estão instalados.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="3f7d2-111">Um segundo computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estão instalados.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="3f7d2-112">Para criar um aplicativo que funciona com várias versões do Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="3f7d2-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="3f7d2-113">Inicie o Visual Studio em um computador em que o Excel está instalado.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="3f7d2-114">No menu **Arquivo**, escolha **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="3f7d2-115">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="3f7d2-116">Selecione **Aplicativo de Console** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="3f7d2-117">Na caixa **Nome** insira `CreateExcelWorkbook` e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="3f7d2-118">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="3f7d2-119">No **Gerenciador de Soluções**, abra o menu de atalho para a pasta **Referências** e escolha **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="3f7d2-120">Na guia **.NET**, escolha a versão mais recente de `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="3f7d2-121">Por exemplo, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="3f7d2-122">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="3f7d2-123">Na lista de referências para o projeto **CreateExcelWorkbook**, selecione a referência para `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="3f7d2-124">Na janela **Propriedades**, verifique se a propriedade `Embed Interop Types` está definida como `True`.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3f7d2-125">O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inseridas.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="3f7d2-126">Se a propriedade `Embed Interop Types` estiver definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office com que o aplicativo será executado.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="3f7d2-127">Abra o arquivo **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="3f7d2-128">Substitua o código no arquivo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3f7d2-128">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="3f7d2-129">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-129">Save the project.</span></span>  
  
9. <span data-ttu-id="3f7d2-130">Pressione CTRL+F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="3f7d2-131">Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="3f7d2-132">Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada</span><span class="sxs-lookup"><span data-stu-id="3f7d2-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="3f7d2-133">Abra o projeto criado por este passo a passo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3f7d2-134">No menu **Build**, escolha **Publicar CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="3f7d2-135">Siga as etapas do Assistente de Publicação para criar uma versão instalável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="3f7d2-136">Para obter mais informações, consulte [Assistente de Publicação (desenvolvimento do Office no Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3f7d2-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span></span>  
  
3.  <span data-ttu-id="3f7d2-137">Instale o aplicativo em um computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estejam instalados.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="3f7d2-138">Quando a instalação for concluída, execute o programa instalado.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="3f7d2-139">Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de amostra: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="3f7d2-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7d2-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f7d2-140">See Also</span></span>

- [<span data-ttu-id="3f7d2-141">Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="3f7d2-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [<span data-ttu-id="3f7d2-142">/link (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="3f7d2-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
