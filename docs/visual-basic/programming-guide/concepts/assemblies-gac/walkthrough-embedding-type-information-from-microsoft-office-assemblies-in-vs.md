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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: c527941d6eae56d66cbede92ced3f66d24937354
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="78f1d-102">Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f1d-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="78f1d-103">Se você inserir informações de tipo em um aplicativo que faz referência a objetos COM, você pode eliminar a necessidade de um assembly de interoperabilidade primária (PIA).</span><span class="sxs-lookup"><span data-stu-id="78f1d-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="78f1d-104">Além disso, as informações de tipo incorporado permite que você atingir a independência de versão para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78f1d-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="78f1d-105">Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca COM sem a necessidade de um PIA específico para cada versão.</span><span class="sxs-lookup"><span data-stu-id="78f1d-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="78f1d-106">Esse é um cenário comum para aplicativos que usam objetos de bibliotecas do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="78f1d-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="78f1d-107">Inserindo informações de tipo permite que a mesma compilação de um programa para trabalhar com diferentes versões do Microsoft Office em computadores diferentes sem precisar reimplantar o programa ou o PIA para cada versão do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="78f1d-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="78f1d-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="78f1d-108">Prerequisites</span></span>  
 <span data-ttu-id="78f1d-109">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="78f1d-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="78f1d-110">Um computador em que o Visual Studio e o Microsoft Excel são instalados.</span><span class="sxs-lookup"><span data-stu-id="78f1d-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="78f1d-111">Um segundo computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estiverem instalados.</span><span class="sxs-lookup"><span data-stu-id="78f1d-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <span data-ttu-id="78f1d-112"><a name="BKMK_createapp"></a>Para criar um aplicativo que funciona com várias versões do Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="78f1d-112"><a name="BKMK_createapp"></a> To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="78f1d-113">Inicie o Visual Studio em um computador em que o Excel está instalado.</span><span class="sxs-lookup"><span data-stu-id="78f1d-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="78f1d-114">No menu **Arquivo**, escolha **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="78f1d-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="78f1d-115">No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="78f1d-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="78f1d-116">Selecione **aplicativo de Console** no **modelos** painel.</span><span class="sxs-lookup"><span data-stu-id="78f1d-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="78f1d-117">No **nome** , digite `CreateExcelWorkbook`e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="78f1d-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="78f1d-118">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="78f1d-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="78f1d-119">Abra o menu de atalho para o projeto CreateExcelWorkbook e, em seguida, escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="78f1d-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="78f1d-120">Escolha o **referências** guia.</span><span class="sxs-lookup"><span data-stu-id="78f1d-120">Choose the **References** tab.</span></span> <span data-ttu-id="78f1d-121">Escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="78f1d-121">Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="78f1d-122">Sobre o **.NET** guia, escolha a versão mais recente do `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="78f1d-122">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="78f1d-123">Por exemplo, **Interop 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="78f1d-123">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="78f1d-124">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="78f1d-124">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="78f1d-125">Na lista de referências para o **CreateExcelWorkbook** de projeto, selecione a referência de `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="78f1d-125">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="78f1d-126">No **propriedades** janela, verifique se o `Embed Interop Types` está definida como `True`.</span><span class="sxs-lookup"><span data-stu-id="78f1d-126">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78f1d-127">O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inserido.</span><span class="sxs-lookup"><span data-stu-id="78f1d-127">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="78f1d-128">Se o `Embed Interop Types` está definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office que o aplicativo será executado com.</span><span class="sxs-lookup"><span data-stu-id="78f1d-128">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="78f1d-129">Abra o arquivo Module1. vb.</span><span class="sxs-lookup"><span data-stu-id="78f1d-129">Open the Module1.vb file.</span></span> <span data-ttu-id="78f1d-130">Substitua o código no arquivo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="78f1d-130">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="78f1d-131">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="78f1d-131">Save the project.</span></span>  
  
9. <span data-ttu-id="78f1d-132">Pressione CTRL + F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="78f1d-132">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="78f1d-133">Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="78f1d-133">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <span data-ttu-id="78f1d-134"><a name="BKMK_publishapp"></a>Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada</span><span class="sxs-lookup"><span data-stu-id="78f1d-134"><a name="BKMK_publishapp"></a> To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="78f1d-135">Abra o projeto criado por este passo a passo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78f1d-135">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="78f1d-136">Sobre o **criar** menu, escolha **CreateExcelWorkbook publicar**.</span><span class="sxs-lookup"><span data-stu-id="78f1d-136">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="78f1d-137">Siga as etapas do Assistente de publicação para criar uma versão instalável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78f1d-137">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="78f1d-138">Para obter mais informações, consulte [o Assistente de publicação (desenvolvimento do Office no Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="78f1d-138">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="78f1d-139">Instale o aplicativo em um computador no qual o .NET Framework 4 ou superior e uma versão diferente do Excel estão instalados.</span><span class="sxs-lookup"><span data-stu-id="78f1d-139">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="78f1d-140">Quando a instalação for concluída, execute o programa instalado.</span><span class="sxs-lookup"><span data-stu-id="78f1d-140">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="78f1d-141">Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="78f1d-141">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f1d-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78f1d-142">See Also</span></span>  
 <span data-ttu-id="78f1d-143">[Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span><span class="sxs-lookup"><span data-stu-id="78f1d-143">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span></span>  
<span data-ttu-id="78f1d-144"> [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)</span><span class="sxs-lookup"><span data-stu-id="78f1d-144"> [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)</span></span>

