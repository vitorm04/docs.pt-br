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
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186533"
---
# <a name="drawing-objects-overview"></a>Visão geral dos objetos de desenho
Este tópico <xref:System.Windows.Media.Drawing> introduz objetos e descreve como usá-los para desenhar formas, bitmaps, texto e mídia de formas eficientes. Use <xref:System.Windows.Media.Drawing> objetos quando criar clipart, pintar com um <xref:System.Windows.Media.DrawingBrush>ou usar <xref:System.Windows.Media.Visual> objetos.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>O que é um objeto de desenho?  
 Um <xref:System.Windows.Media.Drawing> objeto descreve conteúdo visível, como uma forma, bitmap, vídeo ou uma linha de texto. Diferentes tipos de desenhos descrevem diferentes tipos de conteúdo. A seguir está uma lista dos diferentes tipos de objetos de desenho.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Desenha uma forma.  
  
- <xref:System.Windows.Media.ImageDrawing>– Desenha uma imagem.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Desenha texto.  
  
- <xref:System.Windows.Media.VideoDrawing>– Reproduz um arquivo de áudio ou vídeo.  
  
- <xref:System.Windows.Media.DrawingGroup>– Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho de composição.  
  
 <xref:System.Windows.Media.Drawing>objetos são versáteis; há muitas maneiras de <xref:System.Windows.Media.Drawing> usar um objeto.  
  
- Você pode exibi-lo como <xref:System.Windows.Media.DrawingImage> uma <xref:System.Windows.Controls.Image> imagem usando um e um controle.  
  
- Você pode usá-lo com um <xref:System.Windows.Media.DrawingBrush> para <xref:System.Windows.Controls.Page.Background%2A> pintar <xref:System.Windows.Controls.Page>um objeto, como o de um .  
  
- Você pode usá-lo para <xref:System.Windows.Media.DrawingVisual>descrever a aparência de um .  
  
