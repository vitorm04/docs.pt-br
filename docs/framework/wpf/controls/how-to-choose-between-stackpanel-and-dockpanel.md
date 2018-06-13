---
title: Como escolher entre StackPanel e DockPanel
ms.date: 03/30/2017
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
ms.openlocfilehash: c9bfb8d29051a9cfa61d3fcb93b8bb9a68d14e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551928"
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
