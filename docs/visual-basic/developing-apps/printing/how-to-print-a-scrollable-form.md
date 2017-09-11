---
title: "Como: imprimir um formulário rolável (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- entire form, printing
- scrollable form, printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 859f4abbfbb6f40a645c9ccbde84ee4ee02a7547
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="e3c9e-102">Como imprimir um formulário rolável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3c9e-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="e3c9e-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente permite que você imprimir rapidamente uma imagem de um formulário sem usar um <xref:System.Drawing.Printing.PrintDocument>componente.</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="e3c9e-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="e3c9e-104">Por padrão, somente a parte visível do formulário é impresso; Se um usuário tiver redimensionado o formulário em tempo de execução, a imagem não pode imprimir conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="e3c9e-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="e3c9e-105">O procedimento a seguir mostra como imprimir a área cliente completo de um formulário rolável, mesmo se o formulário for redimensionado.</span><span class="sxs-lookup"><span data-stu-id="e3c9e-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="e3c9e-106">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="e3c9e-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="e3c9e-107">Para imprimir a área cliente completo de um formulário rolável</span><span class="sxs-lookup"><span data-stu-id="e3c9e-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="e3c9e-108">No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="e3c9e-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="e3c9e-109">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente será adicionado à bandeja de componentes.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="e3c9e-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="e3c9e-110">No **propriedades** janela, defina a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriedade <xref:System.Drawing.Printing.PrintAction>.</xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="e3c9e-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction>.</span></span>  
  
3.  <span data-ttu-id="e3c9e-111">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="e3c9e-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e3c9e-112">Em alguns sistemas operacionais, texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics>métodos podem não imprimir corretamente.</xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="e3c9e-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="e3c9e-113">Nesse caso, você não poderá imprimir com o `Scrollable` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3c9e-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c9e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3c9e-114">See Also</span></span>  
 <span data-ttu-id="e3c9e-115"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="e3c9e-115"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span></span>   
 <span data-ttu-id="e3c9e-116"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="e3c9e-116"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span></span>   
<span data-ttu-id="e3c9e-117"> [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md) </span><span class="sxs-lookup"><span data-stu-id="e3c9e-117"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md) </span></span>  
<span data-ttu-id="e3c9e-118"> [Como: imprimir a área cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="e3c9e-118"> [How to: Print the Client Area of a Form](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span></span>  
<span data-ttu-id="e3c9e-119"> [Como imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)</span><span class="sxs-lookup"><span data-stu-id="e3c9e-119"> [How to: Print Client and Non-Client Areas of a Form](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)</span></span>
