---
title: Como animar um valor booliano usando quadros-chave
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
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ac129bf133cca88a6d2f6a724d25ea2519cb72e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a>Como animar um valor booliano usando quadros-chave
Este exemplo mostra como o valor da propriedade booliana de animar uma <xref:System.Windows.Controls.Button> controle usando quadros chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.UIElement.IsEnabled%2A> propriedade de um <xref:System.Windows.Controls.Button> controle. Todos os quadros chave nesse exemplo usam uma instância do <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> classe. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> criar saltos repentinos entre valores, ou seja, a movimentação da animação é uma.  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
