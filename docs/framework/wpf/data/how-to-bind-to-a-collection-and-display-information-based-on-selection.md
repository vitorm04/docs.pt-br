---
title: 'Como: Associar a uma coleção e exibir informações com base na seleção'
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
ms.openlocfilehash: bb7d4c89e63982a3052857dcb50d04d36d9517dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314380"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="9cee3-102">Como: Associar a uma coleção e exibir informações com base na seleção</span><span class="sxs-lookup"><span data-stu-id="9cee3-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="9cee3-103">Em um cenário mestre / detalhes simples, você tem uma associação de dados <xref:System.Windows.Controls.ItemsControl> como um <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="9cee3-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="9cee3-104">Com base na seleção do usuário, se exibe mais informações sobre o item selecionado.</span><span class="sxs-lookup"><span data-stu-id="9cee3-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="9cee3-105">Este exemplo mostra como implementar este cenário.</span><span class="sxs-lookup"><span data-stu-id="9cee3-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cee3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9cee3-106">Example</span></span>  
 <span data-ttu-id="9cee3-107">Neste exemplo, `People` é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes.</span><span class="sxs-lookup"><span data-stu-id="9cee3-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="9cee3-108">Esta classe `Person` contém três propriedades: `FirstName`, `LastName` e `HomeTown`, todas de tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="9cee3-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="9cee3-109">O <xref:System.Windows.Controls.ContentControl> usa os seguintes <xref:System.Windows.DataTemplate> que define como as informações de um `Person` é apresentado:</span><span class="sxs-lookup"><span data-stu-id="9cee3-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="9cee3-110">A seguir temos uma imagem do que o exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="9cee3-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="9cee3-111">O <xref:System.Windows.Controls.ContentControl> mostra as outras propriedades da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="9cee3-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="9cee3-112">![Associando a uma coleção](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="9cee3-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="9cee3-113">As duas coisas a se observar neste exemplo são:</span><span class="sxs-lookup"><span data-stu-id="9cee3-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="9cee3-114">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.ContentControl> associar à mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="9cee3-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="9cee3-115">O <xref:System.Windows.Data.Binding.Path%2A> propriedades de ambas as associações não são especificadas porque ambos os controles estão associados ao objeto da coleção inteira.</span><span class="sxs-lookup"><span data-stu-id="9cee3-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="9cee3-116">Você deve definir a <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade para `true` para este trabalho.</span><span class="sxs-lookup"><span data-stu-id="9cee3-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="9cee3-117">A definição dessa propriedade garante que o item selecionado é sempre definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cee3-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="9cee3-118">Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém seus dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza a seleção e moeda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9cee3-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="9cee3-119">Observe que a classe `Person` substitui o método `ToString` da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="9cee3-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="9cee3-120">Por padrão, o <xref:System.Windows.Controls.ListBox> chamadas `ToString` e exibe uma representação de cadeia de caracteres de cada objeto na coleção associada.</span><span class="sxs-lookup"><span data-stu-id="9cee3-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="9cee3-121">É por isso que cada `Person` aparece como um primeiro nome no <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="9cee3-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="9cee3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cee3-122">See also</span></span>

- [<span data-ttu-id="9cee3-123">Usar o padrão de detalhes mestre com os dados hierárquicos</span><span class="sxs-lookup"><span data-stu-id="9cee3-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="9cee3-124">Usar o padrão de detalhes mestre com os dados XML hierárquicos</span><span class="sxs-lookup"><span data-stu-id="9cee3-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="9cee3-125">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="9cee3-125">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9cee3-126">Visão geral de modelagem dos dados</span><span class="sxs-lookup"><span data-stu-id="9cee3-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="9cee3-127">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="9cee3-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
