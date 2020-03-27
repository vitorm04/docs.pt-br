---
title: Como animar um valor booliano usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344930"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a>Como animar um valor booliano usando quadros-chave
Este exemplo mostra como animar o valor <xref:System.Windows.Controls.Button> de propriedade booleana de um controle usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> seguir usa <xref:System.Windows.UIElement.IsEnabled%2A> a classe <xref:System.Windows.Controls.Button> para animar a propriedade de um controle. Todos os quadros-chave neste exemplo <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> usam uma instância da classe. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> como criar saltos repentinos entre os valores, ou seja, o movimento da animação é jerky.  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
