---
title: 'Como: Detectar quando a tecla Enter é pressionada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a99da5804bbc31897198b9b6d9e21da9f17dfe26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051410"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Como: Detectar quando a tecla Enter é pressionada
Este exemplo mostra como detectar quando o <xref:System.Windows.Input.Key.Enter> tecla é pressionada no teclado.  
  
 Esse exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 Quando o usuário pressiona o <xref:System.Windows.Input.Key.Enter> principais na <xref:System.Windows.Controls.TextBox>, a entrada na caixa de texto aparecerá em outra área do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em um <xref:System.Windows.Controls.StackPanel>, um <xref:System.Windows.Controls.TextBlock>e um <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 O código a seguir cria o <xref:System.Windows.UIElement.KeyDown> manipulador de eventos.  Se a chave que é pressionada é o <xref:System.Windows.Input.Key.Enter> chave, será exibida uma mensagem no <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da entrada](input-overview.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
