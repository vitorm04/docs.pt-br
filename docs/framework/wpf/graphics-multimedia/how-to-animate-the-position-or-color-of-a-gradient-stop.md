---
title: "Como animar a posição ou cor de uma marca de gradiente"
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
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968d285d8a3345da9810f0ba4797bf8b2e33d36e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Como animar a posição ou cor de uma marca de gradiente
Este exemplo mostra como animar a <xref:System.Windows.Media.GradientStop.Color%2A> e <xref:System.Windows.Media.GradientStop.Offset%2A> de <xref:System.Windows.Media.GradientStop> objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir anima três paradas de gradiente dentro de um <xref:System.Windows.Media.LinearGradientBrush>. O exemplo usa três animações, cada qual animando uma marca de gradiente diferente:  
  
-   A primeira animação, um <xref:System.Windows.Media.Animation.DoubleAnimation>, anima a primeira parada gradiente <xref:System.Windows.Media.GradientStop.Offset%2A> de 0,0 a 1,0 e, em seguida, volta a 0.0. Como resultado, a primeira cor do gradiente muda do lado esquerdo para o lado direito do retângulo e, em seguida, volta para o lado esquerdo.  
  
-   A segunda animação, um <xref:System.Windows.Media.Animation.ColorAnimation>, anima a segunda parada gradiente <xref:System.Windows.Media.GradientStop.Color%2A> de <xref:System.Windows.Media.Colors.Purple%2A> para <xref:System.Windows.Media.Colors.Yellow%2A> e, em seguida, de volta para <xref:System.Windows.Media.Colors.Purple%2A>. Como resultado, a cor intermediária do gradiente muda de roxo para amarelo e de volta para roxo.  
  
-   A terceira animação, outro <xref:System.Windows.Media.Animation.ColorAnimation>, anima a opacidade da terceira parada gradiente <xref:System.Windows.Media.GradientStop.Color%2A> -1 e, em seguida, novamente. Como resultado, a terceira cor do gradiente desaparece e, em seguida, se torna opaca novamente.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Embora este exemplo usa um <xref:System.Windows.Media.LinearGradientBrush>, o processo é o mesmo para animar <xref:System.Windows.Media.GradientStop> objetos dentro de um <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Para obter exemplos adicionais, consulte o [Exemplo de pincéis](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.GradientStop>  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
