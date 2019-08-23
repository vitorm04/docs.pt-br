---
title: Visão geral dos objetos de desenho
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: d739865a692fa5ef448eba91369015580e5eda97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916308"
---
# <a name="drawing-objects-overview"></a>Visão geral dos objetos de desenho
Este tópico apresenta <xref:System.Windows.Media.Drawing> objetos e descreve como usá-los para desenhar formas, bitmaps, texto e mídia com eficiência. Use <xref:System.Windows.Media.Drawing> objetos ao criar Clip-Art, pinte com um <xref:System.Windows.Media.DrawingBrush>ou use <xref:System.Windows.Media.Visual> objetos.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>O que é um objeto de desenho?  
 Um <xref:System.Windows.Media.Drawing> objeto descreve o conteúdo visível, como uma forma, bitmap, vídeo ou uma linha de texto. Diferentes tipos de desenhos descrevem diferentes tipos de conteúdo. A seguir está uma lista dos diferentes tipos de objetos de desenho.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Desenha uma forma.  
  
- <xref:System.Windows.Media.ImageDrawing>– Desenha uma imagem.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Desenha texto.  
  
- <xref:System.Windows.Media.VideoDrawing>– Reproduz um arquivo de áudio ou de vídeo.  
  
- <xref:System.Windows.Media.DrawingGroup>– Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho composto.  
  
 <xref:System.Windows.Media.Drawing>os objetos são versáteis; Há várias maneiras de usar um <xref:System.Windows.Media.Drawing> objeto.  
  
- Você pode exibi-lo como uma imagem usando um <xref:System.Windows.Media.DrawingImage> e um <xref:System.Windows.Controls.Image> controle.  
  
- Você pode usá-lo com <xref:System.Windows.Media.DrawingBrush> um para pintar um objeto, como o <xref:System.Windows.Controls.Page.Background%2A> de um <xref:System.Windows.Controls.Page>.  
  
- Você pode usá-lo para descrever a aparência de <xref:System.Windows.Media.DrawingVisual>um.  
  
