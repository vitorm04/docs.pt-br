---
title: Como animar a cor ou a opacidade de um SolidColorBrush
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452877"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Como animar a cor ou a opacidade de um SolidColorBrush
Este exemplo mostra como animar o <xref:System.Windows.Media.SolidColorBrush.Color%2A> e <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa três animações para animar o <xref:System.Windows.Media.SolidColorBrush.Color%2A> e <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush>.  
  
- A primeira animação, uma <xref:System.Windows.Media.Animation.ColorAnimation>, altera a cor do pincel para <xref:System.Windows.Media.Colors.Gray%2A> quando o mouse entra no retângulo.  
  
- A próxima animação, outra <xref:System.Windows.Media.Animation.ColorAnimation>, altera a cor do pincel para <xref:System.Windows.Media.Colors.Orange%2A> quando o mouse sai do retângulo.  
  
- A animação final, uma <xref:System.Windows.Media.Animation.DoubleAnimation>, altera a opacidade do pincel para 0,0 quando o botão esquerdo do mouse é pressionado.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Para obter um exemplo mais completo, que mostra como animar diferentes tipos de pincéis, consulte o [exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Para mais informações sobre animação, consulte [Visão Geral de Animação](animation-overview.md).  
  
 Para consistência com outros exemplos de animação, as versões de código deste exemplo usam um objeto <xref:System.Windows.Media.Animation.Storyboard> para aplicar suas animações. No entanto, ao aplicar uma única animação no código, é mais simples usar o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> em vez de usar um <xref:System.Windows.Media.Animation.Storyboard>. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
