---
title: 'Como: Alterar a cor de um elemento usando eventos de foco'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004829"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Como: Alterar a cor de um elemento usando eventos de foco
Este exemplo mostra como alterar a cor de um elemento quando ele é ganho e perde o foco usando os eventos <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus>.  
  
 Este exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir cria a interface do usuário, que consiste em dois objetos <xref:System.Windows.Controls.Button> e anexa manipuladores de eventos para os eventos <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> aos objetos <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 O seguinte código por trás cria os manipuladores de eventos <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus>.  Quando o <xref:System.Windows.Controls.Button> ganha o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> é alterado para vermelho.  Quando o <xref:System.Windows.Controls.Button> perde o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> é alterado de volta para branco.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da entrada](input-overview.md)
