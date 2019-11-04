---
title: Visão geral da geometria
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: f45c13e1af9bc2d1f75da11b13a2c03936b136c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455014"
---
# <a name="geometry-overview"></a>Visão geral da geometria
Esta visão geral descreve como usar o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> classes para descrever formas. Este tópico também contrasta as diferenças entre <xref:System.Windows.Media.Geometry> objetos e <xref:System.Windows.Shapes.Shape> elementos.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>O que é uma geometria?  
 A classe <xref:System.Windows.Media.Geometry> e as classes que derivam dela, como <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>e <xref:System.Windows.Media.CombinedGeometry>, permitem que você descreva a geometria de uma forma 2D. Essas descrições geométricas têm muitos tipos de uso, como definir uma forma para pintar na tela ou definir regiões de teste de clique e recorte. Você pode até mesmo usar uma geometria para definir um caminho de animação.  
  
 <xref:System.Windows.Media.Geometry> objetos podem ser simples, como retângulos e círculos, ou compostos, criados a partir de dois ou mais objetos Geometry.  Geometrias mais complexas podem ser criadas usando as classes <xref:System.Windows.Media.PathGeometry> e <xref:System.Windows.Media.StreamGeometry>, que permitem descrever arcos e curvas.  
  
 Como um <xref:System.Windows.Media.Geometry> é um tipo de <xref:System.Windows.Freezable>, os objetos <xref:System.Windows.Media.Geometry> fornecem vários recursos especiais: eles podem ser declarados como [recursos](../../../desktop-wpf/fundamentals/xaml-resources-define.md), compartilhados entre vários objetos, feitos somente leitura para melhorar o desempenho, clonado e tornado thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos por <xref:System.Windows.Freezable> objetos, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometrias versus formas  
 As classes <xref:System.Windows.Media.Geometry> e <xref:System.Windows.Shapes.Shape> parecem semelhantes, pois ambas descrevem formas 2D (compare <xref:System.Windows.Media.EllipseGeometry> e <xref:System.Windows.Shapes.Ellipse>, por exemplo), mas há diferenças importantes.  
  
 Para um, a classe <xref:System.Windows.Media.Geometry> herda da classe <xref:System.Windows.Freezable> enquanto a classe <xref:System.Windows.Shapes.Shape> herda de <xref:System.Windows.FrameworkElement>. Como eles são elementos, <xref:System.Windows.Shapes.Shape> objetos podem se renderizar e participar do sistema de layout, enquanto <xref:System.Windows.Media.Geometry> objetos não podem.  
  
 Embora os objetos de <xref:System.Windows.Shapes.Shape> sejam mais prontamente utilizáveis do que <xref:System.Windows.Media.Geometry> objetos, <xref:System.Windows.Media.Geometry> objetos são mais versáteis. Embora um objeto <xref:System.Windows.Shapes.Shape> seja usado para renderizar gráficos 2D, um objeto <xref:System.Windows.Media.Geometry> pode ser usado para definir a região geométrica para gráficos 2D, definir uma região para recorte ou definir uma região para teste de clique, por exemplo.  
  
### <a name="the-path-shape"></a>A forma de caminho  
 Uma <xref:System.Windows.Shapes.Shape>, a classe <xref:System.Windows.Shapes.Path>, na verdade usa uma <xref:System.Windows.Media.Geometry> para descrever seu conteúdo. Ao definir a propriedade <xref:System.Windows.Shapes.Path.Data%2A> do <xref:System.Windows.Shapes.Path> com uma <xref:System.Windows.Media.Geometry> e definir suas propriedades <xref:System.Windows.Shapes.Shape.Fill%2A> e <xref:System.Windows.Shapes.Shape.Stroke%2A>, você pode renderizar uma <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Propriedades comuns que usam uma geometria  
 As seções anteriores mencionaram que os objetos de Geometria podem ser usados com outros objetos para uma variedade de propósitos, como desenhar formas, animação e recorte. A tabela a seguir lista várias classes que têm propriedades que usam um objeto <xref:System.Windows.Media.Geometry>.  
  
|Digite|propriedade|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Tipos simples de geometria  
 A classe base para todas as geometrias é a classe abstrata <xref:System.Windows.Media.Geometry>.  As classes que derivam da classe <xref:System.Windows.Media.Geometry> podem ser basicamente agrupadas em três categorias: geometrias simples, geometrias de caminho e geometrias compostas.  
  
 Classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>e <xref:System.Windows.Media.EllipseGeometry> e são usadas para criar formas geométricas básicas, como linhas, retângulos e círculos.  
  
- Uma <xref:System.Windows.Media.LineGeometry> é definida especificando o ponto inicial da linha e o ponto de extremidade.  
  
