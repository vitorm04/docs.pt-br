---
title: Como escolher entre StackPanel e DockPanel
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
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0274a0f078c378a101bdf4a4ae456fd2ce9f4185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Como escolher entre StackPanel e DockPanel
Este exemplo mostra como escolher entre usar um <xref:System.Windows.Controls.StackPanel> ou um <xref:System.Windows.Controls.DockPanel> quando você empilhar conteúdo em um <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Exemplo  
 Embora você possa usar o <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.StackPanel> para elementos filho de pilha, os dois controles nem sempre produzem os mesmos resultados. Por exemplo, a ordem que você coloque elementos filho pode afetar o tamanho dos elementos filho em um <xref:System.Windows.Controls.DockPanel> , mas não em um <xref:System.Windows.Controls.StackPanel>. Esse comportamento diferente ocorre porque <xref:System.Windows.Controls.StackPanel> medidas na direção de empilhamento em <xref:System.Double>.<xref:System.Double.PositiveInfinity>; no entanto, <xref:System.Windows.Controls.DockPanel> medidas somente o tamanho disponível.  
  
 O exemplo a seguir demonstra a diferença básica entre <xref:System.Windows.Controls.DockPanel> e <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
