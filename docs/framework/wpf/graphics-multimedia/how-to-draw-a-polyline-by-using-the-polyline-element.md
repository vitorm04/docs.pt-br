---
title: 'Como: Desenhar uma polilinha usando o elemento Polyline'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934955"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="56988-102">Como: Desenhar uma polilinha usando o elemento Polyline</span><span class="sxs-lookup"><span data-stu-id="56988-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="56988-103">Este exemplo mostra como desenhar uma polilinha, que é uma série de linhas conectadas, usando o <xref:System.Windows.Shapes.Polyline> elemento.</span><span class="sxs-lookup"><span data-stu-id="56988-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="56988-104">Para desenhar uma polilinha, crie um <xref:System.Windows.Shapes.Polyline> elemento e use sua <xref:System.Windows.Shapes.Polyline.Points%2A> propriedade para especificar os vértices de forma.</span><span class="sxs-lookup"><span data-stu-id="56988-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="56988-105">Por fim, use <xref:System.Windows.Shapes.Shape.Stroke%2A> as <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Propriedades e para descrever o contorno de polilinha porque uma linha sem um traço é invisível.</span><span class="sxs-lookup"><span data-stu-id="56988-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56988-106">Como o <xref:System.Windows.Shapes.Polyline> elemento não é uma forma fechada, a <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade não tem efeito, mesmo que você feche deliberadamente o contorno da forma.</span><span class="sxs-lookup"><span data-stu-id="56988-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="56988-107">Para criar uma forma fechada com um <xref:System.Windows.Shapes.Shape.Fill%2A>, use um <xref:System.Windows.Shapes.Polygon> elemento.</span><span class="sxs-lookup"><span data-stu-id="56988-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="56988-108">O exemplo a seguir desenha <xref:System.Windows.Shapes.Polyline> dois elementos dentro <xref:System.Windows.Controls.Canvas>de um.</span><span class="sxs-lookup"><span data-stu-id="56988-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56988-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56988-109">Example</span></span>  
 <span data-ttu-id="56988-110">Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="56988-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="56988-111">Embora este exemplo use um <xref:System.Windows.Controls.Canvas> para conter as polilinhas, você pode usar elementos Polyline (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> um <xref:System.Windows.Controls.Control> ou que ofereça suporte a conteúdo que não seja de texto.</span><span class="sxs-lookup"><span data-stu-id="56988-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="56988-112">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="56988-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56988-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56988-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="56988-114">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="56988-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="56988-115">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="56988-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
