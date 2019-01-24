---
title: 'Como: Identificar o evento MouseDoubleClick para cada item em um ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 2a201eefba6e2623cfd7f733b85e271ce1c4e177
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576044"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Como: Identificar o evento MouseDoubleClick para cada item em um ListView
Para manipular um evento de um item em uma <xref:System.Windows.Controls.ListView>, você precisará adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>. Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não crie explicitamente um <xref:System.Windows.Controls.ListViewItem>, mas você pode manipular o evento para cada item adicionando um <xref:System.Windows.EventSetter> de um estilo de um <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma associação de dados <xref:System.Windows.Controls.ListView> e cria um <xref:System.Windows.Style> para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 A exemplo a seguir manipula o <xref:System.Windows.Controls.Control.MouseDoubleClick> eventos.  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Embora seja mais comum para associar uma <xref:System.Windows.Controls.ListView> a uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> em uma não-associação de dados <xref:System.Windows.Controls.ListView> independentemente se você criar explicitamente um <xref:System.Windows.Controls.ListViewItem>.  Para obter mais informações sobre explícita e implicitamente criado <xref:System.Windows.Controls.ListViewItem> controles, consulte <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Xml.XmlElement>
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Associar dados XML usando um XMLDataProvider e consultas XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)
