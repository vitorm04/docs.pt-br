---
title: 'Como: imprimir um arquivo de texto de várias páginas nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 07e1bb4bcdcaa99635db293f23e5ecb689b6063e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621326"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="74bd3-102">Como: imprimir um arquivo de texto de várias páginas nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74bd3-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="74bd3-103">É muito comum aplicativos do Windows imprimirem texto.</span><span class="sxs-lookup"><span data-stu-id="74bd3-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="74bd3-104">O <xref:System.Drawing.Graphics> classe fornece métodos para desenhar objetos (elementos gráficos ou texto) em um dispositivo, como uma tela ou impressora.</span><span class="sxs-lookup"><span data-stu-id="74bd3-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74bd3-105">O <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos de <xref:System.Windows.Forms.TextRenderer> não têm suporte para impressão.</span><span class="sxs-lookup"><span data-stu-id="74bd3-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="74bd3-106">Você sempre deve usar o <xref:System.Drawing.Graphics.DrawString%2A> métodos de <xref:System.Drawing.Graphics>, conforme mostrado no exemplo de código a seguir, para desenhar o texto para fins de impressão.</span><span class="sxs-lookup"><span data-stu-id="74bd3-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="74bd3-107">Imprimir texto</span><span class="sxs-lookup"><span data-stu-id="74bd3-107">To print text</span></span>  
  
1. <span data-ttu-id="74bd3-108">Adicionar um <xref:System.Drawing.Printing.PrintDocument> componente e uma cadeia de caracteres ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="74bd3-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="74bd3-109">Se a impressão de um documento, defina o <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> propriedade para o documento que você deseja imprimir e abrir e ler o conteúdo de documentos para a cadeia de caracteres que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="74bd3-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="74bd3-110">No <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos, use o <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> classe e o conteúdo do documento para calcular o comprimento da linha e linhas por página.</span><span class="sxs-lookup"><span data-stu-id="74bd3-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="74bd3-111">Depois de cada página é desenhada, verifique se ele é a última página e defina as <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> adequadamente.</span><span class="sxs-lookup"><span data-stu-id="74bd3-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="74bd3-112">O <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado até <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="74bd3-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="74bd3-113">Além disso, verifique se o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento está associado a seu método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="74bd3-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="74bd3-114">No exemplo de código a seguir, o manipulador de eventos é usado para imprimir o conteúdo do arquivo “testPage.txt” na mesma fonte usada no formulário.</span><span class="sxs-lookup"><span data-stu-id="74bd3-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="74bd3-115">Chame o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para gerar o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos.</span><span class="sxs-lookup"><span data-stu-id="74bd3-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="74bd3-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74bd3-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74bd3-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="74bd3-117">Compiling the Code</span></span>  
 <span data-ttu-id="74bd3-118">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="74bd3-118">This example requires:</span></span>  
  
- <span data-ttu-id="74bd3-119">Um arquivo de texto chamado testPage.txt que contém o texto a ser impresso, localizado na raiz da unidade C:\\.</span><span class="sxs-lookup"><span data-stu-id="74bd3-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="74bd3-120">Edite o código para imprimir um arquivo diferente.</span><span class="sxs-lookup"><span data-stu-id="74bd3-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="74bd3-121">Referências aos assemblies System, System.Windows.Forms e System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="74bd3-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="74bd3-122">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="74bd3-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="74bd3-123">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="74bd3-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74bd3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74bd3-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="74bd3-125">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74bd3-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
