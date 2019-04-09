---
title: 'Como: Agrupar itens em um controle ListView do Windows Forms'
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
ms.openlocfilehash: 3a070db6c580f0f3798e52b1afbe0ee36947aeb1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091532"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Como: Agrupar itens em um controle ListView do Windows Forms
Com o recurso de agrupamento a <xref:System.Windows.Forms.ListView> controle, você pode exibir conjuntos de itens relacionados em grupos. Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo. Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação em listas grandes agrupando itens em ordem alfabética, por data, ou por qualquer outro agrupamento lógico. A imagem a seguir mostra alguns itens agrupados.  
  
 ![Grupos de ListView](./media/listviewgroups.gif "ListViewGroups")  
Itens agrupados de ListView  
  
 Para habilitar o agrupamento, primeiro crie um ou mais grupos no designer ou de forma programática. Após a definição de um grupo, você pode atribuir <xref:System.Windows.Forms.ListView> itens aos grupos. Você também pode mover itens de um grupo para outro de forma programática.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> os grupos estão disponíveis apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método. Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Para adicionar grupos  
  
1.  Use o <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> método da <xref:System.Windows.Forms.ListView.Groups%2A> coleção.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Para remover grupos  
  
1.  Use o <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método o <xref:System.Windows.Forms.ListView.Groups%2A> coleção.  
  
     O <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> método Remove um grupo único; o <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> método Remove todos os grupos da lista.  
  
    > [!NOTE]
    >  A remoção de um grupo não remove os itens dentro desse grupo.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Para atribuir itens a grupos ou mover itens entre grupos  
  
1.  Defina o <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriedade dos itens individuais.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como: Adicionar e remover itens com o controle ListView do Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
