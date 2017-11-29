---
title: "Como imprimir um formulário rolável (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 380e0f833dc69718142809c99ed7615256dd2e73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="9fb75-102">Como imprimir um formulário rolável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fb75-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="9fb75-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário sem usar um <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="9fb75-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="9fb75-104">Por padrão, somente a parte visível do formulário é impresso; Se um usuário tiver redimensionado do formulário em tempo de execução, a imagem não pode imprimir conforme pretendido.</span><span class="sxs-lookup"><span data-stu-id="9fb75-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="9fb75-105">O procedimento a seguir mostra como imprimir a área de cliente completa de um formulário rolável, mesmo se o formulário foi redimensionado.</span><span class="sxs-lookup"><span data-stu-id="9fb75-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="9fb75-106">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="9fb75-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="9fb75-107">Para imprimir a área de cliente completa de um formulário rolável</span><span class="sxs-lookup"><span data-stu-id="9fb75-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="9fb75-108">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="9fb75-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="9fb75-109">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente será adicionado à bandeja do componente.</span><span class="sxs-lookup"><span data-stu-id="9fb75-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="9fb75-110">No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="9fb75-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="9fb75-111">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="9fb75-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9fb75-112">Em alguns sistemas operacionais, texto ou gráfico desenhado pelo <xref:System.Drawing.Graphics> métodos podem não imprimir corretamente.</span><span class="sxs-lookup"><span data-stu-id="9fb75-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="9fb75-113">Nesse caso, você não poderá imprimir com o `Scrollable` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9fb75-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb75-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fb75-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="9fb75-115">Componente PrintForm</span><span class="sxs-lookup"><span data-stu-id="9fb75-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="9fb75-116">Como imprimir a área de cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="9fb75-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="9fb75-117">Como imprimir áreas cliente e não cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="9fb75-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
