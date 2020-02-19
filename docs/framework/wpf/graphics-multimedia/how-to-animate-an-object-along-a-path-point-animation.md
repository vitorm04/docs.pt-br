---
title: Como animar um objeto ao longo de um caminho (animação de ponto)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452890"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="3e388-102">Como animar um objeto ao longo de um caminho (animação de ponto)</span><span class="sxs-lookup"><span data-stu-id="3e388-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="3e388-103">Este exemplo mostra como usar um objeto <xref:System.Windows.Media.Animation.PointAnimationUsingPath> para animar uma <xref:System.Windows.Point> ao longo de um caminho curvo.</span><span class="sxs-lookup"><span data-stu-id="3e388-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e388-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e388-104">Example</span></span>  
 <span data-ttu-id="3e388-105">O exemplo a seguir move um <xref:System.Windows.Media.EllipseGeometry> ao longo de um caminho definido por um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="3e388-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="3e388-106">A propriedade <xref:System.Windows.Media.EllipseGeometry.Center%2A> da geometria de elipse, que usa um valor de <xref:System.Windows.Point>, especifica sua posição; para mover a geometria da elipse, você anima sua propriedade <xref:System.Windows.Media.EllipseGeometry.Center%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e388-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="3e388-107">O exemplo usa um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> para animar a propriedade <xref:System.Windows.Media.EllipseGeometry.Center%2A> do objeto <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="3e388-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="3e388-108">Para obter o exemplo completo, consulte [exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="3e388-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="3e388-109">A versão de código do exemplo anterior usou um <xref:System.Windows.Media.Animation.Storyboard> para animar o <xref:System.Windows.Media.EllipseGeometry>, embora apenas uma animação tenha sido aplicada.</span><span class="sxs-lookup"><span data-stu-id="3e388-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="3e388-110">Uma <xref:System.Windows.Media.Animation.Storyboard> geralmente é a maneira mais fácil de aplicar várias animações, pois essas animações podem ser controladas pela mesma <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="3e388-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="3e388-111">No entanto, uma maneira mais fácil de aplicar uma única animação a uma propriedade ao usar o código é usar o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e388-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="3e388-112">Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="3e388-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e388-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="3e388-113">See also</span></span>

- [<span data-ttu-id="3e388-114">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="3e388-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="3e388-115">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="3e388-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="3e388-116">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="3e388-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
