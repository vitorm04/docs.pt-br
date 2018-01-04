---
title: Como identificar o evento MouseDoubleClick para cada item em um ListView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fef9655ab95328e027a303df57c3359a7676eac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="06549-102">Como identificar o evento MouseDoubleClick para cada item em um ListView</span><span class="sxs-lookup"><span data-stu-id="06549-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="06549-103">Para manipular um evento de um item em uma <xref:System.Windows.Controls.ListView>, você precisa adicionar um manipulador de eventos para cada <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="06549-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="06549-104">Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não criar explicitamente uma <xref:System.Windows.Controls.ListViewItem>, mas você pode manipular o evento para cada item, adicionando um <xref:System.Windows.EventSetter> de um estilo de um <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="06549-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06549-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06549-105">Example</span></span>  
 <span data-ttu-id="06549-106">O exemplo a seguir cria uma associação de dados <xref:System.Windows.Controls.ListView> e cria um <xref:System.Windows.Style> para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="06549-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="06549-107">A exemplo a seguir trata o <xref:System.Windows.Controls.Control.MouseDoubleClick> evento.</span><span class="sxs-lookup"><span data-stu-id="06549-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="06549-108">Embora seja mais comum para associar um <xref:System.Windows.Controls.ListView> para uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> em uma não-associados a dados <xref:System.Windows.Controls.ListView> independentemente se você criar explicitamente uma <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="06549-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="06549-109">Para obter mais informações sobre explícita e implicitamente criado <xref:System.Windows.Controls.ListViewItem> controles, consulte <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="06549-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06549-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06549-110">See Also</span></span>  
 <xref:System.Xml.XmlElement>  
 [<span data-ttu-id="06549-111">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="06549-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="06549-112">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="06549-112">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="06549-113">Associar dados XML usando um XMLDataProvider e consultas XPath</span><span class="sxs-lookup"><span data-stu-id="06549-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="06549-114">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="06549-114">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
