---
title: Como animar um objeto usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344711"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Como animar um objeto usando quadros-chave
Este exemplo mostra como animar um objeto, que <xref:System.Windows.Controls.Page.Background%2A> neste <xref:System.Windows.Controls.Page> exemplo é propriedade de um controle, usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> seguir usa a classe <xref:System.Windows.Controls.Page.Background%2A> para <xref:System.Windows.Controls.Page> animar mudanças de cor para a propriedade de um controle. A animação do exemplo muda para um pincel de tela de fundo diferente em intervalos regulares. Esta animação <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> usa a classe para criar três quadros-chave diferentes. A animação usa quadros-chave da seguinte maneira:  
  
1. No final do primeiro segundo, anima uma <xref:System.Windows.Media.LinearGradientBrush> instância da classe. Esta seção do exemplo aplica um gradiente linear à cor da tela de fundo para que a cor faça a transição de amarelo para laranja para vermelho.  
  
2. No final do próximo segundo, anima uma <xref:System.Windows.Media.RadialGradientBrush> instância da classe. Esta seção do exemplo aplica um gradiente radial à cor da tela de fundo para que a cor faça a transição de branco para azul para preto.  
  
3. No final do terceiro segundo, anima uma <xref:System.Windows.Media.DrawingBrush> instância da classe. Esta seção do exemplo aplica um padrão quadriculado à tela de fundo.  
  
4. A animação começa novamente e repete indefinidamente.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>é o único tipo de quadro-chave <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> que você pode usar com a classe. Quadros-chave <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> como criar mudanças bruscas nos valores, ou seja, as mudanças de cor neste exemplo ocorrem de repente.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
