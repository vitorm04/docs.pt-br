---
title: Como modificar o limite ao final de uma linha ou um segmento
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452773"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="c8b04-102">Como modificar o limite ao final de uma linha ou um segmento</span><span class="sxs-lookup"><span data-stu-id="c8b04-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="c8b04-103">Este exemplo mostra como modificar a forma no início ou no final de um elemento de <xref:System.Windows.Shapes.Shape> aberto.</span><span class="sxs-lookup"><span data-stu-id="c8b04-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="c8b04-104">Para alterar o limite no início de um <xref:System.Windows.Shapes.Shape>aberto, use sua propriedade <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8b04-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="c8b04-105">Para alterar o limite no final de um <xref:System.Windows.Shapes.Shape>aberto, use sua propriedade <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8b04-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="c8b04-106">Para exibir as limites de linha disponíveis, consulte a enumeração <xref:System.Windows.Media.PenLineCap>.</span><span class="sxs-lookup"><span data-stu-id="c8b04-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8b04-107">Essa propriedade afeta apenas uma forma aberta, como um <xref:System.Windows.Shapes.Line>, um <xref:System.Windows.Shapes.Polyline>ou um elemento <xref:System.Windows.Shapes.Path> aberto.</span><span class="sxs-lookup"><span data-stu-id="c8b04-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="c8b04-108">O exemplo a seguir desenha quatro elementos <xref:System.Windows.Shapes.Polyline> e usa um conjunto diferente de formas nas extremidades de cada um.</span><span class="sxs-lookup"><span data-stu-id="c8b04-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8b04-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8b04-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="c8b04-110">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="c8b04-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b04-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8b04-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
