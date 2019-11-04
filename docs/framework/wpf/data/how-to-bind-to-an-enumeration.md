---
title: Como associar a uma enumeração
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454446"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="c77d7-102">Como associar a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c77d7-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="c77d7-103">Este exemplo mostra como associar a uma enumeração ligando-se ao método GetValues da enumeração.</span><span class="sxs-lookup"><span data-stu-id="c77d7-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c77d7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c77d7-104">Example</span></span>  
 <span data-ttu-id="c77d7-105">No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de valores de enumeração de <xref:System.Windows.HorizontalAlignment> por meio da vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="c77d7-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="c77d7-106">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> são associados, de modo que você pode alterar o valor da propriedade <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> da <xref:System.Windows.Controls.Button> selecionando um valor na <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="c77d7-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="c77d7-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c77d7-107">See also</span></span>

- [<span data-ttu-id="c77d7-108">Associar a um método</span><span class="sxs-lookup"><span data-stu-id="c77d7-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="c77d7-109">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="c77d7-109">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c77d7-110">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="c77d7-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
