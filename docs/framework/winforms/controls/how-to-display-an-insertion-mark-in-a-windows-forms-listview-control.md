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
ms.openlocfilehash: f5de00fd41b24fc1a7f1ff4484c3a126e98952a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967827"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="0ef37-102">Como: Exibir uma marca de inserção em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0ef37-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="0ef37-103">A marca de inserção no <xref:System.Windows.Forms.ListView> controle mostra aos usuários o ponto em que os itens arrastados serão inseridos.</span><span class="sxs-lookup"><span data-stu-id="0ef37-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="0ef37-104">Quando um usuário arrasta um item para um ponto entre dois outros itens, a marca de inserção mostra o novo local esperado do item.</span><span class="sxs-lookup"><span data-stu-id="0ef37-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ef37-105">O recurso de marca de inserção está disponível [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] somente em quando o aplicativo <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> chama o método.</span><span class="sxs-lookup"><span data-stu-id="0ef37-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0ef37-106">Em sistemas operacionais anteriores, qualquer código relacionado à marca de inserção não tem nenhum efeito e a marca de inserção não será exibida.</span><span class="sxs-lookup"><span data-stu-id="0ef37-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="0ef37-107">Para obter mais informações, consulte <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="0ef37-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="0ef37-108">A imagem a seguir mostra uma marca de inserção:</span><span class="sxs-lookup"><span data-stu-id="0ef37-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="0ef37-109">![Captura de tela que mostra uma marca de inserção de ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="0ef37-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="0ef37-110">O exemplo de código a seguir demonstra como usar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="0ef37-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef37-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef37-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ef37-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0ef37-112">Compiling the Code</span></span>  
 <span data-ttu-id="0ef37-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="0ef37-113">This example requires:</span></span>  
  
- <span data-ttu-id="0ef37-114">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0ef37-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef37-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef37-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="0ef37-116">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="0ef37-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0ef37-117">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="0ef37-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="0ef37-118">Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0ef37-118">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
