---
title: Como exibir ícones do controle ListView dos Windows Forms
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
ms.openlocfilehash: 0e597ed182739947014b4f405ee2dc3149b62849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533598"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Como exibir ícones do controle ListView dos Windows Forms
Windows Forms <xref:System.Windows.Forms.ListView> controle pode exibir ícones de três das listas de imagens. Os modos de exibição de lista, detalhes e SmallIcon exibem imagens da lista de imagens especificado no <xref:System.Windows.Forms.ListView.SmallImageList%2A> propriedade. O modo de exibição LargeIcon exibe imagens da lista de imagem especificado no <xref:System.Windows.Forms.ListView.LargeImageList%2A> propriedade. Uma exibição de lista também pode exibir um conjunto adicional de ícones, definido <xref:System.Windows.Forms.ListView.StateImageList%2A> propriedade, ao lado de ícones grandes ou pequenos. Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Para exibir imagens em uma exibição de lista  
  
1.  Defina a propriedade apropriada —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, ou <xref:System.Windows.Forms.ListView.StateImageList%2A>— para existente <xref:System.Windows.Forms.ImageList> componente que você deseja usar.  
  
     Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  Definir o <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> ou <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> propriedade para cada item de lista que tem um ícone associado.  
  
     Essas propriedades podem ser definidas no código ou no **Editor de coleção ListViewItem**. Para abrir o **Editor de coleção de ListViewItem**, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.ListView.Items%2A>propriedade o **propriedades** janela.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Como adicionar colunas ao controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
