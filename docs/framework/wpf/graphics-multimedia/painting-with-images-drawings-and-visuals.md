---
title: Pintando com imagens, desenhos e visuais
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
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01939eb8735e6764e0f0cba811091c7fdbd6797f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="painting-with-images-drawings-and-visuals"></a>Pintando com imagens, desenhos e visuais
Este tópico descreve como usar <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, e <xref:System.Windows.Media.VisualBrush> objetos para pintar uma área com uma imagem, um <xref:System.Windows.Media.Drawing>, ou um <xref:System.Windows.Media.Visual>.  
    
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de pincéis que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece e seus recursos básicos. Para uma introdução, consulte a [Visão geral de pincéis do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Pintar uma área com uma imagem  
 Um <xref:System.Windows.Media.ImageBrush> pinta uma área com um <xref:System.Windows.Media.ImageSource>. O tipo mais comum de <xref:System.Windows.Media.ImageSource> para usar com um <xref:System.Windows.Media.ImageBrush> é um <xref:System.Windows.Media.Imaging.BitmapImage>, que descreve um gráfico de bitmap. Você pode usar um <xref:System.Windows.Media.DrawingImage> para pintar usando um <xref:System.Windows.Media.Drawing> objeto, mas é mais simples usar uma <xref:System.Windows.Media.DrawingBrush> em vez disso. Para obter mais informações sobre <xref:System.Windows.Media.ImageSource> objetos, consulte o [Imaging Overview](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
 Para pintar com um <xref:System.Windows.Media.ImageBrush>, crie um <xref:System.Windows.Media.Imaging.BitmapImage> e usá-lo para carregar o conteúdo do bitmap. Em seguida, use o <xref:System.Windows.Media.Imaging.BitmapImage> para definir o <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriedade o <xref:System.Windows.Media.ImageBrush>. Finalmente, aplique o <xref:System.Windows.Media.ImageBrush> para o objeto que deseja pintar.  Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode apenas definir o <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriedade o <xref:System.Windows.Media.ImageBrush> com o caminho da imagem para carregar.  
  
 Como todos os <xref:System.Windows.Media.Brush> objetos, um <xref:System.Windows.Media.ImageBrush> pode ser usado para pintar objetos, como formas, painéis, controles e texto. A ilustração a seguir mostra alguns efeitos que podem ser obtidos com um <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemplos de saída de ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objetos pintados por um ImageBrush  
  
 Por padrão, um <xref:System.Windows.Media.ImageBrush> alonga sua imagem para preencher completamente a área que está sendo pintada, possivelmente distorcendo a imagem se a área pintada tiver uma taxa de proporção diferente que a imagem. Você pode alterar esse comportamento alterando a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade do seu valor padrão de <xref:System.Windows.Media.Stretch.Fill> para <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, ou <xref:System.Windows.Media.Stretch.UniformToFill>. Porque <xref:System.Windows.Media.ImageBrush> é um tipo de <xref:System.Windows.Media.TileBrush>, você pode especificar exatamente como um pincel de imagem preenche a área de saída e até mesmo cria padrões. Para obter mais informações sobre avançadas <xref:System.Windows.Media.TileBrush> recursos, consulte o [TileBrush Overview](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Exemplo: pintar um objeto com uma imagem de bitmap  
 O exemplo a seguir usa uma <xref:System.Windows.Media.ImageBrush> para pintar o <xref:System.Windows.Controls.Panel.Background%2A> de um <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Pintar uma área com um desenho  
 Um <xref:System.Windows.Media.DrawingBrush> permite pintar uma área com formas, texto, imagens e vídeo. Formas dentro de um pincel de desenho podem ser próprias pintadas com uma cor sólida, gradiente, imagem, ou até mesmo de outro <xref:System.Windows.Media.DrawingBrush>. A ilustração a seguir demonstra alguns usos de um <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Exemplos de saída de DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objetos pintados por um DrawingBrush  
  
 Um <xref:System.Windows.Media.DrawingBrush> pinta uma área com um <xref:System.Windows.Media.Drawing> objeto. Um <xref:System.Windows.Media.Drawing> objeto descreve conteúdo visível, como uma forma, bitmap, vídeo ou uma linha de texto. Diferentes tipos de desenhos descrevem diferentes tipos de conteúdo. A seguir está uma lista dos diferentes tipos de objetos de desenho.  
  
-   <xref:System.Windows.Media.GeometryDrawing>--Desenha uma forma.  
  
-   <xref:System.Windows.Media.ImageDrawing>--Desenha uma imagem.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>--Desenha texto.  
  
-   <xref:System.Windows.Media.VideoDrawing>– Executa um arquivo de áudio ou vídeo.  
  
-   <xref:System.Windows.Media.DrawingGroup>--Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho composto.  
  
 Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte o [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
 Como um <xref:System.Windows.Media.ImageBrush>, um <xref:System.Windows.Media.DrawingBrush> alonga seu <xref:System.Windows.Media.DrawingBrush.Drawing%2A> para preencher sua área de saída. Você pode substituir esse comportamento alterando a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade da sua configuração padrão de <xref:System.Windows.Media.Stretch.Fill>. Para obter mais informações, consulte a propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Exemplo: pintar um objeto com um desenho  
 O exemplo a seguir mostra como pintar um objeto com um desenho de três elipses. Um <xref:System.Windows.Media.GeometryDrawing> é usado para descrever as reticências.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Pintar uma área com um visual  
 O mais versátil e eficiente de todos os cursores, o <xref:System.Windows.Media.VisualBrush> pinta uma área com um <xref:System.Windows.Media.Visual>. Um <xref:System.Windows.Media.Visual> é um tipo de gráfico de baixo nível que serve como o predecessor de vários componentes gráficos úteis. Por exemplo, o <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, e <xref:System.Windows.Controls.Control> classes são todos os tipos de <xref:System.Windows.Media.Visual> objetos. Usando um <xref:System.Windows.Media.VisualBrush>, você pode pintar áreas com praticamente qualquer [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objeto gráfico.  
  
> [!NOTE]
>  Embora <xref:System.Windows.Media.VisualBrush> é um tipo de <xref:System.Windows.Freezable> do objeto, ele não pode ser congelado (somente leitura) quando sua <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade é definida como um valor diferente de `null`.  
  
 Há duas maneiras para especificar o <xref:System.Windows.Media.VisualBrush.Visual%2A> conteúdo de um <xref:System.Windows.Media.VisualBrush>.  
  
-   Criar um novo <xref:System.Windows.Media.Visual> e usá-lo para definir o <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade o <xref:System.Windows.Media.VisualBrush>. Para obter um exemplo, consulte a seção [Exemplo: pintar um objeto com um Visual](#examplevisualbrush1) a seguir.  
  
-   Use um existente <xref:System.Windows.Media.Visual>, que cria uma imagem duplicada do destino <xref:System.Windows.Media.Visual>. Você pode usar o <xref:System.Windows.Media.VisualBrush> para criar efeitos interessantes, como reflexão e ampliação. Para obter um exemplo, consulte a seção [Exemplo: criar uma reflexão](#examplevisualbrush2).  
  
 Quando você define um novo <xref:System.Windows.Media.VisualBrush.Visual%2A> para um <xref:System.Windows.Media.VisualBrush> e que <xref:System.Windows.Media.Visual> é um <xref:System.Windows.UIElement> (como um painel ou controle), o sistema de layout é executado <xref:System.Windows.UIElement> e seus elementos filhos quando o <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> está definida como `true`. No entanto, a raiz <xref:System.Windows.UIElement> é essencialmente isolada do restante do sistema: estilos e layout externo não podem permear esse limite. Portanto, você deve especificar explicitamente o tamanho da raiz <xref:System.Windows.UIElement>, porque seu único pai é o <xref:System.Windows.Media.VisualBrush> e, portanto, ele não pode automaticamente redimensionar a mesmo para a área que está sendo pintada. Para mais informações sobre o layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md).  
  
 Como <xref:System.Windows.Media.ImageBrush> e <xref:System.Windows.Media.DrawingBrush>, um <xref:System.Windows.Media.VisualBrush> alonga seu conteúdo para preencher sua área de saída. Você pode substituir esse comportamento alterando a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade da sua configuração padrão de <xref:System.Windows.Media.Stretch.Fill>. Para obter mais informações, consulte a propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Exemplo: pintar um objeto com um visual  
 No exemplo a seguir, vários controles e um painel são usados para pintar um retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Exemplo: criar um reflexo  
 O exemplo anterior mostrou como criar um novo <xref:System.Windows.Media.Visual> para uso como um plano de fundo. Você também pode usar um <xref:System.Windows.Media.VisualBrush> para exibir um visual existente; esse recurso permite que você produzir efeitos visuais interessantes, como reflexos e ampliação. O exemplo a seguir usa uma <xref:System.Windows.Media.VisualBrush> para criar um reflexo de um <xref:System.Windows.Controls.Border> que contém vários elementos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um objeto Visual de refletidas](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Um objeto visual refletido  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Para outros exemplos que mostram como ampliar partes da tela e como criar reflexões, consulte o [Exemplo do VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Recursos do TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, e <xref:System.Windows.Media.VisualBrush> são tipos de <xref:System.Windows.Media.TileBrush> objetos. <xref:System.Windows.Media.TileBrush>objetos oferecem uma grande quantidade de controle sobre como uma área é pintada com uma imagem, desenho ou visual. Por exemplo, em vez de apenas pintar uma área com uma única imagem alongada, você pode pintá-la com uma série de blocos de imagens que criam um padrão.  
  
 Um <xref:System.Windows.Media.TileBrush> tem três componentes principais: conteúdo, peças e a área de saída.  
  
 ![Componentes de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Componentes de um TileBrush com um único bloco  
  
 ![Componentes de um TileBrush lado a lado](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Componentes de um TileBrush com vários blocos  
  
 Para obter mais informações sobre os recursos de lado a lado do <xref:System.Windows.Media.TileBrush> objetos, consulte o [TileBrush Overview](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [Visão geral de TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [Visão geral de pincéis do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)  
 [Visão geral da geração de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Visão geral de máscaras da opacidade](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)  
 [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Exemplo de ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Exemplo de VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)