- Uma <xref:System.Windows.Media.RectangleGeometry> é definida com uma estrutura de <xref:System.Windows.Rect> que especifica sua posição relativa e sua altura e largura. Você pode criar um retângulo arredondado definindo as propriedades <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>.  
  
- Um <xref:System.Windows.Media.EllipseGeometry> é definido por um ponto central, um raio x e um y-RADIUS.  Os exemplos a seguir mostram como criar geometrias simples para renderização e recorte.  
  
 Essas mesmas formas, bem como formas mais complexas, podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou combinando objetos Geometry juntos, mas essas classes fornecem um meio mais simples de produzir essas formas geométricas básicas.  
  
 O exemplo a seguir mostra como criar e renderizar um <xref:System.Windows.Media.LineGeometry>.  Como observado anteriormente, um objeto <xref:System.Windows.Media.Geometry> não consegue se desenhar, portanto, o exemplo usa uma forma <xref:System.Windows.Shapes.Path> para renderizar a linha.  Como uma linha não tem nenhuma área, definir a propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> da <xref:System.Windows.Shapes.Path> não teria nenhum efeito; em vez disso, somente as propriedades <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> são especificadas. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Uma LineGeometry desenhada de (10,20) para (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 O exemplo a seguir mostra como criar e renderizar um <xref:System.Windows.Media.EllipseGeometry>.  Os exemplos definem o <xref:System.Windows.Media.EllipseGeometry.Center%2A> do <xref:System.Windows.Media.EllipseGeometry> é definido como o ponto `50,50` e o raio x e o raio y são definidos como `50`, o que cria um círculo com um diâmetro de 100.  O interior da elipse é pintado atribuindo um valor à propriedade Fill do elemento Path, neste caso <xref:System.Windows.Media.Brushes.Gold%2A>. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Uma EllipseGeometry desenhada em (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 O exemplo a seguir mostra como criar e renderizar um <xref:System.Windows.Media.RectangleGeometry>.  A posição e as dimensões do retângulo são definidas por uma estrutura de <xref:System.Windows.Rect>. A posição é `50,50` e a altura e largura são ambas `25`, o que cria um quadrado. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Uma RectangleGeometry desenhada em 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 O exemplo a seguir mostra como usar uma <xref:System.Windows.Media.EllipseGeometry> como a região do clipe para uma imagem.  Um objeto <xref:System.Windows.Controls.Image> é definido com um <xref:System.Windows.FrameworkElement.Width%2A> de 200 e um <xref:System.Windows.FrameworkElement.Height%2A> de 150.  Um <xref:System.Windows.Media.EllipseGeometry> com um valor de <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> de 100, um valor de <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> de 75 e um valor de <xref:System.Windows.Media.EllipseGeometry.Center%2A> de 100, 75 é definido como a propriedade <xref:System.Windows.UIElement.Clip%2A> da imagem.  Somente a parte da imagem que estiver dentro da área da elipse será exibida. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma imagem com e sem recorte](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Uma EllipseGeometry usada para recortar um controle de Imagem  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Geometrias de caminho  
 A classe <xref:System.Windows.Media.PathGeometry> e seu equivalente leve, a classe <xref:System.Windows.Media.StreamGeometry>, fornecem os meios para descrever várias figuras complexas compostas por arcos, curvas e linhas.  
  
 No coração de um <xref:System.Windows.Media.PathGeometry> é uma coleção de objetos <xref:System.Windows.Media.PathFigure>, portanto, nomeados porque cada figura descreve uma forma discreta na <xref:System.Windows.Media.PathGeometry>. Cada <xref:System.Windows.Media.PathFigure> é, em si, composta de um ou mais objetos <xref:System.Windows.Media.PathSegment>, cada um deles descreve um segmento da figura.  
  
 Há muitos tipos de segmentos.  
  
|Tipo de segmento|Descrição|Exemplo|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Cria um arco elíptico entre dois pontos.|[Criar um arco elíptico](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Cria uma curva de Bézier cúbica entre dois pontos.|[Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Cria uma linha entre dois pontos.|[Criar um LineSegment em uma PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Cria uma série de curvas de Bézier cúbicas.|Consulte a página tipo de <xref:System.Windows.Media.PolyBezierSegment>.|  
|<xref:System.Windows.Media.PolyLineSegment>|Cria uma série de linhas.|Consulte a página tipo de <xref:System.Windows.Media.PolyLineSegment>.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Cria uma série de curvas de Bézier quadráticas.|Consulte a página <xref:System.Windows.Media.PolyQuadraticBezierSegment>.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Cria uma curva de Bezier quadrática.|[Criar uma curva de Bezier quadrática](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Os segmentos dentro de uma <xref:System.Windows.Media.PathFigure> são combinados em uma única forma geométrica com o ponto de extremidade de cada segmento sendo o ponto de partida do próximo segmento. A propriedade <xref:System.Windows.Media.PathFigure.StartPoint%2A> de um <xref:System.Windows.Media.PathFigure> especifica o ponto a partir do qual o primeiro segmento é desenhado. Cada segmento subsequente começa no ponto de extremidade do segmento anterior. Por exemplo, uma linha vertical de `10,50` para `10,150` pode ser definida definindo a propriedade <xref:System.Windows.Media.PathFigure.StartPoint%2A> como `10,50` e criando um <xref:System.Windows.Media.LineSegment> com uma configuração de propriedade <xref:System.Windows.Media.LineSegment.Point%2A> de `10,150`.  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.PathGeometry> simples composto de um único <xref:System.Windows.Media.PathFigure> com um <xref:System.Windows.Media.LineSegment> e o exibe usando um elemento <xref:System.Windows.Shapes.Path>. O <xref:System.Windows.Media.PathFigure.StartPoint%2A> do objeto de <xref:System.Windows.Media.PathFigure> é definido como `10,20` e um <xref:System.Windows.Media.LineSegment> é definido com um ponto de extremidade de `100,130`. A ilustração a seguir mostra o <xref:System.Windows.Media.PathGeometry> criado por este exemplo.  
  
 ![Uma LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Uma PathGeometry que contém um único LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Vale a pena contrastar este exemplo com o exemplo de <xref:System.Windows.Media.LineGeometry> anterior.  A sintaxe usada para uma <xref:System.Windows.Media.PathGeometry> é muito mais detalhada do que a usada para uma <xref:System.Windows.Media.LineGeometry>simples, e pode fazer mais sentido usar a classe <xref:System.Windows.Media.LineGeometry> nesse caso, mas a sintaxe detalhada do <xref:System.Windows.Media.PathGeometry> permite regiões geométricas extremamente complexas e complexas.  
  
 Geometrias mais complexas podem ser criadas usando uma combinação de objetos <xref:System.Windows.Media.PathSegment>.  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.BezierSegment>, um <xref:System.Windows.Media.LineSegment>e um <xref:System.Windows.Media.ArcSegment> para criar uma forma. O exemplo primeiro cria uma curva de Bézier cúbica definindo quatro pontos: um ponto de partida, que é o ponto final do segmento anterior, um ponto de extremidade (<xref:System.Windows.Media.BezierSegment.Point3%2A>) e dois pontos de controle (<xref:System.Windows.Media.BezierSegment.Point1%2A> e <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Os dois pontos de controle de uma curva de Bézier cúbica comportam-se como ímãs, atraindo partes do que seria uma linha reta em direção a eles mesmos, produzindo uma curva. O primeiro ponto de controle, <xref:System.Windows.Media.BezierSegment.Point1%2A>, afeta a parte inicial da curva; o segundo ponto de controle, <xref:System.Windows.Media.BezierSegment.Point2%2A>, afeta a parte final da curva.  
  
 Em seguida, o exemplo adiciona um <xref:System.Windows.Media.LineSegment>, que é desenhado entre o ponto de extremidade do <xref:System.Windows.Media.BezierSegment> anterior que o precede para o ponto especificado por sua propriedade <xref:System.Windows.Media.LineSegment>.  
  
 Em seguida, o exemplo adiciona um <xref:System.Windows.Media.ArcSegment>, que é desenhado a partir do ponto de extremidade da <xref:System.Windows.Media.LineSegment> anterior ao ponto especificado por sua propriedade <xref:System.Windows.Media.ArcSegment.Point%2A>. O exemplo também especifica o raio x e y (<xref:System.Windows.Media.ArcSegment.Size%2A>) do arco, um ângulo de rotação (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), um sinalizador indicando o tamanho do ângulo resultante (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) e um valor que indica em qual direção o arco é desenhado (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). A ilustração a seguir mostra a forma criada por esse exemplo.  
  
 ![Uma PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
Uma PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Geometrias ainda mais complexas podem ser criadas usando vários objetos <xref:System.Windows.Media.PathFigure> dentro de um <xref:System.Windows.Media.PathGeometry>.  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.PathGeometry> com dois objetos <xref:System.Windows.Media.PathFigure>, cada um contendo vários objetos <xref:System.Windows.Media.PathSegment>.  O <xref:System.Windows.Media.PathFigure> do exemplo acima e um <xref:System.Windows.Media.PathFigure> com um <xref:System.Windows.Media.PolyLineSegment> e um <xref:System.Windows.Media.QuadraticBezierSegment> são usados.  Uma <xref:System.Windows.Media.PolyLineSegment> é definida com uma matriz de pontos e a <xref:System.Windows.Media.QuadraticBezierSegment> é definida com um ponto de controle e um ponto de extremidade. A ilustração a seguir mostra a forma criada por esse exemplo.  
  
 ![Uma PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
Uma PathGeometry com várias figuras  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Como a classe <xref:System.Windows.Media.PathGeometry>, uma <xref:System.Windows.Media.StreamGeometry> define uma forma geométrica complexa que pode conter curvas, arcos e linhas. Ao contrário de uma <xref:System.Windows.Media.PathGeometry>, o conteúdo de um <xref:System.Windows.Media.StreamGeometry> não oferece suporte à vinculação de dados, animação ou modificação. Use um <xref:System.Windows.Media.StreamGeometry> quando precisar descrever uma geometria complexa, mas não quiser a sobrecarga de suporte à vinculação de dados, à animação ou à modificação. Devido à sua eficiência, a classe <xref:System.Windows.Media.StreamGeometry> é uma boa opção para descrever adorners.  
  
 Para obter um exemplo, consulte [Instruções: criar uma forma usando uma StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Sintaxe de marcação do caminho  
 Os tipos <xref:System.Windows.Media.PathGeometry> e <xref:System.Windows.Media.StreamGeometry> dão suporte a uma sintaxe de atributo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] usando uma série especial de comandos move e Draw. Para obter mais informações, consulte [Sintaxe de marcação de caminho](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Geometrias compostas  
 Objetos de geometria composta podem ser criados usando um <xref:System.Windows.Media.GeometryGroup>, um <xref:System.Windows.Media.CombinedGeometry>ou chamando o método de <xref:System.Windows.Media.Geometry> estático <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
- O objeto <xref:System.Windows.Media.CombinedGeometry> e o método <xref:System.Windows.Media.Geometry.Combine%2A> executa uma operação booliana para combinar a área definida por duas geometrias. <xref:System.Windows.Media.Geometry> objetos que não têm nenhuma área são descartados. Somente dois objetos <xref:System.Windows.Media.Geometry> podem ser combinados (embora essas duas geometrias também possam ser geometrias compostas).  
  
- A classe <xref:System.Windows.Media.GeometryGroup> cria um ajuntamento do <xref:System.Windows.Media.Geometry> objetos que ele contém sem combinar sua área. Qualquer número de objetos <xref:System.Windows.Media.Geometry> pode ser adicionado a um <xref:System.Windows.Media.GeometryGroup>. Para obter um exemplo, consulte [Instruções: criar uma forma composta](how-to-create-a-composite-shape.md).  
  
 Como não executam uma operação de combinação, o uso de objetos <xref:System.Windows.Media.GeometryGroup> fornece benefícios de desempenho usando objetos <xref:System.Windows.Media.CombinedGeometry> ou o método <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Geometrias combinadas  
 A seção anterior mencionou o objeto <xref:System.Windows.Media.CombinedGeometry> e o método <xref:System.Windows.Media.Geometry.Combine%2A> combinam a área definida pelas geometrias que eles contêm. A enumeração <xref:System.Windows.Media.GeometryCombineMode> especifica como as geometrias são combinadas. Os valores possíveis para a propriedade <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> são: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>e <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 No exemplo a seguir, um <xref:System.Windows.Media.CombinedGeometry> é definido com um modo de combinação de Union.  Tanto <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> quanto os <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos do mesmo raio, mas com deslocamento de centros de 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Resultados do modo de combinação Union](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 No exemplo a seguir, um <xref:System.Windows.Media.CombinedGeometry> é definido com um modo de combinação de <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Tanto <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> quanto os <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos do mesmo raio, mas com deslocamento de centros de 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Resultados do modo de combinação Xor](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Para obter exemplos adicionais, consulte [Instruções: criar uma forma composta](how-to-create-a-composite-shape.md) e [Instruções: criar uma geometria combinada](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Recursos congeláveis  
 Como ele é herdado da classe <xref:System.Windows.Freezable>, a classe <xref:System.Windows.Media.Geometry> fornece vários recursos especiais: <xref:System.Windows.Media.Geometry> objetos podem ser declarados como [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md), compartilhados entre vários objetos, feitos somente leitura para melhorar o desempenho, clonado e feito thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos por <xref:System.Windows.Freezable> objetos, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Outras funcionalidades da geometria  
 A classe <xref:System.Windows.Media.Geometry> também fornece métodos de utilitário úteis, como o seguinte:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>-Obtém a área do <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>-determina se a geometria contém outra <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>-determina se o traço de uma <xref:System.Windows.Media.Geometry> contém um ponto especificado.  
  
 Consulte a classe <xref:System.Windows.Media.Geometry> para obter uma lista completa de seus métodos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Sintaxe de marcação de caminho](path-markup-syntax.md)
- [Tópicos explicativos](geometries-how-to-topics.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
