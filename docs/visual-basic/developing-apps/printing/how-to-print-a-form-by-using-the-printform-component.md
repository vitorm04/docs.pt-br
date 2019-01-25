---
title: 'Como: Imprimir um formulário usando o componente PrintForm (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 0a1a62627390c8839625862b9d43d61fc07ebf12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521563"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="985e6-102">Como: Imprimir um formulário usando o componente PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="985e6-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="985e6-103">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário, exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="985e6-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="985e6-104">Os procedimentos a seguir mostram como imprimir um formulário para uma impressora, uma janela de visualização de impressão e um arquivo EPS.</span><span class="sxs-lookup"><span data-stu-id="985e6-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="985e6-105">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los na [Centro de Download](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="985e6-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="985e6-106">Para imprimir um formulário para a impressora padrão</span><span class="sxs-lookup"><span data-stu-id="985e6-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="985e6-107">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="985e6-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="985e6-108">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="985e6-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="985e6-109">No **propriedades** janela, defina as <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="985e6-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="985e6-110">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, nos `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="985e6-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="985e6-111">Para exibir um formulário em uma janela de visualização de impressão</span><span class="sxs-lookup"><span data-stu-id="985e6-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="985e6-112">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="985e6-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="985e6-113">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="985e6-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="985e6-114">No **propriedades** janela, defina as <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span><span class="sxs-lookup"><span data-stu-id="985e6-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span></span>  
  
3.  <span data-ttu-id="985e6-115">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, nos `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="985e6-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="985e6-116">Para imprimir um formulário em um arquivo</span><span class="sxs-lookup"><span data-stu-id="985e6-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="985e6-117">No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="985e6-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="985e6-118">O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="985e6-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="985e6-119">No **propriedades** janela, defina as <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span><span class="sxs-lookup"><span data-stu-id="985e6-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span></span>  
  
3.  <span data-ttu-id="985e6-120">Opcionalmente, selecione o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> propriedade e digite o caminho completo e nome do arquivo para o arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="985e6-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="985e6-121">Se você ignorar essa etapa, o usuário será solicitado para um nome de arquivo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="985e6-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="985e6-122">Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, nos `Click` manipulador de eventos para um **impressão**`Button`).</span><span class="sxs-lookup"><span data-stu-id="985e6-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="985e6-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="985e6-123">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>
- [<span data-ttu-id="985e6-124">Como: imprimir a área de cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="985e6-124">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)
- [<span data-ttu-id="985e6-125">Como: imprimir as áreas de cliente e de não cliente de um formulário</span><span class="sxs-lookup"><span data-stu-id="985e6-125">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [<span data-ttu-id="985e6-126">Como: imprimir um formulário rolável</span><span class="sxs-lookup"><span data-stu-id="985e6-126">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
- [<span data-ttu-id="985e6-127">Componente PrintForm</span><span class="sxs-lookup"><span data-stu-id="985e6-127">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
