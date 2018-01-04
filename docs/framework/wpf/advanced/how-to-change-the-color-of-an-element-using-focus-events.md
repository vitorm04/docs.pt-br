---
title: Como alterar a cor de um elemento usando eventos de foco
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8b0e3f1b0a3287be89aba6e26f0621525c458a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Como alterar a cor de um elemento usando eventos de foco
Este exemplo mostra como alterar a cor de um elemento quando ele recebe e perde o foco usando o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> eventos.  
  
 Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em dois <xref:System.Windows.Controls.Button> objetos e anexa os manipuladores de eventos para o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> eventos para o <xref:System.Windows.Controls.Button> objetos.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 O código a seguir cria o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> manipuladores de eventos.  Quando o <xref:System.Windows.Controls.Button> ganha o foco, teclado do <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> muda para vermelho.  Quando o <xref:System.Windows.Controls.Button> perde o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> é alterada para branco.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)