- Você pode usá-lo para enumerar o conteúdo <xref:System.Windows.Media.Visual>de um.  
  
 O WPF fornece outros tipos de objetos que são capazes de desenhar formas, bitmaps, texto e mídia. Por exemplo, você também pode usar <xref:System.Windows.Shapes.Shape> objetos para desenhar formas e o <xref:System.Windows.Controls.MediaElement> controle fornece outra maneira de adicionar vídeo ao seu aplicativo. Então, quando você deve <xref:System.Windows.Media.Drawing> usar objetos? Quando você puder sacrificar os recursos de nível de estrutura para obter benefícios de desempenho <xref:System.Windows.Freezable> ou quando precisar de recursos. Como <xref:System.Windows.Media.Drawing> os objetos não têm suporte para [layout](../advanced/layout.md), entrada e foco, eles fornecem benefícios de desempenho que os tornam ideais para descrever os planos de fundo, clip-art e para <xref:System.Windows.Media.Visual> desenhos de baixo nível com objetos.  
  
 Como eles são um objeto <xref:System.Windows.Freezable> de tipo <xref:System.Windows.Media.Drawing> , os objetos recebem vários recursos especiais, que incluem o seguinte: eles podem ser declarados como [recursos](../advanced/xaml-resources.md), compartilhados entre vários objetos, feitos somente leitura para melhorar o desempenho, clonado e tornar thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos <xref:System.Windows.Freezable> por objetos, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Desenhar uma forma  
 Para desenhar uma forma, você usa um <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> propriedade de um desenho de geometria descreve a forma para desenhar <xref:System.Windows.Media.GeometryDrawing.Brush%2A> , sua propriedade descreve como o interior da forma deve ser pintado e sua <xref:System.Windows.Media.GeometryDrawing.Pen%2A> propriedade descreve como sua estrutura de tópicos deve ser desenhada.  
  
 O exemplo a seguir usa <xref:System.Windows.Media.GeometryDrawing> um para desenhar uma forma. A forma é descrita por um <xref:System.Windows.Media.GeometryGroup> e dois <xref:System.Windows.Media.EllipseGeometry> objetos. O interior da forma é pintado com um <xref:System.Windows.Media.LinearGradientBrush> e sua estrutura de tópicos é desenhada com um. <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>  
  
 Este exemplo cria o seguinte <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![Uma GeometryDrawing de duas reticências](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Um GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Para obter o exemplo completo, consulte [Instruções: criar um GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Outras <xref:System.Windows.Media.Geometry> classes, como o <xref:System.Windows.Media.PathGeometry> permitem que você crie formas mais complexas criando curvas e arcos. Para obter mais informações <xref:System.Windows.Media.Geometry> sobre objetos, consulte a [visão geral da geometria](geometry-overview.md).  
  
 Para obter mais informações sobre outras maneiras de desenhar formas que não <xref:System.Windows.Media.Drawing> usam objetos, consulte [visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Desenhar uma imagem  
 Para desenhar uma imagem, use um <xref:System.Windows.Media.ImageDrawing>. A <xref:System.Windows.Media.ImageDrawing> propriedade de <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> um objeto descreve a imagem a ser desenhada e sua <xref:System.Windows.Media.ImageDrawing.Rect%2A> propriedade define a região em que a imagem é desenhada.  
  
 O exemplo a seguir desenha uma imagem em um retângulo localizado em (75,75) que tem 100 por 100 pixels. A ilustração a seguir mostra <xref:System.Windows.Media.ImageDrawing> o criado pelo exemplo. Uma borda cinza foi adicionada para mostrar os limites do <xref:System.Windows.Media.ImageDrawing>.  
  
 ![Um 100 de 100 ImageDrawing desenhado em &#40;75, 75&#41; ](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
Um ImageDrawing de 100 por 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Para obter mais informações sobre imagens, consulte [Visão geral de imagens](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Reproduzir mídia (apenas código)  
  
> [!NOTE]
> Embora seja possível declarar um <xref:System.Windows.Media.VideoDrawing> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você só pode carregar e reproduzir sua mídia usando código. Para reproduzir o vídeo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]no, use <xref:System.Windows.Controls.MediaElement> um em vez disso.  
  
 Para reproduzir um arquivo de áudio ou de vídeo, use <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer>um. Há duas maneiras de carregar e reproduzir mídia. A <xref:System.Windows.Media.MediaPlayer> primeira é usar um e um <xref:System.Windows.Media.VideoDrawing> por si só, e a segunda maneira é criar seu próprio <xref:System.Windows.Media.MediaTimeline> para uso com o e <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>o.  
  
> [!NOTE]
> Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
 Para reproduzir mídia sem criar suas próprias <xref:System.Windows.Media.MediaTimeline>, execute as etapas a seguir.  
  
1. Crie um objeto <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Use o <xref:System.Windows.Media.MediaPlayer.Open%2A> método para carregar o arquivo de mídia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Criará um <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Especifique o tamanho e o local para desenhar a mídia definindo a <xref:System.Windows.Media.VideoDrawing.Rect%2A> propriedade <xref:System.Windows.Media.VideoDrawing>do.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Defina a <xref:System.Windows.Media.VideoDrawing.Player%2A> propriedade <xref:System.Windows.Media.VideoDrawing> do com o <xref:System.Windows.Media.MediaPlayer> que você criou.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Use o <xref:System.Windows.Media.MediaPlayer.Play%2A> método <xref:System.Windows.Media.MediaPlayer> do para iniciar a reprodução da mídia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 O exemplo a seguir usa <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer> um para reproduzir um arquivo de vídeo uma vez.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Para obter controle de tempo adicional sobre a mídia, use <xref:System.Windows.Media.MediaTimeline> um com <xref:System.Windows.Media.MediaPlayer> os <xref:System.Windows.Media.VideoDrawing> objetos e. O <xref:System.Windows.Media.MediaTimeline> permite que você especifique se o vídeo deve ser repetido. Para usar um <xref:System.Windows.Media.MediaTimeline> com um <xref:System.Windows.Media.VideoDrawing>, execute as seguintes etapas:  
  
1. Declare o <xref:System.Windows.Media.MediaTimeline> e defina seus comportamentos de tempo.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Crie um <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Media.MediaTimeline>do.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Crie um <xref:System.Windows.Media.MediaPlayer> e use o <xref:System.Windows.Media.MediaClock> para definir sua <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriedade.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Crie um <xref:System.Windows.Media.VideoDrawing> e atribua o <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing.Player%2A>àpropriedade do. <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 O exemplo a seguir usa <xref:System.Windows.Media.MediaTimeline> um com <xref:System.Windows.Media.MediaPlayer> um e <xref:System.Windows.Media.VideoDrawing> um para reproduzir um vídeo repetidamente.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Observe que <xref:System.Windows.Media.MediaTimeline>, ao usar um, você usa o interativo <xref:System.Windows.Media.Animation.ClockController> retornado <xref:System.Windows.Media.MediaClock> da <xref:System.Windows.Media.Animation.Clock.Controller%2A> Propriedade do para controlar a reprodução de mídia em vez dos métodos interativos <xref:System.Windows.Media.MediaPlayer>do.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Desenhar texto  
 Para desenhar texto, use um <xref:System.Windows.Media.GlyphRunDrawing> e um. <xref:System.Windows.Media.GlyphRun> O exemplo a seguir usa <xref:System.Windows.Media.GlyphRunDrawing> um para desenhar o texto "Olá, mundo".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Um <xref:System.Windows.Media.GlyphRun> é um objeto de baixo nível destinado ao uso com cenários de apresentação e impressão de documentos de formato fixo. Uma maneira mais simples de desenhar texto na tela é usar um <xref:System.Windows.Controls.Label> ou um. <xref:System.Windows.Controls.TextBlock> Para obter mais informações <xref:System.Windows.Media.GlyphRun>sobre, consulte a [introdução ao objeto GlyphRun e a visão geral do elemento Glyphs](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) .  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Desenhos de composição  
 Um <xref:System.Windows.Media.DrawingGroup> permite que você combine vários desenhos em um único desenho composto. Usando um <xref:System.Windows.Media.DrawingGroup>, você pode combinar formas, imagens e texto em um único <xref:System.Windows.Media.Drawing> objeto.  
  
 O exemplo a seguir usa <xref:System.Windows.Media.DrawingGroup> um para combinar <xref:System.Windows.Media.GeometryDrawing> dois objetos e <xref:System.Windows.Media.ImageDrawing> um objeto. Este exemplo gerencia a seguinte saída.  
  
 ![Um DrawingGroup com vários desenhos](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Um desenho de composição  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Um <xref:System.Windows.Media.DrawingGroup> também permite aplicar máscaras de opacidade, transformações, efeitos de bitmap e outras operações ao seu conteúdo. <xref:System.Windows.Media.DrawingGroup>as operações são aplicadas na seguinte ordem: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>,,, e, em <xref:System.Windows.Media.DrawingGroup.Transform%2A>seguida.  
  
 A ilustração a seguir mostra a ordem na <xref:System.Windows.Media.DrawingGroup> qual as operações são aplicadas.  
  
 ![Ordem das operações do DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordem das operações do DrawingGroup  
  
 A tabela a seguir descreve as propriedades que você pode usar para <xref:System.Windows.Media.DrawingGroup> manipular o conteúdo de um objeto.  
  
|Propriedade|Descrição|Ilustração|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Altera a opacidade das partes selecionadas do <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [ Controle a opacidade de um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Um DrawingGroup com uma máscara de opacidade](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Altera uniformemente a opacidade do <xref:System.Windows.Media.DrawingGroup> conteúdo. Use essa propriedade para tornar <xref:System.Windows.Media.Drawing> transparente ou parcialmente transparente. Para obter um exemplo, consulte [ Aplicar uma máscara de opacidade a um](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))desenho.|![DrawingGroups com diferentes configurações de opacidade](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Aplica um <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Media.DrawingGroup> ao conteúdo. Para obter um exemplo, consulte [ Aplicar um BitmapEffect a um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup com um BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Corta o <xref:System.Windows.Media.DrawingGroup> conteúdo para uma região que você descreve usando <xref:System.Windows.Media.Geometry>um. Para obter um exemplo, consulte [ Recorte um](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) desenho.|![DrawingGroup com uma região de recorte definida](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Ajusta os pixels independentes de dispositivo aos pixels do dispositivo, conforme as diretrizes especificadas. Essa propriedade é útil para assegurar que gráficos detalhados minuciosamente sejam renderizados com nitidez em monitores de baixo DPI. Para obter um exemplo, consulte [Instruções: aplicar um GuidelineSet a um desenho](how-to-apply-a-guidelineset-to-a-drawing.md).|![Um DrawingGroup com e sem um GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforma o <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [ Aplicar uma transformação a um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Um DrawingGroup girado](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Exibir um desenho como uma imagem  
 Para exibir um <xref:System.Windows.Media.Drawing> com um <xref:System.Windows.Controls.Image> controle, use <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> um como o controle <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> e defina a propriedade do objeto para o desenho que você deseja exibir. <xref:System.Windows.Controls.Image.Source%2A>  
  
 O exemplo a seguir usa <xref:System.Windows.Media.DrawingImage> um e <xref:System.Windows.Controls.Image> um controle para exibir <xref:System.Windows.Media.GeometryDrawing>um. Este exemplo gerencia a seguinte saída.  
  
 ![Uma GeometryDrawing de duas reticências](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Uma DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Pintar um objeto com um desenho  
 Um <xref:System.Windows.Media.DrawingBrush> é um tipo de pincel que pinta uma área com um objeto de desenho. Você pode usá-lo para pintar praticamente qualquer objeto gráfico com um desenho. A <xref:System.Windows.Media.Drawing> propriedade de um <xref:System.Windows.Media.DrawingBrush> descreve seu <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Para renderizar <xref:System.Windows.Media.Drawing> um com <xref:System.Windows.Media.DrawingBrush>um, adicione-o ao Pincel usando a propriedade <xref:System.Windows.Media.Drawing> do pincel e use o pincel para pintar um objeto gráfico, como um controle ou painel.  
  
 Os exemplos a seguir usam <xref:System.Windows.Media.DrawingBrush> um para pintar <xref:System.Windows.Shapes.Shape.Fill%2A> o de <xref:System.Windows.Shapes.Rectangle> um com um padrão criado a <xref:System.Windows.Media.GeometryDrawing>partir de um. Este exemplo gerencia a seguinte saída.  
  
 ![Um DrawingBrush à lado](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
Um GeometryDrawing usado com um DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 A <xref:System.Windows.Media.DrawingBrush> classe fornece uma variedade de opções para alongar e organizar seu conteúdo em blocos. Para obter mais informações <xref:System.Windows.Media.DrawingBrush>sobre o, consulte a visão geral sobre [pintura com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Renderizar um desenho com um Visual  
 Um <xref:System.Windows.Media.DrawingVisual> é um tipo de objeto visual projetado para renderizar um desenho. Trabalhar diretamente com a camada de visual é uma opção para os desenvolvedores que desejam criar um ambiente gráfico altamente personalizado, mas isso não está descrito nesta visão geral. Para obter mais informações, consulte a visão geral [Usando objetos DrawingVisual](using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Objetos DrawingContext  
 A <xref:System.Windows.Media.DrawingContext> classe permite que você preencha um <xref:System.Windows.Media.Visual> ou um <xref:System.Windows.Media.Drawing> com conteúdo visual. Muitos desses objetos gráficos de nível inferior usam um <xref:System.Windows.Media.DrawingContext> porque ele descreve o conteúdo gráfico com muita eficiência.  
  
 Embora os <xref:System.Windows.Media.DrawingContext> métodos Draw pareçam semelhantes aos métodos Draw <xref:System.Drawing.Graphics?displayProperty=nameWithType> do tipo, eles são, na verdade, muito diferentes. <xref:System.Windows.Media.DrawingContext>é usado com um sistema gráfico de modo retido, enquanto o <xref:System.Drawing.Graphics?displayProperty=nameWithType> tipo é usado com um sistema gráfico de modo imediato. Quando você usa os <xref:System.Windows.Media.DrawingContext> comandos Draw de um objeto, na verdade você está armazenando um conjunto de instruções de renderização (embora o mecanismo de armazenamento exato dependa do tipo <xref:System.Windows.Media.DrawingContext>de objeto que fornece o) que será usado posteriormente pelo sistema de gráficos; Não estão desenhando na tela em tempo real. Para obter mais informações sobre como o sistema gráfico do Windows Presentation Foundation (WPF) funciona, consulte a [visão geral da renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).  
  
 Você nunca instancia diretamente um <xref:System.Windows.Media.DrawingContext>; você pode, no entanto, adquirir um contexto de desenho de determinados métodos <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> , <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>como e.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Enumerar o conteúdo de um Visual  
 Além de seus outros usos, <xref:System.Windows.Media.Drawing> os objetos também fornecem um modelo de objeto para enumerar o conteúdo de um. <xref:System.Windows.Media.Visual>  
  
 O exemplo a seguir usa <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> o método para recuperar <xref:System.Windows.Media.DrawingGroup> o valor de <xref:System.Windows.Media.Visual> a e enumerá-lo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de geometria](geometry-overview.md)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Tópicos de instruções](drawings-how-to-topics.md)
