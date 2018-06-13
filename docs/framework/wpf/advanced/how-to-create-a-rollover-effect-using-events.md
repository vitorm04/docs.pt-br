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
ms.openlocfilehash: d458d87586614093b35fcd73969dea04fe620351
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543004"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Como criar um efeito de sobreposição usando eventos
Este exemplo mostra como alterar a cor de um elemento quando o ponteiro do mouse entra e sai da área ocupada pelo elemento.  
  
 Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.  
  
> [!NOTE]
>  Este exemplo demonstra como usar eventos, mas a maneira recomendada para atingir o mesmo efeito é usar um <xref:System.Windows.Trigger> em um estilo. Para obter mais informações, consulte [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em <xref:System.Windows.Controls.Border> em torno de um <xref:System.Windows.Controls.TextBlock>e anexa o <xref:System.Windows.Input.Mouse.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> manipuladores de eventos para o <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 O código a seguir cria o <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> manipuladores de eventos.  Quando o ponteiro do mouse entra o <xref:System.Windows.Controls.Border>, plano de fundo do <xref:System.Windows.Controls.Border> muda para vermelho.  Quando o ponteiro do mouse deixa o <xref:System.Windows.Controls.Border>, plano de fundo do <xref:System.Windows.Controls.Border> é alterada para branco.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
