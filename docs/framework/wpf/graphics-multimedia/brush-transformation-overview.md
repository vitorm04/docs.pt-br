---
title: "Visão geral da transformação de pincel"
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
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa4a533594c1e89942406e7df0a49215e3885418
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="brush-transformation-overview"></a>Visão geral da transformação de pincel
A classe Brush fornece duas propriedades de transformação: <xref:System.Windows.Media.Brush.Transform%2A> e <xref:System.Windows.Media.Brush.RelativeTransform%2A>. As propriedades permitem que você gire, ajuste a escala, distorça e traduza o conteúdo do pincel. Este tópico descreve as diferenças entre essas duas propriedades e fornece exemplos de uso.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve compreender os recursos do pincel que está transformando. Para <xref:System.Windows.Media.LinearGradientBrush> e <xref:System.Windows.Media.RadialGradientBrush>, consulte o [pintura com cores sólidas e visão geral de gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Para <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush>, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Você também deve estar familiarizado com transformações 2D descritas em [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md) (Visão geral de transformações).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Diferenças entre as propriedades Transformação e RelativeTransform  
 Quando você aplica uma transformação a um pincel <xref:System.Windows.Media.Brush.Transform%2A> propriedade, você precisa saber o tamanho da área de pintura se desejar transformar os conteúdos do pincel sobre seu centro. Suponha que a área pintada tenha 200 pixels independentes de dispositivo de largura e 150 de altura.  Se você tiver usado um <xref:System.Windows.Media.RotateTransform> para girar o pincel a saída de 45 graus sobre seu centro, você daria a <xref:System.Windows.Media.RotateTransform> um <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 100 e um <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 75.  
  
 Quando você aplica uma transformação a um pincel <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade, essa transformação é aplicada ao pincel antes que sua saída seja mapeada à área de pintura. A lista a seguir descreve a ordem em que os conteúdos de um pincel são processados e transformados.  
  
1.  Processar o conteúdo do pincel. Para um <xref:System.Windows.Media.GradientBrush>, isso significa determinar a área do gradiente. Para uma <xref:System.Windows.Media.TileBrush>, o <xref:System.Windows.Media.TileBrush.Viewbox%2A> é mapeado para o <xref:System.Windows.Media.TileBrush.Viewport%2A>. Ele se torna a saída do pincel.  
  
2.  Projete a saída do pincel para o retângulo de transformação 1 x 1.  
  
3.  Aplicar o pincel <xref:System.Windows.Media.Brush.RelativeTransform%2A>, se houver.  
  
4.  Projete a saída transformada na área pintada.  
  
5.  Aplicar o pincel <xref:System.Windows.Media.Transform>, se houver.  
  
 Porque o <xref:System.Windows.Media.Brush.RelativeTransform%2A> é aplicado enquanto a saída do pincel é mapeada para um 1x1 retângulo, centro de transformação e os valores de deslocamento parecem ser relativos. Por exemplo, se você tiver usado um <xref:System.Windows.Media.RotateTransform> para girar o pincel a saída de 45 graus sobre seu centro, você daria a <xref:System.Windows.Media.RotateTransform> um <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 0,5 e um <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 A ilustração a seguir mostra a saída de diversos pincéis que foi girada em 45 graus utilizando o <xref:System.Windows.Media.Brush.RelativeTransform%2A> e <xref:System.Windows.Media.Brush.Transform%2A> propriedades.  
  
 ![Propriedades RelativeTransform e Transformação](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilizando RelativeTransform com um TileBrush  
 Como cursores em cascata são mais complexos que outros pincéis, aplicar um <xref:System.Windows.Media.Brush.RelativeTransform%2A> a um pode produzir resultados inesperados. Por exemplo, considere a seguinte imagem.  
  
 ![A imagem de origem](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.ImageBrush> para pintar uma área retangular com a imagem anterior. Ele se aplica uma <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.Media.ImageBrush> do objeto <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade e conjuntos de seu <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade <xref:System.Windows.Media.Stretch.UniformToFill>, que deve preservar a taxa de proporção da imagem quando redimensionado para preencher completamente o retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Este exemplo gera a seguinte saída:  
  
 ![A saída transformada](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Observe que a imagem é distorcida, mesmo que o pincel <xref:System.Windows.Media.TileBrush.Stretch%2A> foi definido como <xref:System.Windows.Media.Stretch.UniformToFill>. Isso ocorre porque a transformação relativa é aplicada após o pincel <xref:System.Windows.Media.TileBrush.Viewbox%2A> é mapeado para seu <xref:System.Windows.Media.TileBrush.Viewport%2A>. A lista a seguir descreve cada etapa do processo:  
  
1.  O conteúdo do pincel de projeto (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) no seu ladrilho base (<xref:System.Windows.Media.TileBrush.Viewport%2A>) usando o pincel <xref:System.Windows.Media.TileBrush.Stretch%2A> configuração.  
  
     ![Alongue o Viewbox para ajustar o visor](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Projete a saída do bloco base para o retângulo de transformação 1 x 1.  
  
     ![Mapeie o visor para o retângulo de transformação](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Aplicar o <xref:System.Windows.Media.RotateTransform>.  
  
     ![Aplique a transformação relativa](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Projete o bloco base transformado na área pintada.  
  
     ![Projete o pincel transformado na área de saída](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemplo: gire um ImageBrush em 45 graus  
 O exemplo a seguir aplica-se um <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade de um <xref:System.Windows.Media.ImageBrush>. O <xref:System.Windows.Media.RotateTransform> do objeto <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades são definidas como 0,5, as coordenadas relativas do centro do conteúdo do ponto. Como resultado, o conteúdo do pincel é girado em torno de seu centro.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 O exemplo a seguir também se aplica uma <xref:System.Windows.Media.RotateTransform> para um <xref:System.Windows.Media.ImageBrush>, mas usa o <xref:System.Windows.Media.Brush.Transform%2A> propriedade em vez do <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade. Para girar o pincel sobre seu centro, o <xref:System.Windows.Media.RotateTransform> do objeto <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> deve ser definido em coordenadas absolutas. Como o retângulo que está sendo pintado pelo pincel tem 175 x 90 pixels, seu ponto central é (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 A ilustração a seguir mostra o pincel sem uma transformação, com a transformação aplicada para o <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade e com a transformação aplicada para o <xref:System.Windows.Media.Brush.Transform%2A> propriedade.  
  
 ![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Este exemplo é parte de um exemplo maior. Para obter o exemplo completo, consulte [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973) (Exemplo de pincéis). Para obter mais informações sobre pincéis, consulte [WPF Brushes Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md) (Visão geral de pincéis do WPF).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Brush.Transform%2A>  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Brush>  
 [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
