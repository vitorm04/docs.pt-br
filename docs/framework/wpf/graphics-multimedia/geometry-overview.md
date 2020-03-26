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
ms.openlocfilehash: ff42e59edd9d98b0b52dc3bdd3ace0c35df60878
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112369"
---
# <a name="geometry-overview"></a>Visão geral da geometria
Esta visão geral descreve como [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> usar as classes para descrever formas. Este tópico também contrasta <xref:System.Windows.Media.Geometry> as <xref:System.Windows.Shapes.Shape> diferenças entre objetos e elementos.  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>O que é uma geometria?  
 A <xref:System.Windows.Media.Geometry> classe e as classes que <xref:System.Windows.Media.EllipseGeometry>derivam dela, tais como , <xref:System.Windows.Media.PathGeometry>e <xref:System.Windows.Media.CombinedGeometry>, permitem que você descreva a geometria de uma forma 2D. Essas descrições geométricas têm muitos tipos de uso, como definir uma forma para pintar na tela ou definir regiões de teste de clique e recorte. Você pode até mesmo usar uma geometria para definir um caminho de animação.  
  
 <xref:System.Windows.Media.Geometry>objetos podem ser simples, como retângulos e círculos, ou composto, criados a partir de dois ou mais objetos de geometria.  Geometrias mais complexas podem ser <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> criadas usando as classes e classes, que permitem descrever arcos e curvas.  
  
 Como <xref:System.Windows.Media.Geometry> a é <xref:System.Windows.Freezable>um <xref:System.Windows.Media.Geometry> tipo de , objetos fornecem várias características especiais: eles podem ser declarados como [recursos,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)compartilhados entre vários objetos, feitos somente de leitura para melhorar o desempenho, clonados e feitos como thread-safe. Para obter mais informações sobre <xref:System.Windows.Freezable> os diferentes recursos fornecidos pelos objetos, consulte a visão geral dos [objetos acongelamento](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>Geometrias vs. Formas  
 As <xref:System.Windows.Media.Geometry> <xref:System.Windows.Shapes.Shape> classes e as classes parecem semelhantes na <xref:System.Windows.Media.EllipseGeometry> forma <xref:System.Windows.Shapes.Ellipse> que ambos descrevem formas 2D (compare e por exemplo), mas há diferenças importantes.  
  
 Por um, <xref:System.Windows.Media.Geometry> a classe <xref:System.Windows.Freezable> herda <xref:System.Windows.Shapes.Shape> da classe <xref:System.Windows.FrameworkElement>enquanto a classe herda de . Por serem elementos, <xref:System.Windows.Shapes.Shape> os objetos podem se <xref:System.Windows.Media.Geometry> render e participar do sistema de layout, enquanto os objetos não podem.  
  
 Embora <xref:System.Windows.Shapes.Shape> os objetos sejam <xref:System.Windows.Media.Geometry> mais <xref:System.Windows.Media.Geometry> facilmente utilizáveis do que os objetos, os objetos são mais versáteis. Enquanto <xref:System.Windows.Shapes.Shape> um objeto é usado para <xref:System.Windows.Media.Geometry> renderizar gráficos 2D, um objeto pode ser usado para definir a região geométrica para gráficos 2D, definir uma região para recorte ou definir uma região para teste de acerto, por exemplo.  
  
### <a name="the-path-shape"></a>A forma de caminho  
 Um <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> a classe, <xref:System.Windows.Media.Geometry> na verdade usa um para descrever seu conteúdo. Ao definir <xref:System.Windows.Shapes.Path.Data%2A> a <xref:System.Windows.Shapes.Path> propriedade <xref:System.Windows.Media.Geometry> do com <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> um e definir <xref:System.Windows.Media.Geometry>suas propriedades, você pode renderizar um .  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>Propriedades comuns que usam uma geometria  
 As seções anteriores mencionaram que os objetos de Geometria podem ser usados com outros objetos para uma variedade de propósitos, como desenhar formas, animação e recorte. A tabela a seguir lista várias <xref:System.Windows.Media.Geometry> classes que possuem propriedades que levam um objeto.  
  
|Type|Propriedade|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>Tipos simples de geometria  
 A classe base para todas as <xref:System.Windows.Media.Geometry>geometrias é a classe abstrata.  As classes que <xref:System.Windows.Media.Geometry> derivam da classe podem ser agrupadas em três categorias: geometrias simples, geometrias de caminho e geometrias compostas.  
  
 Aulas simples de <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>geometria incluem , e <xref:System.Windows.Media.EllipseGeometry> são usadas para criar formas geométricas básicas, como linhas, retângulos e círculos.  
  
- A <xref:System.Windows.Media.LineGeometry> é definido especificando o ponto de partida da linha e o ponto final.  
  
- A <xref:System.Windows.Media.RectangleGeometry> é definido <xref:System.Windows.Rect> com uma estrutura que especifica sua posição relativa e sua altura e largura. Você pode criar um retângulo <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> arredondado definindo as propriedades e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> as propriedades.  
  
- Um <xref:System.Windows.Media.EllipseGeometry> é definido por um ponto central, um raio x e um raio-y.  Os exemplos a seguir mostram como criar geometrias simples para renderização e recorte.  
  
 Essas mesmas formas, bem como formas mais complexas, podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou combinando objetos de geometria, mas essas classes fornecem um meio mais simples para produzir essas formas geométricas básicas.  
  
 O exemplo a seguir mostra <xref:System.Windows.Media.LineGeometry>como criar e renderizar um .  Como observado anteriormente, um <xref:System.Windows.Media.Geometry> objeto é incapaz de desenhar-se, de modo que o exemplo usa uma <xref:System.Windows.Shapes.Path> forma para renderizar a linha.  Como uma linha não tem <xref:System.Windows.Shapes.Shape.Fill%2A> área, <xref:System.Windows.Shapes.Path> definir a propriedade do não teria efeito; em vez <xref:System.Windows.Shapes.Shape.Stroke%2A> disso, apenas as propriedades e propriedades <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> são especificadas. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Uma LineGeometry desenhada de (10,20) para (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 O próximo exemplo mostra como <xref:System.Windows.Media.EllipseGeometry>criar e renderizar um .  Os exemplos <xref:System.Windows.Media.EllipseGeometry.Center%2A> definem <xref:System.Windows.Media.EllipseGeometry> o conjunto do `50,50` é definido para o ponto e o `50`raio-x e o raio-y são ambos definidos para, o que cria um círculo com um diâmetro de 100.  O interior da elipse é pintado atribuindo um valor à propriedade Fill <xref:System.Windows.Media.Brushes.Gold%2A>do elemento Path, neste caso . A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Uma EllipseGeometry desenhada em (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 O exemplo a seguir mostra <xref:System.Windows.Media.RectangleGeometry>como criar e renderizar um .  A posição e as dimensões do retângulo são definidas por uma <xref:System.Windows.Rect> estrutura. A posição é `50,50` e a altura e largura são ambas `25`, o que cria um quadrado. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Uma RectangleGeometry desenhada em 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 O exemplo a seguir <xref:System.Windows.Media.EllipseGeometry> mostra como usar uma região de clipe para uma imagem.  Um <xref:System.Windows.Controls.Image> objeto é <xref:System.Windows.FrameworkElement.Width%2A> definido com um <xref:System.Windows.FrameworkElement.Height%2A> de 200 e um de 150.  Um <xref:System.Windows.Media.EllipseGeometry> com <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> um valor de <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 100, um <xref:System.Windows.Media.EllipseGeometry.Center%2A> valor de 75, e um <xref:System.Windows.UIElement.Clip%2A> valor de 100,75 é definido para a propriedade da imagem.  Somente a parte da imagem que estiver dentro da área da elipse será exibida. A ilustração a seguir mostra a saída do exemplo.  
  
 ![Uma imagem com e sem recorte](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Uma EllipseGeometry usada para recortar um controle de Imagem  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>Geometrias de caminho  
 A <xref:System.Windows.Media.PathGeometry> classe e seu <xref:System.Windows.Media.StreamGeometry> equivalente leve, a classe, fornecem os meios para descrever múltiplas figuras complexas compostas de arcos, curvas e linhas.  
  
 No coração de <xref:System.Windows.Media.PathGeometry> um está <xref:System.Windows.Media.PathFigure> uma coleção de objetos, assim chamado porque <xref:System.Windows.Media.PathGeometry>cada figura descreve uma forma discreta no . Cada <xref:System.Windows.Media.PathFigure> um é composto por <xref:System.Windows.Media.PathSegment> um ou mais objetos, cada um dos quais descreve um segmento da figura.  
  
 Há muitos tipos de segmentos.  
  
|Tipo de segmento|Descrição|Exemplo|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Cria um arco elíptico entre dois pontos.|[Crie um arco elíptico.](how-to-create-an-elliptical-arc.md)|  
|<xref:System.Windows.Media.BezierSegment>|Cria uma curva de Bézier cúbica entre dois pontos.|[Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Cria uma linha entre dois pontos.|[Criar um LineSegment em uma PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Cria uma série de curvas de Bézier cúbicas.|Veja <xref:System.Windows.Media.PolyBezierSegment> a página do tipo.|  
|<xref:System.Windows.Media.PolyLineSegment>|Cria uma série de linhas.|Veja <xref:System.Windows.Media.PolyLineSegment> a página do tipo.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Cria uma série de curvas de Bézier quadráticas.|Veja <xref:System.Windows.Media.PolyQuadraticBezierSegment> a página.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Cria uma curva de Bezier quadrática.|[Crie uma curva de bezier quadrática](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Os segmentos <xref:System.Windows.Media.PathFigure> dentro de um são combinados em uma única forma geométrica com o ponto final de cada segmento sendo o ponto de partida do próximo segmento. A <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriedade <xref:System.Windows.Media.PathFigure> de um especifica o ponto a partir do qual o primeiro segmento é desenhado. Cada segmento subsequente começa no ponto de extremidade do segmento anterior. Por exemplo, uma `10,50` linha `10,150` vertical de para <xref:System.Windows.Media.PathFigure.StartPoint%2A> dado pode ser definida definindo a propriedade para `10,50` e criando <xref:System.Windows.Media.LineSegment> uma com uma <xref:System.Windows.Media.LineSegment.Point%2A> configuração de propriedade de `10,150`.  
  
 O exemplo a <xref:System.Windows.Media.PathGeometry> seguir cria um <xref:System.Windows.Media.PathFigure> simples <xref:System.Windows.Media.LineSegment> composto por <xref:System.Windows.Shapes.Path> um único com um e o exibe usando um elemento. O <xref:System.Windows.Media.PathFigure> objeto <xref:System.Windows.Media.PathFigure.StartPoint%2A> é definido `10,20` e <xref:System.Windows.Media.LineSegment> a é definido `100,130`com um ponto final de . A ilustração <xref:System.Windows.Media.PathGeometry> a seguir mostra a criada por este exemplo.  
  
 ![Uma LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Uma PathGeometry que contém um único LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Vale a pena contrastar este <xref:System.Windows.Media.LineGeometry> exemplo com o exemplo anterior.  A sintaxe <xref:System.Windows.Media.PathGeometry> usada para um é muito mais <xref:System.Windows.Media.LineGeometry>verbosa do que a <xref:System.Windows.Media.LineGeometry> usada para um simples , e pode <xref:System.Windows.Media.PathGeometry> fazer mais sentido usar a classe neste caso, mas a sintaxe verbose do permite regiões geométricas extremamente complexas e complexas.  
  
 Geometrias mais complexas podem ser criadas usando uma combinação de <xref:System.Windows.Media.PathSegment> objetos.  
  
 O próximo exemplo <xref:System.Windows.Media.BezierSegment>usa <xref:System.Windows.Media.LineSegment>uma <xref:System.Windows.Media.ArcSegment> forma , a e uma para criar. O exemplo primeiro cria uma curva de Bezier cúbica é definindo quatro pontos: um<xref:System.Windows.Media.BezierSegment.Point3%2A>ponto de partida, <xref:System.Windows.Media.BezierSegment.Point2%2A>que é o ponto final do segmento anterior, um ponto final ( ), e dois pontos de controle (e<xref:System.Windows.Media.BezierSegment.Point1%2A> ).  Os dois pontos de controle de uma curva de Bézier cúbica comportam-se como ímãs, atraindo partes do que seria uma linha reta em direção a eles mesmos, produzindo uma curva. O primeiro ponto <xref:System.Windows.Media.BezierSegment.Point1%2A>de controle, afeta a parte inicial da curva; o segundo ponto <xref:System.Windows.Media.BezierSegment.Point2%2A>de controle, afeta a parte final da curva.  
  
 O exemplo então <xref:System.Windows.Media.LineSegment>adiciona um , que é <xref:System.Windows.Media.BezierSegment> desenhado entre o ponto final do <xref:System.Windows.Media.LineSegment> precedente que o precedeu ao ponto especificado por sua propriedade.  
  
 O exemplo então <xref:System.Windows.Media.ArcSegment>adiciona um , que é <xref:System.Windows.Media.LineSegment> extraído do ponto final <xref:System.Windows.Media.ArcSegment.Point%2A> do anterior ao ponto especificado por sua propriedade. O exemplo também especifica o raio x e<xref:System.Windows.Media.ArcSegment.Size%2A>y do arco<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>( ), um ângulo de rotação ( ),<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>uma bandeira indicando o tamanho do ângulo<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>do arco resultante ( ), e um valor indicando em que direção o arco é desenhado ( ). A ilustração a seguir mostra a forma criada por esse exemplo.  
  
 ![Uma PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
Uma PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Geometrias ainda mais complexas podem <xref:System.Windows.Media.PathFigure> ser criadas usando vários objetos dentro de um <xref:System.Windows.Media.PathGeometry>.  
  
 O exemplo a <xref:System.Windows.Media.PathGeometry> seguir <xref:System.Windows.Media.PathFigure> cria um com <xref:System.Windows.Media.PathSegment> dois objetos, cada um dos quais contém vários objetos.  O <xref:System.Windows.Media.PathFigure> exemplo acima e <xref:System.Windows.Media.PathFigure> um <xref:System.Windows.Media.PolyLineSegment> com <xref:System.Windows.Media.QuadraticBezierSegment> a e a são usados.  A <xref:System.Windows.Media.PolyLineSegment> é definido com uma <xref:System.Windows.Media.QuadraticBezierSegment> matriz de pontos e o é definido com um ponto de controle e um ponto final. A ilustração a seguir mostra a forma criada por esse exemplo.  
  
 ![Uma PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
Uma PathGeometry com várias figuras  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Como <xref:System.Windows.Media.PathGeometry> a classe, uma <xref:System.Windows.Media.StreamGeometry> define uma forma geométrica complexa que pode conter curvas, arcos e linhas. Ao <xref:System.Windows.Media.PathGeometry>contrário de a <xref:System.Windows.Media.StreamGeometry> , o conteúdo de um não suporta vinculação de dados, animação ou modificação. Use <xref:System.Windows.Media.StreamGeometry> um quando você precisar descrever uma geometria complexa, mas não deseja a sobrecarga de suporte à vinculação de dados, animação ou modificação. Devido à sua eficiência, a <xref:System.Windows.Media.StreamGeometry> classe é uma boa escolha para descrever adornos.  
  
 Para obter um exemplo, consulte [Instruções: criar uma forma usando uma StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Sintaxe de marcação do caminho  
 Os <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> e tipos [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suportam uma sintaxe de atributos usando uma série especial de comandos de movimento e desenho. Para obter mais informações, consulte [Sintaxe de marcação de caminho](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>Geometrias compostas  
 Objetos de geometria composta <xref:System.Windows.Media.GeometryGroup>podem <xref:System.Windows.Media.CombinedGeometry>ser criados <xref:System.Windows.Media.Geometry> usando <xref:System.Windows.Media.Geometry.Combine%2A>a , a, ou chamando o método estático .  
  
- O <xref:System.Windows.Media.CombinedGeometry> objeto <xref:System.Windows.Media.Geometry.Combine%2A> e o método realizam uma operação booleana para combinar a área definida por duas geometrias. <xref:System.Windows.Media.Geometry>objetos que não têm área são descartados. Apenas <xref:System.Windows.Media.Geometry> dois objetos podem ser combinados (embora essas duas geometrias também possam ser geometrias compostas).  
  
- A <xref:System.Windows.Media.GeometryGroup> classe cria uma amálgama dos <xref:System.Windows.Media.Geometry> objetos que contém sem combinar sua área. Qualquer número <xref:System.Windows.Media.Geometry> de objetos <xref:System.Windows.Media.GeometryGroup>pode ser adicionado a um . Para obter um exemplo, consulte [Instruções: criar uma forma composta](how-to-create-a-composite-shape.md).  
  
 Como eles não realizam uma <xref:System.Windows.Media.GeometryGroup> operação de combinação, <xref:System.Windows.Media.CombinedGeometry> o <xref:System.Windows.Media.Geometry.Combine%2A> uso de objetos proporciona benefícios de desempenho sobre o uso de objetos ou o método.  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>Geometrias combinadas  
 A seção <xref:System.Windows.Media.CombinedGeometry> anterior mencionou <xref:System.Windows.Media.Geometry.Combine%2A> o objeto e o método combinam a área definida pelas geometrias que contêm. A <xref:System.Windows.Media.GeometryCombineMode> enumeração especifica como as geometrias são combinadas. Os valores <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> possíveis para <xref:System.Windows.Media.GeometryCombineMode.Union> <xref:System.Windows.Media.GeometryCombineMode.Intersect>a <xref:System.Windows.Media.GeometryCombineMode.Exclude>propriedade <xref:System.Windows.Media.GeometryCombineMode.Xor>são: , , e .  
  
 No exemplo a <xref:System.Windows.Media.CombinedGeometry> seguir, a é definida com um modo de combinação de União.  Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> os são definidos como círculos do mesmo raio, mas com centros compensados por 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Resultados do modo de combinação Union](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 No exemplo a <xref:System.Windows.Media.CombinedGeometry> seguir, a é <xref:System.Windows.Media.GeometryCombineMode.Xor>definida com um modo de combinação de .  Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> os são definidos como círculos do mesmo raio, mas com centros compensados por 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Resultados do modo de combinação Xor](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Para obter exemplos adicionais, consulte [Instruções: criar uma forma composta](how-to-create-a-composite-shape.md) e [Instruções: criar uma geometria combinada](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Recursos congeláveis  
 Por herdar da <xref:System.Windows.Freezable> classe, <xref:System.Windows.Media.Geometry> a classe fornece <xref:System.Windows.Media.Geometry> várias características especiais: os objetos podem ser declarados como [Recursos XAML,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)compartilhados entre vários objetos, feitos somente de leitura para melhorar o desempenho, clonados e feitos como thread-safe. Para obter mais informações sobre <xref:System.Windows.Freezable> os diferentes recursos fornecidos pelos objetos, consulte a visão geral dos [objetos acongelamento](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>Outras funcionalidades da geometria  
 A <xref:System.Windows.Media.Geometry> classe também fornece métodos úteis de utilidade, como o seguinte:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- Fica com <xref:System.Windows.Media.Geometry>a área do.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- Determina se a Geometria contém outra <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- Determina se o <xref:System.Windows.Media.Geometry> traçado de um contém um ponto especificado.  
  
 Consulte <xref:System.Windows.Media.Geometry> a classe para obter uma lista completa de seus métodos.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Sintaxe de marcação de caminho](path-markup-syntax.md)
- [Tópicos de como fazer](geometries-how-to-topics.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral de formas e desenhos básicos no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
