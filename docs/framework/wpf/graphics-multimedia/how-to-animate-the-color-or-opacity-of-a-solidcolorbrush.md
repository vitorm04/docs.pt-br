---
title: 'Como: Animar a cor ou a opacidade de um SolidColorBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: e440cf49b8b16051361650f9659dc6006c2e7b56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789240"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Como: Animar a cor ou a opacidade de um SolidColorBrush
Este exemplo mostra como animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> e <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa três animações para animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> e <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush>.  
  
- A primeira animação, um <xref:System.Windows.Media.Animation.ColorAnimation>, altera a cor do pincel para <xref:System.Windows.Media.Colors.Gray%2A> quando o mouse entra no retângulo.  
  
- A próxima animação, outro <xref:System.Windows.Media.Animation.ColorAnimation>, altera a cor do pincel para <xref:System.Windows.Media.Colors.Orange%2A> quando o mouse sai do retângulo.  
  
- A animação final, um <xref:System.Windows.Media.Animation.DoubleAnimation>, altera a opacidade do pincel como 0,0, quando o botão esquerdo do mouse é pressionado.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Para obter um exemplo mais completo, que mostra como animar diferentes tipos de pincéis, consulte o [exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973). Para mais informações sobre animação, consulte [Visão Geral de Animação](animation-overview.md).  
  
 Para consistência com outros exemplos de animação, as versões de código deste exemplo usam um <xref:System.Windows.Media.Animation.Storyboard> objeto para aplicar suas animações. No entanto, ao aplicar uma única animação no código, é mais simples usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método em vez de usar um <xref:System.Windows.Media.Animation.Storyboard>. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973)
