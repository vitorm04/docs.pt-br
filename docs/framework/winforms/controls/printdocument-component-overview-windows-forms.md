---
title: "Visão geral do componente PrintDocument (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f052283b743d5f1a7ed9d2bb6576390e5343dcae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="b3d33-102">Visão geral do componente PrintDocument (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b3d33-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b3d33-103">O componente [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows.</span><span class="sxs-lookup"><span data-stu-id="b3d33-103">The Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="b3d33-104">Pode ser usado junto com o componente [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.</span><span class="sxs-lookup"><span data-stu-id="b3d33-104">It can be used in conjunction with the [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="b3d33-105">Trabalhando com o componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b3d33-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="b3d33-106">Dois dos principais cenários que envolvem o <xref:System.Drawing.Printing.PrintDocument> componente são:</span><span class="sxs-lookup"><span data-stu-id="b3d33-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="b3d33-107">Trabalhos de impressão simples, como a impressão de um único arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="b3d33-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="b3d33-108">Nesse caso, você poderia adicionar o <xref:System.Drawing.Printing.PrintDocument> componente a um formulário do Windows, em seguida, adicione a lógica de programação que imprime um arquivo de <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b3d33-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="b3d33-109">A lógica de programação deve culminar com o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para imprimir o documento.</span><span class="sxs-lookup"><span data-stu-id="b3d33-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="b3d33-110">Esse método envia uma <xref:System.Drawing.Graphics> contido no objeto de <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> classe para a impressora.</span><span class="sxs-lookup"><span data-stu-id="b3d33-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="b3d33-111">Para obter um exemplo que mostra como imprimir um documento de texto usando o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: imprimir um arquivo de texto com várias páginas no Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b3d33-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="b3d33-112">Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita.</span><span class="sxs-lookup"><span data-stu-id="b3d33-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="b3d33-113">Nesse caso, você deve derivar um novo componente do <xref:System.Drawing.Printing.PrintDocument> componente e substituir (consulte [substitui](~/docs/visual-basic/language-reference/modifiers/overrides.md) do Visual Basic ou [substituir](~/docs/csharp/language-reference/keywords/override.md) para c#) o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.</span><span class="sxs-lookup"><span data-stu-id="b3d33-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="b3d33-114">Quando ele é adicionado a um formulário, o <xref:System.Drawing.Printing.PrintDocument> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="b3d33-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d33-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3d33-115">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="b3d33-116">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3d33-116">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="b3d33-117">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b3d33-117">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
