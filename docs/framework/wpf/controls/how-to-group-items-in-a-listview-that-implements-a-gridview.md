---
title: 'Como: Agrupar itens em um ListView que implemente um GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 3989f0fcdaf2e3d3003aca9feb27cbf02f949389
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364465"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Como: Agrupar itens em um ListView que implemente um GridView
Este exemplo mostra como exibir grupos de itens na <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="example"></a>Exemplo  
 Para exibir os grupos de itens em uma <xref:System.Windows.Controls.ListView>, defina um <xref:System.Windows.Data.CollectionViewSource>. A exemplo a seguir mostra uma <xref:System.Windows.Data.CollectionViewSource> que agrupa itens de dados de acordo com o valor da `Catalog` campo de dados.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 O exemplo a seguir define o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.ListView> para o <xref:System.Windows.Data.CollectionViewSource> que define o exemplo anterior. O exemplo também define um <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> que implementa um <xref:System.Windows.Controls.Expander> controle.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
- [Visão geral de GridView](gridview-overview.md)
