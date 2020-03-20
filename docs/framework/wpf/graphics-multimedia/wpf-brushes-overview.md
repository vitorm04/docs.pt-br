---
title: Visão geral dos pincéis
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186574"
---
# <a name="wpf-brushes-overview"></a>Visão geral de pincéis do WPF
Tudo o que é visível na tela é visível porque foi pintado por um pincel. Por exemplo, um pincel é usado para descrever a tela de fundo de um botão, o primeiro plano do texto e o preenchimento de uma forma. Este tópico apresenta os conceitos de pintura com pincéis [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e fornece exemplos. Os pincéis permitem que você pinte objetos [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] com qualquer coisa, desde cores simples e sólidas a conjuntos complexos de padrões e imagens.  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>Pintando com um pincel  
 Um <xref:System.Windows.Media.Brush> "pinta" uma área com sua saída. Pincéis diferentes têm tipos diferentes de saída. Alguns pincéis pintam uma área com uma cor sólida, outros com um gradiente, um padrão, uma imagem ou um desenho. A ilustração a seguir mostra <xref:System.Windows.Media.Brush> exemplos de cada um dos diferentes tipos.  
  
 ![Tipos de pincel](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Exemplos de pincel  
  
 A maioria dos objetos visuais permite especificar como eles são pintados. A tabela a seguir lista alguns objetos <xref:System.Windows.Media.Brush>e propriedades comuns com os quais você pode usar um .  
  
|Classe|Propriedades do pincel|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 As seções a <xref:System.Windows.Media.Brush> seguir descrevem os diferentes tipos e fornecem um exemplo de cada um.  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>Pintar com uma cor sólida  
 Um <xref:System.Windows.Media.SolidColorBrush> pinta uma área <xref:System.Windows.Media.Color>com um sólido. Existem várias maneiras <xref:System.Windows.Media.SolidColorBrush.Color%2A> de <xref:System.Windows.Media.SolidColorBrush>especificar a de a: por exemplo, você pode especificar seus canais alfa, <xref:System.Windows.Media.Colors> vermelho, azul e verde ou usar uma das cores predefinidas fornecidas pela classe.  
  
 O exemplo a <xref:System.Windows.Media.SolidColorBrush> seguir <xref:System.Windows.Shapes.Shape.Fill%2A> usa <xref:System.Windows.Shapes.Rectangle>um para pintar o de um . A ilustração a seguir mostra o retângulo pintado.  
  
 ![Um retângulo pintado usando um SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Um retângulo pintado usando um SolidColorBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Para obter mais <xref:System.Windows.Media.SolidColorBrush> informações sobre a classe, consulte [Pintura com Cores Sólidas e Visão Geral de Gradientes](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>Pintar com um gradiente linear  
 Um <xref:System.Windows.Media.LinearGradientBrush> paints an area with a linear gradient. Um gradiente linear combina duas ou mais cores em uma linha, o eixo de gradiente. Você <xref:System.Windows.Media.GradientStop> usa objetos para especificar as cores no gradiente e suas posições.  
  
 O exemplo a <xref:System.Windows.Media.LinearGradientBrush> seguir <xref:System.Windows.Shapes.Shape.Fill%2A> usa <xref:System.Windows.Shapes.Rectangle>um para pintar o de um . A ilustração a seguir mostra o retângulo pintado.  
  
 ![Um retângulo pintado usando um Pincel DeGradient Linear](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Um retângulo pintado usando um LinearGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Para obter mais <xref:System.Windows.Media.LinearGradientBrush> informações sobre a classe, consulte [Pintura com Cores Sólidas e Visão Geral de Gradientes](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>Pintar com um gradiente radial  
 Um <xref:System.Windows.Media.RadialGradientBrush> pinta uma área com um gradiente radial. Um gradiente radial combina duas ou mais cores em um círculo. Assim como <xref:System.Windows.Media.LinearGradientBrush> na classe, você usa <xref:System.Windows.Media.GradientStop> objetos para especificar as cores no gradiente e suas posições.  
  
 O exemplo a <xref:System.Windows.Media.RadialGradientBrush> seguir <xref:System.Windows.Shapes.Shape.Fill%2A> usa <xref:System.Windows.Shapes.Rectangle>um para pintar o de um . A ilustração a seguir mostra o retângulo pintado.  
  
 ![Um retângulo pintado usando um RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Um retângulo pintado usando um RadialGradientBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Para obter mais <xref:System.Windows.Media.RadialGradientBrush> informações sobre a classe, consulte [Pintura com Cores Sólidas e Visão Geral de Gradientes](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>Pintar com uma imagem  
 Um <xref:System.Windows.Media.ImageBrush> pinta uma área <xref:System.Windows.Media.ImageSource>com um.  
  
 O exemplo a <xref:System.Windows.Media.ImageBrush> seguir <xref:System.Windows.Shapes.Shape.Fill%2A> usa <xref:System.Windows.Shapes.Rectangle>um para pintar o de um . A ilustração a seguir mostra o retângulo pintado.  
  
 ![Um retângulo pintado por um ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Um retângulo pintado usando uma imagem  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Para obter mais <xref:System.Windows.Media.ImageBrush> informações sobre a classe, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>Pintar com um desenho  
 Um <xref:System.Windows.Media.DrawingBrush> pinta uma área <xref:System.Windows.Media.Drawing>com um. Uma <xref:System.Windows.Media.Drawing> lata pode conter formas, imagens, texto e mídia.  
  
 O exemplo a <xref:System.Windows.Media.DrawingBrush> seguir <xref:System.Windows.Shapes.Shape.Fill%2A> usa <xref:System.Windows.Shapes.Rectangle>um para pintar o de um . A ilustração a seguir mostra o retângulo pintado.  
  
 ![Um retângulo pintado usando um DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Um retângulo pintado usando um DrawingBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Para obter mais <xref:System.Windows.Media.DrawingBrush> informações sobre a classe, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>Pintar com um visual  
 Um <xref:System.Windows.Media.VisualBrush> pinta uma área <xref:System.Windows.Media.Visual> com um objeto. Exemplos de objetos <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Page>visuais <xref:System.Windows.Controls.MediaElement>incluem , e . A <xref:System.Windows.Media.VisualBrush> também permite que você projete conteúdo de uma parte do seu aplicativo para outra área; é muito útil para criar efeitos de reflexão e ampliar partes da tela.  
  
 O exemplo a <xref:System.Windows.Media.VisualBrush> seguir <xref:System.Windows.Shapes.Shape.Fill%2A> usa <xref:System.Windows.Shapes.Rectangle>um para pintar o de um . A ilustração a seguir mostra o retângulo pintado.  
  
 ![Um retângulo pintado usando um VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Um retângulo pintado usando um VisualBrush  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Para obter mais <xref:System.Windows.Media.VisualBrush> informações sobre a classe, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>Pintar usando pincéis do sistema e predefinidos  
 Para conveniência, o Windows Presentation Foundation (WPF) fornece um conjunto de pincéis predefinidos e do sistema que você pode usar para pintar objetos.  
  
- Para obter uma lista de pincéis predefinidos disponíveis, consulte a <xref:System.Windows.Media.Brushes> classe. Para ver um exemplo que mostra como usar um pincel predefinido, consulte [Pintar uma área com uma cor sólida](how-to-paint-an-area-with-a-solid-color.md).  
  
- Para obter uma lista de pincéis disponíveis do sistema, consulte a <xref:System.Windows.SystemColors> classe. Para ver um exemplo, consulte [Pintar uma área com um pincel de sistema](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>Recursos comuns de pincel  
 <xref:System.Windows.Media.Brush>objetos <xref:System.Windows.Media.Brush.Opacity%2A> fornecem uma propriedade que pode ser usada para tornar um pincel transparente ou parcialmente transparente. Um <xref:System.Windows.Media.Brush.Opacity%2A> valor de 0 torna um pincel <xref:System.Windows.Media.Brush.Opacity%2A> completamente transparente, enquanto um valor de 1 torna um pincel completamente opaco. O exemplo a <xref:System.Windows.Media.Brush.Opacity%2A> seguir usa <xref:System.Windows.Media.SolidColorBrush> a propriedade para fazer um 25% opaco.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Se o pincel contiver cores parcialmente transparentes, o valor da opacidade da cor será combinado por multiplicação com o valor da opacidade do pincel. Por exemplo, se um pincel tiver um valor de opacidade de 0,5 e uma cor usada no pincel também tiver um valor de opacidade de 0,5, a cor de saída terá o valor de opacidade de 0,25.  
  
> [!NOTE]
> É mais eficiente mudar o valor da opacidade de um pincel do que mudar <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> a opacidade de um elemento inteiro usando sua propriedade.  
  
 Você pode girar, dimensionar, distorcer e traduzir o <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> conteúdo de um pincel usando suas propriedades ou. Para obter mais informações, veja [Visão geral da transformação de pincel](brush-transformation-overview.md).  
  
 Por serem <xref:System.Windows.Media.Animation.Animatable> objetos, <xref:System.Windows.Media.Brush> os objetos podem ser animados. Para obter mais informações, consulte [Visão geral da animação](animation-overview.md).  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Recursos congeláveis  
 Por herdar da <xref:System.Windows.Freezable> classe, <xref:System.Windows.Media.Brush> a classe fornece <xref:System.Windows.Media.Brush> várias características especiais: objetos podem ser declarados como [recursos,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)compartilhados entre vários objetos e clonados. Além disso, <xref:System.Windows.Media.Brush> todos <xref:System.Windows.Media.VisualBrush> os tipos, exceto podem ser feitos somente de leitura para melhorar o desempenho e torná-lo seguro de rosca.  
  
 Para obter mais informações sobre <xref:System.Windows.Freezable> os diferentes recursos fornecidos pelos objetos, consulte [Visão geral de objetos freezable](../advanced/freezable-objects-overview.md).  
  
 Para obter mais <xref:System.Windows.Media.VisualBrush> informações sobre por <xref:System.Windows.Media.VisualBrush> que os objetos não podem ser congelados, consulte a página do tipo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [Exemplo de ImageBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Exemplo de VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [Tópicos de como fazer](brushes-how-to-topics.md)
- [Outras recomendações de desempenho](../advanced/optimizing-performance-other-recommendations.md)
