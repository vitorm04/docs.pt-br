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
ms.openlocfilehash: 01c460ae18c489a21c860c6d2b10f551e6e68242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="geometry-overview"></a>Visão geral da geometria
Esta visão geral descreve como usar o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> classes para descrever formas. Este tópico também contrasta as diferenças entre <xref:System.Windows.Media.Geometry> objetos e <xref:System.Windows.Shapes.Shape> elementos.  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>O que é uma geometria?  
 O <xref:System.Windows.Media.Geometry> e as classes que derivam dela, como <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, e <xref:System.Windows.Media.CombinedGeometry>, permitem que você descreva a geometria de uma forma 2D. Essas descrições geométricas têm muitos tipos de uso, como definir uma forma para pintar na tela ou definir regiões de teste de clique e recorte. Você pode até mesmo usar uma geometria para definir um caminho de animação.  
  
 <xref:System.Windows.Media.Geometry> objetos podem ser simples, como retângulos e círculos ou compostos, criados a partir de dois ou mais objetos de geometria.  Geometrias mais complexas podem ser criadas usando o <xref:System.Windows.Media.PathGeometry> e <xref:System.Windows.Media.StreamGeometry> classes, que permitem que você descreva arcos e curvas.  
  
 Porque um <xref:System.Windows.Media.Geometry> é um tipo de <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> objetos fornecem vários recursos especiais: eles podem ser declarados como [recursos](../../../../docs/framework/wpf/advanced/xaml-resources.md), compartilhados entre vários objetos, feitos somente leitura para melhorar o desempenho, clonado, e feita a thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos pelo <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometrias versus. Formas  
 O <xref:System.Windows.Media.Geometry> e <xref:System.Windows.Shapes.Shape> classes parecem semelhantes, pois ambas descrevem formas 2-D (compare <xref:System.Windows.Media.EllipseGeometry> e <xref:System.Windows.Shapes.Ellipse> por exemplo), mas há diferenças importantes.  
  
 Por exemplo, o <xref:System.Windows.Media.Geometry> classe herda do <xref:System.Windows.Freezable> classe ao <xref:System.Windows.Shapes.Shape> classe herda de <xref:System.Windows.FrameworkElement>. Como eles são elementos, <xref:System.Windows.Shapes.Shape> objetos pode renderizar a próprios e participar no sistema de layout, enquanto <xref:System.Windows.Media.Geometry> objetos com não.  
  
 Embora <xref:System.Windows.Shapes.Shape> objetos são mais prontamente usáveis que <xref:System.Windows.Media.Geometry> objetos, <xref:System.Windows.Media.Geometry> objetos são mais versáteis. Enquanto um <xref:System.Windows.Shapes.Shape> objeto é usado para renderizar elementos gráficos 2D, um <xref:System.Windows.Media.Geometry> objeto pode ser usado para definir a região geométrica para gráficos 2D, definir uma região de recorte ou definir uma região para teste de clique, por exemplo.  
  
### <a name="the-path-shape"></a>A forma de caminho  
 Um <xref:System.Windows.Shapes.Shape>, o <xref:System.Windows.Shapes.Path> de classe, na verdade usa um <xref:System.Windows.Media.Geometry> para descrever seu conteúdo. Definindo o <xref:System.Windows.Shapes.Path.Data%2A> propriedade o <xref:System.Windows.Shapes.Path> com um <xref:System.Windows.Media.Geometry> e configuração seu <xref:System.Windows.Shapes.Shape.Fill%2A> e <xref:System.Windows.Shapes.Shape.Stroke%2A> propriedades, você pode renderizar um <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Propriedades comuns que usam uma geometria  
 As seções anteriores mencionaram que os objetos de Geometria podem ser usados com outros objetos para uma variedade de propósitos, como desenhar formas, animação e recorte. A tabela a seguir lista várias classes que têm propriedades que recebem um <xref:System.Windows.Media.Geometry> objeto.  
  
|Tipo|Propriedade|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Tipos simples de geometria  
 A classe base para todas as geometrias é a classe abstrata <xref:System.Windows.Media.Geometry>.  As classes que derivam de <xref:System.Windows.Media.Geometry> classe pode ser agrupada aproximadamente em três categorias: geometrias simples, geometrias de caminho e geometrias compostas.  
  
 Classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, e <xref:System.Windows.Media.EllipseGeometry> e são usados para criar formas geométricas básicas, como linhas, retângulos e círculos.  
  
-   Um <xref:System.Windows.Media.LineGeometry> é definida especificando o ponto inicial da linha e o ponto de extremidade.  
  
