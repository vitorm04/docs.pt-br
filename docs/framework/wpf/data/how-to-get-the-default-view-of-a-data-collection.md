---
title: "Como obter a exibição padrão de uma coleta de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebb74e1db2e63269f70a13ef8520ab1383ecae08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="9a454-102">Como obter a exibição padrão de uma coleta de dados</span><span class="sxs-lookup"><span data-stu-id="9a454-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="9a454-103">As exibições permitem que a mesma coleta de dados seja visualizada de diferentes maneiras, dependendo dos critérios de classificação, filtragem ou agrupamento.</span><span class="sxs-lookup"><span data-stu-id="9a454-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="9a454-104">Cada coleta tem uma exibição padrão compartilhada, que é usada como a fonte de associação real quando uma associação especifica uma coleta como sua origem.</span><span class="sxs-lookup"><span data-stu-id="9a454-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="9a454-105">Este exemplo mostra como conseguir a exibição padrão de uma coleta.</span><span class="sxs-lookup"><span data-stu-id="9a454-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a454-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a454-106">Example</span></span>  
 <span data-ttu-id="9a454-107">Para criar a exibição, você precisa de uma referência de objeto para a coleta.</span><span class="sxs-lookup"><span data-stu-id="9a454-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="9a454-108">Esse objeto de dados pode ser obtido referenciando seu próprio objeto code-behind, obtendo o contexto de dados, obtendo uma propriedade da fonte de dados ou obtendo uma propriedade da associação.</span><span class="sxs-lookup"><span data-stu-id="9a454-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="9a454-109">Este exemplo mostra como obter o <xref:System.Windows.FrameworkElement.DataContext%2A> de um objeto de dados e use-lo diretamente para obter a coleção padrão exibir para esta coleção.</span><span class="sxs-lookup"><span data-stu-id="9a454-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="9a454-110">Neste exemplo, o elemento raiz é um <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9a454-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9a454-111">O <xref:System.Windows.FrameworkElement.DataContext%2A> é definido como *minhaFonteDeDados*, que se refere a um provedor de dados que é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de *ordem* objetos.</span><span class="sxs-lookup"><span data-stu-id="9a454-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="9a454-112">Como alternativa, você pode criar uma instância e vincular a sua própria exibição de coleção usando o <xref:System.Windows.Data.CollectionViewSource> classe.</span><span class="sxs-lookup"><span data-stu-id="9a454-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="9a454-113">Essa exibição de coleta é compartilhada somente por controles que se associam a ela diretamente.</span><span class="sxs-lookup"><span data-stu-id="9a454-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="9a454-114">Para um exemplo, consulte a seção Como Criar uma Exibição em [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9a454-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="9a454-115">Para obter exemplos da funcionalidade fornecida por uma exibição de coleta, consulte [Classificar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filtrar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md) e [Navegar pelos objetos em uma exibição de coleta de dados](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="9a454-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a454-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a454-116">See Also</span></span>  
 [<span data-ttu-id="9a454-117">Classificar e agrupar dados usando uma exibição em XAML</span><span class="sxs-lookup"><span data-stu-id="9a454-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="9a454-118">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="9a454-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
