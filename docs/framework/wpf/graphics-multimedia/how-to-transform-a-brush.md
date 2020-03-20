---
title: Como transformar um pincel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187333"
---
# <a name="how-to-transform-a-brush"></a>Como transformar um pincel
Este exemplo mostra <xref:System.Windows.Media.Brush> como transformar objetos usando <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A>suas duas propriedades de transformação: e .  
  
 Os exemplos a <xref:System.Windows.Media.RotateTransform> seguir usam um <xref:System.Windows.Media.ImageBrush> para girar o conteúdo de um em 45 graus.  
  
 A ilustração <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.RotateTransform>seguir mostra <xref:System.Windows.Media.RotateTransform> o sem um , com o aplicado ao <xref:System.Windows.Media.Brush.RelativeTransform%2A> imóvel, e com o <xref:System.Windows.Media.RotateTransform> aplicado ao <xref:System.Windows.Media.Brush.Transform%2A> imóvel.  
  
 ![Configurações de Brush RelativeTransform e Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Exemplo  
 O primeiro exemplo <xref:System.Windows.Media.RotateTransform> se <xref:System.Windows.Media.Brush.RelativeTransform%2A> aplica a <xref:System.Windows.Media.ImageBrush>a a propriedade de um . As <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades de <xref:System.Windows.Media.RotateTransform> um objeto são definidas como 0,5, que é a coordenada relativa do ponto central deste conteúdo. Como resultado, <xref:System.Windows.Media.ImageBrush> o conteúdo gira sobre seu centro.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 O segundo exemplo também <xref:System.Windows.Media.RotateTransform> se <xref:System.Windows.Media.ImageBrush>aplica a a a; no entanto, <xref:System.Windows.Media.Brush.Transform%2A> este exemplo <xref:System.Windows.Media.Brush.RelativeTransform%2A> usa a propriedade em vez da propriedade.  
  
 Para girar o pincel sobre seu <xref:System.Windows.Media.RotateTransform.CenterX%2A> centro, o exemplo define as propriedades do <xref:System.Windows.Media.RotateTransform.CenterY%2A> <xref:System.Windows.Media.RotateTransform> objeto para coordenadas absolutas. Como o pincel pinta um retângulo de 175 x 90 pixels, o ponto central do retângulo é (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Para obter uma <xref:System.Windows.Media.Brush.RelativeTransform%2A> descrição <xref:System.Windows.Media.Brush.Transform%2A> de como as propriedades funcionam, consulte a visão geral da [transformação do pincel](brush-transformation-overview.md).  
  
 Para obter o exemplo completo, consulte [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Para obter mais informações sobre pincéis, consulte [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da transformação de pincel](brush-transformation-overview.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Visão geral de transformações](transforms-overview.md)
