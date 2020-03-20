---
title: Visão geral de TileBrush
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187105"
---
# <a name="tilebrush-overview"></a>Visão geral de TileBrush
<xref:System.Windows.Media.TileBrush>objetos fornecem-lhe uma grande dose de controle sobre <xref:System.Windows.Media.Drawing>como <xref:System.Windows.Media.Visual>uma área é pintada com uma imagem, ou . Este tópico descreve como <xref:System.Windows.Media.TileBrush> usar recursos para obter <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>mais <xref:System.Windows.Media.VisualBrush> controle sobre como um , ou pinta uma área.  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, é útil entender como usar <xref:System.Windows.Media.ImageBrush>os <xref:System.Windows.Media.DrawingBrush>recursos <xref:System.Windows.Media.VisualBrush> básicos da , ou classe. Para uma introdução a esses tipos, consulte a [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>Pintando uma área com blocos  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>são <xref:System.Windows.Media.VisualBrush> tipos <xref:System.Windows.Media.TileBrush> de objetos. Pincéis de bloco oferecem um alto nível de controle sobre como uma área é pintada com uma imagem, desenho ou visual. Por exemplo, em vez de apenas pintar uma área com uma única imagem alongada, você pode pintá-la com uma série de blocos de imagens que criam um padrão.  
  
 Pintar uma área com um pincel de bloco envolve três componentes: o conteúdo, o bloco de base e a área de saída.  
  
 ![Componentes de TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Componentes de um TileBrush com um único azulejo  
  
 ![Componentes de um TileBrush lado a lado](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Componentes de um TileBrush com um TileMode de bloco  
  
 A área de saída é a área <xref:System.Windows.Shapes.Shape.Fill%2A> que <xref:System.Windows.Shapes.Ellipse> está <xref:System.Windows.Controls.Control.Background%2A> sendo <xref:System.Windows.Controls.Button>pintada, como a de um ou de um . As próximas seções descrevem os <xref:System.Windows.Media.TileBrush>outros dois componentes de um .  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>Conteúdo do pincel  
 Existem três tipos <xref:System.Windows.Media.TileBrush> diferentes de e cada um pinta com um tipo diferente de conteúdo.  
  
- Se o pincel <xref:System.Windows.Media.ImageBrush>for um , <xref:System.Windows.Media.ImageBrush.ImageSource%2A> este conteúdo é uma <xref:System.Windows.Media.ImageBrush>imagem A propriedade especifica o conteúdo do .  
  
- Se o pincel <xref:System.Windows.Media.DrawingBrush>for um , este conteúdo é um desenho. A <xref:System.Windows.Media.DrawingBrush.Drawing%2A> propriedade especifica o <xref:System.Windows.Media.DrawingBrush>conteúdo do .  
  
- Se o pincel <xref:System.Windows.Media.VisualBrush>for um, este conteúdo é um visual. A <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade especifica o <xref:System.Windows.Media.VisualBrush>conteúdo do .  
  
 Você pode especificar a <xref:System.Windows.Media.TileBrush> posição e <xref:System.Windows.Media.TileBrush.Viewbox%2A> as dimensões do conteúdo <xref:System.Windows.Media.TileBrush.Viewbox%2A> usando a propriedade, embora seja comum deixar o conjunto para o seu valor padrão. Por padrão, <xref:System.Windows.Media.TileBrush.Viewbox%2A> o é configurado para conter completamente o conteúdo do pincel. Para obter mais informações <xref:System.Windows.Controls.Viewbox>sobre <xref:System.Windows.Controls.Viewbox> a configuração do , consulte a página da propriedade.  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>O bloco de base  
 Um <xref:System.Windows.Media.TileBrush> projeta seu conteúdo em uma telha base. A <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade controla como o <xref:System.Windows.Media.TileBrush> conteúdo é estendido para preencher o azulejo base. A <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade aceita os seguintes <xref:System.Windows.Media.Stretch> valores, definidos pela enumeração:  
  
- <xref:System.Windows.Media.Stretch.None>: O conteúdo do pincel não é esticado para encher o azulejo.  
  
- <xref:System.Windows.Media.Stretch.Fill>: O conteúdo do pincel é dimensionado para caber no azulejo. Como a altura e a largura do conteúdo são dimensionadas de forma independente, a taxa de proporção original do conteúdo pode não ser preservada. Ou seja, o conteúdo do pincel pode ser distorcido para preencher completamente o bloco de saída.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: O conteúdo do pincel é dimensionado de modo que se encaixe completamente dentro do azulejo. A taxa de proporção do conteúdo é preservada.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: O conteúdo do pincel é dimensionado de modo que ele preencha completamente a área de saída, preservando a proporção original do conteúdo.  
  
 A imagem a seguir <xref:System.Windows.Media.TileBrush.Stretch%2A> ilustra as diferentes configurações.  
  
 ![Diferentes configurações de alongamento de TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 No exemplo a seguir, <xref:System.Windows.Media.ImageBrush> o conteúdo de um é definido para que ele não se estique para preencher a área de saída.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Por padrão, <xref:System.Windows.Media.TileBrush> a gera uma única telha (o bloco base) e se estende essa telha para preencher completamente a área de saída. Você pode alterar o tamanho e a <xref:System.Windows.Media.TileBrush.Viewport%2A> posição <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> do azulejo base definindo as propriedades.  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>Tamanho do bloco de base  
 A <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade determina o tamanho e a posição <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> da telha <xref:System.Windows.Media.TileBrush.Viewport%2A> base, e a propriedade determina se a propriedade é especificada usando coordenadas absolutas ou relativas. Se forem relativas, as coordenadas serão relativas ao tamanho da área de saída. O ponto (0,0) representa o canto superior esquerdo da área de saída e (1,1) representa seu canto inferior direito. Para especificar <xref:System.Windows.Media.TileBrush.Viewport%2A> que a propriedade usa <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> coordenadas absolutas, defina a propriedade para <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 A ilustração a seguir mostra <xref:System.Windows.Media.TileBrush> a diferença <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>de saída entre um com relativo versus absoluto . Observe que cada ilustração mostra um padrão lado a lado. A seção a seguir descreve como especificar o padrão de bloco.  
  
 ![Unidades de visor absolutas e relativas](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 No exemplo a seguir, uma imagem é usada para criar um bloco que tem largura e altura de 50%. O bloco de base está localizado em (0,0) da área de saída.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 O próximo exemplo define <xref:System.Windows.Media.ImageBrush> as telhas de um pixels independentes de um dispositivo de 25 por 25. Por <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> serem absolutas, as <xref:System.Windows.Media.ImageBrush> telhas são sempre de 25 por 25 pixels, independentemente do tamanho da área que está sendo pintada.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>Comportamento de agrupamento lado a lado  
 A <xref:System.Windows.Media.TileBrush> produz um padrão de ladrilho quando sua telha base não preenche <xref:System.Windows.Media.TileMode.None> completamente a área de saída e um modo de ladrilho outro então é especificado. Quando a telha de um pincel de ladrilho não preenche completamente a área de saída, sua <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade especifica se a telha base deve ser duplicada para preencher a área de saída e, se for o caso, como a telha base deve ser duplicada. A <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade aceita os seguintes <xref:System.Windows.Media.TileMode> valores, definidos pela enumeração:  
  
- <xref:System.Windows.Media.TileMode.None>: Somente a telha base é desenhada.  
  
- <xref:System.Windows.Media.TileMode.Tile>: O azulejo base é desenhado e a área restante é preenchida repetindo a telha base de forma que a borda direita de uma telha seja adjacente à borda esquerda da próxima e da mesma forma para baixo e superior.  
  
- <xref:System.Windows.Media.TileMode.FlipX>: O <xref:System.Windows.Media.TileMode.Tile>mesmo que , mas colunas alternativas de telhas são invertidas horizontalmente.  
  
- <xref:System.Windows.Media.TileMode.FlipY>: O <xref:System.Windows.Media.TileMode.Tile>mesmo que , mas linhas alternativas de telhas são invertidas verticalmente.  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: Uma <xref:System.Windows.Media.TileMode.FlipX> combinação <xref:System.Windows.Media.TileMode.FlipY>de e .  
  
 A imagem a seguir ilustra os modos diferentes de preenchimento lado a lado.  
  
 ![Configurações diferentes de TileMode de TileBrush](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 No exemplo a seguir, uma imagem é usada para pintar um retângulo que tem 100 pixels de largura e 100 pixels de altura. Ao definir o <xref:System.Windows.Media.TileBrush.Viewport%2A> pincel foi definido como 0,0,0,25,0,25, o azulejo base do pincel é feito para ser 1/4 da área de saída. O pincel <xref:System.Windows.Media.TileBrush.TileMode%2A> está pronto <xref:System.Windows.Media.TileMode.FlipXY>para. de modo que ele preenche o retângulo com linhas de blocos.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Tópicos de como fazer](brushes-how-to-topics.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Exemplo de ImageBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Exemplo de VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
