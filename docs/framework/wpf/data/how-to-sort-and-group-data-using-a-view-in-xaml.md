---
title: Como organizar e agrupar dados usando uma exibição em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460120"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="b36a4-102">Como organizar e agrupar dados usando uma exibição em XAML</span><span class="sxs-lookup"><span data-stu-id="b36a4-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="b36a4-103">Este exemplo mostra como criar uma exibição de uma coleção de dados em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b36a4-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="b36a4-104">Modos de exibição permitem as funcionalidades de agrupamento, classificação, filtragem e a noção de um item atual.</span><span class="sxs-lookup"><span data-stu-id="b36a4-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b36a4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b36a4-105">Example</span></span>  
 <span data-ttu-id="b36a4-106">No exemplo a seguir, o recurso estático chamado *places* é definido como uma coleção de objetos *Place*, na qual cada objeto *Place* consiste em um nome de cidade e o estado.</span><span class="sxs-lookup"><span data-stu-id="b36a4-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="b36a4-107">O prefixo *src* é mapeado para o namespace no qual a fonte de dados *Places* está definida.</span><span class="sxs-lookup"><span data-stu-id="b36a4-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="b36a4-108">O prefixo *scm* mapeia para `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` e *dat* mapeia para `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="b36a4-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="b36a4-109">O exemplo a seguir cria uma exibição da coleta de dados classificada por nome de cidade e agrupada por estado.</span><span class="sxs-lookup"><span data-stu-id="b36a4-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="b36a4-110">Em seguida, o modo de exibição, pode ser uma origem da associação, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b36a4-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="b36a4-111">Para associações a dados XML definidos em um recurso <xref:System.Windows.Data.XmlDataProvider>, preceda o nome XML com um símbolo @.</span><span class="sxs-lookup"><span data-stu-id="b36a4-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="b36a4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b36a4-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="b36a4-113">Obter a exibição padrão de uma coleta de dados</span><span class="sxs-lookup"><span data-stu-id="b36a4-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="b36a4-114">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="b36a4-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="b36a4-115">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="b36a4-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
