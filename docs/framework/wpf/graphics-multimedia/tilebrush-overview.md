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
ms.openlocfilehash: a610acfef416a978ab8ecd9a561a135ecf3611cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125287"
---
# <a name="tilebrush-overview"></a>Visão geral de TileBrush
<xref:System.Windows.Media.TileBrush> objetos oferecem uma grande quantidade de controle sobre como uma área é pintada com uma imagem <xref:System.Windows.Media.Drawing>, ou <xref:System.Windows.Media.Visual>. Este tópico descreve como usar <xref:System.Windows.Media.TileBrush> recursos para obter mais controle sobre como uma <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush> pinta uma área.  

<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, é útil entender como usar os recursos básicos do <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush> classe. Para obter uma introdução a esses tipos, consulte a [pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Pintando uma área com blocos  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, estão <xref:System.Windows.Media.VisualBrush> são tipos de <xref:System.Windows.Media.TileBrush> objetos. Pincéis de bloco oferecem um alto nível de controle sobre como uma área é pintada com uma imagem, desenho ou visual. Por exemplo, em vez de apenas pintar uma área com uma única imagem alongada, você pode pintá-la com uma série de blocos de imagens que criam um padrão.  
  
 Pintar uma área com um pincel de bloco envolve três componentes: o conteúdo, o bloco de base e a área de saída.  
  
 ![Componentes de TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Componentes de um TileBrush com um único bloco  
  
 ![Componentes de um TileBrush lado a lado](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Componentes de um TileBrush com um TileMode de bloco  
  
 A área de saída é a área que está sendo pintada, como o <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Ellipse> ou o <xref:System.Windows.Controls.Control.Background%2A> de um <xref:System.Windows.Controls.Button>. As próximas seções descrevem os outros dois componentes de um <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>Conteúdo do pincel  
 Há três tipos diferentes de <xref:System.Windows.Media.TileBrush> e cada um pinta com um tipo diferente de conteúdo.  
  
-   Se o pincel for um <xref:System.Windows.Media.ImageBrush>, esse conteúdo é uma imagem do <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriedade especifica os conteúdos do <xref:System.Windows.Media.ImageBrush>.  
  
-   Se o pincel for um <xref:System.Windows.Media.DrawingBrush>, esse conteúdo é um desenho. O <xref:System.Windows.Media.DrawingBrush.Drawing%2A> propriedade especifica os conteúdos do <xref:System.Windows.Media.DrawingBrush>.  
  
-   Se o pincel for um <xref:System.Windows.Media.VisualBrush>, esse conteúdo é um visual. O <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade especifica o conteúdo do <xref:System.Windows.Media.VisualBrush>.  
  
 Você pode especificar a posição e dimensões da <xref:System.Windows.Media.TileBrush> conteúdo usando o <xref:System.Windows.Media.TileBrush.Viewbox%2A> propriedade, embora seja comum deixar o <xref:System.Windows.Media.TileBrush.Viewbox%2A> definido como seu valor padrão. Por padrão, o <xref:System.Windows.Media.TileBrush.Viewbox%2A> está configurado para conter completamente o conteúdo do pincel. Para obter mais informações sobre como configurar o <xref:System.Windows.Controls.Viewbox>, consulte o <xref:System.Windows.Controls.Viewbox> página de propriedades.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>O bloco de base  
 Um <xref:System.Windows.Media.TileBrush> projeta seu conteúdo em um bloco de base. O <xref:System.Windows.Media.TileBrush.Stretch%2A> controles de propriedade como <xref:System.Windows.Media.TileBrush> conteúdo é alongado para preencher o bloco de base. O <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade aceita os seguintes valores, definidos pela <xref:System.Windows.Media.Stretch> enumeração:  
  
-   <xref:System.Windows.Media.Stretch.None>: O conteúdo do pincel não é alongado para preencher o bloco.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: O conteúdo do pincel é dimensionado para preencher o bloco. Como a altura e a largura do conteúdo são dimensionadas de forma independente, a taxa de proporção original do conteúdo pode não ser preservada. Ou seja, o conteúdo do pincel pode ser distorcido para preencher completamente o bloco de saída.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: O conteúdo do pincel é dimensionado para que ele caiba completamente dentro do bloco. A taxa de proporção do conteúdo é preservada.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: O conteúdo do pincel é dimensionado para que ele preencha completamente a área de saída enquanto preserva a taxa de proporção original do conteúdo.  
  
 A imagem a seguir ilustra as diferentes <xref:System.Windows.Media.TileBrush.Stretch%2A> configurações.  
  
 ![Diferentes configurações de alongamento de TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 No exemplo a seguir, o conteúdo de um <xref:System.Windows.Media.ImageBrush> é definido para que ele não seja alongado para preencher a área de saída.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Por padrão, um <xref:System.Windows.Media.TileBrush> gera um único bloco (o bloco de base) e alonga esse bloco para preencher completamente a área de saída. Você pode alterar o tamanho e posição do bloco base, definindo a <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Tamanho do bloco de base  
 O <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade determina o tamanho e posição do bloco base e o <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedade determina se o <xref:System.Windows.Media.TileBrush.Viewport%2A> é especificado usando coordenadas absolutas ou relativas. Se forem relativas, as coordenadas serão relativas ao tamanho da área de saída. O ponto (0,0) representa o canto superior esquerdo da área de saída e (1,1) representa seu canto inferior direito. Para especificar que o <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade usa coordenadas absolutas, defina a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedade <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 A ilustração a seguir mostra a diferença na saída entre um <xref:System.Windows.Media.TileBrush> com relativas versus absolutas <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Observe que cada ilustração mostra um padrão lado a lado. A seção a seguir descreve como especificar o padrão de bloco.  
  
 ![Unidades de visor absolutas e relativas](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 No exemplo a seguir, uma imagem é usada para criar um bloco que tem largura e altura de 50%. O bloco de base está localizado em (0,0) da área de saída.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 O exemplo a seguir define os blocos de um <xref:System.Windows.Media.ImageBrush> para 25 por 25 pixels independentes de dispositivo. Porque o <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> são absolutos, o <xref:System.Windows.Media.ImageBrush> blocos sempre são 25 por 25 pixels, independentemente do tamanho da área que está sendo pintada.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Comportamento de agrupamento lado a lado  
 Um <xref:System.Windows.Media.TileBrush> produz um padrão lado a lado quando seu bloco base não preenche completamente a área de saída e um modo de preenchimento diferente <xref:System.Windows.Media.TileMode.None> for especificado. Quando bloco um bloco do pincel de não preenche completamente a área de saída, seus <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade especifica se o bloco de base deve ser duplicado para preencher a área de saída e, em caso afirmativo, como o bloco de base deve ser duplicado. O <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade aceita os seguintes valores, definidos pela <xref:System.Windows.Media.TileMode> enumeração:  
  
-   <xref:System.Windows.Media.TileMode.None>: Somente o bloco de base é desenhado.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: O bloco de base é desenhado e a área restante é preenchida repetindo o bloco de base, de modo que a borda direita de um bloco é adjacente à borda esquerda do próximo e da mesma forma para a parte inferior e superior.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: O mesmo que <xref:System.Windows.Media.TileMode.Tile>, mas colunas alternadas de blocos são invertidas horizontalmente.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: O mesmo que <xref:System.Windows.Media.TileMode.Tile>, mas linhas alternadas de blocos são invertidas verticalmente.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Uma combinação de <xref:System.Windows.Media.TileMode.FlipX> e <xref:System.Windows.Media.TileMode.FlipY>.  
  
 A imagem a seguir ilustra os modos diferentes de preenchimento lado a lado.  
  
 ![Configurações diferentes de TileMode de TileBrush](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 No exemplo a seguir, uma imagem é usada para pintar um retângulo que tem 100 pixels de largura e 100 pixels de altura. Definindo o pincel <xref:System.Windows.Media.TileBrush.Viewport%2A> tiver sido definido para 0,0,0.25,0.25, bloco de base do pincel é feito para ser 1 e 4 da área de saída. O pincel <xref:System.Windows.Media.TileBrush.TileMode%2A> é definido como <xref:System.Windows.Media.TileMode.FlipXY>. de modo que ele preenche o retângulo com linhas de blocos.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Tópicos de instruções](brushes-how-to-topics.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Exemplo de ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [Exemplo de VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
