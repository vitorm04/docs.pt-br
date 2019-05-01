---
title: 'Como: Associar a uma enumeração'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021005"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="27648-102">Como: Associar a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="27648-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="27648-103">Este exemplo mostra como associar a uma enumeração associando ao método GetValues da enumeração.</span><span class="sxs-lookup"><span data-stu-id="27648-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27648-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27648-104">Example</span></span>  
 <span data-ttu-id="27648-105">No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de <xref:System.Windows.HorizontalAlignment> valores de enumeração por meio da vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="27648-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="27648-106">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> são vinculados, de modo que você pode alterar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor da propriedade da <xref:System.Windows.Controls.Button> selecionando um valor no <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="27648-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="27648-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27648-107">See also</span></span>

- [<span data-ttu-id="27648-108">Associar a um método</span><span class="sxs-lookup"><span data-stu-id="27648-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="27648-109">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="27648-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="27648-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="27648-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
