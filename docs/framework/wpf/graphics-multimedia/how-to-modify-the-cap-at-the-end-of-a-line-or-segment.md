---
title: 'Como: Modificar o limite ao final de uma linha ou um segmento'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 9476fad503cf761672ae8460fcffb860ff683310
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645009"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="ec5aa-102">Como: Modificar o limite ao final de uma linha ou um segmento</span><span class="sxs-lookup"><span data-stu-id="ec5aa-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="ec5aa-103">Este exemplo mostra como modificar a forma no início ou final de uma abertura <xref:System.Windows.Shapes.Shape> elemento.</span><span class="sxs-lookup"><span data-stu-id="ec5aa-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="ec5aa-104">Para alterar o limite no início de uma abertura <xref:System.Windows.Shapes.Shape>, use seu <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ec5aa-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="ec5aa-105">Para alterar o limite ao final de uma abertura <xref:System.Windows.Shapes.Shape>, use seu <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ec5aa-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="ec5aa-106">Para exibir as terminações de linha disponíveis, consulte o <xref:System.Windows.Media.PenLineCap> enumeração.</span><span class="sxs-lookup"><span data-stu-id="ec5aa-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec5aa-107">Essa propriedade afeta apenas uma forma aberta, como um <xref:System.Windows.Shapes.Line>, um <xref:System.Windows.Shapes.Polyline>, ou um aberto <xref:System.Windows.Shapes.Path> elemento.</span><span class="sxs-lookup"><span data-stu-id="ec5aa-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="ec5aa-108">O exemplo a seguir desenha quatro <xref:System.Windows.Shapes.Polyline> elementos e usa um conjunto de formas diferentes nas extremidades de cada um.</span><span class="sxs-lookup"><span data-stu-id="ec5aa-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec5aa-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec5aa-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="ec5aa-110">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="ec5aa-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5aa-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec5aa-111">See also</span></span>
- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
