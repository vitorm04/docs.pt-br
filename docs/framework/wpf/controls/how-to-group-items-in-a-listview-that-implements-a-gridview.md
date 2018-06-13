---
title: Como agrupar itens em um ListView que implemente um GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551902"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Como agrupar itens em um ListView que implemente um GridView
Este exemplo mostra como exibir grupos de itens de <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="example"></a>Exemplo  
 Para exibir os grupos de itens em uma <xref:System.Windows.Controls.ListView>, definir um <xref:System.Windows.Data.CollectionViewSource>. A exemplo a seguir mostra um <xref:System.Windows.Data.CollectionViewSource> que grupos de itens de dados de acordo com o valor da `Catalog` campo de dados.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 O exemplo a seguir define o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.ListView> para o <xref:System.Windows.Data.CollectionViewSource> que define o exemplo anterior. O exemplo também define um <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> que implementa um <xref:System.Windows.Controls.Expander> controle.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
