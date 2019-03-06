---
title: 'Como: Melhorar o desempenho de um TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: d04d5997e6f02a4227704b668fdf19324ea20f26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364730"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="30007-102">Como: Melhorar o desempenho de um TreeView</span><span class="sxs-lookup"><span data-stu-id="30007-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="30007-103">Se um <xref:System.Windows.Controls.TreeView> contém muitos itens, a quantidade de tempo que leva para carregar pode causar um atraso significativo na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="30007-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="30007-104">Você pode melhorar o tempo de carregamento, definindo o `VirtualizingStackPanel.IsVirtualizing` anexado à propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="30007-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="30007-105">A interface do usuário também pode ser lento para reagir quando o usuário rola a <xref:System.Windows.Controls.TreeView> usando a roda do mouse ou arrastando o controle de posição de uma barra de rolagem.</span><span class="sxs-lookup"><span data-stu-id="30007-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="30007-106">Você pode melhorar o desempenho do <xref:System.Windows.Controls.TreeView> quando o usuário rola, definindo o `VirtualizingStackPanel.VirtualizationMode` anexado à propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30007-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30007-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30007-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="30007-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="30007-108">Description</span></span>  
<span data-ttu-id="30007-109">O exemplo a seguir cria uma <xref:System.Windows.Controls.TreeView> que define o `VirtualizingStackPanel.IsVirtualizing` propriedade anexada como true e o `VirtualizingStackPanel.VirtualizationMode` anexado à propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> para otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="30007-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="30007-110">Código</span><span class="sxs-lookup"><span data-stu-id="30007-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="30007-111">O exemplo a seguir mostra os dados que o exemplo anterior usa.</span><span class="sxs-lookup"><span data-stu-id="30007-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="30007-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30007-112">See also</span></span>
- [<span data-ttu-id="30007-113">Controles</span><span class="sxs-lookup"><span data-stu-id="30007-113">Controls</span></span>](../advanced/optimizing-performance-controls.md)
