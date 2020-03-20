---
title: 'Otimizando desempenho: elementos gráficos e geração de imagens 2D'
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
ms.openlocfilehash: 03b2b64736407bf54c9bf957fe93d2d3d6e343f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186773"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Otimizando desempenho: elementos gráficos e geração de imagens 2D
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma ampla variedade de gráficos 2D e funcionalidade de imagem que pode ser otimizada para suas necessidades de aplicativo. Este tópico fornece informações sobre otimização de desempenho nessas áreas.  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>Desenho e formas  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece <xref:System.Windows.Media.Drawing> tanto <xref:System.Windows.Shapes.Shape> e objetos para representar o conteúdo do desenho gráfico. No <xref:System.Windows.Media.Drawing> entanto, os <xref:System.Windows.Shapes.Shape> objetos são construções mais simples do que objetos e fornecem melhores características de desempenho.  
  
 A <xref:System.Windows.Shapes.Shape> permite que você desenhe uma forma gráfica para a tela. Por serem derivados <xref:System.Windows.FrameworkElement> da <xref:System.Windows.Shapes.Shape> classe, os objetos podem ser usados dentro de painéis e a maioria dos controles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece várias camadas de acesso aos elementos gráficos e serviços de renderização. Na camada superior, <xref:System.Windows.Shapes.Shape> os objetos são fáceis de usar e fornecem muitos recursos úteis, como layout e manuseio de eventos. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece alguns objetos de forma prontos para uso. Todos os objetos <xref:System.Windows.Shapes.Shape> de forma herdam da classe. Os objetos <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line>de <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>forma <xref:System.Windows.Shapes.Polyline>disponíveis <xref:System.Windows.Shapes.Rectangle>incluem, , , , , e .  
  
 <xref:System.Windows.Media.Drawing>objetos, por outro lado, não <xref:System.Windows.FrameworkElement> derivam da classe e fornecem uma implementação de peso mais leve para renderização de formas, imagens e texto.  
  
 Existem quatro <xref:System.Windows.Media.Drawing> tipos de objetos:  
  
- <xref:System.Windows.Media.GeometryDrawing>Desenha uma forma.  
  
- <xref:System.Windows.Media.ImageDrawing>Desenha uma imagem.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Desenha texto.  
  