- Você pode usá-lo para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.  
  
 O WPF fornece outros tipos de objetos que são capazes de desenhar formas, bitmaps, texto e mídia. Por exemplo, você <xref:System.Windows.Shapes.Shape> também pode usar objetos <xref:System.Windows.Controls.MediaElement> para desenhar formas, e o controle fornece outra maneira de adicionar vídeo ao seu aplicativo. Então, quando você <xref:System.Windows.Media.Drawing> deve usar objetos? Quando você pode sacrificar recursos de nível de <xref:System.Windows.Freezable> estrutura para obter benefícios de desempenho ou quando você precisa de recursos. Como <xref:System.Windows.Media.Drawing> os objetos não têm suporte para [layout,](../advanced/layout.md)entrada e foco, eles fornecem benefícios de desempenho que <xref:System.Windows.Media.Visual> os tornam ideais para descrever fundos, clip-art e para desenho de baixo nível com objetos.  
  
 Por serem um <xref:System.Windows.Freezable> objeto <xref:System.Windows.Media.Drawing> de tipo, os objetos ganham vários recursos especiais, que incluem o seguinte: eles podem ser declarados como [recursos,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)compartilhados entre vários objetos, feitos somente de leitura para melhorar o desempenho, clonados e feitos como thread-safe. Para obter mais informações sobre <xref:System.Windows.Freezable> os diferentes recursos fornecidos pelos objetos, consulte a visão geral dos [objetos acongelamento](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Desenhar uma forma  
 Para desenhar uma forma, <xref:System.Windows.Media.GeometryDrawing>você usa um . A propriedade de <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> um desenho de geometria <xref:System.Windows.Media.GeometryDrawing.Brush%2A> descreve a forma de desenhar, sua propriedade <xref:System.Windows.Media.GeometryDrawing.Pen%2A> descreve como o interior da forma deve ser pintado, e sua propriedade descreve como seu contorno deve ser desenhado.  
  
 O exemplo a <xref:System.Windows.Media.GeometryDrawing> seguir usa um para desenhar uma forma. A forma é <xref:System.Windows.Media.GeometryGroup> descrita <xref:System.Windows.Media.EllipseGeometry> por um e dois objetos. O interior da forma é <xref:System.Windows.Media.LinearGradientBrush> pintado com um e <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>seu contorno é desenhado com um .  
  
 Este exemplo cria <xref:System.Windows.Media.GeometryDrawing>o seguinte .  
  
 ![Um GeometryDrawing de duas elipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Um GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Para obter o exemplo completo, consulte [Instruções: criar um GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Outras <xref:System.Windows.Media.Geometry> classes, <xref:System.Windows.Media.PathGeometry> como a habilitação de criar formas mais complexas, criando curvas e arcos. Para obter <xref:System.Windows.Media.Geometry> mais informações sobre objetos, consulte a [visão geral da geometria](geometry-overview.md).  
  
 Para obter mais informações sobre outras formas <xref:System.Windows.Media.Drawing> de desenhar formas que não usam objetos, consulte [Formas e Desenho Básico em Visão Geral do WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Desenhar uma imagem  
 Para desenhar uma imagem, <xref:System.Windows.Media.ImageDrawing>você usa um . A <xref:System.Windows.Media.ImageDrawing> propriedade <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> de um objeto descreve a <xref:System.Windows.Media.ImageDrawing.Rect%2A> imagem a ser desenhada, e sua propriedade define a região onde a imagem é desenhada.  
  
 O exemplo a seguir desenha uma imagem em um retângulo localizado em (75,75) que tem 100 por 100 pixels. A ilustração <xref:System.Windows.Media.ImageDrawing> a seguir mostra o criado pelo exemplo. Uma borda cinza foi adicionada para <xref:System.Windows.Media.ImageDrawing>mostrar os limites do .  
  
 ![Um ImageDrawing de 100 por 100 desenhado a &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
Um ImageDrawing de 100 por 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Para obter mais informações sobre imagens, consulte [Visão geral de imagens](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Reproduzir mídia (apenas código)  
  
> [!NOTE]
> Embora você possa <xref:System.Windows.Media.VideoDrawing> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]declarar um in , você só pode carregar e reproduzir sua mídia usando código. Para reproduzir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]vídeo, <xref:System.Windows.Controls.MediaElement> use um em vez disso.  
  
 Para reproduzir um arquivo de áudio <xref:System.Windows.Media.VideoDrawing> ou <xref:System.Windows.Media.MediaPlayer>vídeo, você usa um e um . Há duas maneiras de carregar e reproduzir mídia. A primeira é <xref:System.Windows.Media.MediaPlayer> usar <xref:System.Windows.Media.VideoDrawing> um e um por si só, e a segunda maneira é criar o seu próprio <xref:System.Windows.Media.MediaTimeline> para usar com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
 Para reproduzir mídia sem criar a sua própria, <xref:System.Windows.Media.MediaTimeline>você executa as seguintes etapas.  
  
1. Crie um objeto <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Use <xref:System.Windows.Media.MediaPlayer.Open%2A> o método para carregar o arquivo de mídia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Criará um <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Especifique o tamanho e o <xref:System.Windows.Media.VideoDrawing.Rect%2A> local <xref:System.Windows.Media.VideoDrawing>para desenhar a mídia definindo a propriedade do .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Defina <xref:System.Windows.Media.VideoDrawing.Player%2A> a <xref:System.Windows.Media.VideoDrawing> propriedade <xref:System.Windows.Media.MediaPlayer> do com o que você criou.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Use <xref:System.Windows.Media.MediaPlayer.Play%2A> o método <xref:System.Windows.Media.MediaPlayer> do para começar a reproduzir a mídia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 O exemplo a <xref:System.Windows.Media.VideoDrawing> seguir <xref:System.Windows.Media.MediaPlayer> usa a e a para reproduzir um arquivo de vídeo uma vez.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Para obter controle de tempo adicional <xref:System.Windows.Media.MediaTimeline> sobre <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> a mídia, use um com o e objetos. O <xref:System.Windows.Media.MediaTimeline> habilita-se a especificar se o vídeo deve se repetir. Para usar <xref:System.Windows.Media.MediaTimeline> um <xref:System.Windows.Media.VideoDrawing>com a, você executa as seguintes etapas:  
  
1. Declare <xref:System.Windows.Media.MediaTimeline> o e defina seus comportamentos de tempo.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Crie <xref:System.Windows.Media.MediaClock> um <xref:System.Windows.Media.MediaTimeline>a partir do .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Crie <xref:System.Windows.Media.MediaPlayer> um e <xref:System.Windows.Media.MediaClock> use <xref:System.Windows.Media.MediaPlayer.Clock%2A> o para definir sua propriedade.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Criar <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer> atribuir <xref:System.Windows.Media.VideoDrawing.Player%2A> a propriedade <xref:System.Windows.Media.VideoDrawing>do .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 O exemplo a <xref:System.Windows.Media.MediaTimeline> seguir <xref:System.Windows.Media.MediaPlayer> usa <xref:System.Windows.Media.VideoDrawing> um com a e a para reproduzir um vídeo repetidamente.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Observe que, quando <xref:System.Windows.Media.MediaTimeline>você usa um <xref:System.Windows.Media.Animation.ClockController> , você <xref:System.Windows.Media.Animation.Clock.Controller%2A> usa <xref:System.Windows.Media.MediaClock> o retorno interativo da propriedade do <xref:System.Windows.Media.MediaPlayer>para controlar a reprodução de mídia em vez dos métodos interativos de .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Desenhar texto  
 Para desenhar texto, <xref:System.Windows.Media.GlyphRunDrawing> você <xref:System.Windows.Media.GlyphRun>usa um e um . O exemplo a <xref:System.Windows.Media.GlyphRunDrawing> seguir usa um para desenhar o texto "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> é um objeto de baixo nível destinado a ser usado com apresentação de documentos em formato fixo e cenários de impressão. Uma maneira mais simples de desenhar texto <xref:System.Windows.Controls.Label> para <xref:System.Windows.Controls.TextBlock>a tela é usar um ou um . Para obter <xref:System.Windows.Media.GlyphRun>mais informações sobre, consulte a introdução à visão geral [do Elemento GlyphRun e do Elemento Glifos.](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Desenhos de composição  
 A <xref:System.Windows.Media.DrawingGroup> permite que você combine vários desenhos em um único desenho composto. Usando um <xref:System.Windows.Media.DrawingGroup>, você pode combinar formas, imagens e texto em um único <xref:System.Windows.Media.Drawing> objeto.  
  
 O exemplo a <xref:System.Windows.Media.DrawingGroup> seguir <xref:System.Windows.Media.GeometryDrawing> usa um <xref:System.Windows.Media.ImageDrawing> para combinar dois objetos e um objeto. Este exemplo gerencia a seguinte saída.  
  
 ![Um DrawingGroup com vários desenhos](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Um desenho de composição  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> também permite que você aplique máscaras de opacidade, transformações, efeitos de bitmap e outras operações ao seu conteúdo. <xref:System.Windows.Media.DrawingGroup>as operações são aplicadas <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> <xref:System.Windows.Media.DrawingGroup.Opacity%2A>na <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>seguinte <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>ordem: <xref:System.Windows.Media.DrawingGroup.Transform%2A>, , , , , e depois .  
  
 A ilustração a seguir <xref:System.Windows.Media.DrawingGroup> mostra a ordem em que as operações são aplicadas.  
  
 ![Ordem das operações do DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordem das operações do DrawingGroup  
  
 A tabela a seguir descreve as propriedades <xref:System.Windows.Media.DrawingGroup> que você pode usar para manipular o conteúdo de um objeto.  
  
|Propriedade|Descrição|Ilustração|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Altera a opacidade das partes <xref:System.Windows.Media.DrawingGroup> selecionadas do conteúdo. Para obter um exemplo, consulte [Instruções: controlar a opacidade de um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Um DrawingGroup com uma máscara de opacidade](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Muda uniformemente a opacidade do <xref:System.Windows.Media.DrawingGroup> conteúdo. Use esta propriedade <xref:System.Windows.Media.Drawing> para tornar transparente ou parcialmente transparente. Para obter um exemplo, consulte [Instruções: aplicar uma máscara de opacidade a um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DesenhoGrupos com diferentes configurações de opacidade](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Aplica a <xref:System.Windows.Media.Effects.BitmapEffect> ao <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [Instruções: aplicar um BitmapEffect a um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup com um BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Clipes <xref:System.Windows.Media.DrawingGroup> do conteúdo para uma <xref:System.Windows.Media.Geometry>região que você descreve usando um . Para obter um exemplo, consulte [Instruções: recortar um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)).|![DrawingGroup com uma região de clipe definida](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Ajusta os pixels independentes de dispositivo aos pixels do dispositivo, conforme as diretrizes especificadas. Essa propriedade é útil para assegurar que gráficos detalhados minuciosamente sejam renderizados com nitidez em monitores de baixo DPI. Para obter um exemplo, consulte [Instruções: aplicar um GuidelineSet a um desenho](how-to-apply-a-guidelineset-to-a-drawing.md).|![Um DrawingGroup com e sem um Conjunto de Diretrizes](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforma o <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [Instruções: aplicar uma transformação a um desenho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Um Grupo de Desenho rotativo](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Exibir um desenho como uma imagem  
 Para exibir <xref:System.Windows.Media.Drawing> um <xref:System.Windows.Controls.Image> com um <xref:System.Windows.Media.DrawingImage> controle, use <xref:System.Windows.Controls.Image.Source%2A> um <xref:System.Windows.Media.DrawingImage> como controle <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Image> e defina a propriedade do objeto para o desenho que deseja exibir.  
  
 O exemplo a <xref:System.Windows.Media.DrawingImage> seguir <xref:System.Windows.Controls.Image> usa um <xref:System.Windows.Media.GeometryDrawing>e um controle para exibir um . Este exemplo gerencia a seguinte saída.  
  
 ![Um GeometryDrawing de duas elipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Uma DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Pintar um objeto com um desenho  
 A <xref:System.Windows.Media.DrawingBrush> é um tipo de pincel que pinta uma área com um objeto de desenho. Você pode usá-lo para pintar praticamente qualquer objeto gráfico com um desenho. A <xref:System.Windows.Media.Drawing> propriedade <xref:System.Windows.Media.DrawingBrush> de um <xref:System.Windows.Media.DrawingBrush.Drawing%2A>descreve sua. Para renderizar <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush>um com um , adicione-o <xref:System.Windows.Media.Drawing> ao pincel usando a propriedade do pincel e use o pincel para pintar um objeto gráfico, como um controle ou painel.  
  
 Os exemplos a <xref:System.Windows.Media.DrawingBrush> seguir usam <xref:System.Windows.Shapes.Shape.Fill%2A> um <xref:System.Windows.Shapes.Rectangle> para pintar o <xref:System.Windows.Media.GeometryDrawing>de um com um padrão criado a partir de um . Este exemplo gerencia a seguinte saída.  
  
 ![DrawingBrush organizado lado a lado](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
Um GeometryDrawing usado com um DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 A <xref:System.Windows.Media.DrawingBrush> classe oferece uma variedade de opções para alongamento e revestimento de seu conteúdo. Para obter <xref:System.Windows.Media.DrawingBrush>mais informações sobre , consulte a visão geral [da Pintura com Imagens, Desenhos e Visuais.](painting-with-images-drawings-and-visuals.md)  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Renderizar um desenho com um Visual  
 A <xref:System.Windows.Media.DrawingVisual> é um tipo de objeto visual projetado para renderizar um desenho. Trabalhar diretamente com a camada de visual é uma opção para os desenvolvedores que desejam criar um ambiente gráfico altamente personalizado, mas isso não está descrito nesta visão geral. Para obter mais informações, consulte a visão geral [Usando objetos DrawingVisual](using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>Objetos DrawingContext  
 A <xref:System.Windows.Media.DrawingContext> classe permite que <xref:System.Windows.Media.Visual> você <xref:System.Windows.Media.Drawing> preencha um ou um com conteúdo visual. Muitos desses objetos gráficos <xref:System.Windows.Media.DrawingContext> de nível inferior usam a porque descreve o conteúdo gráfico de forma muito eficiente.  
  
 Embora <xref:System.Windows.Media.DrawingContext> os métodos de desenho pareçam semelhantes aos métodos de desenho do <xref:System.Drawing.Graphics?displayProperty=nameWithType> tipo, eles são realmente muito diferentes. <xref:System.Windows.Media.DrawingContext>é usado com um sistema gráfico <xref:System.Drawing.Graphics?displayProperty=nameWithType> de modo retido, enquanto o tipo é usado com um sistema gráfico de modo imediato. Quando você <xref:System.Windows.Media.DrawingContext> usa os comandos de desenho de um objeto, você está realmente armazenando um conjunto de instruções de renderização (embora o mecanismo exato de armazenamento dependa do tipo de objeto que fornece o <xref:System.Windows.Media.DrawingContext>) que mais tarde será usado pelo sistema gráfico; você não está desenhando para a tela em tempo real. Para obter mais informações sobre como funciona o sistema gráfico do Windows Presentation Foundation (WPF), consulte a [visão geral da renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).  
  
 Você nunca instancia diretamente um; <xref:System.Windows.Media.DrawingContext> você pode, no entanto, adquirir um contexto <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>de desenho a partir de certos métodos, tais como e .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Enumerar o conteúdo de um Visual  
 Além de seus outros <xref:System.Windows.Media.Drawing> usos, os objetos também fornecem <xref:System.Windows.Media.Visual>um modelo de objeto para enumerar o conteúdo de a .  
  
 O exemplo a <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> seguir usa <xref:System.Windows.Media.DrawingGroup> o <xref:System.Windows.Media.Visual> método para recuperar o valor de a eenumerar-lo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de geometria](geometry-overview.md)
- [Visão geral de formas e desenhos básicos no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Tópicos de como fazer](drawings-how-to-topics.md)
