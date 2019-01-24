---
title: 'Como: Exibir subitens em colunas com o controle ListView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: bd41dda048aadc399c7f8ffe0926b010991d08a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686745"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="50406-102">Como: Exibir subitens em colunas com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50406-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="50406-103">Os formulários do Windows <xref:System.Windows.Forms.ListView> controle pode exibir texto adicional ou subitens, para cada item na exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="50406-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="50406-104">A primeira coluna exibe o texto do item, por exemplo, o número de um funcionário.</span><span class="sxs-lookup"><span data-stu-id="50406-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="50406-105">A segunda, terceira e colunas seguintes exibem o primeiro, segundo e subitens associados seguintes.</span><span class="sxs-lookup"><span data-stu-id="50406-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="50406-106">Para adicionar subitens a um item de lista</span><span class="sxs-lookup"><span data-stu-id="50406-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="50406-107">Adicione as colunas necessárias.</span><span class="sxs-lookup"><span data-stu-id="50406-107">Add any columns needed.</span></span> <span data-ttu-id="50406-108">Porque a primeira coluna exibirá o item <xref:System.Windows.Forms.ListView.Text%2A> propriedade, você precisa de mais uma coluna que o número de subitens.</span><span class="sxs-lookup"><span data-stu-id="50406-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="50406-109">Para obter mais informações sobre como adicionar colunas, consulte [como: Adicionar colunas para o Windows Forms controle ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="50406-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="50406-110">Chame o <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> método de coleção retornada pela <xref:System.Windows.Forms.ListViewItem.SubItems%2A> propriedade de um item.</span><span class="sxs-lookup"><span data-stu-id="50406-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="50406-111">O exemplo de código a seguir define o nome do funcionário e o departamento para um item de lista.</span><span class="sxs-lookup"><span data-stu-id="50406-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="50406-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50406-112">See also</span></span>
- [<span data-ttu-id="50406-113">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="50406-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="50406-114">Como: Adicionar e remover itens com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50406-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="50406-115">Como: Adicionar colunas para o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50406-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="50406-116">Como: Exibir ícones para o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50406-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="50406-117">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="50406-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
