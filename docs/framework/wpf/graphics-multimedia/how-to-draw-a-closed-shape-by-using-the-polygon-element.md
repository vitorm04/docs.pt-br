---
title: Como desenhar uma forma fechada usando o elemento Polygon
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 89c78877e196e803f6b4139ffcfa2b4def1a07d7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468086"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="cd77f-102">Como desenhar uma forma fechada usando o elemento Polygon</span><span class="sxs-lookup"><span data-stu-id="cd77f-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="cd77f-103">Este exemplo mostra como desenhar uma forma fechada usando o <xref:System.Windows.Shapes.Polygon> elemento.</span><span class="sxs-lookup"><span data-stu-id="cd77f-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="cd77f-104">Para desenhar uma forma fechada, crie uma <xref:System.Windows.Shapes.Polygon> elemento e use seu <xref:System.Windows.Shapes.Polygon.Points%2A> propriedade para especificar os vértices de uma forma.</span><span class="sxs-lookup"><span data-stu-id="cd77f-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="cd77f-105">Uma linha é desenhada automaticamente que conecta o primeiro e último pontos.</span><span class="sxs-lookup"><span data-stu-id="cd77f-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="cd77f-106">Por fim, especifique um <xref:System.Windows.Shapes.Shape.Fill%2A>, um <xref:System.Windows.Shapes.Shape.Stroke%2A>, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="cd77f-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd77f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd77f-107">Example</span></span>  
 <span data-ttu-id="cd77f-108">Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="cd77f-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="cd77f-109">Embora o exemplo usa uma <xref:System.Windows.Controls.Canvas> para conter os polígonos, você pode usar elementos de polígono (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não textual.</span><span class="sxs-lookup"><span data-stu-id="cd77f-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="cd77f-110">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="cd77f-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>
