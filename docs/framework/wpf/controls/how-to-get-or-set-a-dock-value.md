---
title: 'Como: Obter ou definir um valor de encaixe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: 7825377146532a6660e1838fa25631b788afe035
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374512"
---
# <a name="how-to-get-or-set-a-dock-value"></a>Como: Obter ou definir um valor de encaixe
O exemplo a seguir mostra como atribuir um <xref:System.Windows.Controls.Dock> valor para um objeto. O exemplo usa o <xref:System.Windows.Controls.DockPanel.GetDock%2A> e <xref:System.Windows.Controls.DockPanel.SetDock%2A> métodos de <xref:System.Windows.Controls.DockPanel>.  
  
## <a name="example"></a>Exemplo  
 O exemplo cria uma instância das <xref:System.Windows.Controls.TextBlock> elemento, `txt1`e atribui uma <xref:System.Windows.Controls.Dock> valor de `Top` usando o <xref:System.Windows.Controls.DockPanel.SetDock%2A> método de <xref:System.Windows.Controls.DockPanel>. Ele, em seguida, anexa o valor da <xref:System.Windows.Controls.Dock> propriedade para o <xref:System.Windows.Controls.TextBlock.Text%2A> da <xref:System.Windows.Controls.TextBlock> elemento usando o <xref:System.Windows.Controls.DockPanel.GetDock%2A> método. Por fim, o exemplo adiciona o <xref:System.Windows.Controls.TextBlock> elemento para o pai <xref:System.Windows.Controls.DockPanel>, `dp1`.  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [Visão geral de painéis](panels-overview.md)
