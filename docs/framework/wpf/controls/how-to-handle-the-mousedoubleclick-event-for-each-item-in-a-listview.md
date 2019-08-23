---
title: 'Como: Tratar o evento MouseDoubleClick para cada item em um ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962070"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Como: Tratar o evento MouseDoubleClick para cada item em um ListView
Para manipular um evento para um item em um <xref:System.Windows.Controls.ListView>, você precisa adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>um. Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não cria explicitamente <xref:System.Windows.Controls.ListViewItem>um, mas pode manipular o evento para cada item adicionando um <xref:System.Windows.EventSetter> a um estilo de um <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma associação <xref:System.Windows.Controls.ListView> de dados e cria um <xref:System.Windows.Style> para adicionar um manipulador de eventos <xref:System.Windows.Controls.ListViewItem>a cada um.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 O exemplo a seguir trata <xref:System.Windows.Controls.Control.MouseDoubleClick> o evento.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Embora seja mais comum associar <xref:System.Windows.Controls.ListView> um a uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> um em um não associado <xref:System.Windows.Controls.ListView> a dados, independentemente de você criar explicitamente um <xref:System.Windows.Controls.ListViewItem>.  Para obter mais informações sobre controles criados <xref:System.Windows.Controls.ListViewItem> explicitamente e implicitamente, consulte. <xref:System.Windows.Controls.ItemsControl>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XmlElement>
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Estilo e modelagem](styling-and-templating.md)
- [Associar dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral de ListView](listview-overview.md)
