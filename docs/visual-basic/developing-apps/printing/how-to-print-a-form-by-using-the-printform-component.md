---
title: "Como: imprimir um formulário usando o componente PrintForm (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Form, printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 19
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
ms.openlocfilehash: fc6de60bc02a5d8527a7c5e78a7c357944f81131
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="40ea2-102">Como imprimir um formulário usando o componente PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40ea2-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="40ea2-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente permite que você imprimir rapidamente uma imagem de um formulário exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument>componente.</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="40ea2-104">Os procedimentos a seguir mostram como imprimir um formulário para uma impressora, uma janela de visualização de impressão e um arquivo EPS.</span><span class="sxs-lookup"><span data-stu-id="40ea2-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="40ea2-105">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="40ea2-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="40ea2-106">Imprimir um formulário para a impressora padrão</span><span class="sxs-lookup"><span data-stu-id="40ea2-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="40ea2-107">No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="40ea2-108">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente é adicionado à bandeja de componentes.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="40ea2-109">No **propriedades** janela, defina a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriedade <xref:System.Drawing.Printing.PrintAction>.</xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="40ea2-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction>.</span></span>  
  
3.  <span data-ttu-id="40ea2-110">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="40ea2-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="40ea2-111">Para exibir um formulário em uma janela de visualização de impressão</span><span class="sxs-lookup"><span data-stu-id="40ea2-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="40ea2-112">No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="40ea2-113">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente é adicionado à bandeja de componentes.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="40ea2-114">No **propriedades** janela, defina a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriedade <xref:System.Drawing.Printing.PrintAction>.</xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="40ea2-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction>.</span></span>  
  
3.  <span data-ttu-id="40ea2-115">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="40ea2-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="40ea2-116">Imprimir um formulário em um arquivo</span><span class="sxs-lookup"><span data-stu-id="40ea2-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="40ea2-117">No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="40ea2-118">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente é adicionado à bandeja de componentes.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="40ea2-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="40ea2-119">No **propriedades** janela, defina a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriedade <xref:System.Drawing.Printing.PrintAction>.</xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="40ea2-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction>.</span></span>  
  
3.  <span data-ttu-id="40ea2-120">Opcionalmente, selecione a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>propriedade e digite o caminho completo e nome do arquivo para o arquivo de destino.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A></span><span class="sxs-lookup"><span data-stu-id="40ea2-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="40ea2-121">Se você ignorar essa etapa, o usuário será solicitado um nome de arquivo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40ea2-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="40ea2-122">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="40ea2-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="40ea2-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40ea2-123">See Also</span></span>  
 <span data-ttu-id="40ea2-124"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="40ea2-124"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span></span>   
 <span data-ttu-id="40ea2-125"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A></span><span class="sxs-lookup"><span data-stu-id="40ea2-125"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A></span></span>   
<span data-ttu-id="40ea2-126"> [Como: imprimir a área cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="40ea2-126"> [How to: Print the Client Area of a Form](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span></span>  
<span data-ttu-id="40ea2-127"> [Como: Imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="40ea2-127"> [How to: Print Client and Non-Client Areas of a Form](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span></span>  
<span data-ttu-id="40ea2-128"> [Como: imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md) </span><span class="sxs-lookup"><span data-stu-id="40ea2-128"> [How to: Print a Scrollable Form](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md) </span></span>  
<span data-ttu-id="40ea2-129"> [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)</span><span class="sxs-lookup"><span data-stu-id="40ea2-129"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)</span></span>
