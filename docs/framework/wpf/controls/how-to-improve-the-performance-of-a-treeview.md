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
ms.workload: dotnet
ms.openlocfilehash: 2c13a9c89bdcb149df61f26177ea8705e502402f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>Como melhorar o desempenho de um TreeView
Se um <xref:System.Windows.Controls.TreeView> contém muitos itens, a quantidade de tempo que leva para carregar pode causar um atraso significativo na interface do usuário. Você pode melhorar o tempo de carregamento, definindo o `VirtualizingStackPanel.IsVirtualizing` anexado propriedade `true`.  A interface do usuário também pode ser lento para reagir quando um usuário rolar a <xref:System.Windows.Controls.TreeView> usando a roda do mouse ou arrastando o controle deslizante de uma barra de rolagem. Você pode melhorar o desempenho do <xref:System.Windows.Controls.TreeView> quando o usuário rolar definindo o `VirtualizingStackPanel.VirtualizationMode` anexado a propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
O exemplo a seguir cria um <xref:System.Windows.Controls.TreeView> que define o `VirtualizingStackPanel.IsVirtualizing` anexado a propriedade como true e o `VirtualizingStackPanel.VirtualizationMode` anexado a propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> para otimizar o desempenho.  
  
## <a name="code"></a>Código  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 O exemplo a seguir mostra os dados que usa o exemplo anterior.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>Consulte também  
 [Controles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
