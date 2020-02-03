---
title: 'Como: imprimir um arquivo de texto de várias páginas'
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
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740654"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="5c117-102">Como imprimir um arquivo de texto de várias páginas no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c117-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="5c117-103">É muito comum aplicativos do Windows imprimirem texto.</span><span class="sxs-lookup"><span data-stu-id="5c117-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="5c117-104">A classe <xref:System.Drawing.Graphics> fornece métodos para desenhar objetos (gráficos ou texto) em um dispositivo, como uma tela ou impressora.</span><span class="sxs-lookup"><span data-stu-id="5c117-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c117-105">Os métodos de <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de <xref:System.Windows.Forms.TextRenderer> não têm suporte para impressão.</span><span class="sxs-lookup"><span data-stu-id="5c117-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="5c117-106">Você sempre deve usar os métodos <xref:System.Drawing.Graphics.DrawString%2A> de <xref:System.Drawing.Graphics>, conforme mostrado no exemplo de código a seguir, para desenhar texto para fins de impressão.</span><span class="sxs-lookup"><span data-stu-id="5c117-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="5c117-107">Imprimir texto</span><span class="sxs-lookup"><span data-stu-id="5c117-107">To print text</span></span>  
  
1. <span data-ttu-id="5c117-108">Adicione um componente <xref:System.Drawing.Printing.PrintDocument> e uma cadeia de caracteres ao formulário.</span><span class="sxs-lookup"><span data-stu-id="5c117-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="5c117-109">Se estiver imprimindo um documento, defina a propriedade <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> como o documento que você deseja imprimir e abra e leia o conteúdo dos documentos para a cadeia de caracteres que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5c117-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="5c117-110">No manipulador de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage>, use a propriedade <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> da classe <xref:System.Drawing.Printing.PrintPageEventArgs> e o conteúdo do documento para calcular o comprimento e as linhas de linha por página.</span><span class="sxs-lookup"><span data-stu-id="5c117-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="5c117-111">Depois que cada página for desenhada, verifique se ela é a última página e defina a propriedade <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> do <xref:System.Drawing.Printing.PrintPageEventArgs> de acordo.</span><span class="sxs-lookup"><span data-stu-id="5c117-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="5c117-112">O evento <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado até que <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> seja `false`.</span><span class="sxs-lookup"><span data-stu-id="5c117-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="5c117-113">Além disso, verifique se o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage> está associado ao seu método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="5c117-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="5c117-114">No exemplo de código a seguir, o manipulador de eventos é usado para imprimir o conteúdo do arquivo “testPage.txt” na mesma fonte usada no formulário.</span><span class="sxs-lookup"><span data-stu-id="5c117-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="5c117-115">Chame o método <xref:System.Drawing.Printing.PrintDocument.Print%2A> para gerar o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="5c117-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="5c117-116">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5c117-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c117-117">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="5c117-117">Compiling the Code</span></span>  
 <span data-ttu-id="5c117-118">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5c117-118">This example requires:</span></span>  
  
- <span data-ttu-id="5c117-119">Um arquivo de texto chamado testPage.txt que contém o texto a ser impresso, localizado na raiz da unidade C:\\.</span><span class="sxs-lookup"><span data-stu-id="5c117-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="5c117-120">Edite o código para imprimir um arquivo diferente.</span><span class="sxs-lookup"><span data-stu-id="5c117-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="5c117-121">Referências aos assemblies System, System.Windows.Forms e System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="5c117-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="5c117-122">Para obter informações sobre como criar este exemplo a partir da linha de comando C#para Visual Basic ou Visual, consulte [criando a linha de comando ou a](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) criação de linha de comando [com CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5c117-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5c117-123">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="5c117-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c117-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c117-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="5c117-125">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c117-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
