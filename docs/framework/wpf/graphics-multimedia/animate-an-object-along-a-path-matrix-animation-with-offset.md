---
title: Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453098"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="37aa3-102">Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)</span><span class="sxs-lookup"><span data-stu-id="37aa3-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="37aa3-103">Este exemplo mostra como usar a classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para animar um objeto ao longo de um caminho e fazer com que essa animação acumule seus valores de deslocamento à medida que ele se repetir.</span><span class="sxs-lookup"><span data-stu-id="37aa3-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37aa3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37aa3-104">Example</span></span>  
 <span data-ttu-id="37aa3-105">O exemplo a seguir usa o objeto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para animar a propriedade <xref:System.Windows.Media.MatrixTransform.Matrix%2A> de um <xref:System.Windows.Media.MatrixTransform> aplicado a um botão.</span><span class="sxs-lookup"><span data-stu-id="37aa3-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="37aa3-106">Como resultado, um botão se move ao longo de um caminho curvo.</span><span class="sxs-lookup"><span data-stu-id="37aa3-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="37aa3-107">Além disso, o exemplo define a propriedade <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> como `true`, o que faz com que o deslocamento da matriz animada seja acumulado à medida que a animação se repete.</span><span class="sxs-lookup"><span data-stu-id="37aa3-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="37aa3-108">Como o deslocamento é acumulado, o botão se move para mais longe na tela quando a animação se repete, em vez de recomeçar da posição inicial.</span><span class="sxs-lookup"><span data-stu-id="37aa3-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="37aa3-109">Observe que, embora a propriedade <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> faça com que os valores de deslocamento sejam acumulados em repetições, isso não faz com que os valores de rotação sejam acumulados.</span><span class="sxs-lookup"><span data-stu-id="37aa3-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="37aa3-110">Para tornar os valores de rotação acumulados, defina as propriedades <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> da animação e <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="37aa3-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="37aa3-111">Para obter o exemplo completo, consulte [exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="37aa3-111">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="37aa3-112">Para obter um exemplo que mostra como animar um valor de <xref:System.Windows.Media.Matrix> ao longo de um caminho sem acumulação de deslocamento, consulte [animar um objeto ao longo de um caminho (animação de matriz)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="37aa3-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37aa3-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="37aa3-113">See also</span></span>

- [<span data-ttu-id="37aa3-114">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="37aa3-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="37aa3-115">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="37aa3-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
