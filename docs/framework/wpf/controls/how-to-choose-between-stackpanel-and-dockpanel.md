---
title: 'Como: Escolher entre StackPanel e DockPanel'
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
ms.openlocfilehash: 8338421dfb1bea856c15edf9d324cec955584f9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206961"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Como: Escolher entre StackPanel e DockPanel
Este exemplo mostra como escolher entre usar um <xref:System.Windows.Controls.StackPanel> ou um <xref:System.Windows.Controls.DockPanel> quando você empilhar conteúdo em um <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Exemplo  
 Embora você possa usar qualquer uma <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.StackPanel> para a pilha de elementos filho, os dois controles nem sempre produzem os mesmos resultados. Por exemplo, a ordem posicionar os elementos filho pode afetar o tamanho dos elementos filho em uma <xref:System.Windows.Controls.DockPanel> , mas não em um <xref:System.Windows.Controls.StackPanel>. Esse comportamento diferente ocorre porque <xref:System.Windows.Controls.StackPanel> medidas na direção de empilhamento em <xref:System.Double>.<xref:System.Double.PositiveInfinity>; no entanto, <xref:System.Windows.Controls.DockPanel> mede apenas o tamanho disponível.  
  
 O exemplo a seguir demonstra essa diferença chave entre <xref:System.Windows.Controls.DockPanel> e <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [Visão geral de painéis](panels-overview.md)
