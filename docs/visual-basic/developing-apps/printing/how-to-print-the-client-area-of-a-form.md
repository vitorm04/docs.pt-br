---
title: "Como: imprimir a área cliente de um formulário (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- client area, printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
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
ms.openlocfilehash: 2b5c340a944af0b9a846b9dac92e5a619183d716
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="0097c-102">Como imprimir a área cliente de um formulário (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0097c-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="0097c-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente permite que você imprimir rapidamente uma imagem de um formulário sem usar um <xref:System.Drawing.Printing.PrintDocument>componente.</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="0097c-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="0097c-104">O procedimento a seguir mostra como imprimir apenas a área cliente de um formulário, sem a barra de título, bordas e barras de rolagem.</span><span class="sxs-lookup"><span data-stu-id="0097c-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="0097c-105">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="0097c-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="0097c-106">Para imprimir a área cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="0097c-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="0097c-107">No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="0097c-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="0097c-108">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente é adicionado à bandeja de componentes.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="0097c-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="0097c-109">No **propriedades** janela, defina a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriedade <xref:System.Drawing.Printing.PrintAction>.</xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="0097c-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction>.</span></span>  
  
3.  <span data-ttu-id="0097c-110">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="0097c-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0097c-111">Em alguns sistemas operacionais, texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics>métodos podem não imprimir corretamente.</xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="0097c-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="0097c-112">Nesse caso, use o método de impressão compatível:`PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="0097c-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0097c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0097c-113">See Also</span></span>  
 <span data-ttu-id="0097c-114"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="0097c-114"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span></span>   
 <span data-ttu-id="0097c-115"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="0097c-115"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span></span>   
<span data-ttu-id="0097c-116"> [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md) </span><span class="sxs-lookup"><span data-stu-id="0097c-116"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md) </span></span>  
<span data-ttu-id="0097c-117"> [Como: Imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="0097c-117"> [How to: Print Client and Non-Client Areas of a Form](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span></span>  
<span data-ttu-id="0097c-118"> [Como imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)</span><span class="sxs-lookup"><span data-stu-id="0097c-118"> [How to: Print a Scrollable Form](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)</span></span>
