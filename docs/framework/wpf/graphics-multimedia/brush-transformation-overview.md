---
title: Visão geral da transformação de pincel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186522"
---
# <a name="brush-transformation-overview"></a>Visão geral da transformação de pincel
A classe Brush fornece <xref:System.Windows.Media.Brush.Transform%2A> duas <xref:System.Windows.Media.Brush.RelativeTransform%2A>propriedades de transformação: e . As propriedades permitem que você gire, ajuste a escala, distorça e traduza o conteúdo do pincel. Este tópico descreve as diferenças entre essas duas propriedades e fornece exemplos de uso.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve compreender os recursos do pincel que está transformando. Para <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>e , consulte a [pintura com cores sólidas e visão geral gradientes](painting-with-solid-colors-and-gradients-overview.md). Para <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush>ou , ver [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md). Você também deve estar familiarizado com transformações 2D descritas em [Transforms Overview](transforms-overview.md) (Visão geral de transformações).  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Diferenças entre as propriedades Transformação e RelativeTransform  
 Quando você aplica uma transformação <xref:System.Windows.Media.Brush.Transform%2A> na propriedade de um pincel, você precisa saber o tamanho da área pintada se quiser transformar o conteúdo do pincel sobre seu centro. Suponha que a área pintada tenha 200 pixels independentes de dispositivo de largura e 150 de altura.  Se você <xref:System.Windows.Media.RotateTransform> usou um para girar a saída do pincel 45 graus <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> sobre o centro, <xref:System.Windows.Media.RotateTransform.CenterY%2A> você daria um de 100 e um de 75.  
  
 Quando você aplica uma transformação <xref:System.Windows.Media.Brush.RelativeTransform%2A> na propriedade de um pincel, essa transformação é aplicada ao pincel antes de sua saída ser mapeada para a área pintada. A lista a seguir descreve a ordem em que os conteúdos de um pincel são processados e transformados.  
  
1. Processar o conteúdo do pincel. Para <xref:System.Windows.Media.GradientBrush>um, isso significa determinar a área de gradiente. Para <xref:System.Windows.Media.TileBrush>um <xref:System.Windows.Media.TileBrush.Viewbox%2A> , o é <xref:System.Windows.Media.TileBrush.Viewport%2A>mapeado para o . Ele se torna a saída do pincel.  
  
2. Projete a saída do pincel para o retângulo de transformação 1 x 1.  
  
3. Aplique o pincel, <xref:System.Windows.Media.Brush.RelativeTransform%2A>se tiver um.  
  
4. Projete a saída transformada na área pintada.  
  
5. Aplique o pincel, <xref:System.Windows.Media.Transform>se tiver um.  
  
 Como <xref:System.Windows.Media.Brush.RelativeTransform%2A> o é aplicado enquanto a saída do pincel é mapeada para um retângulo 1 x 1, os valores de centro de transformação e deslocamento parecem ser relativos. Por exemplo, se <xref:System.Windows.Media.RotateTransform> você usou um para girar a saída do pincel 45 <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> graus sobre o <xref:System.Windows.Media.RotateTransform.CenterY%2A> centro, você daria um de 0,5 e 0,5.  
  
 A ilustração a seguir mostra a saída de vários pincéis que foram girados em 45 graus usando as <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A> propriedades.  
  
 ![Propriedades RelativeTransform e Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilizando RelativeTransform com um TileBrush  
 Como os pincéis de azulejo <xref:System.Windows.Media.Brush.RelativeTransform%2A> sao mais complexos do que outros pincéis, aplicar um a um pode produzir resultados inesperados. Por exemplo, considere a seguinte imagem.  
  
 ![A imagem de origem](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 O exemplo a <xref:System.Windows.Media.ImageBrush> seguir usa um para pintar uma área retangular com a imagem anterior. Aplica-se <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.ImageBrush> à propriedade <xref:System.Windows.Media.Brush.RelativeTransform%2A> do objeto, <xref:System.Windows.Media.TileBrush.Stretch%2A> e <xref:System.Windows.Media.Stretch.UniformToFill>define sua propriedade para , que deve preservar a proporção da imagem quando ela é esticada para preencher completamente o retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Esse exemplo gera a saída a seguir:  
  
 ![A saída transformada](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Observe que a imagem está distorcida, mesmo <xref:System.Windows.Media.TileBrush.Stretch%2A> que <xref:System.Windows.Media.Stretch.UniformToFill>o pincel tenha sido definido para . Isso porque a transformação relativa é aplicada <xref:System.Windows.Media.TileBrush.Viewbox%2A> depois que o <xref:System.Windows.Media.TileBrush.Viewport%2A>pincel é mapeado para o seu . A lista a seguir descreve cada etapa do processo:  
  
1. Projete o conteúdo<xref:System.Windows.Media.TileBrush.Viewbox%2A>do pincel ( )<xref:System.Windows.Media.TileBrush.Viewport%2A>em sua telha base ( ) usando a configuração do <xref:System.Windows.Media.TileBrush.Stretch%2A> pincel.  
  
     ![Estique a caixa de visualização para se adequar ao Viewport](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Projete a saída do bloco base para o retângulo de transformação 1 x 1.  
  
     ![Mapeie o Viewport para o retângulo de transformação](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Aplique <xref:System.Windows.Media.RotateTransform>o .  
  
     ![Aplique a transformação relativa](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Projete o bloco base transformado na área pintada.  
  
     ![Projete o pincel transformado na área de saída](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemplo: gire um ImageBrush em 45 graus  
 O exemplo a <xref:System.Windows.Media.RotateTransform> seguir <xref:System.Windows.Media.Brush.RelativeTransform%2A> aplica-se <xref:System.Windows.Media.ImageBrush>a a propriedade de um . As <xref:System.Windows.Media.RotateTransform> propriedades <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> objetos estão definidos como 0,5, as coordenadas relativas do ponto central do conteúdo. Como resultado, o conteúdo do pincel é girado em torno de seu centro.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 O próximo exemplo também <xref:System.Windows.Media.RotateTransform> se <xref:System.Windows.Media.ImageBrush>aplica a <xref:System.Windows.Media.Brush.Transform%2A> a a <xref:System.Windows.Media.Brush.RelativeTransform%2A> , mas usa a propriedade em vez da propriedade. Para girar o pincel sobre <xref:System.Windows.Media.RotateTransform> seu <xref:System.Windows.Media.RotateTransform.CenterX%2A> centro, o objeto deve <xref:System.Windows.Media.RotateTransform.CenterY%2A> ser definido como coordenadas absolutas. Como o retângulo que está sendo pintado pelo pincel tem 175 x 90 pixels, seu ponto central é (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 A ilustração a seguir mostra o pincel sem <xref:System.Windows.Media.Brush.RelativeTransform%2A> transformação, com a transformação aplicada ao imóvel, e com a transformação aplicada ao <xref:System.Windows.Media.Brush.Transform%2A> imóvel.  
  
 ![Configurações de Brush RelativeTransform e Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Este exemplo é parte de um exemplo maior. Para obter o exemplo completo, consulte [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes) (Exemplo de pincéis). Para obter mais informações sobre pincéis, consulte [WPF Brushes Overview](wpf-brushes-overview.md) (Visão geral de pincéis do WPF).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de transformações](transforms-overview.md)
