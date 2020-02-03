---
title: Exibir ícones para controle ListView
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
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744509"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="45e22-102">Como exibir ícones do controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45e22-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="45e22-103">O controle de <xref:System.Windows.Forms.ListView> de Windows Forms pode exibir ícones de três listas de imagens.</span><span class="sxs-lookup"><span data-stu-id="45e22-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="45e22-104">Os modos de exibição lista, detalhes e SmallIcon exibem imagens da lista de imagens especificada na propriedade <xref:System.Windows.Forms.ListView.SmallImageList%2A>.</span><span class="sxs-lookup"><span data-stu-id="45e22-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="45e22-105">A exibição LargeIcon exibe imagens da lista de imagens especificada na propriedade <xref:System.Windows.Forms.ListView.LargeImageList%2A>.</span><span class="sxs-lookup"><span data-stu-id="45e22-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="45e22-106">Um modo de exibição de lista também pode exibir um conjunto adicional de ícones, definido na propriedade <xref:System.Windows.Forms.ListView.StateImageList%2A>, ao lado dos ícones grandes ou pequenos.</span><span class="sxs-lookup"><span data-stu-id="45e22-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="45e22-107">Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="45e22-107">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="45e22-108">Para exibir imagens em uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="45e22-108">To display images in a list view</span></span>  
  
1. <span data-ttu-id="45e22-109">Defina a propriedade apropriada —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>ou <xref:System.Windows.Forms.ListView.StateImageList%2A>— para o componente <xref:System.Windows.Forms.ImageList> existente que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="45e22-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="45e22-110">Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.</span><span class="sxs-lookup"><span data-stu-id="45e22-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. <span data-ttu-id="45e22-111">Defina a propriedade <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> ou <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> para cada item de lista que tenha um ícone associado.</span><span class="sxs-lookup"><span data-stu-id="45e22-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="45e22-112">Essas propriedades podem ser definidas no código ou no **Editor de coleção ListViewItem**.</span><span class="sxs-lookup"><span data-stu-id="45e22-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="45e22-113">Para abrir o **Editor de coleção ListViewItem**, clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Items%2A> na janela **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="45e22-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="45e22-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45e22-114">See also</span></span>

- [<span data-ttu-id="45e22-115">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="45e22-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="45e22-116">Como adicionar e remover itens com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45e22-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="45e22-117">Como Adicionar Colunas ao Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45e22-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="45e22-118">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="45e22-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="45e22-119">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="45e22-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
