---
title: Como exibir conteúdo de ListView usando um GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554045"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="303c1-102">Como exibir conteúdo de ListView usando um GridView</span><span class="sxs-lookup"><span data-stu-id="303c1-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="303c1-103">Este exemplo mostra como definir um <xref:System.Windows.Controls.GridView> modo de exibição para um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="303c1-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="303c1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="303c1-104">Example</span></span>  
 <span data-ttu-id="303c1-105">Você pode definir o modo de exibição de um <xref:System.Windows.Controls.GridView> especificando <xref:System.Windows.Controls.GridViewColumn> objetos.</span><span class="sxs-lookup"><span data-stu-id="303c1-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="303c1-106">O exemplo a seguir mostra como definir <xref:System.Windows.Controls.GridViewColumn> objetos que associam ao conteúdo especificado para o <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="303c1-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="303c1-107">Isso <xref:System.Windows.Controls.GridView> exemplo especifica três <xref:System.Windows.Controls.GridViewColumn> objetos que são mapeados para o `FirstName`, `LastName`, e `EmployeeNumber` campos do `EmployeeInfoDataSource` que é definido como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> do <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="303c1-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="303c1-108">A ilustração a seguir mostra como esse exemplo é exibido.</span><span class="sxs-lookup"><span data-stu-id="303c1-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="303c1-109">![ListView com saída de GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="303c1-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303c1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="303c1-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="303c1-111">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="303c1-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="303c1-112">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="303c1-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="303c1-113">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="303c1-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
