---
title: Exibir subitens em colunas com controle ListView
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
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745549"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Como exibir subitens em colunas com o controle ListView dos Windows Forms
O controle de <xref:System.Windows.Forms.ListView> de Windows Forms pode exibir texto ou subitens adicionais para cada item na exibição de detalhes. A primeira coluna exibe o texto do item, por exemplo, o número de um funcionário. A segunda, terceira e colunas seguintes exibem o primeiro, segundo e subitens associados seguintes.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Para adicionar subitens a um item de lista  
  
1. Adicione as colunas necessárias. Como a primeira coluna exibirá a propriedade <xref:System.Windows.Forms.ListView.Text%2A> do item, você precisará de mais uma coluna do que há subitens. Para obter mais informações sobre como adicionar colunas, veja [Como adicionar colunas ao controle ListView dos Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Chame o método <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> da coleção retornada pela propriedade <xref:System.Windows.Forms.ListViewItem.SubItems%2A> de um item. O exemplo de código a seguir define o nome do funcionário e o departamento para um item de lista.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Veja também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como adicionar colunas ao controle ListView do Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como Exibir Ícones do Controle ListView dos Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
