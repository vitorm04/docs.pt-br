---
title: 'Como: Exibir conteúdo de ListView usando um GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 1066869c80bf5bd87d656bcb4994c188ee0e8efc
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185604"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="83877-102">Como: Exibir conteúdo de ListView usando um GridView</span><span class="sxs-lookup"><span data-stu-id="83877-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="83877-103">Este exemplo mostra como definir um <xref:System.Windows.Controls.GridView> modo de exibição para um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="83877-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83877-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83877-104">Example</span></span>  
 <span data-ttu-id="83877-105">Você pode definir o modo de exibição de um <xref:System.Windows.Controls.GridView> especificando <xref:System.Windows.Controls.GridViewColumn> objetos.</span><span class="sxs-lookup"><span data-stu-id="83877-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="83877-106">O exemplo a seguir mostra como definir <xref:System.Windows.Controls.GridViewColumn> objetos que ligam para o conteúdo de dados que é especificado para o <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="83877-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="83877-107">Isso <xref:System.Windows.Controls.GridView> exemplo especifica três <xref:System.Windows.Controls.GridViewColumn> objetos que são mapeados para o `FirstName`, `LastName`, e `EmployeeNumber` campos do `EmployeeInfoDataSource` que é definido como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> do <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="83877-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="83877-108">A ilustração a seguir mostra como esse exemplo é exibido.</span><span class="sxs-lookup"><span data-stu-id="83877-108">The following illustration shows how this example appears.</span></span>  
  
 ![Captura de tela que mostra um ListView com saída de GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a><span data-ttu-id="83877-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83877-110">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="83877-111">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="83877-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="83877-112">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="83877-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="83877-113">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="83877-113">How-to Topics</span></span>](listview-how-to-topics.md)
