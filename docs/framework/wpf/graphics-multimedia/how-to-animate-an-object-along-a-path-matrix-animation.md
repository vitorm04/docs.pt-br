---
title: Como animar um objeto ao longo de um caminho (animação de matriz)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452903"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="bdb3b-102">Como animar um objeto ao longo de um caminho (animação de matriz)</span><span class="sxs-lookup"><span data-stu-id="bdb3b-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="bdb3b-103">Este exemplo mostra como usar a classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para animar um objeto ao longo de um caminho que é definido por um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdb3b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bdb3b-104">Example</span></span>  
 <span data-ttu-id="bdb3b-105">O exemplo a seguir anima um objeto ao longo de um caminho fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="bdb3b-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="bdb3b-106">Aplica um <xref:System.Windows.Media.MatrixTransform> ao objeto para movê-lo.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="bdb3b-107">Define o caminho usando um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="bdb3b-108">Cria um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e o usa para animar a propriedade <xref:System.Windows.Media.Matrix> da <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="bdb3b-109">O <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> usa o <xref:System.Windows.Media.PathGeometry> e o usa para gerar valores de <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="bdb3b-110">Para obter o exemplo completo, consulte [exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="bdb3b-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="bdb3b-111">Para obter mais informações sobre caminhos geométricos, consulte a [visão geral da geometria](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bdb3b-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb3b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="bdb3b-112">See also</span></span>

- [<span data-ttu-id="bdb3b-113">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="bdb3b-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="bdb3b-114">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="bdb3b-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="bdb3b-115">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="bdb3b-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
