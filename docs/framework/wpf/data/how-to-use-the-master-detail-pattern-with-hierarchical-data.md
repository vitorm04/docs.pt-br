---
title: 'Como: Usar o padrão de detalhes mestre com os dados hierárquicos'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e0bbb24b07fdc1c362e2be43d69d189defbc27a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931880"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="6435f-102">Como: Usar o padrão de detalhes mestre com os dados hierárquicos</span><span class="sxs-lookup"><span data-stu-id="6435f-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="6435f-103">Este exemplo mostra como implementar o cenário de detalhes mestre.</span><span class="sxs-lookup"><span data-stu-id="6435f-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6435f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6435f-104">Example</span></span>  
 <span data-ttu-id="6435f-105">Neste exemplo, `LeagueList` é uma coleção de `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="6435f-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="6435f-106">Cada `League` tem um `Name` e uma coleção de `Divisions` e cada `Division` tem um nome e uma coleção de `Teams`.</span><span class="sxs-lookup"><span data-stu-id="6435f-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="6435f-107">Cada `Team` tem um nome de equipe.</span><span class="sxs-lookup"><span data-stu-id="6435f-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="6435f-108">Segue uma captura de tela do exemplo.</span><span class="sxs-lookup"><span data-stu-id="6435f-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="6435f-109">O `Divisions` <xref:System.Windows.Controls.ListBox> controla automaticamente as seleções na `Leagues` <xref:System.Windows.Controls.ListBox> e exibir os dados correspondentes.</span><span class="sxs-lookup"><span data-stu-id="6435f-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="6435f-110">O `Teams` <xref:System.Windows.Controls.ListBox> controla as seleções nos outros dois <xref:System.Windows.Controls.ListBox> controles.</span><span class="sxs-lookup"><span data-stu-id="6435f-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Captura de tela que mostra um mestre&#45;exemplo de cenário de detalhes.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="6435f-112">As duas coisas a se observar neste exemplo são:</span><span class="sxs-lookup"><span data-stu-id="6435f-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="6435f-113">Os três <xref:System.Windows.Controls.ListBox> controles se ligam à mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="6435f-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="6435f-114">Defina as <xref:System.Windows.Data.Binding.Path%2A> propriedade da associação para especificar o nível de dados que você deseja o <xref:System.Windows.Controls.ListBox> para exibir.</span><span class="sxs-lookup"><span data-stu-id="6435f-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="6435f-115">Você deve definir a <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade para `true` no <xref:System.Windows.Controls.ListBox> controles que a seleção estiver acompanhando.</span><span class="sxs-lookup"><span data-stu-id="6435f-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="6435f-116">A definição dessa propriedade garante que o item selecionado é sempre definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="6435f-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="6435f-117">Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém seus dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza a seleção e moeda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6435f-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="6435f-118">A técnica é um pouco diferente quando você usa dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6435f-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="6435f-119">Para ver um exemplo, confira [Usar o padrão de detalhes mestre com os dados XML hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="6435f-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6435f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6435f-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="6435f-121">Associar a uma coleção e exibir informações com base na seleção</span><span class="sxs-lookup"><span data-stu-id="6435f-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="6435f-122">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="6435f-122">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="6435f-123">Visão geral de modelagem dos dados</span><span class="sxs-lookup"><span data-stu-id="6435f-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="6435f-124">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="6435f-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
