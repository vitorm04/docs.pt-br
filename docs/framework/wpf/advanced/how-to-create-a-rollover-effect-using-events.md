---
title: Como criar um efeito de sobreposição usando eventos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: ccdc8aeb26b538814b2f9020e1e3a5b311fa5a99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460164"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Como criar um efeito de sobreposição usando eventos
Este exemplo mostra como alterar a cor de um elemento conforme o ponteiro do mouse entra e sai da área ocupada pelo elemento.  
  
 Este exemplo consiste em um arquivo de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.  
  
> [!NOTE]
> Este exemplo demonstra como usar eventos, mas a maneira recomendada para atingir esse mesmo efeito é usar um <xref:System.Windows.Trigger> em um estilo. Para obter mais informações, consulte [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir cria a interface do usuário, que consiste em <xref:System.Windows.Controls.Border> em um <xref:System.Windows.Controls.TextBlock>e anexa os manipuladores de eventos <xref:System.Windows.Input.Mouse.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> à <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 O code-behind a seguir cria os manipuladores de eventos <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave>.  Quando o ponteiro do mouse entra no <xref:System.Windows.Controls.Border>, o plano de fundo da <xref:System.Windows.Controls.Border> é alterado para vermelho.  Quando o ponteiro do mouse sai do <xref:System.Windows.Controls.Border>, o plano de fundo da <xref:System.Windows.Controls.Border> é alterado de volta para branco.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
