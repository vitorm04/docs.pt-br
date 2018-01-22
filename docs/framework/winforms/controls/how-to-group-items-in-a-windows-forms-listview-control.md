---
title: Como agrupar itens em um controle ListView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f9596d5a344b2e14ea73120a4d2412917eba365
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="75143-102">Como agrupar itens em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75143-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="75143-103">Com o recurso de agrupamento do <xref:System.Windows.Forms.ListView> controle, você pode exibir conjuntos de itens relacionados em grupos.</span><span class="sxs-lookup"><span data-stu-id="75143-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="75143-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="75143-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="75143-105">Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação listas grandes mais fáceis com o agrupamento de itens em ordem alfabética, por data, ou por qualquer outro grupo lógico.</span><span class="sxs-lookup"><span data-stu-id="75143-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="75143-106">A imagem a seguir mostra alguns itens agrupados.</span><span class="sxs-lookup"><span data-stu-id="75143-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="75143-107">![Grupos de ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="75143-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="75143-108">Itens agrupados de ListView</span><span class="sxs-lookup"><span data-stu-id="75143-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="75143-109">Para habilitar o agrupamento, primeiro crie um ou mais grupos no designer ou de forma programática.</span><span class="sxs-lookup"><span data-stu-id="75143-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="75143-110">Após a definição de um grupo, você pode atribuir <xref:System.Windows.Forms.ListView> itens aos grupos.</span><span class="sxs-lookup"><span data-stu-id="75143-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="75143-111">Você também pode mover itens de um grupo para outro de forma programática.</span><span class="sxs-lookup"><span data-stu-id="75143-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75143-112"><xref:System.Windows.Forms.ListView>os grupos estão disponíveis apenas em [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="75143-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="75143-113">Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="75143-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="75143-114">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75143-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="75143-115">Para adicionar grupos</span><span class="sxs-lookup"><span data-stu-id="75143-115">To add groups</span></span>  
  
1.  <span data-ttu-id="75143-116">Use o <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> método o <xref:System.Windows.Forms.ListView.Groups%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="75143-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="75143-117">Para remover grupos</span><span class="sxs-lookup"><span data-stu-id="75143-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="75143-118">Use o <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método o <xref:System.Windows.Forms.ListView.Groups%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="75143-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="75143-119">O <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> método Remove um grupo único; o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método Remove todos os grupos da lista.</span><span class="sxs-lookup"><span data-stu-id="75143-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75143-120">A remoção de um grupo não remove os itens dentro desse grupo.</span><span class="sxs-lookup"><span data-stu-id="75143-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="75143-121">Para atribuir itens a grupos ou mover itens entre grupos</span><span class="sxs-lookup"><span data-stu-id="75143-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="75143-122">Definir o <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriedade dos itens individuais.</span><span class="sxs-lookup"><span data-stu-id="75143-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="75143-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75143-123">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="75143-124">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="75143-124">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="75143-125">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="75143-125">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="75143-126">Recursos do Windows XP e controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75143-126">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="75143-127">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75143-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
