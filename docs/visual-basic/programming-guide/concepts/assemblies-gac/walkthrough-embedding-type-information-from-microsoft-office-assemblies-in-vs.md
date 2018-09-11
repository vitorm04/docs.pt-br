---
title: 'Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: bc8f7585964bdd60bac5d5a466f6276fab288c78
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273197"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="5a11a-102">Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a11a-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="5a11a-103">Se inserir informações de tipo em um aplicativo que faz referência a objetos COM, você poderá eliminar a necessidade de um PIA (assembly de interoperabilidade primário).</span><span class="sxs-lookup"><span data-stu-id="5a11a-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="5a11a-104">Além disso, as informações de tipo inseridas permitem que você conquiste a independência de versão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a11a-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="5a11a-105">Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca COM sem precisar especificar um PIA específico para cada versão.</span><span class="sxs-lookup"><span data-stu-id="5a11a-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="5a11a-106">Esse é um cenário comum para aplicativos que usam objetos de bibliotecas do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="5a11a-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="5a11a-107">Inserir informações de tipo possibilita que a mesma build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores sem precisar reimplantar o programa ou o PIA para cada versão do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="5a11a-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="5a11a-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5a11a-108">Prerequisites</span></span>  
 <span data-ttu-id="5a11a-109">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5a11a-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="5a11a-110">Um computador em que o Visual Studio e o Microsoft Excel estão instalados.</span><span class="sxs-lookup"><span data-stu-id="5a11a-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="5a11a-111">Um segundo computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estão instalados.</span><span class="sxs-lookup"><span data-stu-id="5a11a-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="5a11a-112">Para criar um aplicativo que funciona com várias versões do Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="5a11a-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="5a11a-113">Inicie o Visual Studio em um computador em que o Excel está instalado.</span><span class="sxs-lookup"><span data-stu-id="5a11a-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="5a11a-114">No menu **Arquivo**, escolha **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="5a11a-115">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="5a11a-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="5a11a-116">Selecione **Aplicativo de Console** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="5a11a-117">Na caixa **Nome** insira `CreateExcelWorkbook` e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="5a11a-118">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5a11a-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="5a11a-119">Abra o menu de atalho para o projeto de CreateExcelWorkbook e, em seguida, escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="5a11a-120">Escolha o **referências** guia. Escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="5a11a-121">Na guia **.NET**, escolha a versão mais recente de `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="5a11a-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="5a11a-122">Por exemplo, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="5a11a-123">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="5a11a-124">Na lista de referências para o projeto **CreateExcelWorkbook**, selecione a referência para `Microsoft.Office.Interop.Excel` que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="5a11a-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="5a11a-125">Na janela **Propriedades**, verifique se a propriedade `Embed Interop Types` está definida como `True`.</span><span class="sxs-lookup"><span data-stu-id="5a11a-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a11a-126">O aplicativo criado neste passo a passo é executado com diferentes versões do Microsoft Office por conta das informações de tipo de interoperabilidade inseridas.</span><span class="sxs-lookup"><span data-stu-id="5a11a-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="5a11a-127">Se a propriedade `Embed Interop Types` estiver definida como `False`, você deve incluir um PIA para cada versão do Microsoft Office com que o aplicativo será executado.</span><span class="sxs-lookup"><span data-stu-id="5a11a-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="5a11a-128">Abra o arquivo Module1.vb.</span><span class="sxs-lookup"><span data-stu-id="5a11a-128">Open the Module1.vb file.</span></span> <span data-ttu-id="5a11a-129">Substitua o código no arquivo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5a11a-129">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="5a11a-130">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5a11a-130">Save the project.</span></span>  
  
9. <span data-ttu-id="5a11a-131">Pressione CTRL+F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5a11a-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="5a11a-132">Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de exemplo: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="5a11a-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="5a11a-133">Para publicar o aplicativo em um computador em que uma versão diferente do Microsoft Office está instalada</span><span class="sxs-lookup"><span data-stu-id="5a11a-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="5a11a-134">Abra o projeto criado por este passo a passo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a11a-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5a11a-135">No menu **Build**, escolha **Publicar CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="5a11a-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="5a11a-136">Siga as etapas do Assistente de Publicação para criar uma versão instalável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a11a-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="5a11a-137">Para obter mais informações, consulte [Assistente de Publicação (desenvolvimento do Office no Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5a11a-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span></span>  
  
3.  <span data-ttu-id="5a11a-138">Instale o aplicativo em um computador em que o .NET Framework 4 ou superior e uma versão diferente do Excel estejam instalados.</span><span class="sxs-lookup"><span data-stu-id="5a11a-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="5a11a-139">Quando a instalação for concluída, execute o programa instalado.</span><span class="sxs-lookup"><span data-stu-id="5a11a-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="5a11a-140">Verifique se uma pasta de trabalho do Excel foi criada no local especificado no código de amostra: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="5a11a-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a11a-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a11a-141">See also</span></span>

- [<span data-ttu-id="5a11a-142">Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a11a-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
- [<span data-ttu-id="5a11a-143">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a11a-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
