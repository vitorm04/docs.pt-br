---
title: 'Como: Detectar quando a tecla Enter foi pressionada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004814"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Como: Detectar quando a tecla Enter foi pressionada
Este exemplo mostra como detectar quando a chave <xref:System.Windows.Input.Key.Enter> é pressionada no teclado.  
  
 Este exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 Quando o usuário pressiona a tecla <xref:System.Windows.Input.Key.Enter> no <xref:System.Windows.Controls.TextBox>, a entrada na caixa de texto é exibida em outra área do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 O XAML a seguir cria a interface do usuário, que consiste em um <xref:System.Windows.Controls.StackPanel>, um <xref:System.Windows.Controls.TextBlock> e um <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 O seguinte código por trás cria o manipulador de eventos <xref:System.Windows.UIElement.KeyDown>.  Se a chave que é pressionada for a chave <xref:System.Windows.Input.Key.Enter>, uma mensagem será exibida no <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da entrada](input-overview.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
