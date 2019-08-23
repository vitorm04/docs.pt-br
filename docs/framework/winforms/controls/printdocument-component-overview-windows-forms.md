---
title: Visão geral do componente PrintDocument (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928983"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="0e4aa-102">Visão geral do componente PrintDocument (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0e4aa-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="0e4aa-103">O componente [PrintDocument](printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="0e4aa-104">Pode ser usado junto com o componente [PrintDialog](printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="0e4aa-105">Trabalhando com o componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="0e4aa-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="0e4aa-106">Dois dos principais cenários que envolvem o <xref:System.Drawing.Printing.PrintDocument> componente são:</span><span class="sxs-lookup"><span data-stu-id="0e4aa-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="0e4aa-107">Trabalhos de impressão simples, como a impressão de um único arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="0e4aa-108">Nesse caso, você adicionaria o <xref:System.Drawing.Printing.PrintDocument> componente a um Windows Form e adicionaria a lógica de programação que imprime um arquivo no manipulador de <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="0e4aa-109">A lógica de programação deve culminar com <xref:System.Drawing.Printing.PrintDocument.Print%2A> o método para imprimir o documento.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="0e4aa-110">Esse método envia um <xref:System.Drawing.Graphics> objeto, contido <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> na propriedade da <xref:System.Drawing.Printing.PrintPageEventArgs> classe, para a impressora.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="0e4aa-111">Para obter um exemplo que mostra como imprimir um documento de texto usando <xref:System.Drawing.Printing.PrintDocument> o componente, [consulte Como: Imprima um arquivo de texto de várias páginas em](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="0e4aa-112">Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="0e4aa-113">Nesse caso, você deve derivar um novo componente <xref:System.Drawing.Printing.PrintDocument> do componente e substituir (consulte [substituições](../../../visual-basic/language-reference/modifiers/overrides.md) para Visual Basic ou [substituir](../../../csharp/language-reference/keywords/override.md) para C#) o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="0e4aa-114">Quando ele é adicionado a um formulário, o <xref:System.Drawing.Printing.PrintDocument> componente aparece na bandeja na parte inferior da designer de formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e4aa-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e4aa-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e4aa-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="0e4aa-116">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e4aa-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="0e4aa-117">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="0e4aa-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
