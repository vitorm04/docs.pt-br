---
title: Como associar a uma coleção e exibir informações com base na seleção
description: Siga este exemplo para descobrir como associar a uma coleção e exibir informações com base na seleção no Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619605"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="6be2d-103">Como associar a uma coleção e exibir informações com base na seleção</span><span class="sxs-lookup"><span data-stu-id="6be2d-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="6be2d-104">Em um cenário de detalhes mestre simples, você tem uma associação de dados, como <xref:System.Windows.Controls.ItemsControl> um <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="6be2d-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="6be2d-105">Com base na seleção do usuário, se exibe mais informações sobre o item selecionado.</span><span class="sxs-lookup"><span data-stu-id="6be2d-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="6be2d-106">Este exemplo mostra como implementar este cenário.</span><span class="sxs-lookup"><span data-stu-id="6be2d-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6be2d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6be2d-107">Example</span></span>  
 <span data-ttu-id="6be2d-108">Neste exemplo, `People` é uma <xref:System.Collections.ObjectModel.ObservableCollection%601> das `Person` classes.</span><span class="sxs-lookup"><span data-stu-id="6be2d-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="6be2d-109">Esta classe `Person` contém três propriedades: `FirstName`, `LastName` e `HomeTown`, todas de tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="6be2d-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="6be2d-110">O <xref:System.Windows.Controls.ContentControl> usa o seguinte <xref:System.Windows.DataTemplate> que define como as informações de um `Person` são apresentadas:</span><span class="sxs-lookup"><span data-stu-id="6be2d-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="6be2d-111">A seguir temos uma imagem do que o exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="6be2d-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="6be2d-112">O <xref:System.Windows.Controls.ContentControl> mostra as outras propriedades da pessoa selecionada.</span><span class="sxs-lookup"><span data-stu-id="6be2d-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="6be2d-113">![Associação a uma coleção](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="6be2d-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="6be2d-114">Os dois aspectos a observar neste exemplo são:</span><span class="sxs-lookup"><span data-stu-id="6be2d-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="6be2d-115">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.ContentControl> associado à mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="6be2d-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="6be2d-116">As <xref:System.Windows.Data.Binding.Path%2A> Propriedades de ambas as associações não são especificadas porque ambos os controles estão sendo vinculados a todo o objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="6be2d-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="6be2d-117">Você deve definir a <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade como para `true` que isso funcione.</span><span class="sxs-lookup"><span data-stu-id="6be2d-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="6be2d-118">Definir essa propriedade garante que o item selecionado sempre seja definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="6be2d-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="6be2d-119">Como alternativa, se o <xref:System.Windows.Controls.ListBox> obter dados de um <xref:System.Windows.Data.CollectionViewSource> , ele sincronizará a seleção e a moeda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6be2d-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="6be2d-120">Observe que a classe `Person` substitui o método `ToString` da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="6be2d-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="6be2d-121">Por padrão, o <xref:System.Windows.Controls.ListBox> chama `ToString` e exibe uma representação de cadeia de caracteres de cada objeto na coleção associada.</span><span class="sxs-lookup"><span data-stu-id="6be2d-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="6be2d-122">É por isso que cada `Person` um aparece como um primeiro nome no <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="6be2d-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="6be2d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6be2d-123">See also</span></span>

- [<span data-ttu-id="6be2d-124">Usar o padrão de detalhes mestre com dados hierárquicos</span><span class="sxs-lookup"><span data-stu-id="6be2d-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="6be2d-125">Usar o padrão de detalhes mestre com dados XML hierárquicos</span><span class="sxs-lookup"><span data-stu-id="6be2d-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="6be2d-126">Visão geral da ligação de dados</span><span class="sxs-lookup"><span data-stu-id="6be2d-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6be2d-127">Visão geral de modelagem dos dados</span><span class="sxs-lookup"><span data-stu-id="6be2d-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="6be2d-128">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="6be2d-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
