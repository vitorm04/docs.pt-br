---
title: 'Como: Associar a uma enumeração'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: df26d2bd08e4691837f739a4e71d3bb1a25bdd00
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377788"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="c7c4d-102">Como: Associar a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c7c4d-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="c7c4d-103">Este exemplo mostra como associar a uma enumeração associando ao método GetValues da enumeração.</span><span class="sxs-lookup"><span data-stu-id="c7c4d-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7c4d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7c4d-104">Example</span></span>  
 <span data-ttu-id="c7c4d-105">No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de <xref:System.Windows.HorizontalAlignment> valores de enumeração por meio da vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="c7c4d-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="c7c4d-106">O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> são vinculados, de modo que você pode alterar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor da propriedade da <xref:System.Windows.Controls.Button> selecionando um valor no <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="c7c4d-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="c7c4d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7c4d-107">See also</span></span>
- [<span data-ttu-id="c7c4d-108">Associar a um método</span><span class="sxs-lookup"><span data-stu-id="c7c4d-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="c7c4d-109">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="c7c4d-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="c7c4d-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="c7c4d-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
