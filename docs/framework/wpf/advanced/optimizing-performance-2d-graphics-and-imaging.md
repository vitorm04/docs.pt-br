---
title: 'Otimizando o desempenho: Elementos gráficos e geração de imagens 2D'
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
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933346"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Otimizando o desempenho: Elementos gráficos e geração de imagens 2D
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma ampla variedade de gráficos 2D e funcionalidade de imagem que pode ser otimizada para suas necessidades de aplicativo. Este tópico fornece informações sobre otimização de desempenho nessas áreas.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Desenho e formas  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece ambos <xref:System.Windows.Media.Drawing> os <xref:System.Windows.Shapes.Shape> objetos e para representar conteúdo de desenho gráfico. No entanto, <xref:System.Windows.Media.Drawing> os objetos são construções mais <xref:System.Windows.Shapes.Shape> simples do que objetos e fornecem melhores características de desempenho.  
  
 Um <xref:System.Windows.Shapes.Shape> permite desenhar uma forma gráfica na tela. Como elas são derivadas da <xref:System.Windows.FrameworkElement> classe, <xref:System.Windows.Shapes.Shape> os objetos podem ser usados dentro de painéis e da maioria dos controles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece várias camadas de acesso aos elementos gráficos e serviços de renderização. Na camada superior, <xref:System.Windows.Shapes.Shape> os objetos são fáceis de usar e fornecem muitos recursos úteis, como layout e manipulação de eventos. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece alguns objetos de forma prontos para uso. Todos os objetos de forma herdam da <xref:System.Windows.Shapes.Shape> classe. Os <xref:System.Windows.Shapes.Ellipse>objetos <xref:System.Windows.Shapes.Polygon> deforma<xref:System.Windows.Shapes.Rectangle>disponíveis <xref:System.Windows.Shapes.Line>incluem, <xref:System.Windows.Shapes.Polyline>,,, e. <xref:System.Windows.Shapes.Path>  
  
 <xref:System.Windows.Media.Drawing>os objetos, por outro lado, não derivam da <xref:System.Windows.FrameworkElement> classe e fornecem uma implementação mais leve para renderizar formas, imagens e texto.  
  
 Há quatro tipos de <xref:System.Windows.Media.Drawing> objetos:  
  
- <xref:System.Windows.Media.GeometryDrawing>Desenha uma forma.  
  
- <xref:System.Windows.Media.ImageDrawing>Desenha uma imagem.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Desenha texto.  
  
- <xref:System.Windows.Media.DrawingGroup>Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho composto.  
  
 O <xref:System.Windows.Media.GeometryDrawing> objeto é usado para renderizar o conteúdo da geometria. A <xref:System.Windows.Media.Geometry> classe e as classes concretas que derivam dela, <xref:System.Windows.Media.CombinedGeometry>como, <xref:System.Windows.Media.EllipseGeometry>e <xref:System.Windows.Media.PathGeometry>fornecem um meio para renderizar gráficos 2D, bem como fornecer suporte a testes de colisão e recorte. Objetos geométricos podem ser usados para definir a região de um controle, por exemplo, ou para definir a região de corte para aplicar a uma imagem. Objetos geométricos podem ser regiões simples, como retângulos e círculos ou regiões de composição criadas de dois ou mais objetos geométricos. Regiões geométricas mais complexas podem ser criadas <xref:System.Windows.Media.PathSegment>por meio da <xref:System.Windows.Media.ArcSegment>combinação de objetos derivados <xref:System.Windows.Media.BezierSegment>, como <xref:System.Windows.Media.QuadraticBezierSegment>, e.  
  
 Na superfície, a <xref:System.Windows.Media.Geometry> classe e a <xref:System.Windows.Shapes.Shape> classe são bastante semelhantes. Ambos são usados na renderização de elementos gráficos 2D e têm classes concretas semelhantes que derivam deles, por exemplo, <xref:System.Windows.Media.EllipseGeometry> e <xref:System.Windows.Shapes.Ellipse>. No entanto, existem diferenças importantes entre esses dois conjuntos de classes. Para um, a <xref:System.Windows.Media.Geometry> classe não tem parte da funcionalidade <xref:System.Windows.Shapes.Shape> da classe, como a capacidade de se desenhar. Para desenhar um objeto geométrico, outra classe, como DrawingContext, Drawing ou Path (vale a pena observar que um Path é um Shape) deve ser usada para executar a operação de desenho. Propriedades de processamento, como preenchimento, traço e a espessura do traço estão na classe que desenha o objeto geométrico, enquanto um objeto de forma contém essas propriedades. Uma maneira de pensar nessa diferença é que um objeto geométrico define uma região, um círculo por exemplo, enquanto um objeto de forma define uma região, define como a região é preenchida e destacada e participa do sistema de layout.  
  
 Como <xref:System.Windows.Shapes.Shape> os objetos derivam <xref:System.Windows.FrameworkElement> da classe, usá-los pode adicionar significativamente mais consumo de memória em seu aplicativo. Se você realmente não precisar dos <xref:System.Windows.FrameworkElement> recursos para seu conteúdo gráfico, considere o uso de <xref:System.Windows.Media.Drawing> objetos mais leves.  
  
 Para obter mais informações <xref:System.Windows.Media.Drawing> sobre objetos, consulte [visão geral de objetos de desenho](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Classe StreamGeometry  
 O <xref:System.Windows.Media.StreamGeometry> objeto é uma alternativa leve ao <xref:System.Windows.Media.PathGeometry> para a criação de formas geométricas. Use um <xref:System.Windows.Media.StreamGeometry> quando precisar descrever uma geometria complexa. <xref:System.Windows.Media.StreamGeometry>é otimizado para lidar <xref:System.Windows.Media.PathGeometry> com muitos objetos e tem um desempenho melhor quando comparado <xref:System.Windows.Media.PathGeometry> ao uso de muitos objetos individuais.  
  
 O exemplo a seguir usa a sintaxe de atributo para criar <xref:System.Windows.Media.StreamGeometry> um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]triangular no.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Para obter mais informações <xref:System.Windows.Media.StreamGeometry> sobre objetos, consulte [criar uma forma usando um StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Objetos DrawingVisual  
 O <xref:System.Windows.Media.DrawingVisual> objeto é uma classe leve de desenho que é usada para renderizar formas, imagens ou texto. Essa classe é considerada leve porque não fornece layout nem manipulação de eventos, o que melhora o desempenho. Por esse motivo, desenhos são ideais para planos de fundo e clip-art. Para obter mais informações, consulte [Usando objetos DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Imagens  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a geração de imagens fornece uma melhoria significativa nos recursos de geração de imagens nas versões anteriores do Windows. Recursos de imagens, como exibir um bitmap ou usar uma imagem em um controle comum foram primeiramente tratados pela interface de programação Microsoft Windows GDI (Graphics Device Interface) ou Microsoft Windows GDI+ (API). Essa API fornece a funcionalidade de linha de base de imagens, mas não têm recursos como o suporte para a extensibilidade de codec e suporte às imagens de alta fidelidade. WPF Imaging API foi remodelado para superar os defeitos do GDI e GDI+ e fornecer um novo conjunto de APIs para exibir e usar imagens em seus aplicativos.  
  
 Ao usar imagens, considere as seguintes recomendações para obter um melhor desempenho:  
  
- Se seu aplicativo requer que você exiba imagens em miniatura, considere a criação de uma versão de tamanho reduzido da imagem. Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carrega a imagem e a decodifica para seu tamanho máximo. Se você quiser apenas uma versão em miniatura da imagem, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desnecessariamente decodifica a imagem ao seu tamanho máximo e, em seguida, a redimensiona até um tamanho da miniatura. Para evitar essa sobrecarga desnecessária, você pode solicitar que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] decodifique a imagem para um tamanho de miniatura ou solicitar que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carregue uma imagem em miniatura.  
  
- Sempre decodifique a imagem para o tamanho desejado e não para o tamanho padrão. Conforme mencionado acima, solicite que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] decodifique a imagem para um tamanho desejado e não para o tamanho total padrão. Você reduzirá não apenas seu conjunto de trabalho do aplicativo, mas também a velocidade de execução.  
  
