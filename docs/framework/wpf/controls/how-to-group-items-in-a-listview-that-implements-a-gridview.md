---
title: 'Como: Agrupar itens em um ListView que implemente um GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: b3dd6891976a942b299c87fca25e430e9ee59a51
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177665"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="cddca-102">Como: Agrupar itens em um ListView que implemente um GridView</span><span class="sxs-lookup"><span data-stu-id="cddca-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="cddca-103">Este exemplo mostra como exibir grupos de itens na <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="cddca-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cddca-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cddca-104">Example</span></span>  
 <span data-ttu-id="cddca-105">Para exibir os grupos de itens em uma <xref:System.Windows.Controls.ListView>, defina um <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="cddca-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="cddca-106">A exemplo a seguir mostra uma <xref:System.Windows.Data.CollectionViewSource> que agrupa itens de dados de acordo com o valor da `Catalog` campo de dados.</span><span class="sxs-lookup"><span data-stu-id="cddca-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="cddca-107">O exemplo a seguir define o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.ListView> para o <xref:System.Windows.Data.CollectionViewSource> que define o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="cddca-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="cddca-108">O exemplo também define um <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> que implementa um <xref:System.Windows.Controls.Expander> controle.</span><span class="sxs-lookup"><span data-stu-id="cddca-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="cddca-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cddca-109">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="cddca-110">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="cddca-110">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="cddca-111">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="cddca-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="cddca-112">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="cddca-112">GridView Overview</span></span>](gridview-overview.md)
