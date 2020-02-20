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
ms.openlocfilehash: 1d3a56014e0975f3616b7f90021b4290ced5daab
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453124"
---
# <a name="brush-transformation-overview"></a>Visão geral da transformação de pincel
A classe Brush fornece duas propriedades de transformação: <xref:System.Windows.Media.Brush.Transform%2A> e <xref:System.Windows.Media.Brush.RelativeTransform%2A>. As propriedades permitem que você gire, ajuste a escala, distorça e traduza o conteúdo do pincel. Este tópico descreve as diferenças entre essas duas propriedades e fornece exemplos de uso.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Para entender esse tópico, você deve compreender os recursos do pincel que está transformando. Para <xref:System.Windows.Media.LinearGradientBrush> e <xref:System.Windows.Media.RadialGradientBrush>, consulte [visão geral de pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md). Para <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>ou <xref:System.Windows.Media.VisualBrush>, consulte [pintura com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md). Você também deve estar familiarizado com transformações 2D descritas em [Transforms Overview](transforms-overview.md) (Visão geral de transformações).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Diferenças entre as propriedades Transformação e RelativeTransform  
 Ao aplicar uma transformação à propriedade <xref:System.Windows.Media.Brush.Transform%2A> de um pincel, você precisa saber o tamanho da área de pintura se desejar transformar o conteúdo do pincel sobre seu centro. Suponha que a área pintada tenha 200 pixels independentes de dispositivo de largura e 150 de altura.  Se você usou um <xref:System.Windows.Media.RotateTransform> para girar a saída do pincel 45 graus sobre seu centro, você daria ao <xref:System.Windows.Media.RotateTransform> uma <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 100 e uma <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 75.  
  
 Quando você aplica uma transformação à propriedade <xref:System.Windows.Media.Brush.RelativeTransform%2A> de um pincel, essa transformação é aplicada ao pincel antes de sua saída ser mapeada para a área de pintura. A lista a seguir descreve a ordem em que os conteúdos de um pincel são processados e transformados.  
  
1. Processar o conteúdo do pincel. Para um <xref:System.Windows.Media.GradientBrush>, isso significa determinar a área de gradiente. Para um <xref:System.Windows.Media.TileBrush>, o <xref:System.Windows.Media.TileBrush.Viewbox%2A> é mapeado para o <xref:System.Windows.Media.TileBrush.Viewport%2A>. Ele se torna a saída do pincel.  
  
2. Projete a saída do pincel para o retângulo de transformação 1 x 1.  
  
3. Aplique o <xref:System.Windows.Media.Brush.RelativeTransform%2A>do pincel, se ele tiver um.  
  
4. Projete a saída transformada na área pintada.  
  
5. Aplique o <xref:System.Windows.Media.Transform>do pincel, se ele tiver um.  
  
 Como a <xref:System.Windows.Media.Brush.RelativeTransform%2A> é aplicada enquanto a saída do pincel é mapeada para um retângulo 1 x 1, os valores central de transformação e deslocamento parecem ser relativos. Por exemplo, se você usou um <xref:System.Windows.Media.RotateTransform> para girar a saída do pincel 45 graus sobre seu centro, você daria ao <xref:System.Windows.Media.RotateTransform> uma <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 0,5 e uma <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 A ilustração a seguir mostra a saída de vários pincéis que foram girados por 45 graus usando as propriedades <xref:System.Windows.Media.Brush.RelativeTransform%2A> e <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Propriedades de RelativeTransform e de transformação](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilizando RelativeTransform com um TileBrush  
 Como os pincéis de bloco são mais complexos do que outros pincéis, a aplicação de um <xref:System.Windows.Media.Brush.RelativeTransform%2A> a um pode produzir resultados inesperados. Por exemplo, considere a seguinte imagem.  
  
 ![A imagem de origem](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.ImageBrush> para pintar uma área retangular com a imagem anterior. Ele aplica uma <xref:System.Windows.Media.RotateTransform> à propriedade <xref:System.Windows.Media.Brush.RelativeTransform%2A> do objeto <xref:System.Windows.Media.ImageBrush> e define sua propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A> como <xref:System.Windows.Media.Stretch.UniformToFill>, que deve preservar a taxa de proporção da imagem quando ela é ampliada para preencher completamente o retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Esse exemplo gera a saída a seguir:  
  
 ![A saída transformada](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Observe que a imagem está distorcida, embora o <xref:System.Windows.Media.TileBrush.Stretch%2A> do pincel tenha sido definido como <xref:System.Windows.Media.Stretch.UniformToFill>. Isso ocorre porque a transformação relativa é aplicada depois que o <xref:System.Windows.Media.TileBrush.Viewbox%2A> do pincel é mapeado para sua <xref:System.Windows.Media.TileBrush.Viewport%2A>. A lista a seguir descreve cada etapa do processo:  
  
1. Projetar o conteúdo do pincel (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) em seu bloco base (<xref:System.Windows.Media.TileBrush.Viewport%2A>) usando a configuração de <xref:System.Windows.Media.TileBrush.Stretch%2A> do pincel.  
  
     ![Alongar o Viewbox para ajustar o visor](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Projete a saída do bloco base para o retângulo de transformação 1 x 1.  
  
     ![Mapear o visor para o retângulo de transformação](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Aplique o <xref:System.Windows.Media.RotateTransform>.  
  
     ![Aplicar a transformação relativa](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Projete o bloco base transformado na área pintada.  
  
     ![Projetar o pincel transformado na área de saída](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemplo: gire um ImageBrush em 45 graus  
 O exemplo a seguir aplica um <xref:System.Windows.Media.RotateTransform> à propriedade <xref:System.Windows.Media.Brush.RelativeTransform%2A> de um <xref:System.Windows.Media.ImageBrush>. As propriedades <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> do objeto de <xref:System.Windows.Media.RotateTransform> são definidas como 0,5, as coordenadas relativas do ponto central do conteúdo. Como resultado, o conteúdo do pincel é girado em torno de seu centro.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 O exemplo a seguir também aplica um <xref:System.Windows.Media.RotateTransform> a um <xref:System.Windows.Media.ImageBrush>, mas usa a propriedade <xref:System.Windows.Media.Brush.Transform%2A> em vez da propriedade <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Para girar o pincel sobre seu centro, a <xref:System.Windows.Media.RotateTransform.CenterX%2A> do <xref:System.Windows.Media.RotateTransform> do objeto e <xref:System.Windows.Media.RotateTransform.CenterY%2A> devem ser definidas como coordenadas absolutas. Como o retângulo que está sendo pintado pelo pincel tem 175 x 90 pixels, seu ponto central é (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 A ilustração a seguir mostra o pincel sem uma transformação, com a transformação aplicada à propriedade <xref:System.Windows.Media.Brush.RelativeTransform%2A> e com a transformação aplicada à propriedade <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Configurações de RelativeTransform e transformação de pincel](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Este exemplo é parte de um exemplo maior. Para obter o exemplo completo, consulte [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes) (Exemplo de pincéis). Para obter mais informações sobre pincéis, consulte [WPF Brushes Overview](wpf-brushes-overview.md) (Visão geral de pincéis do WPF).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de transformações](transforms-overview.md)
