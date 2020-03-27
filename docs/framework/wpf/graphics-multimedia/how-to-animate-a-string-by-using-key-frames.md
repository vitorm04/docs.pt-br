---
title: Como animar uma cadeia de caracteres usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344662"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Como animar uma cadeia de caracteres usando quadros-chave
Este exemplo mostra como animar uma string, que <xref:System.Windows.Controls.ContentControl.Content%2A> neste <xref:System.Windows.Controls.Button> exemplo é a propriedade de um controle, usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Controls.ContentControl.Content%2A> a classe <xref:System.Windows.Controls.Button>para animar a propriedade de um .  
  
 Todos os quadros-chave neste exemplo <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> usam uma instância da classe porque uma animação de seqüência de strings criada com quadros-chave só pode usar quadros de tecla discretos. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> como criar saltos repentinos entre os valores, ou seja, as alterações na animação ocorrem rapidamente e não são sutis.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
