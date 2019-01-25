---
title: 'Como: Exibir uma marca de inserção em um controle ListView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 6e2e89baf17c63ea3ad4814cd761449baeb78405
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627506"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="1d084-102">Como: Exibir uma marca de inserção em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d084-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="1d084-103">A marca de inserção no <xref:System.Windows.Forms.ListView> controle mostra aos usuários o ponto onde os itens arrastados serão inseridos.</span><span class="sxs-lookup"><span data-stu-id="1d084-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="1d084-104">Quando um usuário arrasta um item para um ponto entre dois outros itens, a marca de inserção mostra o local da nova esperado do item.</span><span class="sxs-lookup"><span data-stu-id="1d084-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d084-105">O recurso de marca de inserção está disponível apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="1d084-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1d084-106">Em sistemas operacionais anteriores, nenhum código relacionado à marca de inserção não tem nenhum efeito e a marca de inserção não será exibida.</span><span class="sxs-lookup"><span data-stu-id="1d084-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="1d084-107">Para obter mais informações, consulte <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="1d084-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="1d084-108">A imagem a seguir mostra uma marca de inserção:</span><span class="sxs-lookup"><span data-stu-id="1d084-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="1d084-109">![Uma marca de inserção de ListView](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="1d084-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="1d084-110">O exemplo de código a seguir demonstra como usar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="1d084-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d084-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d084-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d084-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1d084-112">Compiling the Code</span></span>  
 <span data-ttu-id="1d084-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1d084-113">This example requires:</span></span>  
  
-   <span data-ttu-id="1d084-114">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1d084-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1d084-115">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1d084-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1d084-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="1d084-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1d084-117">Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1d084-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d084-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d084-118">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="1d084-119">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="1d084-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="1d084-120">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="1d084-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="1d084-121">Recursos do Windows XP e controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d084-121">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [<span data-ttu-id="1d084-122">Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d084-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
