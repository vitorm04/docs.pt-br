---
title: "Como detectar quando a tecla Enter é pressionada"
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
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8311083b4b82d4ab4827e8d0a2cf958c67347014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Como detectar quando a tecla Enter é pressionada
Este exemplo mostra como detectar quando o <xref:System.Windows.Input.Key.Enter> tecla é pressionada no teclado.  
  
 Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 Quando o usuário pressiona o <xref:System.Windows.Input.Key.Enter> chave no <xref:System.Windows.Controls.TextBox>, a entrada na caixa de texto aparecerá em outra área do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em uma <xref:System.Windows.Controls.StackPanel>, um <xref:System.Windows.Controls.TextBlock>e um <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 O código a seguir cria o <xref:System.Windows.UIElement.KeyDown> manipulador de eventos.  Se a chave que é pressionada for o <xref:System.Windows.Input.Key.Enter> chave, será exibida uma mensagem no <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