- <xref:System.Windows.Media.DrawingGroup>Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho de composição.  
  
 O <xref:System.Windows.Media.GeometryDrawing> objeto é usado para renderizar conteúdo de geometria. A <xref:System.Windows.Media.Geometry> classe e as classes concretas <xref:System.Windows.Media.CombinedGeometry>que <xref:System.Windows.Media.EllipseGeometry>derivam dela, tais como , e <xref:System.Windows.Media.PathGeometry>, fornecem um meio para renderizar gráficos 2D, bem como fornecer suporte para testes de hit e recorte. Objetos geométricos podem ser usados para definir a região de um controle, por exemplo, ou para definir a região de corte para aplicar a uma imagem. Objetos geométricos podem ser regiões simples, como retângulos e círculos ou regiões de composição criadas de dois ou mais objetos geométricos. Regiões geométricas mais complexas podem <xref:System.Windows.Media.PathSegment>ser criadas combinando objetos derivados, tais como <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>e <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na superfície, <xref:System.Windows.Media.Geometry> a classe <xref:System.Windows.Shapes.Shape> e a classe são bastante semelhantes. Ambos são usados na renderização de gráficos 2D e ambos <xref:System.Windows.Media.EllipseGeometry> têm <xref:System.Windows.Shapes.Ellipse>classes de concreto semelhantes que derivam deles, por exemplo, e . No entanto, existem diferenças importantes entre esses dois conjuntos de classes. Por um <xref:System.Windows.Media.Geometry> exemplo, a classe carece de <xref:System.Windows.Shapes.Shape> algumas funcionalidades da classe, como a capacidade de desenhar a si mesma. Para desenhar um objeto geométrico, outra classe, como DrawingContext, Drawing ou Path (vale a pena observar que um Path é um Shape) deve ser usada para executar a operação de desenho. Propriedades de processamento, como preenchimento, traço e a espessura do traço estão na classe que desenha o objeto geométrico, enquanto um objeto de forma contém essas propriedades. Uma maneira de pensar nessa diferença é que um objeto geométrico define uma região, um círculo por exemplo, enquanto um objeto de forma define uma região, define como a região é preenchida e destacada e participa do sistema de layout.  
  
 Uma <xref:System.Windows.Shapes.Shape> vez que <xref:System.Windows.FrameworkElement> os objetos derivam da classe, usá-los pode adicionar significativamente mais consumo de memória em sua aplicação. Se você realmente <xref:System.Windows.FrameworkElement> não precisa dos recursos para o seu <xref:System.Windows.Media.Drawing> conteúdo gráfico, considere usar os objetos mais leves.  
  
 Para obter <xref:System.Windows.Media.Drawing> mais informações sobre objetos, consulte [Visão geral de objetos de desenho](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>Classe StreamGeometry  
 O <xref:System.Windows.Media.StreamGeometry> objeto é uma <xref:System.Windows.Media.PathGeometry> alternativa leve para criar formas geométricas. Use <xref:System.Windows.Media.StreamGeometry> um quando você precisa descrever uma geometria complexa. <xref:System.Windows.Media.StreamGeometry>é otimizado para <xref:System.Windows.Media.PathGeometry> manusear muitos objetos e <xref:System.Windows.Media.PathGeometry> tem melhor desempenho quando comparado ao uso de muitos objetos individuais.  
  
 O exemplo a seguir usa sintaxe de atributos para criar um triangular <xref:System.Windows.Media.StreamGeometry> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Para obter <xref:System.Windows.Media.StreamGeometry> mais informações sobre objetos, consulte [Criar uma forma usando uma geometria de fluxo](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>Objetos DrawingVisual  
 O <xref:System.Windows.Media.DrawingVisual> objeto é uma classe de desenho leve que é usada para renderizar formas, imagens ou texto. Essa classe é considerada leve porque não fornece layout ou manipulação de eventos, o que melhora o desempenho. Por esse motivo, desenhos são ideais para telas de fundo e clip-art. Para obter mais informações, consulte [Usando objetos DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>
## <a name="images"></a>Imagens  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a imagem fornece uma melhoria significativa sobre os recursos de imagem em versões anteriores do Windows. Recursos de imagens, como exibir um bitmap ou usar uma imagem em um controle comum foram primeiramente tratados pela interface de programação Microsoft Windows GDI (Graphics Device Interface) ou Microsoft Windows GDI+ (API). Essa API fornece a funcionalidade de linha de base de imagens, mas não têm recursos como o suporte para a extensibilidade de codec e suporte às imagens de alta fidelidade. WPF Imaging API foi remodelado para superar os defeitos do GDI e GDI+ e fornecer um novo conjunto de APIs para exibir e usar imagens em seus aplicativos.  
  
 Ao usar imagens, considere as seguintes recomendações para obter um melhor desempenho:  
  
- Se seu aplicativo requer que você exiba imagens em miniatura, considere a criação de uma versão de tamanho reduzido da imagem. Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carrega a imagem e a decodifica para seu tamanho máximo. Se você quiser apenas uma versão em miniatura da imagem, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desnecessariamente decodifica a imagem ao seu tamanho máximo e, em seguida, a redimensiona até um tamanho da miniatura. Para evitar essa sobrecarga desnecessária, você pode solicitar que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] decodifique a imagem para um tamanho de miniatura ou solicitar que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carregue uma imagem em miniatura.  
  
- Sempre decodifique a imagem para o tamanho desejado e não para o tamanho padrão. Conforme mencionado acima, solicite que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] decodifique a imagem para um tamanho desejado e não para o tamanho total padrão. Você reduzirá não apenas seu conjunto de trabalho do aplicativo, mas também a velocidade de execução.  
  
- Se possível, combine as imagens em uma única imagem, como um filme composto de várias imagens.  
  
- Para obter mais informações, consulte [Visão geral de imagens](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Ao animar a dimensão de qualquer bitmap, o algoritmo de reamostragem da imagem de alta qualidade padrão às vezes pode consumir recursos de sistema suficientes para causar degradação da taxa de quadros, efetivamente causando o travamento de animações. Ao definir <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> a <xref:System.Windows.Media.RenderOptions> propriedade <xref:System.Windows.Media.BitmapScalingMode.LowQuality> do objeto para você, você pode criar uma animação mais suave ao dimensionar um bitmap. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>o modo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diz ao mecanismo de renderização para mudar de um algoritmo otimizado para qualidade para um algoritmo otimizado por velocidade ao processar imagens.  
  
 O exemplo a seguir <xref:System.Windows.Media.BitmapScalingMode> mostra como definir o objeto para uma imagem.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão, não armazena o <xref:System.Windows.Media.TileBrush> conteúdo renderizado <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>de objetos, tais como e . Em cenários estáticos onde <xref:System.Windows.Media.TileBrush> nem o conteúdo nem o uso da cena está mudando, isso faz sentido, já que conserva a memória do vídeo. Não faz tanto sentido quando <xref:System.Windows.Media.TileBrush> um com conteúdo estático é usado de forma <xref:System.Windows.Media.DrawingBrush> não <xref:System.Windows.Media.VisualBrush> estática — por exemplo, quando uma estática ou é mapeada para a superfície de um objeto 3D rotativo. O comportamento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão é rerenderizar todo <xref:System.Windows.Media.DrawingBrush> o <xref:System.Windows.Media.VisualBrush> conteúdo do ou para cada quadro, mesmo que o conteúdo seja imutável.  
  
 Ao definir <xref:System.Windows.Media.RenderOptions.CachingHint%2A> a <xref:System.Windows.Media.RenderOptions> propriedade <xref:System.Windows.Media.CachingHint.Cache> do objeto para você, você pode aumentar o desempenho usando versões em cache dos objetos de escova de ladrilhos.  
  
 Os <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> valores e propriedades são valores de tamanho relativo que determinam quando o <xref:System.Windows.Media.TileBrush> objeto deve ser regenerado devido a alterações na escala. Por exemplo, ao <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> definir a propriedade como 2.0, o cache para o <xref:System.Windows.Media.TileBrush> único precisa ser regenerado quando seu tamanho excede o dobro do tamanho do cache atual.  
  
 O exemplo a seguir mostra como usar <xref:System.Windows.Media.DrawingBrush>a opção de dica de cache para um .  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Confira também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando o desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitar o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos de aplicação](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
- [Dicas e truques de animação](../graphics-multimedia/animation-tips-and-tricks.md)
