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
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Como: Exibir subitens em colunas com o controle ListView do Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.ListView> controle pode exibir texto adicional ou subitens, para cada item na exibição de detalhes. A primeira coluna exibe o texto do item, por exemplo, o número de um funcionário. A segunda, terceira e colunas seguintes exibem o primeiro, segundo e subitens associados seguintes.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Para adicionar subitens a um item de lista  
  
1.  Adicione as colunas necessárias. Porque a primeira coluna exibirá o item <xref:System.Windows.Forms.ListView.Text%2A> propriedade, você precisa de mais uma coluna que o número de subitens. Para obter mais informações sobre como adicionar colunas, consulte [como: Adicionar colunas para o Windows Forms controle ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Chame o <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> método de coleção retornada pela <xref:System.Windows.Forms.ListViewItem.SubItems%2A> propriedade de um item. O exemplo de código a seguir define o nome do funcionário e o departamento para um item de lista.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Como: Adicionar e remover itens com o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como: Adicionar colunas para o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como: Exibir ícones para o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
