---
title: Visão geral de formas e desenho básico no WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 47df352c3b001f088f34ea057b34698efc4f4b53
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47233272"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="02d2b-102">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="02d2b-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="02d2b-103">Este tópico fornece uma visão geral de como desenhar com <xref:System.Windows.Shapes.Shape> objetos.</span><span class="sxs-lookup"><span data-stu-id="02d2b-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="02d2b-104">Um <xref:System.Windows.Shapes.Shape> é um tipo de <xref:System.Windows.UIElement> que permite que você desenhe uma forma na tela.</span><span class="sxs-lookup"><span data-stu-id="02d2b-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="02d2b-105">Como eles são elementos de interface do usuário <xref:System.Windows.Shapes.Shape> objetos que podem ser usados dentro de <xref:System.Windows.Controls.Panel> elementos e a maioria dos controles.</span><span class="sxs-lookup"><span data-stu-id="02d2b-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="02d2b-106">oferece várias camadas de acesso aos elementos gráficos e serviços de renderização.</span><span class="sxs-lookup"><span data-stu-id="02d2b-106"> offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="02d2b-107">Na camada superior, <xref:System.Windows.Shapes.Shape> objetos são fáceis de usar e fornecem muitos recursos úteis, como layout e participação no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistema de eventos.</span><span class="sxs-lookup"><span data-stu-id="02d2b-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="02d2b-108">Objetos de forma</span><span class="sxs-lookup"><span data-stu-id="02d2b-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="02d2b-109">Fornece uma série de prontos para uso <xref:System.Windows.Shapes.Shape> objetos.</span><span class="sxs-lookup"><span data-stu-id="02d2b-109"> provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="02d2b-110">Todos os objetos de forma herdam a <xref:System.Windows.Shapes.Shape> classe.</span><span class="sxs-lookup"><span data-stu-id="02d2b-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="02d2b-111">Objetos de forma disponíveis incluem <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, e <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="02d2b-112"><xref:System.Windows.Shapes.Shape> objetos compartilham as propriedades comuns a seguir.</span><span class="sxs-lookup"><span data-stu-id="02d2b-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="02d2b-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Descreve como o contorno da forma é pintado.</span><span class="sxs-lookup"><span data-stu-id="02d2b-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="02d2b-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Descreve a espessura do contorno da forma.</span><span class="sxs-lookup"><span data-stu-id="02d2b-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="02d2b-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Descreve como o interior da forma é pintado.</span><span class="sxs-lookup"><span data-stu-id="02d2b-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="02d2b-116">Propriedades de dados para especificar as coordenadas e vértices, medido em pixels independentes de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="02d2b-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="02d2b-117">Porque eles derivam de <xref:System.Windows.UIElement>, objetos de forma podem ser usados dentro de painéis e a maioria dos controles.</span><span class="sxs-lookup"><span data-stu-id="02d2b-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="02d2b-118">O <xref:System.Windows.Controls.Canvas> painel é uma opção particularmente boa para criar desenhos complexos porque ele dá suporte ao posicionamento absoluto de seus objetos filho.</span><span class="sxs-lookup"><span data-stu-id="02d2b-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="02d2b-119">O <xref:System.Windows.Shapes.Line> classe permite que você desenhe uma linha entre dois pontos.</span><span class="sxs-lookup"><span data-stu-id="02d2b-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="02d2b-120">O exemplo a seguir mostra várias maneiras para especificar as coordenadas de linha e propriedades de traço.</span><span class="sxs-lookup"><span data-stu-id="02d2b-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="02d2b-121">A imagem a seguir mostra o renderizado <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="02d2b-122">![Ilustração de linha](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="02d2b-122">![Line illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="02d2b-123">Embora o <xref:System.Windows.Shapes.Line> classe forneça um <xref:System.Windows.Shapes.Shape.Fill%2A> configuração da propriedade, ele não tem nenhum efeito porque um <xref:System.Windows.Shapes.Line> não tem nenhuma área.</span><span class="sxs-lookup"><span data-stu-id="02d2b-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="02d2b-124">Outra forma comum é o <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="02d2b-125">Criar uma <xref:System.Windows.Shapes.Ellipse> definindo a forma <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="02d2b-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="02d2b-126">Para desenhar um círculo, especifique um <xref:System.Windows.Shapes.Ellipse> cujos <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> valores são iguais.</span><span class="sxs-lookup"><span data-stu-id="02d2b-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="02d2b-127">A imagem a seguir mostra um exemplo de um renderizado <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="02d2b-128">![Ilustração de elipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="02d2b-128">![Ellipse illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="02d2b-129">Usando caminhos e geometrias</span><span class="sxs-lookup"><span data-stu-id="02d2b-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="02d2b-130">O <xref:System.Windows.Shapes.Path> classe permite que você desenhe curvas e formas complexas.</span><span class="sxs-lookup"><span data-stu-id="02d2b-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="02d2b-131">Esses curvas e formas são descritas usando <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="02d2b-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="02d2b-132">Para usar um <xref:System.Windows.Shapes.Path>, você cria um <xref:System.Windows.Media.Geometry> e usá-lo para definir o <xref:System.Windows.Shapes.Path> do objeto <xref:System.Windows.Shapes.Path.Data%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="02d2b-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="02d2b-133">Há uma variedade de <xref:System.Windows.Media.Geometry> objetos à sua escolha.</span><span class="sxs-lookup"><span data-stu-id="02d2b-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="02d2b-134">O <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, e <xref:System.Windows.Media.EllipseGeometry> classes descrevem formas relativamente simples.</span><span class="sxs-lookup"><span data-stu-id="02d2b-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="02d2b-135">Para criar formas mais complexas ou criar curvas, use um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="02d2b-136">PathGeometry e PathSegments</span><span class="sxs-lookup"><span data-stu-id="02d2b-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="02d2b-137"><xref:System.Windows.Media.PathGeometry> objetos são compostos de um ou mais <xref:System.Windows.Media.PathFigure> objetos; cada <xref:System.Windows.Media.PathFigure> representa uma forma ou "Figura" diferente.</span><span class="sxs-lookup"><span data-stu-id="02d2b-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="02d2b-138">Cada <xref:System.Windows.Media.PathFigure> é composto de um ou mais <xref:System.Windows.Media.PathSegment> objetos, cada um representando uma parte conectada da figura ou forma.</span><span class="sxs-lookup"><span data-stu-id="02d2b-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="02d2b-139">Tipos de segmento incluem o seguinte: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, e <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="02d2b-140">No exemplo a seguir, um <xref:System.Windows.Shapes.Path> é usado para desenhar uma curva de Bezier quadrática.</span><span class="sxs-lookup"><span data-stu-id="02d2b-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="02d2b-141">A imagem a seguir mostra a forma renderizada.</span><span class="sxs-lookup"><span data-stu-id="02d2b-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="02d2b-142">![Ilustração de caminho](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="02d2b-142">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="02d2b-143">Para obter mais informações sobre <xref:System.Windows.Media.PathGeometry> e o outro <xref:System.Windows.Media.Geometry> classes, consulte o [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="02d2b-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="02d2b-144">Sintaxe XAML abreviada</span><span class="sxs-lookup"><span data-stu-id="02d2b-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="02d2b-145">Na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você também pode usar uma sintaxe abreviada especial para descrever um <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="02d2b-146">No exemplo a seguir, a sintaxe abreviada é usada para desenhar uma forma complexa.</span><span class="sxs-lookup"><span data-stu-id="02d2b-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="02d2b-147">A imagem a seguir mostra um renderizado <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="02d2b-148">![Ilustração de caminho](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="02d2b-148">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="02d2b-149">O <xref:System.Windows.Shapes.Path.Data%2A> cadeia de caracteres do atributo começa com o comando "moveto", indicado por M, que estabelece um ponto inicial para o caminho no sistema de coordenadas do <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="02d2b-150"><xref:System.Windows.Shapes.Path> parâmetros de dados diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="02d2b-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="02d2b-151">O M maiusculo indica um local absoluto para o novo ponto atual.</span><span class="sxs-lookup"><span data-stu-id="02d2b-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="02d2b-152">Um m minúsculo indicaria coordenadas relativas.</span><span class="sxs-lookup"><span data-stu-id="02d2b-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="02d2b-153">O primeiro segmento é um início de curva de Bézier cúbico no (100,200) e terminando em (400,175), desenhado usando os dois controle pontos (100,25) e (400,350).</span><span class="sxs-lookup"><span data-stu-id="02d2b-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="02d2b-154">Este segmento é indicado pelo comando C no <xref:System.Windows.Shapes.Path.Data%2A> cadeia de caracteres de atributo.</span><span class="sxs-lookup"><span data-stu-id="02d2b-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="02d2b-155">Novamente, o C maiúsculo indica um caminho absoluto; o c minúsculo indicaria um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="02d2b-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="02d2b-156">O segundo segmento começa com um comando absoluto horizontal "lineto" H, que especifica uma linha desenhada do ponto de extremidade do subcaminho anterior (400,175) para um novo ponto de extremidade (280,175).</span><span class="sxs-lookup"><span data-stu-id="02d2b-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="02d2b-157">Como é um comando horizontal "lineto", o valor especificado é um *x*-coordenada.</span><span class="sxs-lookup"><span data-stu-id="02d2b-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="02d2b-158">Para obter a sintaxe de caminho completo, consulte o <xref:System.Windows.Shapes.Path.Data%2A> referência e [criar uma forma usando um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="02d2b-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="02d2b-159">Pintando formas</span><span class="sxs-lookup"><span data-stu-id="02d2b-159">Painting Shapes</span></span>  
 <span data-ttu-id="02d2b-160"><xref:System.Windows.Media.Brush> objetos são usados para desenhar uma forma <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="02d2b-161">No exemplo a seguir, o traço e preenchimento de um <xref:System.Windows.Shapes.Ellipse> são especificados.</span><span class="sxs-lookup"><span data-stu-id="02d2b-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="02d2b-162">Observe que a entrada válida para propriedades de pincel pode ser uma palavra-chave ou o valor hexadecimal da cor.</span><span class="sxs-lookup"><span data-stu-id="02d2b-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="02d2b-163">Para obter mais informações sobre palavras-chave de cores disponíveis, consulte Propriedades do <xref:System.Windows.Media.Colors> classe o <xref:System.Windows.Media> namespace.</span><span class="sxs-lookup"><span data-stu-id="02d2b-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
```xaml
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 <span data-ttu-id="02d2b-164">A imagem a seguir mostra o renderizado <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="02d2b-165">![Uma elipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="02d2b-165">![An ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="02d2b-166">Como alternativa, você pode usar a sintaxe de elemento de propriedade para criar explicitamente uma <xref:System.Windows.Media.SolidColorBrush> objeto para pintar a forma com uma cor sólida.</span><span class="sxs-lookup"><span data-stu-id="02d2b-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 <span data-ttu-id="02d2b-167">A ilustração a seguir mostra a forma renderizada.</span><span class="sxs-lookup"><span data-stu-id="02d2b-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="02d2b-168">![Ilustração de SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="02d2b-168">![SolidColorBrush illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="02d2b-169">Você também pode pintar um traço ou preenchimento da forma com gradientes, imagens, padrões e muito mais.</span><span class="sxs-lookup"><span data-stu-id="02d2b-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="02d2b-170">Para obter mais informações, consulte o [pintura com cores sólidas e gradientes Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="02d2b-170">For more information, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="02d2b-171">Formas alongáveis</span><span class="sxs-lookup"><span data-stu-id="02d2b-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="02d2b-172">O <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, e <xref:System.Windows.Shapes.Rectangle> classes todas têm um <xref:System.Windows.Shapes.Shape.Stretch%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="02d2b-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="02d2b-173">Essa propriedade determina como um <xref:System.Windows.Shapes.Shape> conteúdo do objeto (de forma a ser desenhada) é alongado para preencher o <xref:System.Windows.Shapes.Shape> espaço de layout do objeto.</span><span class="sxs-lookup"><span data-stu-id="02d2b-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="02d2b-174">Um <xref:System.Windows.Shapes.Shape> espaço de layout do objeto é a quantidade de espaço a <xref:System.Windows.Shapes.Shape> é alocado pelo sistema de layout, devido a uma explícita <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> configuração ou por causa da sua <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="02d2b-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="02d2b-175">Para obter informações adicionais sobre layout no Windows Presentation Foundation, consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md) visão geral.</span><span class="sxs-lookup"><span data-stu-id="02d2b-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../../../../docs/framework/wpf/advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="02d2b-176">A propriedade Stretch usa um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="02d2b-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="02d2b-177"><xref:System.Windows.Media.Stretch.None>: O <xref:System.Windows.Shapes.Shape> conteúdo do objeto não é alongado.</span><span class="sxs-lookup"><span data-stu-id="02d2b-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="02d2b-178"><xref:System.Windows.Media.Stretch.Fill>: O <xref:System.Windows.Shapes.Shape> conteúdo do objeto é alongado para preencher o espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="02d2b-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="02d2b-179">A taxa de proporção não é preservada.</span><span class="sxs-lookup"><span data-stu-id="02d2b-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="02d2b-180"><xref:System.Windows.Media.Stretch.Uniform>: O <xref:System.Windows.Shapes.Shape> conteúdo do objeto é alongado tanto quanto possível para preencher o espaço de layout enquanto preserva sua taxa de proporção original.</span><span class="sxs-lookup"><span data-stu-id="02d2b-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="02d2b-181"><xref:System.Windows.Media.Stretch.UniformToFill>: O <xref:System.Windows.Shapes.Shape> conteúdo do objeto é alongado para preencher completamente o espaço de layout enquanto preserva sua taxa de proporção original.</span><span class="sxs-lookup"><span data-stu-id="02d2b-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="02d2b-182">Observe que, quando um <xref:System.Windows.Shapes.Shape> conteúdo do objeto é alongado, o <xref:System.Windows.Shapes.Shape> contorno do objeto é pintado após o alongamento.</span><span class="sxs-lookup"><span data-stu-id="02d2b-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="02d2b-183">No exemplo a seguir, um <xref:System.Windows.Shapes.Polygon> é usado para desenhar um triângulo muito pequeno de (0,0) a (0,1) a (1,1).</span><span class="sxs-lookup"><span data-stu-id="02d2b-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="02d2b-184">O <xref:System.Windows.Shapes.Polygon> do objeto <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> são definidos como 100, e sua propriedade de alongamento é definida como Fill.</span><span class="sxs-lookup"><span data-stu-id="02d2b-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="02d2b-185">Como resultado, o <xref:System.Windows.Shapes.Polygon> conteúdo do objeto (o triângulo) é alongado para preencher o espaço maior.</span><span class="sxs-lookup"><span data-stu-id="02d2b-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a><span data-ttu-id="02d2b-186">transformando as formas</span><span class="sxs-lookup"><span data-stu-id="02d2b-186">Transforming Shapes</span></span>  
 <span data-ttu-id="02d2b-187">O <xref:System.Windows.Media.Transform> classe fornece os meios para transformar formas em um plano bidimensional.</span><span class="sxs-lookup"><span data-stu-id="02d2b-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="02d2b-188">Os diferentes tipos de transformação incluem rotação (<xref:System.Windows.Media.RotateTransform>), escala (<xref:System.Windows.Media.ScaleTransform>), distorção (<xref:System.Windows.Media.SkewTransform>) e translação (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="02d2b-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="02d2b-189">Uma transformação comum a ser aplicada a uma forma é uma rotação.</span><span class="sxs-lookup"><span data-stu-id="02d2b-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="02d2b-190">Para girar uma forma, criar uma <xref:System.Windows.Media.RotateTransform> e especifique seu <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="02d2b-191">Um <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 gira o elemento 45 graus no sentido horário; um ângulo de 90 gira o elemento 90 graus no sentido horário; e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="02d2b-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="02d2b-192">Defina as <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades para controlar o ponto de rotação do elemento.</span><span class="sxs-lookup"><span data-stu-id="02d2b-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="02d2b-193">Esses valores de propriedade são expressos no espaço de coordenadas do elemento que está sendo transformado.</span><span class="sxs-lookup"><span data-stu-id="02d2b-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="02d2b-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> têm valores padrão de zero.</span><span class="sxs-lookup"><span data-stu-id="02d2b-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="02d2b-195">Por fim, aplique o <xref:System.Windows.Media.RotateTransform> ao elemento.</span><span class="sxs-lookup"><span data-stu-id="02d2b-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="02d2b-196">Se você não deseja que a transformação afete o layout, defina a forma <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="02d2b-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="02d2b-197">No exemplo a seguir, um <xref:System.Windows.Media.RotateTransform> é usado para girar uma forma 45 graus sobre o canto esquerdo superior (0,0) da forma.</span><span class="sxs-lookup"><span data-stu-id="02d2b-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="02d2b-198">No próximo exemplo, outra forma é girada 45 graus, mas dessa vez é girada em torno do ponto (25,50).</span><span class="sxs-lookup"><span data-stu-id="02d2b-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="02d2b-199">A ilustração a seguir mostra os resultados da aplicação das duas transformações.</span><span class="sxs-lookup"><span data-stu-id="02d2b-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="02d2b-200">![rotações de 45 graus com diferentes pontos centrais](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="02d2b-200">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="02d2b-201">Nos exemplos anteriores, um única transformação foi aplicada a cada objeto de forma.</span><span class="sxs-lookup"><span data-stu-id="02d2b-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="02d2b-202">Para aplicar várias transformações a uma forma (ou qualquer outro elemento de interface do usuário), use um <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="02d2b-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d2b-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02d2b-203">See Also</span></span>  
 [<span data-ttu-id="02d2b-204">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="02d2b-204">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="02d2b-205">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="02d2b-205">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="02d2b-206">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="02d2b-206">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="02d2b-207">Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF</span><span class="sxs-lookup"><span data-stu-id="02d2b-207">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [<span data-ttu-id="02d2b-208">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="02d2b-208">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
