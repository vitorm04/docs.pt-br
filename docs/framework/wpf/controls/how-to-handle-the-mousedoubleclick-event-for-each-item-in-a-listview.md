---
title: Como identificar o evento MouseDoubleClick para cada item em um ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646106"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="d7f5f-102">Como identificar o evento MouseDoubleClick para cada item em um ListView</span><span class="sxs-lookup"><span data-stu-id="d7f5f-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="d7f5f-103">Para lidar com um evento <xref:System.Windows.Controls.ListView>para um item em um <xref:System.Windows.Controls.ListViewItem>, você precisa adicionar um manipulador de eventos a cada um .</span><span class="sxs-lookup"><span data-stu-id="d7f5f-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="d7f5f-104">Quando <xref:System.Windows.Controls.ListView> a está vinculada a uma fonte de dados, você não cria explicitamente um <xref:System.Windows.Controls.ListViewItem>, <xref:System.Windows.EventSetter> mas você pode <xref:System.Windows.Controls.ListViewItem>lidar com o evento para cada item adicionando um a um estilo de a .</span><span class="sxs-lookup"><span data-stu-id="d7f5f-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7f5f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7f5f-105">Example</span></span>  
 <span data-ttu-id="d7f5f-106">O exemplo a seguir <xref:System.Windows.Controls.ListView> cria um <xref:System.Windows.Style> limite de dados <xref:System.Windows.Controls.ListViewItem>e cria um para adicionar um manipulador de eventos a cada um .</span><span class="sxs-lookup"><span data-stu-id="d7f5f-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="d7f5f-107">O exemplo a <xref:System.Windows.Controls.Control.MouseDoubleClick> seguir lida com o evento.</span><span class="sxs-lookup"><span data-stu-id="d7f5f-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="d7f5f-108">Embora seja mais comum <xref:System.Windows.Controls.ListView> vincular a a uma fonte de dados, você <xref:System.Windows.Controls.ListViewItem> pode usar um <xref:System.Windows.Controls.ListView> estilo para adicionar um <xref:System.Windows.Controls.ListViewItem>manipulador de eventos a cada um em um não-data-bound, independentemente de você criar explicitamente um .</span><span class="sxs-lookup"><span data-stu-id="d7f5f-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="d7f5f-109">Para obter mais informações sobre controles <xref:System.Windows.Controls.ListViewItem> explicitamente e <xref:System.Windows.Controls.ItemsControl>implicitamente criados, consulte .</span><span class="sxs-lookup"><span data-stu-id="d7f5f-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f5f-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7f5f-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="d7f5f-111">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="d7f5f-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="d7f5f-112">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="d7f5f-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d7f5f-113">Vincule-se aos dados XML usando um XMLDataProvider e consultas XPath</span><span class="sxs-lookup"><span data-stu-id="d7f5f-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="d7f5f-114">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="d7f5f-114">ListView Overview</span></span>](listview-overview.md)
