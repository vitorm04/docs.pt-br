---
title: Como girar um objeto usando um caminho geométrico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186872"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="ce229-102">Como girar um objeto usando um caminho geométrico</span><span class="sxs-lookup"><span data-stu-id="ce229-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="ce229-103">Este exemplo mostra como girar (pivô) um objeto ao <xref:System.Windows.Media.PathGeometry> longo de um caminho geométrico que é definido por um objeto.</span><span class="sxs-lookup"><span data-stu-id="ce229-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce229-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce229-104">Example</span></span>  
 <span data-ttu-id="ce229-105">O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> seguir usa três objetos para mover um retângulo ao longo de um caminho geométrico.</span><span class="sxs-lookup"><span data-stu-id="ce229-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="ce229-106">O <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> primeiro anima <xref:System.Windows.Media.RotateTransform> um que é aplicado ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="ce229-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="ce229-107">A animação gera valores de ângulos.</span><span class="sxs-lookup"><span data-stu-id="ce229-107">The animation generates angle values.</span></span> <span data-ttu-id="ce229-108">Isso faz o retângulo girar ao longo dos contornos do caminho.</span><span class="sxs-lookup"><span data-stu-id="ce229-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="ce229-109">Os outros dois objetos <xref:System.Windows.Media.TranslateTransform.Y%2A> animam <xref:System.Windows.Media.TranslateTransform> os <xref:System.Windows.Media.TranslateTransform.X%2A> valores de um que é aplicado ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="ce229-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="ce229-110">Eles fazem o retângulo ser mover horizontal e verticalmente ao longo do caminho.</span><span class="sxs-lookup"><span data-stu-id="ce229-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="ce229-111">Outra maneira de girar um objeto usando um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> caminho geométrico é usar um objeto e definir sua <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="ce229-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="ce229-112">Para obter mais informações e um exemplo, consulte ["Gire um objeto usando um caminho geométrico" (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="ce229-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="ce229-113">Para obter a amostra completa, consulte [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="ce229-113">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce229-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce229-114">See also</span></span>

- [<span data-ttu-id="ce229-115">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="ce229-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ce229-116">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="ce229-116">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="ce229-117">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="ce229-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