-   Um <xref:System.Windows.Media.RectangleGeometry> está definida com um <xref:System.Windows.Rect> estrutura que especifica sua posição relativa e sua altura e largura. Você pode criar um retângulo arredondado definindo o <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades.  
  
-   Um <xref:System.Windows.Media.EllipseGeometry> é definido por um ponto central, um raio de x e y-raio.  Os exemplos a seguir mostram como criar geometrias simples para renderização e recorte.  
  
 Essas mesmas formas, bem como formas mais complexas, podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou combinando objetos geometria juntos, mas essas classes fornecem um meio mais simples para produzir essas formas geométricas básicas.  
  
 O exemplo a seguir mostra como criar e processar um <xref:System.Windows.Media.LineGeometry>.  Conforme observado anteriormente, um <xref:System.Windows.Media.Geometry> não é possível desenhar a próprio, então o exemplo usa objeto um <xref:System.Windows.Shapes.Path> forma para processar a linha.  Porque uma linha não tem nenhuma área, definindo o <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade o <xref:System.Windows.Shapes.Path> não causa nenhum efeito; em vez disso, somente o <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedades são especificadas. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Um LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Uma LineGeometry desenhada de (10,20) para (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 O exemplo a seguir mostra como criar e processar um <xref:System.Windows.Media.EllipseGeometry>.  Os conjuntos de exemplos de <xref:System.Windows.Media.EllipseGeometry.Center%2A> do <xref:System.Windows.Media.EllipseGeometry> é definido como o ponto de `50,50` e o raio x e y-radius são definidos como `50`, que cria um círculo com diâmetro de 100.  O interior da elipse é pintado atribuindo um valor à propriedade de preenchimento do elemento Path, nesse caso <xref:System.Windows.Media.Brushes.Gold%2A>. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Um EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Uma EllipseGeometry desenhada em (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 O exemplo a seguir mostra como criar e processar um <xref:System.Windows.Media.RectangleGeometry>.  A posição e as dimensões do retângulo são definidas por um <xref:System.Windows.Rect> estrutura. A posição é `50,50` e a altura e largura são ambas `25`, o que cria um quadrado. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma geometria de retângulos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Uma RectangleGeometry desenhada em 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 O exemplo a seguir mostra como usar um <xref:System.Windows.Media.EllipseGeometry> como a região de clip para uma imagem.  Um <xref:System.Windows.Controls.Image> objeto é definido com um <xref:System.Windows.FrameworkElement.Width%2A> de 200 e um <xref:System.Windows.FrameworkElement.Height%2A> de 150.  Um <xref:System.Windows.Media.EllipseGeometry> com um <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> valor de 100, uma <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> valor de 75 e um <xref:System.Windows.Media.EllipseGeometry.Center%2A> valor 100,75 é definido como o <xref:System.Windows.UIElement.Clip%2A> propriedades da imagem.  Somente a parte da imagem que estiver dentro da área da elipse será exibida. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma imagem com e sem recorte](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Uma EllipseGeometry usada para recortar um controle de Imagem  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Geometrias de caminho  
 O <xref:System.Windows.Media.PathGeometry> classe e seu equivalente leve, a <xref:System.Windows.Media.StreamGeometry> classe, fornecem os meios para descrever múltiplas figuras complexas compostas de arcos, curvas e linhas.  
  
 No Centro de um <xref:System.Windows.Media.PathGeometry> é uma coleção de <xref:System.Windows.Media.PathFigure> objetos, chamados assim porque cada figura descreve uma forma discreta no <xref:System.Windows.Media.PathGeometry>. Cada <xref:System.Windows.Media.PathFigure> é composto de um ou mais <xref:System.Windows.Media.PathSegment> objetos, cada um deles descreve um segmento da figura.  
  
 Há muitos tipos de segmentos.  
  
|Tipo de segmento|Descrição|Exemplo|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Cria um arco elíptico entre dois pontos.|[Criar um arco elíptico](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Cria uma curva de Bézier cúbica entre dois pontos.|[Criar uma curva de Bézier cúbica](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Cria uma linha entre dois pontos.|[Criar um LineSegment em uma PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Cria uma série de curvas de Bézier cúbicas.|Consulte o <xref:System.Windows.Media.PolyBezierSegment> página de tipo.|  
|<xref:System.Windows.Media.PolyLineSegment>|Cria uma série de linhas.|Consulte o <xref:System.Windows.Media.PolyLineSegment> página de tipo.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Cria uma série de curvas de Bézier quadráticas.|Consulte o <xref:System.Windows.Media.PolyQuadraticBezierSegment> página.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Cria uma curva de Bezier quadrática.|[Criar uma curva de Bezier quadrática](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 Os segmentos de dentro de um <xref:System.Windows.Media.PathFigure> são combinados em uma única forma geométrica com o ponto de extremidade de cada segmento sendo o ponto inicial do segmento seguinte. O <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriedade de um <xref:System.Windows.Media.PathFigure> Especifica o ponto do qual o primeiro segmento é desenhado. Cada segmento subsequente começa no ponto de extremidade do segmento anterior. Por exemplo, uma linha vertical da `10,50` para `10,150` podem ser definidas, definindo o <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriedade `10,50` e criando um <xref:System.Windows.Media.LineSegment> com um <xref:System.Windows.Media.LineSegment.Point%2A> configuração da propriedade de `10,150`.  
  
 O exemplo a seguir cria um simples <xref:System.Windows.Media.PathGeometry> composta de um único <xref:System.Windows.Media.PathFigure> com um <xref:System.Windows.Media.LineSegment> e exibe-o usando um <xref:System.Windows.Shapes.Path> elemento. O <xref:System.Windows.Media.PathFigure> do objeto <xref:System.Windows.Media.PathFigure.StartPoint%2A> é definido como `10,20` e um <xref:System.Windows.Media.LineSegment> está definida com um ponto final de `100,130`. A ilustração a seguir mostra o <xref:System.Windows.Media.PathGeometry> criado por esse exemplo.  
  
 ![Um LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Uma PathGeometry que contém um único LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Vale a pena contrastar esse exemplo com anterior <xref:System.Windows.Media.LineGeometry> exemplo.  A sintaxe usada para um <xref:System.Windows.Media.PathGeometry> é muito mais detalhado do que aquela usada para uma simples <xref:System.Windows.Media.LineGeometry>, e pode fazer mais sentido usar a <xref:System.Windows.Media.LineGeometry> classe nesse caso, mas a sintaxe detalhada do <xref:System.Windows.Media.PathGeometry> permite extremamente complexas e complexas regiões geométricas.  
  
 Geometrias mais complexas podem ser criadas usando uma combinação de <xref:System.Windows.Media.PathSegment> objetos.  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.BezierSegment>, um <xref:System.Windows.Media.LineSegment>e um <xref:System.Windows.Media.ArcSegment> para criar forma. O exemplo cria uma curva Bézier cúbica definindo quatro pontos: um ponto inicial, que é o ponto de extremidade do segmento anterior, um ponto final (<xref:System.Windows.Media.BezierSegment.Point3%2A>), e dois pontos de controle (<xref:System.Windows.Media.BezierSegment.Point1%2A> e <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Os dois pontos de controle de uma curva de Bézier cúbica comportam-se como ímãs, atraindo partes do que seria uma linha reta em direção a eles mesmos, produzindo uma curva. O primeiro ponto de controle, <xref:System.Windows.Media.BezierSegment.Point1%2A>, afeta o início parte da curva; o segundo ponto de controle, <xref:System.Windows.Media.BezierSegment.Point2%2A>, afeta a parte final da curva.  
  
 O exemplo adiciona um <xref:System.Windows.Media.LineSegment>, que é desenhada entre o ponto de extremidade de anterior <xref:System.Windows.Media.BezierSegment> precedente ao ponto especificado por seu <xref:System.Windows.Media.LineSegment> propriedade.  
  
 O exemplo adiciona um <xref:System.Windows.Media.ArcSegment>, que é desenhado a partir do ponto de extremidade dos <xref:System.Windows.Media.LineSegment> para o ponto especificado por seu <xref:System.Windows.Media.ArcSegment.Point%2A> propriedade. O exemplo também especifica os raios do arco x e y-(<xref:System.Windows.Media.ArcSegment.Size%2A>), um ângulo de rotação (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), um sinalizador que indica quanto o ângulo do arco resultante deve ser (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) e um valor que indica em qual direção o arco é desenhado (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). A ilustração a seguir mostra a forma criada por esse exemplo.  
  
 ![Um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
Uma PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Geometrias ainda mais complexas podem ser criadas por meio de várias <xref:System.Windows.Media.PathFigure> objetos dentro de um <xref:System.Windows.Media.PathGeometry>.  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.PathGeometry> com dois <xref:System.Windows.Media.PathFigure> objetos, cada uma delas contém várias <xref:System.Windows.Media.PathSegment> objetos.  O <xref:System.Windows.Media.PathFigure> do exemplo acima e uma <xref:System.Windows.Media.PathFigure> com um <xref:System.Windows.Media.PolyLineSegment> e um <xref:System.Windows.Media.QuadraticBezierSegment> são usados.  Um <xref:System.Windows.Media.PolyLineSegment> está definida com uma matriz de pontos e o <xref:System.Windows.Media.QuadraticBezierSegment> é definido com um ponto de controle e um ponto de extremidade. A ilustração a seguir mostra a forma criada por esse exemplo.  
  
 ![Um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
Uma PathGeometry com várias figuras  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Como o <xref:System.Windows.Media.PathGeometry> classe, um <xref:System.Windows.Media.StreamGeometry> define uma forma geométrica complexa que pode conter linhas, arcos e curvas. Ao contrário de um <xref:System.Windows.Media.PathGeometry>, o conteúdo de um <xref:System.Windows.Media.StreamGeometry> não dão suporte a associação de dados, animação ou modificação. Use um <xref:System.Windows.Media.StreamGeometry> quando você precisa descrever uma geometria complexa, mas não quiser que a sobrecarga de associação de dados, animação ou modificação de suporte. Por causa de sua eficiência, a <xref:System.Windows.Media.StreamGeometry> classe é uma boa escolha para descrever decoradores.  
  
 Para obter um exemplo, consulte [Instruções: criar uma forma usando uma StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Sintaxe de marcação do caminho  
 O <xref:System.Windows.Media.PathGeometry> e <xref:System.Windows.Media.StreamGeometry> tipos de suporte a um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] usando uma série especial de movimentação de sintaxe de atributo e comandos de desenho. Para obter mais informações, consulte [Sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Geometrias compostas  
 Objetos de geometria composta podem ser criados usando um <xref:System.Windows.Media.GeometryGroup>, um <xref:System.Windows.Media.CombinedGeometry>, ou chamando estático <xref:System.Windows.Media.Geometry> método <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   O <xref:System.Windows.Media.CombinedGeometry> objeto e o <xref:System.Windows.Media.Geometry.Combine%2A> método executa uma operação booleana para combinar a área definida pelas duas geometrias. <xref:System.Windows.Media.Geometry> objetos que não possuem área são descartados. Apenas dois <xref:System.Windows.Media.Geometry> objetos podem ser combinados (Embora essas duas geometrias também podem ser geometrias compostas).  
  
-   O <xref:System.Windows.Media.GeometryGroup> classe cria uma junção do <xref:System.Windows.Media.Geometry> objetos que ele contém sem combinar suas áreas. Qualquer número de <xref:System.Windows.Media.Geometry> objetos podem ser adicionados a um <xref:System.Windows.Media.GeometryGroup>. Para obter um exemplo, consulte [Instruções: criar uma forma composta](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md).  
  
 Porque eles não executam uma operação de combinar, usando <xref:System.Windows.Media.GeometryGroup> objetos fornece benefícios de desempenho com o uso <xref:System.Windows.Media.CombinedGeometry> objetos ou o <xref:System.Windows.Media.Geometry.Combine%2A> método.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Geometrias combinadas  
 A seção anterior mencionada o <xref:System.Windows.Media.CombinedGeometry> objeto e o <xref:System.Windows.Media.Geometry.Combine%2A> método combinar a área definida pelas geometrias que eles contêm. O <xref:System.Windows.Media.GeometryCombineMode> enumeração que especifica como as geometrias são combinadas. Os valores possíveis para a <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> propriedade são: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, e <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 No exemplo a seguir, um <xref:System.Windows.Media.CombinedGeometry> é definido com um modo combinar de união.  Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros de deslocamento por 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Resultados do modo de combinar de União](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 No exemplo a seguir, uma <xref:System.Windows.Media.CombinedGeometry> está definida com um modo combinar de <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros de deslocamento por 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Resultados do modo de combinar de Xor](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Para obter exemplos adicionais, consulte [Instruções: criar uma forma composta](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md) e [Instruções: criar uma geometria combinada](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Recursos congeláveis  
 Porque ele herda do <xref:System.Windows.Freezable> classe, o <xref:System.Windows.Media.Geometry> classe fornece vários recursos especiais: <xref:System.Windows.Media.Geometry> objetos podem ser declarados como [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md), compartilhados entre vários objetos, feitos somente leitura para melhorar desempenho, clonados e tornados thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos pelo <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Outras funcionalidades da geometria  
 O <xref:System.Windows.Media.Geometry> classe também fornece métodos de utilitário úteis, como o seguinte:  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -Obtém a área do <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> -Determina se o Geometry contém outro <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> -Determina se o traço de um <xref:System.Windows.Media.Geometry> contém um ponto específico.  
  
 Consulte o <xref:System.Windows.Media.Geometry> classe para uma lista completa de seus métodos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Geometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral de formas e desenho básico no WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
