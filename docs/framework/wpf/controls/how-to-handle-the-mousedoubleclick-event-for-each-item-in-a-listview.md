---
title: 'Como: Tratar o evento MouseDoubleClick para cada item em um ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962070"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="cd7ba-102">Como: Tratar o evento MouseDoubleClick para cada item em um ListView</span><span class="sxs-lookup"><span data-stu-id="cd7ba-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="cd7ba-103">Para manipular um evento para um item em um <xref:System.Windows.Controls.ListView>, você precisa adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>um.</span><span class="sxs-lookup"><span data-stu-id="cd7ba-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="cd7ba-104">Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não cria explicitamente <xref:System.Windows.Controls.ListViewItem>um, mas pode manipular o evento para cada item adicionando um <xref:System.Windows.EventSetter> a um estilo de um <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="cd7ba-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd7ba-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7ba-105">Example</span></span>  
 <span data-ttu-id="cd7ba-106">O exemplo a seguir cria uma associação <xref:System.Windows.Controls.ListView> de dados e cria um <xref:System.Windows.Style> para adicionar um manipulador de eventos <xref:System.Windows.Controls.ListViewItem>a cada um.</span><span class="sxs-lookup"><span data-stu-id="cd7ba-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="cd7ba-107">O exemplo a seguir trata <xref:System.Windows.Controls.Control.MouseDoubleClick> o evento.</span><span class="sxs-lookup"><span data-stu-id="cd7ba-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="cd7ba-108">Embora seja mais comum associar <xref:System.Windows.Controls.ListView> um a uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> um em um não associado <xref:System.Windows.Controls.ListView> a dados, independentemente de você criar explicitamente um <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="cd7ba-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="cd7ba-109">Para obter mais informações sobre controles criados <xref:System.Windows.Controls.ListViewItem> explicitamente e implicitamente, consulte. <xref:System.Windows.Controls.ItemsControl></span><span class="sxs-lookup"><span data-stu-id="cd7ba-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7ba-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd7ba-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="cd7ba-111">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="cd7ba-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="cd7ba-112">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="cd7ba-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="cd7ba-113">Associar dados XML usando um XMLDataProvider e consultas XPath</span><span class="sxs-lookup"><span data-stu-id="cd7ba-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="cd7ba-114">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="cd7ba-114">ListView Overview</span></span>](listview-overview.md)
