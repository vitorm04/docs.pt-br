---
title: 'Como: Adicionar e remover itens com o controle ListView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: 8a97d73b9b2c46d02ae0794ad66b20a04db58af6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327653"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="567ef-102">Como: Adicionar e remover itens com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="567ef-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="567ef-103">O processo de adicionar um item em um Windows Forms <xref:System.Windows.Forms.ListView> controle consiste principalmente de especificar o item e atribuir propriedades a ele.</span><span class="sxs-lookup"><span data-stu-id="567ef-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="567ef-104">A adição ou remoção de itens de lista pode ser feita a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="567ef-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="567ef-105">Para adicionar itens programaticamente</span><span class="sxs-lookup"><span data-stu-id="567ef-105">To add items programmatically</span></span>  
  
1. <span data-ttu-id="567ef-106">Use o <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> método da <xref:System.Windows.Forms.ListView.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="567ef-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="567ef-107">Para remover itens de forma programática</span><span class="sxs-lookup"><span data-stu-id="567ef-107">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="567ef-108">Use o <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> método o <xref:System.Windows.Forms.ListView.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="567ef-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="567ef-109">O <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> método Remove um item único; o <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> método Remove todos os itens da lista.</span><span class="sxs-lookup"><span data-stu-id="567ef-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="567ef-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="567ef-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="567ef-111">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="567ef-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="567ef-112">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="567ef-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
