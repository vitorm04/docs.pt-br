---
title: 'Como: Agrupar itens em um controle ListView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966628"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="5a144-102">Como: Agrupar itens em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5a144-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="5a144-103">Com o recurso de agrupamento do <xref:System.Windows.Forms.ListView> controle, você pode exibir conjuntos de itens relacionados em grupos.</span><span class="sxs-lookup"><span data-stu-id="5a144-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="5a144-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="5a144-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="5a144-105">Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação de listas grandes ao agrupar itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico.</span><span class="sxs-lookup"><span data-stu-id="5a144-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="5a144-106">A imagem a seguir mostra alguns itens agrupados.</span><span class="sxs-lookup"><span data-stu-id="5a144-106">The following image shows some grouped items.</span></span>  
  
 ![Captura de tela de grupos ímpares e até mesmo de ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="5a144-108">Para habilitar o agrupamento, primeiro crie um ou mais grupos no designer ou de forma programática.</span><span class="sxs-lookup"><span data-stu-id="5a144-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="5a144-109">Depois que um grupo tiver sido definido, você poderá <xref:System.Windows.Forms.ListView> atribuir itens a grupos.</span><span class="sxs-lookup"><span data-stu-id="5a144-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="5a144-110">Você também pode mover itens de um grupo para outro de forma programática.</span><span class="sxs-lookup"><span data-stu-id="5a144-110">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a144-111"><xref:System.Windows.Forms.ListView>os grupos estão disponíveis somente [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] em quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método.</span><span class="sxs-lookup"><span data-stu-id="5a144-111"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5a144-112">Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="5a144-112">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="5a144-113">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a144-113">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="5a144-114">Para adicionar grupos</span><span class="sxs-lookup"><span data-stu-id="5a144-114">To add groups</span></span>  
  
1. <span data-ttu-id="5a144-115">Use o <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> método <xref:System.Windows.Forms.ListView.Groups%2A> da coleção.</span><span class="sxs-lookup"><span data-stu-id="5a144-115">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="5a144-116">Para remover grupos</span><span class="sxs-lookup"><span data-stu-id="5a144-116">To remove groups</span></span>  
  
1. <span data-ttu-id="5a144-117">Use o <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> método <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ou da <xref:System.Windows.Forms.ListView.Groups%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="5a144-117">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="5a144-118">O <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> método Remove um único grupo; o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método remove todos os grupos da lista.</span><span class="sxs-lookup"><span data-stu-id="5a144-118">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5a144-119">A remoção de um grupo não remove os itens dentro desse grupo.</span><span class="sxs-lookup"><span data-stu-id="5a144-119">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="5a144-120">Para atribuir itens a grupos ou mover itens entre grupos</span><span class="sxs-lookup"><span data-stu-id="5a144-120">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="5a144-121">Defina a <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriedade de itens individuais.</span><span class="sxs-lookup"><span data-stu-id="5a144-121">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="5a144-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a144-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="5a144-123">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="5a144-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="5a144-124">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="5a144-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="5a144-125">Como: Adicionar e remover itens com o controle Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="5a144-125">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
