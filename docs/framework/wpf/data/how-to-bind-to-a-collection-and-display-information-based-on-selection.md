---
title: Como associar a uma coleção e exibir informações com base na seleção
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459151"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="a75e1-102">Como associar a uma coleção e exibir informações com base na seleção</span><span class="sxs-lookup"><span data-stu-id="a75e1-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="a75e1-103">Em um cenário de detalhes mestre simples, você tem um <xref:System.Windows.Controls.ItemsControl> associado a dados, como um <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="a75e1-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="a75e1-104">Com base na seleção do usuário, se exibe mais informações sobre o item selecionado.</span><span class="sxs-lookup"><span data-stu-id="a75e1-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="a75e1-105">Este exemplo mostra como implementar este cenário.</span><span class="sxs-lookup"><span data-stu-id="a75e1-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a75e1-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a75e1-106">Example</span></span>  
 <span data-ttu-id="a75e1-107">Neste exemplo, `People` é uma <xref:System.Collections.ObjectModel.ObservableCollection%601> de classes de `Person`.</span><span class="sxs-lookup"><span data-stu-id="a75e1-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="a75e1-108">Esta classe `Person` contém três propriedades: `FirstName`, `LastName` e `HomeTown`, todas de tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="a75e1-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="a75e1-109">O <xref:System.Windows.Controls.ContentControl> usa as seguintes <xref:System.Windows.DataTemplate> que definem como as informações de um `Person` são apresentadas:</span><span class="sxs-lookup"><span data-stu-id="a75e1-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="a75e1-110">A seguir temos uma imagem do que o exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="a75e1-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="a75e1-111">O <xref:System.Windows.Controls.ContentControl> mostra as outras propriedades da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="a75e1-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="a75e1-112">![Associação a uma coleção](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="a75e1-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="a75e1-113">As duas coisas a se observar neste exemplo são:</span><span class="sxs-lookup"><span data-stu-id="a75e1-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="a75e1-114">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.ContentControl> se associam à mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="a75e1-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="a75e1-115">As propriedades <xref:System.Windows.Data.Binding.Path%2A> de ambas as associações não são especificadas porque ambos os controles estão sendo vinculados a todo o objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="a75e1-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="a75e1-116">Você deve definir a propriedade <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> como `true` para que isso funcione.</span><span class="sxs-lookup"><span data-stu-id="a75e1-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="a75e1-117">Definir essa propriedade garante que o item selecionado sempre seja definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="a75e1-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="a75e1-118">Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza a seleção e a moeda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a75e1-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="a75e1-119">Observe que a classe `Person` substitui o método `ToString` da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="a75e1-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="a75e1-120">Por padrão, o <xref:System.Windows.Controls.ListBox> chama `ToString` e exibe uma representação de cadeia de caracteres de cada objeto na coleção associada.</span><span class="sxs-lookup"><span data-stu-id="a75e1-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="a75e1-121">É por isso que cada `Person` aparece como um primeiro nome na <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="a75e1-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="a75e1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a75e1-122">See also</span></span>

- [<span data-ttu-id="a75e1-123">Usar o padrão de detalhes mestre com os dados hierárquicos</span><span class="sxs-lookup"><span data-stu-id="a75e1-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="a75e1-124">Usar o padrão de detalhes mestre com os dados XML hierárquicos</span><span class="sxs-lookup"><span data-stu-id="a75e1-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="a75e1-125">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="a75e1-125">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a75e1-126">Visão geral de modelagem dos dados</span><span class="sxs-lookup"><span data-stu-id="a75e1-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="a75e1-127">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="a75e1-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
