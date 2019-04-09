---
title: 'Como: Navegar pelos objetos em um CollectionView de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 1507ab4db0c91b670d8bca754f6fd67d887c7041
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138171"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="8ea69-102">Como: Navegar pelos objetos em um CollectionView de dados</span><span class="sxs-lookup"><span data-stu-id="8ea69-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="8ea69-103">As exibições permitem que a mesma coleção de dados seja visualizada de diferentes maneiras, dependendo da classificação, filtragem ou agrupamento.</span><span class="sxs-lookup"><span data-stu-id="8ea69-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="8ea69-104">Os modos de exibição também fornecem um conceito de ponteiro de registro atual e permitem a movimentação do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8ea69-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="8ea69-105">Este exemplo mostra como obter o objeto atual, bem como navegar pelos objetos em uma coleção de dados usando a funcionalidade fornecida no <xref:System.Windows.Data.CollectionView> classe.</span><span class="sxs-lookup"><span data-stu-id="8ea69-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ea69-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ea69-106">Example</span></span>  
 <span data-ttu-id="8ea69-107">Neste exemplo, `myCollectionView` é um <xref:System.Windows.Data.CollectionView> objeto que é um modo de exibição sobre uma coleção associada.</span><span class="sxs-lookup"><span data-stu-id="8ea69-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="8ea69-108">No exemplo a seguir, o `OnButton` é um manipulador de eventos para os botões `Previous` e `Next` em um aplicativo, que são botões que permitem que o usuário navegue pela coleção de dados.</span><span class="sxs-lookup"><span data-stu-id="8ea69-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="8ea69-109">Observe que o <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> e <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> propriedades de relatório se o ponteiro de registro atual chegou até o início e o final da lista respectivamente assim que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> e <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> podem ser chamados adequadamente.</span><span class="sxs-lookup"><span data-stu-id="8ea69-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="8ea69-110">O <xref:System.Windows.Data.CollectionView.CurrentItem%2A> propriedade do modo de exibição é convertida como um `Order` para retornar o item atual da ordem na coleção.</span><span class="sxs-lookup"><span data-stu-id="8ea69-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="8ea69-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ea69-111">See also</span></span>

- [<span data-ttu-id="8ea69-112">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="8ea69-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="8ea69-113">Classificar dados em uma exibição</span><span class="sxs-lookup"><span data-stu-id="8ea69-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="8ea69-114">Filtrar dados em uma exibição</span><span class="sxs-lookup"><span data-stu-id="8ea69-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="8ea69-115">Classificar e agrupar dados usando uma exibição em XAML</span><span class="sxs-lookup"><span data-stu-id="8ea69-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="8ea69-116">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="8ea69-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
