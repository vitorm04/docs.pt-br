---
title: Como animar a posição ou cor de uma marca de gradiente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452838"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Como animar a posição ou cor de uma marca de gradiente
Este exemplo mostra como animar o <xref:System.Windows.Media.GradientStop.Color%2A> e <xref:System.Windows.Media.GradientStop.Offset%2A> de objetos <xref:System.Windows.Media.GradientStop>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir anima três paradas de gradientes dentro de um <xref:System.Windows.Media.LinearGradientBrush>. O exemplo usa três animações, cada qual animando uma marca de gradiente diferente:  
  
- A primeira animação, uma <xref:System.Windows.Media.Animation.DoubleAnimation>, anima a <xref:System.Windows.Media.GradientStop.Offset%2A> da primeira parada de gradiente de 0,0 para 1,0 e, em seguida, de volta para 0,0. Como resultado, a primeira cor do gradiente muda do lado esquerdo para o lado direito do retângulo e, em seguida, volta para o lado esquerdo.  
  
- A segunda animação, uma <xref:System.Windows.Media.Animation.ColorAnimation>, anima a segunda <xref:System.Windows.Media.GradientStop.Color%2A> de parada de gradiente de <xref:System.Windows.Media.Colors.Purple%2A> para <xref:System.Windows.Media.Colors.Yellow%2A> e, em seguida, de volta para <xref:System.Windows.Media.Colors.Purple%2A>. Como resultado, a cor intermediária do gradiente muda de roxo para amarelo e de volta para roxo.  
  
- A terceira animação, outra <xref:System.Windows.Media.Animation.ColorAnimation>, anima a opacidade do terceiro <xref:System.Windows.Media.GradientStop.Color%2A> de parada de gradiente por-1 e, em seguida, de volta. Como resultado, a terceira cor do gradiente desaparece e, em seguida, se torna opaca novamente.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Embora este exemplo use uma <xref:System.Windows.Media.LinearGradientBrush>, o processo é o mesmo para animar <xref:System.Windows.Media.GradientStop> objetos dentro de um <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Para obter exemplos adicionais, consulte o [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.GradientStop>
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
