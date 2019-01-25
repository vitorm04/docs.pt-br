---
title: 'Otimizando desempenho: Elementos gráficos e geração de imagens 2D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: d138f7ebc6fe62f03cd80189185c8ba73d3a2006
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630808"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Otimizando desempenho: Elementos gráficos e geração de imagens 2D
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma ampla variedade de gráficos 2D e funcionalidade de imagem que pode ser otimizada para suas necessidades de aplicativo. Este tópico fornece informações sobre otimização de desempenho nessas áreas.  
  
  
<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Desenho e formas  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece os dois <xref:System.Windows.Media.Drawing> e <xref:System.Windows.Shapes.Shape> objetos para representar o conteúdo de desenho gráfico. No entanto, <xref:System.Windows.Media.Drawing> objetos são construções mais simples que <xref:System.Windows.Shapes.Shape> objetos e fornecem melhores características de desempenho.  
  
 Um <xref:System.Windows.Shapes.Shape> permite que você desenhe uma forma gráfica na tela. Como eles são derivados de <xref:System.Windows.FrameworkElement> classe, <xref:System.Windows.Shapes.Shape> objetos podem ser usados dentro de painéis e a maioria dos controles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece várias camadas de acesso aos elementos gráficos e serviços de renderização. Na camada superior, <xref:System.Windows.Shapes.Shape> objetos são fáceis de usar e fornecem muitos recursos úteis, como layout e manipulação de eventos. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece alguns objetos de forma prontos para uso. Todos os objetos de forma herdam a <xref:System.Windows.Shapes.Shape> classe. Objetos de forma disponíveis incluem <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, e <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> objetos, por outro lado, não derivam de <xref:System.Windows.FrameworkElement> de classe e fornecer uma implementação mais leve para processamento de formas, imagens e texto.  
  
 Há quatro tipos de <xref:System.Windows.Media.Drawing> objetos:  
  
-   <xref:System.Windows.Media.GeometryDrawing> Desenha uma forma.  
  
-   <xref:System.Windows.Media.ImageDrawing> Desenha uma imagem.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> Desenha texto.  
  
