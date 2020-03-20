---
title: Itens de grupo no Controle ListView
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141985"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="35650-102">Como agrupar itens em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35650-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="35650-103">Com o recurso de <xref:System.Windows.Forms.ListView> agrupamento do controle, você pode exibir conjuntos relacionados de itens em grupos.</span><span class="sxs-lookup"><span data-stu-id="35650-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="35650-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="35650-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="35650-105">Você pode <xref:System.Windows.Forms.ListView> usar grupos para facilitar a navegação em grandes listas agrupando itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico.</span><span class="sxs-lookup"><span data-stu-id="35650-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="35650-106">A imagem a seguir mostra alguns itens agrupados.</span><span class="sxs-lookup"><span data-stu-id="35650-106">The following image shows some grouped items.</span></span>  
  
 ![Captura de tela de grupos ímpares e até mesmo ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 <span data-ttu-id="35650-108">Para habilitar o agrupamento, primeiro crie um ou mais grupos no designer ou de forma programática.</span><span class="sxs-lookup"><span data-stu-id="35650-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="35650-109">Depois que um grupo for definido, você pode atribuir <xref:System.Windows.Forms.ListView> itens a grupos.</span><span class="sxs-lookup"><span data-stu-id="35650-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="35650-110">Você também pode mover itens de um grupo para outro de forma programática.</span><span class="sxs-lookup"><span data-stu-id="35650-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="35650-111">Para adicionar grupos</span><span class="sxs-lookup"><span data-stu-id="35650-111">To add groups</span></span>  
  
1. <span data-ttu-id="35650-112">Use <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> o método <xref:System.Windows.Forms.ListView.Groups%2A> da coleção.</span><span class="sxs-lookup"><span data-stu-id="35650-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="35650-113">Para remover grupos</span><span class="sxs-lookup"><span data-stu-id="35650-113">To remove groups</span></span>  
  
1. <span data-ttu-id="35650-114">Use <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método <xref:System.Windows.Forms.ListView.Groups%2A> ou da coleção.</span><span class="sxs-lookup"><span data-stu-id="35650-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="35650-115">O <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> método remove um único grupo; o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método remove todos os grupos da lista.</span><span class="sxs-lookup"><span data-stu-id="35650-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="35650-116">A remoção de um grupo não remove os itens dentro desse grupo.</span><span class="sxs-lookup"><span data-stu-id="35650-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="35650-117">Para atribuir itens a grupos ou mover itens entre grupos</span><span class="sxs-lookup"><span data-stu-id="35650-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="35650-118">Defina <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> a propriedade de itens individuais.</span><span class="sxs-lookup"><span data-stu-id="35650-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="35650-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="35650-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="35650-120">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="35650-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="35650-121">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="35650-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="35650-122">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35650-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
