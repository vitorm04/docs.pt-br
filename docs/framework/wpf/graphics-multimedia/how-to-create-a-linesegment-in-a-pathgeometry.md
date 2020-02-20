---
title: Como criar um LineSegment em um PathGeometry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: fc7fbad1e534988a36d85c55c1b6a8249692ad67
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452078"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="c2901-102">Como criar um LineSegment em um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="c2901-102">How to: Create a LineSegment in a PathGeometry</span></span>

<span data-ttu-id="c2901-103">Este exemplo mostra como criar um segmento de linha.</span><span class="sxs-lookup"><span data-stu-id="c2901-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="c2901-104">Para criar um segmento de linha, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.LineSegment>.</span><span class="sxs-lookup"><span data-stu-id="c2901-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>

## <a name="example"></a><span data-ttu-id="c2901-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2901-105">Example</span></span>

<span data-ttu-id="c2901-106">Os exemplos a seguir desenham um <xref:System.Windows.Media.LineSegment> de (10, 50) a (200, 70).</span><span class="sxs-lookup"><span data-stu-id="c2901-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="c2901-107">A ilustração a seguir mostra o <xref:System.Windows.Media.LineSegment>resultante; foi adicionado um plano de fundo de grade para mostrar o sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="c2901-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>

<span data-ttu-id="c2901-108">![Um LineSegment em um PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") Um LineSegment desenhado de (10, 50) a (200, 70)</span><span class="sxs-lookup"><span data-stu-id="c2901-108">![A LineSegment in a PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") A LineSegment drawn from (10,50) to (200,70)</span></span>

<span data-ttu-id="c2901-109">XAML</span><span class="sxs-lookup"><span data-stu-id="c2901-109">[xaml]</span></span>

<span data-ttu-id="c2901-110">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de atributo para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="c2901-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

<span data-ttu-id="c2901-111">XAML</span><span class="sxs-lookup"><span data-stu-id="c2901-111">[xaml]</span></span>

<span data-ttu-id="c2901-112">(Observe que essa sintaxe de atributo, na verdade, cria uma <xref:System.Windows.Media.StreamGeometry>, uma versão de peso mais leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="c2901-112">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="c2901-113">Para obter mais informações, consulte a página [sintaxe de marcação de caminho](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="c2901-113">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>

<span data-ttu-id="c2901-114">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar um segmento de linha usando a sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="c2901-114">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="c2901-115">O seguinte é equivalente ao exemplo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.</span><span class="sxs-lookup"><span data-stu-id="c2901-115">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1">
  <Path.Data>
    <PathGeometry>
      <PathFigure StartPoint="10,50">
        <LineSegment Point="200,70" />
      </PathFigure>
    </PathGeometry>
  </Path.Data>
</Path>
```

```csharp
PathFigure myPathFigure = new PathFigure();
myPathFigure.StartPoint = new Point(10, 50);

LineSegment myLineSegment = new LineSegment();
myLineSegment.Point = new Point(200, 70);

PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();
myPathSegmentCollection.Add(myLineSegment);

myPathFigure.Segments = myPathSegmentCollection;

PathFigureCollection myPathFigureCollection = new PathFigureCollection();
myPathFigureCollection.Add(myPathFigure);

PathGeometry myPathGeometry = new PathGeometry();
myPathGeometry.Figures = myPathFigureCollection;

Path myPath = new Path();
myPath.Stroke = Brushes.Black;
myPath.StrokeThickness = 1;
myPath.Data = myPathGeometry;
```

```vb
Dim myPathFigure As New PathFigure()
myPathFigure.StartPoint = New Point(10, 50)

Dim myLineSegment As New LineSegment()
myLineSegment.Point = New Point(200, 70)

Dim myPathSegmentCollection As New PathSegmentCollection()
myPathSegmentCollection.Add(myLineSegment)

myPathFigure.Segments = myPathSegmentCollection

Dim myPathFigureCollection As New PathFigureCollection()
myPathFigureCollection.Add(myPathFigure)

Dim myPathGeometry As New PathGeometry()
myPathGeometry.Figures = myPathFigureCollection

Dim myPath As New Path()
myPath.Stroke = Brushes.Black
myPath.StrokeThickness = 1
myPath.Data = myPathGeometry
```

<span data-ttu-id="c2901-116">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="c2901-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2901-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2901-117">See also</span></span>

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="c2901-118">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="c2901-118">Geometry Overview</span></span>](geometry-overview.md)
