---
title: Como identificar o evento MouseDoubleClick para cada item em um ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646106"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Como identificar o evento MouseDoubleClick para cada item em um ListView
Para lidar com um evento <xref:System.Windows.Controls.ListView>para um item em um <xref:System.Windows.Controls.ListViewItem>, você precisa adicionar um manipulador de eventos a cada um . Quando <xref:System.Windows.Controls.ListView> a está vinculada a uma fonte de dados, você não cria explicitamente um <xref:System.Windows.Controls.ListViewItem>, <xref:System.Windows.EventSetter> mas você pode <xref:System.Windows.Controls.ListViewItem>lidar com o evento para cada item adicionando um a um estilo de a .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir <xref:System.Windows.Controls.ListView> cria um <xref:System.Windows.Style> limite de dados <xref:System.Windows.Controls.ListViewItem>e cria um para adicionar um manipulador de eventos a cada um .  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 O exemplo a <xref:System.Windows.Controls.Control.MouseDoubleClick> seguir lida com o evento.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Embora seja mais comum <xref:System.Windows.Controls.ListView> vincular a a uma fonte de dados, você <xref:System.Windows.Controls.ListViewItem> pode usar um <xref:System.Windows.Controls.ListView> estilo para adicionar um <xref:System.Windows.Controls.ListViewItem>manipulador de eventos a cada um em um não-data-bound, independentemente de você criar explicitamente um .  Para obter mais informações sobre controles <xref:System.Windows.Controls.ListViewItem> explicitamente e <xref:System.Windows.Controls.ItemsControl>implicitamente criados, consulte .  
  
## <a name="see-also"></a>Confira também

- <xref:System.Xml.XmlElement>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vincule-se aos dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral de ListView](listview-overview.md)
