---
title: 'Como: Associar aos resultados de uma consulta LINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 5464ee9c59a7c99a83774a7535b9b3c422c1d2e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185894"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="780c6-102">Como: Associar aos resultados de uma consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="780c6-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="780c6-103">Este exemplo demonstra como executar uma consulta LINQ e associar aos resultados.</span><span class="sxs-lookup"><span data-stu-id="780c6-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="780c6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="780c6-104">Example</span></span>  
 <span data-ttu-id="780c6-105">O seguinte exemplo cria duas caixas de listagem.</span><span class="sxs-lookup"><span data-stu-id="780c6-105">The following example creates two list boxes.</span></span> <span data-ttu-id="780c6-106">A primeira caixa de listagem contém três itens de lista.</span><span class="sxs-lookup"><span data-stu-id="780c6-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="780c6-107">Selecionar um item na primeira caixa de listagem invoca o manipulador de eventos a seguir.</span><span class="sxs-lookup"><span data-stu-id="780c6-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="780c6-108">Neste exemplo, `Tasks` é uma coleção de objetos `Task`.</span><span class="sxs-lookup"><span data-stu-id="780c6-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="780c6-109">A classe `Task` tem uma propriedade chamada `Priority`.</span><span class="sxs-lookup"><span data-stu-id="780c6-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="780c6-110">Esse manipulador de eventos executa uma consulta LINQ que retorna a coleção de `Task` objetos que têm o valor de prioridade selecionado e, em seguida, define que, como o <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="780c6-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="780c6-111">A segunda caixa de listagem associado a essa coleção porque seu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> valor é definido como `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="780c6-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="780c6-112">Como resultado, ele exibe a coleção retornada (com base nas `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="780c6-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780c6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="780c6-113">See also</span></span>

- [<span data-ttu-id="780c6-114">Disponibilizar dados para associação em XAML</span><span class="sxs-lookup"><span data-stu-id="780c6-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="780c6-115">Associar a uma coleção e exibir informações com base na seleção</span><span class="sxs-lookup"><span data-stu-id="780c6-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="780c6-116">Novidades no WPF versão 4.5</span><span class="sxs-lookup"><span data-stu-id="780c6-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="780c6-117">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="780c6-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="780c6-118">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="780c6-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
