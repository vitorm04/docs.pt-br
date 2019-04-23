---
title: 'Como: Tratar o evento MouseDoubleClick para cada item em um ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 443e5c620ef5bf240d3e317f0234aac0b29b456f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145074"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Como: Tratar o evento MouseDoubleClick para cada item em um ListView
Para manipular um evento de um item em uma <xref:System.Windows.Controls.ListView>, você precisará adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>. Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não crie explicitamente um <xref:System.Windows.Controls.ListViewItem>, mas você pode manipular o evento para cada item adicionando um <xref:System.Windows.EventSetter> de um estilo de um <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma associação de dados <xref:System.Windows.Controls.ListView> e cria um <xref:System.Windows.Style> para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 A exemplo a seguir manipula o <xref:System.Windows.Controls.Control.MouseDoubleClick> eventos.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Embora seja mais comum para associar uma <xref:System.Windows.Controls.ListView> a uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> em uma não-associação de dados <xref:System.Windows.Controls.ListView> independentemente se você criar explicitamente um <xref:System.Windows.Controls.ListViewItem>.  Para obter mais informações sobre explícita e implicitamente criado <xref:System.Windows.Controls.ListViewItem> controles, consulte <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XmlElement>
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Estilo e modelagem](styling-and-templating.md)
- [Associar dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral de ListView](listview-overview.md)
