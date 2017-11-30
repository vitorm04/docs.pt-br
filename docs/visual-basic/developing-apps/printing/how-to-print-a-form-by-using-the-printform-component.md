---
title: "Como imprimir um formulário usando o componente PrintForm (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5edad4f04b98dcf0dfa328f111db5dcb423036e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="3208a-102">Como imprimir um formulário usando o componente PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3208a-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="3208a-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="3208a-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="3208a-104">Os procedimentos a seguir mostram como imprimir um formulário para uma impressora, uma janela de visualização de impressão e um arquivo EPS.</span><span class="sxs-lookup"><span data-stu-id="3208a-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="3208a-105">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="3208a-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="3208a-106">Para imprimir um formulário para a impressora padrão</span><span class="sxs-lookup"><span data-stu-id="3208a-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="3208a-107">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="3208a-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="3208a-108">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.</span><span class="sxs-lookup"><span data-stu-id="3208a-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="3208a-109">No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="3208a-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="3208a-110">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="3208a-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="3208a-111">Para exibir um formulário em uma janela de visualização de impressão</span><span class="sxs-lookup"><span data-stu-id="3208a-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="3208a-112">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="3208a-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="3208a-113">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.</span><span class="sxs-lookup"><span data-stu-id="3208a-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="3208a-114">No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span><span class="sxs-lookup"><span data-stu-id="3208a-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span></span>  
  
3.  <span data-ttu-id="3208a-115">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="3208a-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="3208a-116">Para imprimir um formulário em um arquivo</span><span class="sxs-lookup"><span data-stu-id="3208a-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="3208a-117">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="3208a-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="3208a-118">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.</span><span class="sxs-lookup"><span data-stu-id="3208a-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="3208a-119">No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span><span class="sxs-lookup"><span data-stu-id="3208a-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span></span>  
  
3.  <span data-ttu-id="3208a-120">Opcionalmente, selecione o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> propriedade e digite o caminho completo e nome do arquivo para o arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="3208a-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="3208a-121">Se você ignorar essa etapa, o usuário será solicitado um nome de arquivo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3208a-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="3208a-122">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="3208a-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3208a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3208a-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [<span data-ttu-id="3208a-124">Como imprimir a área de cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="3208a-124">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="3208a-125">Como imprimir áreas cliente e não cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="3208a-125">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="3208a-126">Como imprimir um formulário rolável</span><span class="sxs-lookup"><span data-stu-id="3208a-126">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [<span data-ttu-id="3208a-127">Componente PrintForm</span><span class="sxs-lookup"><span data-stu-id="3208a-127">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
