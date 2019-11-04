---
title: Como identificar o evento MouseDoubleClick para cada item em um ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460224"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Como identificar o evento MouseDoubleClick para cada item em um ListView
Para manipular um evento para um item em um <xref:System.Windows.Controls.ListView>, você precisa adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>. Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não cria explicitamente uma <xref:System.Windows.Controls.ListViewItem>, mas pode manipular o evento para cada item adicionando um <xref:System.Windows.EventSetter> a um estilo de um <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ListView> associado a dados e cria uma <xref:System.Windows.Style> para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 O exemplo a seguir manipula o evento <xref:System.Windows.Controls.Control.MouseDoubleClick>.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Embora seja mais comum associar um <xref:System.Windows.Controls.ListView> a uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> em um <xref:System.Windows.Controls.ListView> não associado a dados, independentemente de você criar explicitamente um <xref:System.Windows.Controls.ListViewItem>.  Para obter mais informações sobre controles de <xref:System.Windows.Controls.ListViewItem> criados de forma explícita e implícita, consulte <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XmlElement>
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Associar dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral de ListView](listview-overview.md)
