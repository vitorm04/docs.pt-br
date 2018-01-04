---
title: "Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5259e930060a8ac6118d232f08d02193a6a1b300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="b82b9-102">Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)</span><span class="sxs-lookup"><span data-stu-id="b82b9-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="b82b9-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> valores de classe para animar um objeto ao longo de um caminho e fazer com que essa animação acumule seu deslocamento enquanto ela se repete.</span><span class="sxs-lookup"><span data-stu-id="b82b9-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b82b9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b82b9-104">Example</span></span>  
 <span data-ttu-id="b82b9-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform> aplicado a um botão.</span><span class="sxs-lookup"><span data-stu-id="b82b9-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="b82b9-106">Como resultado, um botão se move ao longo de um caminho curvo.</span><span class="sxs-lookup"><span data-stu-id="b82b9-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="b82b9-107">Além disso, o exemplo define o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriedade `true`, que faz com que o deslocamento da matriz animada se acumule a medida que a animação se repete.</span><span class="sxs-lookup"><span data-stu-id="b82b9-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="b82b9-108">Como o deslocamento é acumulado, o botão se move para mais longe na tela quando a animação se repete, em vez de recomeçar da posição inicial.</span><span class="sxs-lookup"><span data-stu-id="b82b9-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="b82b9-109">Observe que, embora o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriedade faz com que os valores de deslocamento se acumulem entre repetições, ele não os valores de rotação acumular.</span><span class="sxs-lookup"><span data-stu-id="b82b9-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="b82b9-110">Para fazer com que os valores de rotação acumular, defina a animação <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> e <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> propriedades `true`.</span><span class="sxs-lookup"><span data-stu-id="b82b9-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="b82b9-111">Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="b82b9-111">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="b82b9-112">Para obter um exemplo mostrando como animar uma <xref:System.Windows.Media.Matrix> ao longo de um caminho sem acúmulo de deslocamento, consulte [animar um objeto ao longo de um caminho (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="b82b9-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82b9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b82b9-113">See Also</span></span>  
 [<span data-ttu-id="b82b9-114">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="b82b9-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b82b9-115">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="b82b9-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
