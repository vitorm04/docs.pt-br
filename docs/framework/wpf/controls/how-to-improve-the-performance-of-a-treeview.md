---
title: Como melhorar o desempenho de um TreeView
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
helpviewer_keywords: TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 209f2c5645758aba4d1e10fc36fe773faa975e6b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="1b888-102">Como melhorar o desempenho de um TreeView</span><span class="sxs-lookup"><span data-stu-id="1b888-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="1b888-103">Se um <xref:System.Windows.Controls.TreeView> contém muitos itens, a quantidade de tempo que leva para carregar pode causar um atraso significativo na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1b888-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="1b888-104">Você pode melhorar o tempo de carregamento, definindo o `VirtualizingStackPanel.IsVirtualizing` anexado propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="1b888-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="1b888-105">A interface do usuário também pode ser lento para reagir quando um usuário rolar a <xref:System.Windows.Controls.TreeView> usando a roda do mouse ou arrastando o controle deslizante de uma barra de rolagem.</span><span class="sxs-lookup"><span data-stu-id="1b888-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="1b888-106">Você pode melhorar o desempenho do <xref:System.Windows.Controls.TreeView> quando o usuário rolar definindo o `VirtualizingStackPanel.VirtualizationMode` anexado a propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b888-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b888-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1b888-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="1b888-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b888-108">Description</span></span>  
<span data-ttu-id="1b888-109">O exemplo a seguir cria um <xref:System.Windows.Controls.TreeView> que define o `VirtualizingStackPanel.IsVirtualizing` anexado a propriedade como true e o `VirtualizingStackPanel.VirtualizationMode` anexado a propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> para otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="1b888-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="1b888-110">Código</span><span class="sxs-lookup"><span data-stu-id="1b888-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="1b888-111">O exemplo a seguir mostra os dados que usa o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1b888-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="1b888-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b888-112">See Also</span></span>  
 [<span data-ttu-id="1b888-113">Controles</span><span class="sxs-lookup"><span data-stu-id="1b888-113">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
