---
title: 'Como: Particionar espaço usando o elemento DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: ab51270644bf370944ebc933c765b40c528681c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158880"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Como: Particionar espaço usando o elemento DockPanel
O exemplo a seguir cria um simples [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework usando um <xref:System.Windows.Controls.DockPanel> elemento. O <xref:System.Windows.Controls.DockPanel> particiona o espaço disponível para seus elementos filho.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade, que é uma propriedade anexada, para encaixar dois idênticos <xref:System.Windows.Controls.Border> elementos no <xref:System.Windows.Controls.Dock.Top> do espaço particionado. Um terceiro <xref:System.Windows.Controls.Border> elemento é encaixado a <xref:System.Windows.Controls.Dock.Left>, com sua largura definida para 200 pixels. Um quarto <xref:System.Windows.Controls.Border> é encaixado a <xref:System.Windows.Controls.Dock.Bottom> da tela. A última <xref:System.Windows.Controls.Border> elemento preenche automaticamente o espaço restante.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Por padrão, o último filho de um <xref:System.Windows.Controls.DockPanel> elemento preenche o espaço não alocado restante. Se você não quiser esse comportamento, defina `LastChildFill="False"`.  
  
 O aplicativo compilado produz uma nova interface do usuário que se parece com isso.  
  
 ![Um cenário de DockPanel típico.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DockPanel>
- [Visão geral de painéis](panels-overview.md)