-   <xref:System.Windows.Media.DrawingGroup> Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho composto.  
  
 O <xref:System.Windows.Media.GeometryDrawing> objeto é usado para renderizar o conteúdo de geometria. O <xref:System.Windows.Media.Geometry> classe e as classes concretas que derivam dela, como <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, e <xref:System.Windows.Media.PathGeometry>, fornecem um meio para processamento de gráficos 2D, bem como fornecer teste de clique e suporte a recorte. Objetos geométricos podem ser usados para definir a região de um controle, por exemplo, ou para definir a região de corte para aplicar a uma imagem. Objetos geométricos podem ser regiões simples, como retângulos e círculos ou regiões de composição criadas de dois ou mais objetos geométricos. Regiões geométricas mais complexas podem ser criadas combinando <xref:System.Windows.Media.PathSegment>-derivados de objetos, como <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, e <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Superficialmente, o <xref:System.Windows.Media.Geometry> classe e o <xref:System.Windows.Shapes.Shape> classe são bastante semelhantes. Ambos são usados no processamento de gráficos 2D e têm classes concretas semelhantes que derivam delas, por exemplo, <xref:System.Windows.Media.EllipseGeometry> e <xref:System.Windows.Shapes.Ellipse>. No entanto, existem diferenças importantes entre esses dois conjuntos de classes. Por exemplo, o <xref:System.Windows.Media.Geometry> classe não tem algumas das funcionalidades do <xref:System.Windows.Shapes.Shape> classe, como a capacidade de desenhar a mesmo. Para desenhar um objeto geométrico, outra classe, como DrawingContext, Drawing ou Path (vale a pena observar que um Path é um Shape) deve ser usada para executar a operação de desenho. Propriedades de processamento, como preenchimento, traço e a espessura do traço estão na classe que desenha o objeto geométrico, enquanto um objeto de forma contém essas propriedades. Uma maneira de pensar nessa diferença é que um objeto geométrico define uma região, um círculo por exemplo, enquanto um objeto de forma define uma região, define como a região é preenchida e destacada e participa do sistema de layout.  
  
 Uma vez que <xref:System.Windows.Shapes.Shape> objetos derivam o <xref:System.Windows.FrameworkElement> classe, usá-los pode adicionar significativamente mais consumo de memória em seu aplicativo. Se você realmente não precisa de <xref:System.Windows.FrameworkElement> recursos para seu conteúdo gráfico, considere o uso de peso leve <xref:System.Windows.Media.Drawing> objetos.  
  
 Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Classe StreamGeometry  
 O <xref:System.Windows.Media.StreamGeometry> objeto é uma alternativa leve para <xref:System.Windows.Media.PathGeometry> para criar formas geométricas. Use um <xref:System.Windows.Media.StreamGeometry> quando precisar descrever uma geometria complexa. <xref:System.Windows.Media.StreamGeometry> é otimizada para lidar com muitas <xref:System.Windows.Media.PathGeometry> objetos e executa melhor quando comparada ao uso individual muitos <xref:System.Windows.Media.PathGeometry> objetos.  
  
 O exemplo a seguir usa a sintaxe de atributo para criar um triangular <xref:System.Windows.Media.StreamGeometry> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Para obter mais informações sobre <xref:System.Windows.Media.StreamGeometry> objetos, consulte [criar uma forma usando um StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Objetos DrawingVisual  
 O <xref:System.Windows.Media.DrawingVisual> objeto é uma classe que é usada para renderizar formas, imagens ou texto leve. Essa classe é considerada leve porque não fornece layout nem manipulação de eventos, o que melhora o desempenho. Por esse motivo, desenhos são ideais para planos de fundo e clip-art. Para obter mais informações, consulte [Usando objetos DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Imagens  
 Geração de imagens [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma melhoria significativa nos recursos de imagem em versões anteriores do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Recursos de imagens, como exibir um bitmap ou usar uma imagem em um controle comum foram primeiramente tratados pela interface de programação Microsoft Windows GDI (Graphics Device Interface) ou Microsoft Windows GDI+ (API). Essa API fornece a funcionalidade de linha de base de imagens, mas não têm recursos como o suporte para a extensibilidade de codec e suporte às imagens de alta fidelidade. WPF Imaging API foi remodelado para superar os defeitos do GDI e GDI+ e fornecer um novo conjunto de APIs para exibir e usar imagens em seus aplicativos.  
  
 Ao usar imagens, considere as seguintes recomendações para obter um melhor desempenho:  
  
-   Se seu aplicativo requer que você exiba imagens em miniatura, considere a criação de uma versão de tamanho reduzido da imagem. Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carrega a imagem e a decodifica para seu tamanho máximo. Se você quiser apenas uma versão em miniatura da imagem, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desnecessariamente decodifica a imagem ao seu tamanho máximo e, em seguida, a redimensiona até um tamanho da miniatura. Para evitar essa sobrecarga desnecessária, você pode solicitar que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] decodifique a imagem para um tamanho de miniatura ou solicitar que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carregue uma imagem em miniatura.  
  
-   Sempre decodifique a imagem para o tamanho desejado e não para o tamanho padrão. Conforme mencionado acima, solicite que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] decodifique a imagem para um tamanho desejado e não para o tamanho total padrão. Você reduzirá não apenas seu conjunto de trabalho do aplicativo, mas também a velocidade de execução.  
  
-   Se possível, combine as imagens em uma única imagem, como um filme composto de várias imagens.  
  
-   Para obter mais informações, consulte [Visão geral de geração de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Ao animar a dimensão de qualquer bitmap, o algoritmo de reamostragem da imagem de alta qualidade padrão às vezes pode consumir recursos de sistema suficientes para causar degradação da taxa de quadros, efetivamente causando o travamento de animações. Definindo o <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> propriedade do <xref:System.Windows.Media.RenderOptions> do objeto para <xref:System.Windows.Media.BitmapScalingMode.LowQuality> você pode criar uma animação mais suave ao dimensionamento de um bitmap. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> modo informa o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de renderização para alternar de um algoritmo de qualidade otimizada para um algoritmo de velocidade otimizada ao processar imagens.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Media.BitmapScalingMode> para um objeto de imagem.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não armazena em cache o conteúdo renderizado dos <xref:System.Windows.Media.TileBrush> objetos, como <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>. Em cenários estáticos onde nem o conteúdo nem o uso do <xref:System.Windows.Media.TileBrush> na cena está mudando, isso faz sentido, já que ele economiza memória de vídeo. Não faz tanto sentido quando um <xref:System.Windows.Media.TileBrush> com conteúdo estático é usado em uma forma não estática — por exemplo, quando um estático <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> é mapeado para a superfície de um objeto 3D que gira. O comportamento padrão do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é renderizar novamente todo o conteúdo do <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> para cada quadro, mesmo que o conteúdo seja inalterável.  
  
 Definindo o <xref:System.Windows.Media.RenderOptions.CachingHint%2A> propriedade do <xref:System.Windows.Media.RenderOptions> do objeto para <xref:System.Windows.Media.CachingHint.Cache> pode aumentar o desempenho usando versões em cache dos objetos de pincel lado a lado.  
  
 O <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> e <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> valores de propriedade são valores de tamanho relativo que determinam quando o <xref:System.Windows.Media.TileBrush> objeto deve ser regenerado devido a alterações na escala. Por exemplo, definindo a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> propriedade para 2.0, o cache para o <xref:System.Windows.Media.TileBrush> só precisa ser regenerado quando seu tamanho excede duas vezes o tamanho do cache atual.  
  
 O exemplo a seguir mostra como usar a opção de dica de cache para um <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Consulte também
- [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)
- [Aproveitando o hardware](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
- [Dicas e truques de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
