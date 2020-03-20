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
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Como agrupar itens em um controle ListView dos Windows Forms
Com o recurso de <xref:System.Windows.Forms.ListView> agrupamento do controle, você pode exibir conjuntos relacionados de itens em grupos. Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo. Você pode <xref:System.Windows.Forms.ListView> usar grupos para facilitar a navegação em grandes listas agrupando itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico. A imagem a seguir mostra alguns itens agrupados.  
  
 ![Captura de tela de grupos ímpares e até mesmo ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 Para habilitar o agrupamento, primeiro crie um ou mais grupos no designer ou de forma programática. Depois que um grupo for definido, você pode atribuir <xref:System.Windows.Forms.ListView> itens a grupos. Você também pode mover itens de um grupo para outro de forma programática.  
  
### <a name="to-add-groups"></a>Para adicionar grupos  
  
1. Use <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> o método <xref:System.Windows.Forms.ListView.Groups%2A> da coleção.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Para remover grupos  
  
1. Use <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método <xref:System.Windows.Forms.ListView.Groups%2A> ou da coleção.  
  
     O <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> método remove um único grupo; o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método remove todos os grupos da lista.  
  
    > [!NOTE]
    > A remoção de um grupo não remove os itens dentro desse grupo.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Para atribuir itens a grupos ou mover itens entre grupos  
  
1. Defina <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> a propriedade de itens individuais.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