- Se possível, combine as imagens em uma única imagem, como um filme composto de várias imagens.  
  
- Para obter mais informações, consulte [Visão geral de geração de imagens](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Ao animar a dimensão de qualquer bitmap, o algoritmo de reamostragem da imagem de alta qualidade padrão às vezes pode consumir recursos de sistema suficientes para causar degradação da taxa de quadros, efetivamente causando o travamento de animações. Ao definir a <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> propriedade <xref:System.Windows.Media.RenderOptions> do objeto como <xref:System.Windows.Media.BitmapScalingMode.LowQuality> você pode criar uma animação mais suave ao dimensionar um bitmap. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modo informa ao mecanismo de renderização para alternar de um algoritmo com otimização de qualidade para um algoritmo otimizado para velocidade durante o processamento de imagens.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Media.BitmapScalingMode> para um objeto Image.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o não armazena em cache o conteúdo <xref:System.Windows.Media.TileBrush> renderizado de objetos <xref:System.Windows.Media.DrawingBrush> , <xref:System.Windows.Media.VisualBrush>como e. Em cenários estáticos em que nem o conteúdo nem o <xref:System.Windows.Media.TileBrush> uso do na cena estão mudando, isso faz sentido, pois ele conserva a memória de vídeo. Isso não faz tanto sentido quando um <xref:System.Windows.Media.TileBrush> com conteúdo estático é usado em uma maneira não estática — por exemplo, quando um estático <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> é mapeado para a superfície de um objeto 3D rotativo. O comportamento padrão de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é renderizar novamente todo o conteúdo <xref:System.Windows.Media.DrawingBrush> do ou <xref:System.Windows.Media.VisualBrush> para cada quadro, mesmo que o conteúdo fique inalterado.  
  
 Ao definir a <xref:System.Windows.Media.RenderOptions.CachingHint%2A> propriedade <xref:System.Windows.Media.RenderOptions> do objeto como <xref:System.Windows.Media.CachingHint.Cache> você pode aumentar o desempenho usando versões armazenadas em cache dos objetos de pincel com o lado do ladrilho.  
  
 Os <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> valores <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> de propriedade e são valores de tamanho relativo que determinam quando o <xref:System.Windows.Media.TileBrush> objeto deve ser regenerado devido a alterações na escala. Por exemplo, ao definir a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> Propriedade como 2,0, o cache para o <xref:System.Windows.Media.TileBrush> só precisa ser regenerado quando seu tamanho excede o dobro do tamanho do cache atual.  
  
 O exemplo a seguir mostra como usar a opção de dica de cache <xref:System.Windows.Media.DrawingBrush>para um.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Consulte também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
- [Dicas e truques de animação](../graphics-multimedia/animation-tips-and-tricks.md)
