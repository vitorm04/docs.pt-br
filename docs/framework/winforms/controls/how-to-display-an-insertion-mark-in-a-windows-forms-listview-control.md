---
title: 'Como: Exibir uma marca de inserção em um controle ListView do Windows Forms'
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
ms.openlocfilehash: f3dff351052eaaf70737c6410c1367ab568f6fd0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586512"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="028f8-102">Como: Exibir uma marca de inserção em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="028f8-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="028f8-103">A marca de inserção no <xref:System.Windows.Forms.ListView> controle mostra aos usuários o ponto onde os itens arrastados serão inseridos.</span><span class="sxs-lookup"><span data-stu-id="028f8-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="028f8-104">Quando um usuário arrasta um item para um ponto entre dois outros itens, a marca de inserção mostra o local da nova esperado do item.</span><span class="sxs-lookup"><span data-stu-id="028f8-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="028f8-105">O recurso de marca de inserção está disponível apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="028f8-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="028f8-106">Em sistemas operacionais anteriores, nenhum código relacionado à marca de inserção não tem nenhum efeito e a marca de inserção não será exibida.</span><span class="sxs-lookup"><span data-stu-id="028f8-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="028f8-107">Para obter mais informações, consulte <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="028f8-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="028f8-108">A imagem a seguir mostra uma marca de inserção:</span><span class="sxs-lookup"><span data-stu-id="028f8-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="028f8-109">![Captura de tela que mostra uma marca de inserção de ListView. ](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="028f8-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="028f8-110">O exemplo de código a seguir demonstra como usar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="028f8-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="028f8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="028f8-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="028f8-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="028f8-112">Compiling the Code</span></span>  
 <span data-ttu-id="028f8-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="028f8-113">This example requires:</span></span>  
  
- <span data-ttu-id="028f8-114">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="028f8-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028f8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="028f8-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="028f8-116">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="028f8-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="028f8-117">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="028f8-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="028f8-118">Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="028f8-118">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
