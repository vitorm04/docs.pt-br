---
title: Visão geral do componente PrintDocument
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728545"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="b4cd8-102">Visão geral do componente PrintDocument (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b4cd8-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="b4cd8-103">O componente [PrintDocument](printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="b4cd8-104">Pode ser usado junto com o componente [PrintDialog](printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="b4cd8-105">Trabalhando com o componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b4cd8-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="b4cd8-106">Dois dos principais cenários que envolvem o componente <xref:System.Drawing.Printing.PrintDocument> são:</span><span class="sxs-lookup"><span data-stu-id="b4cd8-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="b4cd8-107">Trabalhos de impressão simples, como a impressão de um único arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="b4cd8-108">Nesse caso, você adicionaria o componente <xref:System.Drawing.Printing.PrintDocument> a um Windows Form e adicionaria a lógica de programação que imprime um arquivo no manipulador de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="b4cd8-109">A lógica de programação deve culminar com o método <xref:System.Drawing.Printing.PrintDocument.Print%2A> para imprimir o documento.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="b4cd8-110">Esse método envia um objeto <xref:System.Drawing.Graphics>, contido na propriedade <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> da classe <xref:System.Drawing.Printing.PrintPageEventArgs>, para a impressora.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="b4cd8-111">Para obter um exemplo que mostra como imprimir um documento de texto usando o componente <xref:System.Drawing.Printing.PrintDocument>, consulte [como imprimir um arquivo de texto de várias páginas em Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b4cd8-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="b4cd8-112">Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="b4cd8-113">Nesse caso, você deve derivar um novo componente do componente <xref:System.Drawing.Printing.PrintDocument> e substituir (consulte [substituições](../../../visual-basic/language-reference/modifiers/overrides.md) para Visual Basic ou [substituir](../../../csharp/language-reference/keywords/override.md) para C#) o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="b4cd8-114">Quando ele é adicionado a um formulário, o componente <xref:System.Drawing.Printing.PrintDocument> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4cd8-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4cd8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4cd8-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="b4cd8-116">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4cd8-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="b4cd8-117">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b4cd8-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
