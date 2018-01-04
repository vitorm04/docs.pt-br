---
title: "Visão geral dos objetos de desenho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abdc98a6fbf48a30f2f5702e7c2d78396381de6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="drawing-objects-overview"></a>Visão geral dos objetos de desenho
Este tópico apresenta <xref:System.Windows.Media.Drawing> objetos e descreve como usá-los para desenhar formas, bitmaps, texto e mídia de forma eficiente. Use <xref:System.Windows.Media.Drawing> pintar objetos quando você cria clip-art, com um <xref:System.Windows.Media.DrawingBrush>, ou use <xref:System.Windows.Media.Visual> objetos.  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>O que é um objeto de desenho?  
 Um <xref:System.Windows.Media.Drawing> objeto descreve conteúdo visível, como uma forma, bitmap, vídeo ou uma linha de texto. Diferentes tipos de desenhos descrevem diferentes tipos de conteúdo. A seguir está uma lista dos diferentes tipos de objetos de desenho.  
  
-   <xref:System.Windows.Media.GeometryDrawing>--Desenha uma forma.  
  
-   <xref:System.Windows.Media.ImageDrawing>--Desenha uma imagem.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>--Desenha texto.  
  
-   <xref:System.Windows.Media.VideoDrawing>– Executa um arquivo de áudio ou vídeo.  
  
-   <xref:System.Windows.Media.DrawingGroup>--Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho composto.  
  
 <xref:System.Windows.Media.Drawing>objetos são versáteis; Há muitas maneiras que você pode usar um <xref:System.Windows.Media.Drawing> objeto.  
  
-   Você pode exibi-lo como uma imagem usando uma <xref:System.Windows.Media.DrawingImage> e um <xref:System.Windows.Controls.Image> controle.  
  
-   Você pode usá-lo com um <xref:System.Windows.Media.DrawingBrush> para pintar um objeto, como o <xref:System.Windows.Controls.Page.Background%2A> de um <xref:System.Windows.Controls.Page>.  
  
-   Você pode usá-lo para descrever a aparência de um <xref:System.Windows.Media.DrawingVisual>.  
  
