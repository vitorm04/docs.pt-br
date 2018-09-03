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
ms.openlocfilehash: f88133a5e927a1a1f59b1aa02826d140c107d002
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469980"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="54a50-102">Como animar um objeto ao longo de um caminho (animação de matriz)</span><span class="sxs-lookup"><span data-stu-id="54a50-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="54a50-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> classe para animar um objeto ao longo de um caminho que é definido por um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="54a50-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54a50-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54a50-104">Example</span></span>  
 <span data-ttu-id="54a50-105">O exemplo a seguir anima um objeto ao longo de um caminho, fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="54a50-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="54a50-106">Aplica-se um <xref:System.Windows.Media.MatrixTransform> ao objeto para movê-lo.</span><span class="sxs-lookup"><span data-stu-id="54a50-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="54a50-107">Define o caminho usando um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="54a50-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="54a50-108">Cria uma <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e o utiliza para animar a <xref:System.Windows.Media.Matrix> propriedade do <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="54a50-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="54a50-109">O <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> leva a <xref:System.Windows.Media.PathGeometry> e o utiliza para gerar <xref:System.Windows.Media.Matrix> valores.</span><span class="sxs-lookup"><span data-stu-id="54a50-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="54a50-110">Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="54a50-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="54a50-111">Para obter mais informações sobre caminhos geométricos, consulte a [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="54a50-111">For more information about geometric paths, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a50-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54a50-112">See Also</span></span>  
 [<span data-ttu-id="54a50-113">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="54a50-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="54a50-114">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="54a50-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="54a50-115">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="54a50-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
