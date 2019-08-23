---
title: 'Como: Criar um efeito de sobreposição usando eventos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960382"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Como: Criar um efeito de sobreposição usando eventos
Este exemplo mostra como alterar a cor de um elemento conforme o ponteiro do mouse entra e sai da área ocupada pelo elemento.  
  
 Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo e um arquivo code-behind.  
  
> [!NOTE]
> Este exemplo demonstra como usar eventos, mas a maneira recomendada para atingir esse mesmo efeito é usar um <xref:System.Windows.Trigger> em um estilo. Para obter mais informações, consulte [Estilo e modelagem](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que <xref:System.Windows.Controls.Border> consiste em um <xref:System.Windows.Controls.TextBlock>e anexa os manipuladores <xref:System.Windows.Input.Mouse.MouseEnter> de <xref:System.Windows.UIElement.MouseLeave> eventos e ao <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 O code-behind a seguir <xref:System.Windows.UIElement.MouseEnter> cria <xref:System.Windows.UIElement.MouseLeave> os manipuladores de eventos e.  Quando o ponteiro do mouse entra <xref:System.Windows.Controls.Border>no, o plano <xref:System.Windows.Controls.Border> de fundo do é alterado para vermelho.  Quando o ponteiro do mouse sai <xref:System.Windows.Controls.Border>do, o plano <xref:System.Windows.Controls.Border> de fundo do é alterado de volta para branco.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
