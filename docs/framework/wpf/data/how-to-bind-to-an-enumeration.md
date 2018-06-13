---
title: Como associar a uma enumeração
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 921f15a32eeb5ccb20e879466fcfee3233bbd29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554941"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="27cbd-102">Como associar a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="27cbd-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="27cbd-103">Este exemplo mostra como associar a uma enumeração associando ao método GetValues da enumeração.</span><span class="sxs-lookup"><span data-stu-id="27cbd-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27cbd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27cbd-104">Example</span></span>  
 <span data-ttu-id="27cbd-105">No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de <xref:System.Windows.HorizontalAlignment> valores de enumeração por meio de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="27cbd-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="27cbd-106">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> associados, de modo que você pode alterar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor da propriedade a <xref:System.Windows.Controls.Button> selecionando um valor na <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="27cbd-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="27cbd-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27cbd-107">See Also</span></span>  
 [<span data-ttu-id="27cbd-108">Associar a um método</span><span class="sxs-lookup"><span data-stu-id="27cbd-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [<span data-ttu-id="27cbd-109">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="27cbd-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="27cbd-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="27cbd-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
