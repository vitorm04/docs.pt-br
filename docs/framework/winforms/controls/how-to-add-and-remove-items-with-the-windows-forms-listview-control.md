---
title: Adicionar e remover itens com controle ListView
description: Saiba como adicionar e remover um item com o controle Windows Forms ListView especificando o item e atribuindo Propriedades a ele.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618084"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="12b42-103">Como adicionar e remover itens com o controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12b42-103">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="12b42-104">O processo de adicionar um item a um controle de Windows Forms <xref:System.Windows.Forms.ListView> consiste principalmente em especificar o item e atribuir propriedades a ele.</span><span class="sxs-lookup"><span data-stu-id="12b42-104">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="12b42-105">A adição ou remoção de itens de lista pode ser feita a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="12b42-105">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="12b42-106">Para adicionar itens programaticamente</span><span class="sxs-lookup"><span data-stu-id="12b42-106">To add items programmatically</span></span>  
  
1. <span data-ttu-id="12b42-107">Use o <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> método da <xref:System.Windows.Forms.ListView.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="12b42-107">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="12b42-108">Para remover itens programaticamente</span><span class="sxs-lookup"><span data-stu-id="12b42-108">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="12b42-109">Use o <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> método ou da <xref:System.Windows.Forms.ListView.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="12b42-109">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="12b42-110">O <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> método Remove um único item; o <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> método remove todos os itens da lista.</span><span class="sxs-lookup"><span data-stu-id="12b42-110">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="12b42-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12b42-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="12b42-112">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="12b42-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="12b42-113">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="12b42-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
