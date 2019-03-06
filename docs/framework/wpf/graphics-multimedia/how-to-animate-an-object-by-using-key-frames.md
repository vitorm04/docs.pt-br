---
title: 'Como: Animar um objeto usando quadros-chave'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 1e0e464adf70aeeaecb522d328d3087ca66a530c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368552"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Como: Animar um objeto usando quadros-chave
Este exemplo mostra como animar um objeto, que neste exemplo é o <xref:System.Windows.Controls.Page.Background%2A> propriedade de um <xref:System.Windows.Controls.Page> controle usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe para animar a cor muda para o <xref:System.Windows.Controls.Page.Background%2A> propriedade de um <xref:System.Windows.Controls.Page> controle. A animação do exemplo muda para um pincel de tela de fundo diferente em intervalos regulares. Essa animação usa o <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe para criar três quadros-chave diferentes. A animação usa quadros-chave da seguinte maneira:  
  
1.  No final do primeiro segundo, anima uma instância da <xref:System.Windows.Media.LinearGradientBrush> classe. Esta seção do exemplo aplica um gradiente linear à cor da tela de fundo para que a cor faça a transição de amarelo para laranja para vermelho.  
  
2.  No final do próximo segundo, anima uma instância da <xref:System.Windows.Media.RadialGradientBrush> classe. Esta seção do exemplo aplica um gradiente radial à cor da tela de fundo para que a cor faça a transição de branco para azul para preto.  
  
3.  No final do terceiro segundo, anima uma instância da <xref:System.Windows.Media.DrawingBrush> classe. Esta seção do exemplo aplica um padrão quadriculado à tela de fundo.  
  
4.  A animação começa novamente e repete indefinidamente.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> é o único tipo de quadro-chave que você pode usar com o <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe. Quadros-chave como <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> criam alterações repentinas em valores, ou seja, as alterações de cor nesse exemplo ocorrem repentinamente.  
  
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
