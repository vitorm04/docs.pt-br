---
title: 'Como: Animar um objeto usando quadros principais'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933904"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Como: Animar um objeto usando quadros principais
Este exemplo mostra como animar um objeto, que neste exemplo é a <xref:System.Windows.Controls.Page.Background%2A> propriedade de um <xref:System.Windows.Controls.Page> controle, usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> a classe para animar as alterações <xref:System.Windows.Controls.Page.Background%2A> de cor da <xref:System.Windows.Controls.Page> propriedade de um controle. A animação do exemplo muda para um pincel de tela de fundo diferente em intervalos regulares. Essa animação usa a <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe para criar três quadros-chave diferentes. A animação usa quadros-chave da seguinte maneira:  
  
1. No final do primeiro segundo, o anima uma instância da <xref:System.Windows.Media.LinearGradientBrush> classe. Esta seção do exemplo aplica um gradiente linear à cor da tela de fundo para que a cor faça a transição de amarelo para laranja para vermelho.  
  
2. No final do próximo segundo, o anima uma instância da <xref:System.Windows.Media.RadialGradientBrush> classe. Esta seção do exemplo aplica um gradiente radial à cor da tela de fundo para que a cor faça a transição de branco para azul para preto.  
  
3. No final do terceiro segundo, o anima uma instância da <xref:System.Windows.Media.DrawingBrush> classe. Esta seção do exemplo aplica um padrão quadriculado à tela de fundo.  
  
4. A animação começa novamente e repete indefinidamente.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>é o único tipo de quadro-chave que você pode usar com <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> a classe. Quadros-chave <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> como criar alterações repentinas em valores, ou seja, as alterações de cor neste exemplo ocorrem de repente.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