-   Você pode usá-lo para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.  
  
 O WPF fornece outros tipos de objetos que são capazes de desenhar formas, bitmaps, texto e mídia. Por exemplo, você também pode usar <xref:System.Windows.Shapes.Shape> objetos para desenhar formas e o <xref:System.Windows.Controls.MediaElement> controle oferece uma maneira de adicionar um vídeo a seu aplicativo. Então quando você deve usar <xref:System.Windows.Media.Drawing> objetos? Quando você puder sacrificar características de nível de framework para obter benefícios de desempenho ou quando você precisar <xref:System.Windows.Freezable> recursos. Porque <xref:System.Windows.Media.Drawing> objetos não têm suporte para [Layout](../../../../docs/framework/wpf/advanced/layout.md), entrada e foco, eles fornecem benefícios de desempenho que os tornam ideais para descrever clip-art, desenho de baixo nível com <xref:System.Windows.Media.Visual> objetos.  
  
 Porque eles são um tipo <xref:System.Windows.Freezable> objeto, <xref:System.Windows.Media.Drawing> objetos obtém vários recursos especiais, que incluem o seguinte: eles podem ser declarados como [recursos](../../../../docs/framework/wpf/advanced/xaml-resources.md), compartilhados entre vários objetos, feitos somente leitura para melhorar desempenho, clonados e tornados thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos pelo <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Desenhar uma forma  
 Para desenhar uma forma, você deve usar um <xref:System.Windows.Media.GeometryDrawing>. Um desenho de geometria <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> propriedade descreve a forma ao desenhar, seu <xref:System.Windows.Media.GeometryDrawing.Brush%2A> propriedade descreve como o interior da forma deve ser pintado e sua <xref:System.Windows.Media.GeometryDrawing.Pen%2A> propriedade descreve como seu contorno deve ser desenhado.  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.GeometryDrawing> para desenhar uma forma. A forma é descrita por um <xref:System.Windows.Media.GeometryGroup> e dois <xref:System.Windows.Media.EllipseGeometry> objetos. O interior da forma é pintado com um <xref:System.Windows.Media.LinearGradientBrush> e seu contorno é desenhado com uma <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Este exemplo cria o seguinte <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![Um GeometryDrawing de duas elipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Um GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Para obter o exemplo completo, consulte [Instruções: criar um GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 Outros <xref:System.Windows.Media.Geometry> classes, como <xref:System.Windows.Media.PathGeometry> permitem que você crie formas mais complexas criando curvas e arcos. Para obter mais informações sobre <xref:System.Windows.Media.Geometry> objetos, consulte o [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Para obter mais informações sobre outras maneiras para desenhar formas que não usam <xref:System.Windows.Media.Drawing> objetos, consulte [formas e desenho básico no WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Desenhar uma imagem  
 Para desenhar uma imagem, você deve usar um <xref:System.Windows.Media.ImageDrawing>. Um <xref:System.Windows.Media.ImageDrawing> do objeto <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> propriedade descreve a imagem a ser desenhada e sua <xref:System.Windows.Media.ImageDrawing.Rect%2A> propriedade define a região onde a imagem é desenhada.  
  
 O exemplo a seguir desenha uma imagem em um retângulo localizado em (75,75) que tem 100 por 100 pixels. A ilustração a seguir mostra o <xref:System.Windows.Media.ImageDrawing> criado pelo exemplo. Uma borda cinza foi adicionada para mostrar os limites do <xref:System.Windows.Media.ImageDrawing>.  
  
 ![Um ImageDrawing 100 por 100 desenhado em &#40; 75,75 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
Um ImageDrawing de 100 por 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Para obter mais informações sobre imagens, consulte [Visão geral de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Reproduzir mídia (apenas código)  
  
> [!NOTE]
>  Embora seja possível declarar um <xref:System.Windows.Media.VideoDrawing> em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você só pode carregar e reproduzir sua mídia utilizando código. Para reproduzir o vídeo de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], use um <xref:System.Windows.Controls.MediaElement> em vez disso.  
  
 Para reproduzir um arquivo de áudio ou vídeo, você deve usar um <xref:System.Windows.Media.VideoDrawing> e um <xref:System.Windows.Media.MediaPlayer>. Há duas maneiras de carregar e reproduzir mídia. A primeira é usar um <xref:System.Windows.Media.MediaPlayer> e um <xref:System.Windows.Media.VideoDrawing> por si só e a segunda maneira é criar seus próprios <xref:System.Windows.Media.MediaTimeline> para usar com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
 Para reproduzir mídia sem criar seu próprio <xref:System.Windows.Media.MediaTimeline>, execute as seguintes etapas.  
  
1.  Crie um objeto <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Use o <xref:System.Windows.Media.MediaPlayer.Open%2A> método para carregar o arquivo de mídia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Criará um <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Especifique o tamanho e local para desenhar a mídia definindo a <xref:System.Windows.Media.VideoDrawing.Rect%2A> propriedade o <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Definir o <xref:System.Windows.Media.VideoDrawing.Player%2A> propriedade do <xref:System.Windows.Media.VideoDrawing> com o <xref:System.Windows.Media.MediaPlayer> criado por você.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Use o <xref:System.Windows.Media.MediaPlayer.Play%2A> método o <xref:System.Windows.Media.MediaPlayer> para iniciar a reprodução de mídia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.VideoDrawing> e um <xref:System.Windows.Media.MediaPlayer> para reproduzir um arquivo de vídeo uma vez.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Para obter controle adicional sobre a mídia de tempo, use um <xref:System.Windows.Media.MediaTimeline> com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing> objetos. O <xref:System.Windows.Media.MediaTimeline> permite que você especifique se o vídeo deve ser repetida. Para usar um <xref:System.Windows.Media.MediaTimeline> com um <xref:System.Windows.Media.VideoDrawing>, execute as seguintes etapas:  
  
1.  Declare o <xref:System.Windows.Media.MediaTimeline> e defina seu comportamento de tempo.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Criar um <xref:System.Windows.Media.MediaClock> do <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Criar um <xref:System.Windows.Media.MediaPlayer> e usar o <xref:System.Windows.Media.MediaClock> para definir seu <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriedade.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Criar um <xref:System.Windows.Media.VideoDrawing> e atribua o <xref:System.Windows.Media.MediaPlayer> para o <xref:System.Windows.Media.VideoDrawing.Player%2A> propriedade o <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.MediaTimeline> com um <xref:System.Windows.Media.MediaPlayer> e um <xref:System.Windows.Media.VideoDrawing> para executar um vídeo repetidamente.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Observe que, quando você usa um <xref:System.Windows.Media.MediaTimeline>, você usa o interativo <xref:System.Windows.Media.Animation.ClockController> retornado do <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriedade do <xref:System.Windows.Media.MediaClock> para controlar a reprodução de mídia em vez dos métodos interativos do <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Desenhar texto  
 Para desenhar texto, você deve usar um <xref:System.Windows.Media.GlyphRunDrawing> e um <xref:System.Windows.Media.GlyphRun>. O exemplo a seguir usa um <xref:System.Windows.Media.GlyphRunDrawing> para desenhar o texto "Olá, mundo".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Um <xref:System.Windows.Media.GlyphRun> é um objeto de baixo nível para uso com a apresentação do documento de formato fixo e cenários de impressão. Uma maneira simples de desenhar texto na tela é usar um <xref:System.Windows.Controls.Label> ou <xref:System.Windows.Controls.TextBlock>. Para obter mais informações sobre <xref:System.Windows.Media.GlyphRun>, consulte o [Introdução ao objeto GlyphRun e elemento Glyphs](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) visão geral.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Desenhos de composição  
 Um <xref:System.Windows.Media.DrawingGroup> permite que você combine múltiplos desenhos em um único desenho composto. Usando um <xref:System.Windows.Media.DrawingGroup>, você pode combinar formas, imagens e texto em uma única <xref:System.Windows.Media.Drawing> objeto.  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingGroup> para combinar dois <xref:System.Windows.Media.GeometryDrawing> objetos e um <xref:System.Windows.Media.ImageDrawing> objeto. Este exemplo gerencia a seguinte saída.  
  
 ![Um DrawingGroup com vários desenhos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Um desenho de composição  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Um <xref:System.Windows.Media.DrawingGroup> também permite que você aplique máscaras de opacidade, transformações, efeitos de bitmap e outras operações para seu conteúdo. <xref:System.Windows.Media.DrawingGroup>as operações são aplicadas na seguinte ordem: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>e, em seguida, <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 A ilustração a seguir mostra a ordem na qual <xref:System.Windows.Media.DrawingGroup> operações são aplicadas.  
  
 ![Ordem de DrawingGroup das operações](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordem das operações do DrawingGroup  
  
 A tabela a seguir descreve as propriedades que você pode usar para manipular um <xref:System.Windows.Media.DrawingGroup> conteúdo do objeto.  
  
|Propriedade|Descrição|Ilustração|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Altera a opacidade de partes selecionadas do <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [Instruções: controlar a opacidade de um desenho](http://msdn.microsoft.com/en-us/68580652-7d32-4d27-93cc-a5148cf4d5ee).|![Um DrawingGroup com uma máscara de opacidade](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Altera uniformemente a opacidade do <xref:System.Windows.Media.DrawingGroup> conteúdo. Use esta propriedade para tornar um <xref:System.Windows.Media.Drawing> transparente ou parcialmente transparente. Para obter um exemplo, consulte [Instruções: aplicar uma máscara de opacidade a um desenho](http://msdn.microsoft.com/en-us/d77b420b-9be2-479c-a45e-82f4da30eb9f).|![DrawingGroups com diferentes configurações de opacidade](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Aplica-se um <xref:System.Windows.Media.Effects.BitmapEffect> para o <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [Instruções: aplicar um BitmapEffect a um desenho](http://msdn.microsoft.com/en-us/c5b1de83-8d09-47fb-96db-5f174471f4b5).|![DrawingGroup com um BlurBitmapEffect](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Recorta o <xref:System.Windows.Media.DrawingGroup> o conteúdo para uma região descreve como usar um <xref:System.Windows.Media.Geometry>. Para obter um exemplo, consulte [Instruções: recortar um desenho](http://msdn.microsoft.com/en-us/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058).|![DrawingGroup com uma região de recorte definida](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Ajusta os pixels independentes de dispositivo aos pixels do dispositivo, conforme as diretrizes especificadas. Essa propriedade é útil para assegurar que gráficos detalhados minuciosamente sejam renderizados com nitidez em monitores de baixo DPI. Para obter um exemplo, consulte [Instruções: aplicar um GuidelineSet a um desenho](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).|![Um DrawingGroup com e sem um GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforma o <xref:System.Windows.Media.DrawingGroup> conteúdo. Para obter um exemplo, consulte [Instruções: aplicar uma transformação a um desenho](http://msdn.microsoft.com/en-us/0d525f2b-682d-4d67-9660-cf46929fbabd).|![Um DrawingGroup girado](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Exibir um desenho como uma imagem  
 Para exibir um <xref:System.Windows.Media.Drawing> com um <xref:System.Windows.Controls.Image> controlar, use um <xref:System.Windows.Media.DrawingImage> como o <xref:System.Windows.Controls.Image> do controle <xref:System.Windows.Controls.Image.Source%2A> e defina o <xref:System.Windows.Media.DrawingImage> do objeto <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> propriedade ao desenho que você deseja exibir.  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingImage> e um <xref:System.Windows.Controls.Image> controle para exibir um <xref:System.Windows.Media.GeometryDrawing>. Este exemplo gerencia a seguinte saída.  
  
 ![Um GeometryDrawing de duas elipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Uma DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Pintar um objeto com um desenho  
 Um <xref:System.Windows.Media.DrawingBrush> é um tipo de pincel que pinta uma área com um objeto de desenho. Você pode usá-lo para pintar praticamente qualquer objeto gráfico com um desenho. O <xref:System.Windows.Media.Drawing> propriedade de um <xref:System.Windows.Media.DrawingBrush> descreve seu <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Para renderizar um <xref:System.Windows.Media.Drawing> com um <xref:System.Windows.Media.DrawingBrush>, adicione-ao Pincel utilizando o pincel <xref:System.Windows.Media.Drawing> propriedade e use o pincel para desenhar um gráfico de objeto, como um controle ou painel.  
  
 Os exemplos a seguir usa uma <xref:System.Windows.Media.DrawingBrush> para pintar o <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Rectangle> com um padrão criado de um <xref:System.Windows.Media.GeometryDrawing>. Este exemplo gerencia a seguinte saída.  
  
 ![Um DrawingBrush lado a lado](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
Um GeometryDrawing usado com um DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 O <xref:System.Windows.Media.DrawingBrush> classe fornece uma variedade de opções para redimensionar e lado a lado seu conteúdo. Para obter mais informações sobre <xref:System.Windows.Media.DrawingBrush>, consulte o [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md) visão geral.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Renderizar um desenho com um Visual  
 Um <xref:System.Windows.Media.DrawingVisual> é um tipo de objeto visual projetado para renderizar um desenho. Trabalhar diretamente com a camada de visual é uma opção para os desenvolvedores que desejam criar um ambiente gráfico altamente personalizado, mas isso não está descrito nesta visão geral. Para obter mais informações, consulte a visão geral [Usando objetos DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Objetos DrawingContext  
 O <xref:System.Windows.Media.DrawingContext> classe permite que você popule um <xref:System.Windows.Media.Visual> ou <xref:System.Windows.Media.Drawing> com conteúdo visual. Usam esses objetos de gráfico de baixo nível um <xref:System.Windows.Media.DrawingContext> porque descreve conteúdo gráfico de maneira muito eficiente.  
  
 Embora o <xref:System.Windows.Media.DrawingContext> métodos de desenho pareçam semelhantes aos métodos de desenho de <xref:System.Drawing.Graphics?displayProperty=nameWithType> tipo, eles são realmente muito diferentes. <xref:System.Windows.Media.DrawingContext>é usada com um sistema de gráfico de modo retido, enquanto o <xref:System.Drawing.Graphics?displayProperty=nameWithType> tipo é usado com um sistema de gráfico de modo imediato. Quando você usa um <xref:System.Windows.Media.DrawingContext> comandos de desenho do objeto, na verdade você está armazenando um conjunto de instruções (embora o mecanismo de armazenamento exata depende do tipo de objeto que fornece o <xref:System.Windows.Media.DrawingContext>) que serão usados mais tarde pelo sistema gráfico; não estiver desenhando na tela em tempo real. Para obter mais informações sobre como o sistema gráfico do [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] funciona, consulte a [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Você nunca instancia diretamente um <xref:System.Windows.Media.DrawingContext>; no entanto, você pode adquirir um contexto de desenho de alguns métodos, como <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Enumerar o conteúdo de um Visual  
 Além de seus outros usos, <xref:System.Windows.Media.Drawing> objetos também fornecem um modelo de objeto para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.  
  
 O exemplo a seguir usa o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método para recuperar o <xref:System.Windows.Media.DrawingGroup> valor de um <xref:System.Windows.Media.Visual> e enumerá-lo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Visão geral de formas e desenho básico no WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)
