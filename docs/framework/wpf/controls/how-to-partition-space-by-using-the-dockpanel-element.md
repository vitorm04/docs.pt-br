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
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960194"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Como: Particionar espaço usando o elemento DockPanel
O exemplo a seguir cria uma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] estrutura simples usando <xref:System.Windows.Controls.DockPanel> um elemento. O <xref:System.Windows.Controls.DockPanel> espaço disponível de partições para seus elementos filho.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a <xref:System.Windows.Controls.DockPanel.Dock%2A> Propriedade, que é uma propriedade anexada, para encaixar dois elementos <xref:System.Windows.Controls.Dock.Top> idênticos <xref:System.Windows.Controls.Border> no do espaço particionado. Um terceiro <xref:System.Windows.Controls.Border> elemento é encaixado <xref:System.Windows.Controls.Dock.Left>no, com sua largura definida como 200 pixels. Um quarto <xref:System.Windows.Controls.Border> é encaixado no <xref:System.Windows.Controls.Dock.Bottom> da tela. O último <xref:System.Windows.Controls.Border> elemento preenche automaticamente o espaço restante.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> Por padrão, o último filho de um <xref:System.Windows.Controls.DockPanel> elemento preenche o espaço não alocado restante. Se você não quiser esse comportamento, defina `LastChildFill="False"`.  
  
 O aplicativo compilado produz uma nova interface do usuário parecida com esta.  
  
 ![Um cenário de DockPanel típico.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DockPanel>
- [Visão geral de painéis](panels-overview.md)
