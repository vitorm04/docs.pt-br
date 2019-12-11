---
title: Como agrupar itens em um controle ListView dos Windows Forms
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
ms.openlocfilehash: 1b716498ec5a45fbde499a1f53b2bdccd28a7176
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960169"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="56f62-102">Como agrupar itens em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56f62-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="56f62-103">Com o recurso de agrupamento do controle de <xref:System.Windows.Forms.ListView>, você pode exibir conjuntos de itens relacionados em grupos.</span><span class="sxs-lookup"><span data-stu-id="56f62-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="56f62-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="56f62-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="56f62-105">Você pode usar grupos de <xref:System.Windows.Forms.ListView> para facilitar a navegação de listas grandes ao agrupar itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico.</span><span class="sxs-lookup"><span data-stu-id="56f62-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="56f62-106">A imagem a seguir mostra alguns itens agrupados.</span><span class="sxs-lookup"><span data-stu-id="56f62-106">The following image shows some grouped items.</span></span>  
  
 ![Captura de tela de grupos ímpares e até mesmo de ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="56f62-108">Para habilitar o agrupamento, primeiro crie um ou mais grupos no designer ou de forma programática.</span><span class="sxs-lookup"><span data-stu-id="56f62-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="56f62-109">Depois que um grupo tiver sido definido, você poderá atribuir <xref:System.Windows.Forms.ListView> itens a grupos.</span><span class="sxs-lookup"><span data-stu-id="56f62-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="56f62-110">Você também pode mover itens de um grupo para outro de forma programática.</span><span class="sxs-lookup"><span data-stu-id="56f62-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="56f62-111">Para adicionar grupos</span><span class="sxs-lookup"><span data-stu-id="56f62-111">To add groups</span></span>  
  
1. <span data-ttu-id="56f62-112">Use o método <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> da coleção <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="56f62-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="56f62-113">Para remover grupos</span><span class="sxs-lookup"><span data-stu-id="56f62-113">To remove groups</span></span>  
  
1. <span data-ttu-id="56f62-114">Use o método <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> da coleção de <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="56f62-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="56f62-115">O método <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> remove um único grupo; o método <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> remove todos os grupos da lista.</span><span class="sxs-lookup"><span data-stu-id="56f62-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="56f62-116">A remoção de um grupo não remove os itens dentro desse grupo.</span><span class="sxs-lookup"><span data-stu-id="56f62-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="56f62-117">Para atribuir itens a grupos ou mover itens entre grupos</span><span class="sxs-lookup"><span data-stu-id="56f62-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="56f62-118">Defina a propriedade <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> de itens individuais.</span><span class="sxs-lookup"><span data-stu-id="56f62-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="56f62-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56f62-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="56f62-120">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="56f62-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="56f62-121">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="56f62-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="56f62-122">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56f62-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
