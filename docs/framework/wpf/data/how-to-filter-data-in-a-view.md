---
title: Como filtrar dados em uma exibição
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: 55ec68e8918c9f7fbc9d3ac0062926cc03cb5e10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556647"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="241c7-102">Como filtrar dados em uma exibição</span><span class="sxs-lookup"><span data-stu-id="241c7-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="241c7-103">Este exemplo mostra como filtrar dados em uma exibição.</span><span class="sxs-lookup"><span data-stu-id="241c7-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="241c7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="241c7-104">Example</span></span>  
 <span data-ttu-id="241c7-105">Para criar um filtro, defina um método que forneça a lógica de filtragem.</span><span class="sxs-lookup"><span data-stu-id="241c7-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="241c7-106">O método é usado como um retorno de chamada e aceita um parâmetro do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="241c7-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="241c7-107">O método a seguir retorna todos os objetos `Order` com a propriedade `filled` definida como "Não", filtrando o resto dos objetos.</span><span class="sxs-lookup"><span data-stu-id="241c7-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="241c7-108">É possível aplicar o filtro, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="241c7-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="241c7-109">Neste exemplo, `myCollectionView` é um <xref:System.Windows.Data.ListCollectionView> objeto.</span><span class="sxs-lookup"><span data-stu-id="241c7-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="241c7-110">Para desfazer a filtragem, você pode definir o <xref:System.Windows.Data.CollectionView.Filter%2A> propriedade `null`:</span><span class="sxs-lookup"><span data-stu-id="241c7-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="241c7-111">Para obter informações sobre como criar ou obter uma exibição, consulte [Obter a exibição padrão de uma coleção de dados](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="241c7-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="241c7-112">Para o exemplo completo, consulte [Classificando e filtrando itens em um exemplo de exibição](http://go.microsoft.com/fwlink/?LinkID=160040).</span><span class="sxs-lookup"><span data-stu-id="241c7-112">For the complete example, see [Sorting and Filtering Items in a View Sample](http://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="241c7-113">Se o objeto de exibição for proveniente de um <xref:System.Windows.Data.CollectionViewSource> do objeto, você aplicar lógica de filtragem, definindo um manipulador de eventos para o <xref:System.Windows.Data.CollectionViewSource.Filter> evento.</span><span class="sxs-lookup"><span data-stu-id="241c7-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="241c7-114">No exemplo a seguir, `listingDataView` é uma instância de <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="241c7-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="241c7-115">O seguinte exemplo mostra a implementação do manipulador de eventos do filtro `ShowOnlyBargainsFilter` de exemplo.</span><span class="sxs-lookup"><span data-stu-id="241c7-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="241c7-116">Este manipulador de eventos usa o <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> propriedade filtrar `AuctionItem` objetos que têm um `CurrentPrice` de US $25 ou maior.</span><span class="sxs-lookup"><span data-stu-id="241c7-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="241c7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="241c7-117">See Also</span></span>  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [<span data-ttu-id="241c7-118">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="241c7-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="241c7-119">Classificar dados em uma exibição</span><span class="sxs-lookup"><span data-stu-id="241c7-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="241c7-120">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="241c7-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
