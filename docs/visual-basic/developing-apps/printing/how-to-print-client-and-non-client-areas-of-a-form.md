---
title: Como imprimir áreas cliente e não cliente de um formulário (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856732"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="0ce47-102">Como imprimir áreas cliente e não cliente de um formulário (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce47-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="0ce47-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário, exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="0ce47-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="0ce47-104">O procedimento a seguir mostra como imprimir um formulário, incluindo a área de cliente e a área não cliente.</span><span class="sxs-lookup"><span data-stu-id="0ce47-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="0ce47-105">A área de cliente não inclui a barra de título, bordas e rolagem barras.</span><span class="sxs-lookup"><span data-stu-id="0ce47-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="0ce47-106">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los na [Centro de Download](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="0ce47-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="0ce47-107">Para imprimir o cliente e as áreas não cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="0ce47-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="0ce47-108">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="0ce47-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="0ce47-109">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="0ce47-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="0ce47-110">No **propriedades** janela, defina as <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="0ce47-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="0ce47-111">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, nos `Click` manipulador de eventos para impressão `Button`).</span><span class="sxs-lookup"><span data-stu-id="0ce47-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0ce47-112">Em alguns sistemas operacionais, texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics> métodos podem não imprimir corretamente.</span><span class="sxs-lookup"><span data-stu-id="0ce47-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="0ce47-113">In this case, use o método de impressão compatível: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span><span class="sxs-lookup"><span data-stu-id="0ce47-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce47-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ce47-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="0ce47-115">Componente PrintForm</span><span class="sxs-lookup"><span data-stu-id="0ce47-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="0ce47-116">Como imprimir um formulário rolável</span><span class="sxs-lookup"><span data-stu-id="0ce47-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
