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
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="3072b-102">Como agrupar itens em um ListView que implemente um GridView</span><span class="sxs-lookup"><span data-stu-id="3072b-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="3072b-103">Este exemplo mostra como exibir grupos de itens de <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="3072b-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3072b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3072b-104">Example</span></span>  
 <span data-ttu-id="3072b-105">Para exibir os grupos de itens em uma <xref:System.Windows.Controls.ListView>, definir um <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="3072b-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="3072b-106">A exemplo a seguir mostra um <xref:System.Windows.Data.CollectionViewSource> que grupos de itens de dados de acordo com o valor da `Catalog` campo de dados.</span><span class="sxs-lookup"><span data-stu-id="3072b-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="3072b-107">O exemplo a seguir define o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.ListView> para o <xref:System.Windows.Data.CollectionViewSource> que define o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3072b-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="3072b-108">O exemplo também define um <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> que implementa um <xref:System.Windows.Controls.Expander> controle.</span><span class="sxs-lookup"><span data-stu-id="3072b-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="3072b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3072b-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="3072b-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="3072b-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="3072b-111">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="3072b-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="3072b-112">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="3072b-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
