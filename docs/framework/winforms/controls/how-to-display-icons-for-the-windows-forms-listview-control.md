---
title: 'Como: Exibir ícones para o controle ListView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: ab515da932a4c73410e6ef22bec5ba8af200f270
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704447"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="cd59a-102">Como: Exibir ícones para o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd59a-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="cd59a-103">Os formulários do Windows <xref:System.Windows.Forms.ListView> controle pode exibir ícones das três listas de imagens.</span><span class="sxs-lookup"><span data-stu-id="cd59a-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="cd59a-104">Os modos de exibição de lista, detalhes e SmallIcon exibem imagens da lista de imagens especificada no <xref:System.Windows.Forms.ListView.SmallImageList%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cd59a-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="cd59a-105">O modo de exibição LargeIcon exibe imagens da lista de imagens especificada no <xref:System.Windows.Forms.ListView.LargeImageList%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cd59a-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="cd59a-106">Uma exibição de lista também pode exibir um conjunto adicional de ícones, definido no <xref:System.Windows.Forms.ListView.StateImageList%2A> propriedade, ao lado de ícones grandes ou pequenos.</span><span class="sxs-lookup"><span data-stu-id="cd59a-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="cd59a-107">Para obter mais informações sobre listas de imagens, consulte [componente ImageList](imagelist-component-windows-forms.md) e [como: Adicionar ou remover imagens com o Windows Forms componente ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="cd59a-107">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="cd59a-108">Para exibir imagens em uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="cd59a-108">To display images in a list view</span></span>  
  
1.  <span data-ttu-id="cd59a-109">Defina a propriedade apropriada —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, ou <xref:System.Windows.Forms.ListView.StateImageList%2A>— ao existente <xref:System.Windows.Forms.ImageList> componente que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="cd59a-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="cd59a-110">Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.</span><span class="sxs-lookup"><span data-stu-id="cd59a-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  <span data-ttu-id="cd59a-111">Defina as <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> ou <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> propriedade para cada item de lista que tem um ícone associado.</span><span class="sxs-lookup"><span data-stu-id="cd59a-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="cd59a-112">Essas propriedades podem ser definidas no código ou no **Editor de coleção ListViewItem**.</span><span class="sxs-lookup"><span data-stu-id="cd59a-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="cd59a-113">Para abrir o **Editor de coleção ListViewItem**, clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.ListView.Items%2A>propriedade de **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="cd59a-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="cd59a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd59a-114">See also</span></span>
- [<span data-ttu-id="cd59a-115">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="cd59a-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="cd59a-116">Como: Adicionar e remover itens com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd59a-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="cd59a-117">Como: Adicionar colunas para o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd59a-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="cd59a-118">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cd59a-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="cd59a-119">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="cd59a-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
