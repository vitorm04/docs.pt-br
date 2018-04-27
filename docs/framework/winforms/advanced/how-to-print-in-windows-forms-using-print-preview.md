---
title: Como imprimir no Windows Forms usando Visualizar Impressão
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abdae9dc9f7a68f1272cb7499705728b72825247
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="b64fa-102">Como imprimir no Windows Forms usando Visualizar Impressão</span><span class="sxs-lookup"><span data-stu-id="b64fa-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="b64fa-103">É muito comum na programação do Windows Forms oferecer a visualização de impressão além dos serviços de impressão.</span><span class="sxs-lookup"><span data-stu-id="b64fa-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="b64fa-104">Uma maneira fácil de adicionar serviços de visualização de impressão ao seu aplicativo é usar um <xref:System.Windows.Forms.PrintPreviewDialog> controle em combinação com o <xref:System.Drawing.Printing.PrintDocument.PrintPage> lógica de tratamento de evento para imprimir um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b64fa-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="b64fa-105">Visualizar um documento de texto com um controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="b64fa-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1.  <span data-ttu-id="b64fa-106">Adicionar um <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>e duas cadeias de caracteres ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="b64fa-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  <span data-ttu-id="b64fa-107">Definir o <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> propriedade para o documento que você deseja imprimir e abrir e ler o conteúdo do documento para a cadeia de caracteres que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b64fa-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="b64fa-108">Como você faria para imprimir o documento, no <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos, use o <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade o <xref:System.Drawing.Printing.PrintPageEventArgs> classe e o conteúdo do arquivo para calcular linhas por página e processar o conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="b64fa-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="b64fa-109">Depois de cada página é desenhada, verifique se ela é a última página e defina o <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> propriedade o <xref:System.Drawing.Printing.PrintPageEventArgs> adequadamente.</span><span class="sxs-lookup"><span data-stu-id="b64fa-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="b64fa-110">O <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado até <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="b64fa-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="b64fa-111">Após a renderização do documento ser concluída, redefina a cadeia de caracteres a ser renderizada.</span><span class="sxs-lookup"><span data-stu-id="b64fa-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="b64fa-112">Além disso, verifique se o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento está associado a seu método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="b64fa-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b64fa-113">Você poderá já ter concluído as etapas 2 e 3 se tiver implementado a impressão em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b64fa-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="b64fa-114">No exemplo de código a seguir, o manipulador de eventos é usado para imprimir o arquivo “testPage.txt” na mesma fonte usada no formulário.</span><span class="sxs-lookup"><span data-stu-id="b64fa-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="b64fa-115">Definir o <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> propriedade do <xref:System.Windows.Forms.PrintPreviewDialog> o controle para o <xref:System.Drawing.Printing.PrintDocument> componente no formulário.</span><span class="sxs-lookup"><span data-stu-id="b64fa-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  <span data-ttu-id="b64fa-116">Chamar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método sobre o <xref:System.Windows.Forms.PrintPreviewDialog> controle.</span><span class="sxs-lookup"><span data-stu-id="b64fa-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="b64fa-117">Normalmente, você poderia chamar <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> do <xref:System.Windows.Forms.Control.Click> método de manipulação de eventos de um botão.</span><span class="sxs-lookup"><span data-stu-id="b64fa-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="b64fa-118">Chamando <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> gera o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos e processa a saída para o <xref:System.Windows.Forms.PrintPreviewDialog> controle.</span><span class="sxs-lookup"><span data-stu-id="b64fa-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="b64fa-119">Quando o usuário clica no ícone de impressão na caixa de diálogo, o <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado novamente, enviando a saída para a impressora, em vez da caixa de diálogo de visualização.</span><span class="sxs-lookup"><span data-stu-id="b64fa-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="b64fa-120">É por isso a cadeia de caracteres é redefinida no final do processo de renderização na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="b64fa-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="b64fa-121">O seguinte exemplo de código mostra o <xref:System.Windows.Forms.Control.Click> método do manipulador de eventos para um botão no formulário.</span><span class="sxs-lookup"><span data-stu-id="b64fa-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="b64fa-122">Esse método de manipulação de eventos chama os métodos para ler o documento e mostrar a caixa de diálogo de visualização de impressão.</span><span class="sxs-lookup"><span data-stu-id="b64fa-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b64fa-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b64fa-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b64fa-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b64fa-124">Compiling the Code</span></span>  
 <span data-ttu-id="b64fa-125">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b64fa-125">This example requires:</span></span>  
  
-   <span data-ttu-id="b64fa-126">Referências aos assemblies System, System.Windows.Forms e System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="b64fa-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="b64fa-127">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b64fa-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b64fa-128">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="b64fa-128">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="b64fa-129">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b64fa-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64fa-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b64fa-130">See Also</span></span>  
 [<span data-ttu-id="b64fa-131">Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b64fa-131">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="b64fa-132">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b64fa-132">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="b64fa-133">Impressão mais segura no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b64fa-133">More Secure Printing in Windows Forms</span></span>](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
