---
title: Como obter ou definir um valor de encaixe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: b792c8b2342416fb380827b702efa28885145d66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554775"
---
# <a name="how-to-get-or-set-a-dock-value"></a>Como obter ou definir um valor de encaixe
O exemplo a seguir mostra como atribuir um <xref:System.Windows.Controls.Dock> valor para um objeto. O exemplo usa o <xref:System.Windows.Controls.DockPanel.GetDock%2A> e <xref:System.Windows.Controls.DockPanel.SetDock%2A> métodos de <xref:System.Windows.Controls.DockPanel>.  
  
## <a name="example"></a>Exemplo  
 O exemplo cria uma instância do <xref:System.Windows.Controls.TextBlock> elemento, `txt1`e atribui um <xref:System.Windows.Controls.Dock> valor `Top` usando o <xref:System.Windows.Controls.DockPanel.SetDock%2A> método <xref:System.Windows.Controls.DockPanel>. Ele, em seguida, anexa o valor do <xref:System.Windows.Controls.Dock> propriedade para o <xref:System.Windows.Controls.TextBlock.Text%2A> do <xref:System.Windows.Controls.TextBlock> elemento usando o <xref:System.Windows.Controls.DockPanel.GetDock%2A> método. Finalmente, o exemplo adiciona o <xref:System.Windows.Controls.TextBlock> elemento pai <xref:System.Windows.Controls.DockPanel>, `dp1`.  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>  
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
