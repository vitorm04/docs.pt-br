---
title: Pintando com imagens, desenhos e visuais
ms.date: 03/30/2017
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
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186916"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Pintando com imagens, desenhos e visuais
Este tópico descreve como <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>usar <xref:System.Windows.Media.VisualBrush> , e objetos para pintar <xref:System.Windows.Media.Drawing>uma <xref:System.Windows.Media.Visual>área com uma imagem, a , ou a .  

<a name="prereqs"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de pincéis que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece e seus recursos básicos. Para uma introdução, consulte a [Visão geral de pincéis do WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>Pintar uma área com uma imagem  
 Um <xref:System.Windows.Media.ImageBrush> pinta uma área <xref:System.Windows.Media.ImageSource>com um . O tipo mais <xref:System.Windows.Media.ImageSource> comum <xref:System.Windows.Media.ImageBrush> de <xref:System.Windows.Media.Imaging.BitmapImage>usar com um é um , que descreve um gráfico bitmap. Você pode <xref:System.Windows.Media.DrawingImage> usar um <xref:System.Windows.Media.Drawing> para pintar usando um objeto, mas é mais simples de usar um <xref:System.Windows.Media.DrawingBrush> em vez disso. Para obter <xref:System.Windows.Media.ImageSource> mais informações sobre objetos, consulte a [visão geral de imagens](imaging-overview.md).  
  
 Para pintar <xref:System.Windows.Media.ImageBrush>com um <xref:System.Windows.Media.Imaging.BitmapImage> , crie-o e use-o para carregar o conteúdo do bitmap. Em seguida, <xref:System.Windows.Media.Imaging.BitmapImage> use <xref:System.Windows.Media.ImageBrush.ImageSource%2A> o para <xref:System.Windows.Media.ImageBrush>definir a propriedade do . Finalmente, aplique <xref:System.Windows.Media.ImageBrush> o objeto que deseja pintar.  Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você também <xref:System.Windows.Media.ImageBrush.ImageSource%2A> pode apenas <xref:System.Windows.Media.ImageBrush> definir a propriedade do com o caminho da imagem para carregar.  
  
 Como <xref:System.Windows.Media.Brush> todos os <xref:System.Windows.Media.ImageBrush> objetos, um pode ser usado para pintar objetos como formas, painéis, controles e texto. A ilustração a seguir mostra alguns efeitos que podem ser alcançados com um <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemplos de saída de ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objetos pintados por um ImageBrush  
  
 Por padrão, <xref:System.Windows.Media.ImageBrush> um alonga sua imagem para preencher completamente a área que está sendo pintada, possivelmente distorcendo a imagem se a área pintada tiver uma proporção diferente da imagem. Você pode alterar esse <xref:System.Windows.Media.TileBrush.Stretch%2A> comportamento alterando a <xref:System.Windows.Media.Stretch.Fill> <xref:System.Windows.Media.Stretch.None>propriedade <xref:System.Windows.Media.Stretch.Uniform>do <xref:System.Windows.Media.Stretch.UniformToFill>seu valor padrão de para , ou . Como <xref:System.Windows.Media.ImageBrush> é um <xref:System.Windows.Media.TileBrush>tipo de , você pode especificar exatamente como um pincel de imagem preenche a área de saída e até mesmo criar padrões. Para obter mais <xref:System.Windows.Media.TileBrush> informações sobre recursos avançados, consulte a visão geral do [TileBrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Exemplo: pintar um objeto com uma imagem de bitmap  
 O exemplo a <xref:System.Windows.Media.ImageBrush> seguir <xref:System.Windows.Controls.Panel.Background%2A> usa <xref:System.Windows.Controls.Canvas>um para pintar o de um .  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>Pintar uma área com um desenho  
 A <xref:System.Windows.Media.DrawingBrush> permite que você pinte uma área com formas, texto, imagens e vídeo. As formas dentro de um pincel de desenho podem ser pintadas com <xref:System.Windows.Media.DrawingBrush>uma cor sólida, gradiente, imagem ou até mesmo outra . A ilustração a seguir <xref:System.Windows.Media.DrawingBrush>demonstra alguns usos de um .  
  
 ![Exemplos de saída de DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objetos pintados por um DrawingBrush  
  
 Um <xref:System.Windows.Media.DrawingBrush> pinta uma área <xref:System.Windows.Media.Drawing> com um objeto. Um <xref:System.Windows.Media.Drawing> objeto descreve conteúdo visível, como uma forma, bitmap, vídeo ou uma linha de texto. Diferentes tipos de desenhos descrevem diferentes tipos de conteúdo. A seguir está uma lista dos diferentes tipos de objetos de desenho.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Desenha uma forma.  
  
- <xref:System.Windows.Media.ImageDrawing>– Desenha uma imagem.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Desenha texto.  
  
- <xref:System.Windows.Media.VideoDrawing>– Reproduz um arquivo de áudio ou vídeo.  
  
- <xref:System.Windows.Media.DrawingGroup>– Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho de composição.  
  
 Para obter <xref:System.Windows.Media.Drawing> mais informações sobre objetos, consulte a visão geral dos [objetos de desenho](drawing-objects-overview.md).  
  
 Como <xref:System.Windows.Media.ImageBrush>um <xref:System.Windows.Media.DrawingBrush> , um <xref:System.Windows.Media.DrawingBrush.Drawing%2A> alonga seu para preencher sua área de saída. Você pode substituir esse comportamento <xref:System.Windows.Media.TileBrush.Stretch%2A> alterando a <xref:System.Windows.Media.Stretch.Fill>propriedade da configuração padrão de . Para obter mais informações, consulte a propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>Exemplo: pintar um objeto com um desenho  
 O exemplo a seguir mostra como pintar um objeto com um desenho de três elipses. A <xref:System.Windows.Media.GeometryDrawing> é usado para descrever as elipses.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>Pintar uma área com um visual  
 O mais versátil e poderoso de <xref:System.Windows.Media.VisualBrush> todos os pincéis, as tintas uma área com um <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> é um tipo gráfico de baixo nível que serve como ancestral de muitos componentes gráficos úteis. Por exemplo, <xref:System.Windows.Window> <xref:System.Windows.FrameworkElement>as <xref:System.Windows.Controls.Control> classes e classes <xref:System.Windows.Media.Visual> são todos os tipos de objetos. Usando <xref:System.Windows.Media.VisualBrush>um , você pode [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pintar áreas com quase qualquer objeto gráfico.  
  
> [!NOTE]
> Embora <xref:System.Windows.Media.VisualBrush> seja um <xref:System.Windows.Freezable> tipo de objeto, ele não pode <xref:System.Windows.Media.VisualBrush.Visual%2A> ser congelado (feito somente `null`leitura) quando sua propriedade é definida como um valor diferente de .  
  
 Existem duas maneiras <xref:System.Windows.Media.VisualBrush.Visual%2A> de <xref:System.Windows.Media.VisualBrush>especificar o conteúdo de a .  
  
- Crie um <xref:System.Windows.Media.Visual> novo e use-o para definir a <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade do <xref:System.Windows.Media.VisualBrush>. Para obter um exemplo, consulte a seção [Exemplo: pintar um objeto com um Visual](#examplevisualbrush1) a seguir.  
  
- Use um <xref:System.Windows.Media.Visual>existente, que cria uma <xref:System.Windows.Media.Visual>imagem duplicada do alvo. Você pode então <xref:System.Windows.Media.VisualBrush> usar o para criar efeitos interessantes, como reflexão e ampliação. Para obter um exemplo, consulte a seção [Exemplo: criar uma reflexão](#examplevisualbrush2).  
  
 Quando você define <xref:System.Windows.Media.VisualBrush.Visual%2A> um <xref:System.Windows.Media.VisualBrush> novo <xref:System.Windows.Media.Visual> para <xref:System.Windows.UIElement> a e que é um (como <xref:System.Windows.UIElement> um painel ou <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> controle), o `true`sistema de layout é executado sobre os elementos da criança quando a propriedade é definida para . No entanto, a raiz <xref:System.Windows.UIElement> é essencialmente isolada do resto do sistema: estilos e layout externo não podem permear esse limite. Portanto, você deve especificar explicitamente o <xref:System.Windows.UIElement>tamanho da raiz, <xref:System.Windows.Media.VisualBrush> pois seu único pai é o e, portanto, não pode dimensionar automaticamente para a área que está sendo pintada. Para mais informações sobre o layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte [Layout](../advanced/layout.md).  
  
 Gosta <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>e, <xref:System.Windows.Media.VisualBrush> um alonga seu conteúdo para preencher sua área de saída. Você pode substituir esse comportamento <xref:System.Windows.Media.TileBrush.Stretch%2A> alterando a <xref:System.Windows.Media.Stretch.Fill>propriedade da configuração padrão de . Para obter mais informações, consulte a propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>Exemplo: pintar um objeto com um visual  
 No exemplo a seguir, vários controles e um painel são usados para pintar um retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>Exemplo: criar um reflexo  
 O exemplo anterior mostrou como <xref:System.Windows.Media.Visual> criar um novo para uso como plano de fundo. Você também pode <xref:System.Windows.Media.VisualBrush> usar um para exibir um visual existente; essa capacidade permite produzir efeitos visuais interessantes, como reflexões e ampliação. O exemplo a <xref:System.Windows.Media.VisualBrush> seguir usa um <xref:System.Windows.Controls.Border> para criar um reflexo de um que contém vários elementos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um objeto visual refletido](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Um objeto visual refletido  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Para outros exemplos que mostram como ampliar partes da tela e como criar reflexões, consulte o [Exemplo do VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>Recursos do TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>e <xref:System.Windows.Media.VisualBrush> são <xref:System.Windows.Media.TileBrush> tipos de objetos. <xref:System.Windows.Media.TileBrush>objetos fornecem-lhe uma grande quantidade de controle sobre como uma área é pintada com uma imagem, desenho ou visual. Por exemplo, em vez de apenas pintar uma área com uma única imagem alongada, você pode pintá-la com uma série de blocos de imagens que criam um padrão.  
  
 A <xref:System.Windows.Media.TileBrush> tem três componentes principais: conteúdo, telhas e área de saída.  
  
 ![Componentes de TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Componentes de um TileBrush com um único azulejo  
  
 ![Componentes de um TileBrush lado a lado](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Componentes de um TileBrush com vários blocos  
  
 Para obter mais informações sobre <xref:System.Windows.Media.TileBrush> os recursos de revestimento de objetos, consulte a [visão geral do TileBrush](tilebrush-overview.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Visão geral de TileBrush](tilebrush-overview.md)
- [Visão geral de pincéis do WPF](wpf-brushes-overview.md)
- [Visão geral da geração de imagens](imaging-overview.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de máscaras da opacidade](opacity-masks-overview.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Exemplo de ImageBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Exemplo de VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
