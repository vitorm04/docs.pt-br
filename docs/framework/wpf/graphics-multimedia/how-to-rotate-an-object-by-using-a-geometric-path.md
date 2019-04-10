---
title: 'Como: Girar um objeto usando um caminho geométrico'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 3e35169da7297ec62e0114ab21f4ba81c0a656ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229206"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="ebf0d-102">Como: Girar um objeto usando um caminho geométrico</span><span class="sxs-lookup"><span data-stu-id="ebf0d-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="ebf0d-103">Este exemplo mostra como girar um objeto ao longo de um caminho geométrico que é definido por um <xref:System.Windows.Media.PathGeometry> objeto.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebf0d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebf0d-104">Example</span></span>  
 <span data-ttu-id="ebf0d-105">O exemplo a seguir usa três <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="ebf0d-106">A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima um <xref:System.Windows.Media.RotateTransform> que é aplicado ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="ebf0d-107">A animação gera valores de ângulos.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-107">The animation generates angle values.</span></span> <span data-ttu-id="ebf0d-108">Isso faz o retângulo girar ao longo dos contornos do caminho.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="ebf0d-109">Os dois objetos animam os <xref:System.Windows.Media.TranslateTransform.X%2A> e <xref:System.Windows.Media.TranslateTransform.Y%2A> valores de um <xref:System.Windows.Media.TranslateTransform> que é aplicado ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="ebf0d-110">Eles fazem o retângulo ser mover horizontal e verticalmente ao longo do caminho.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="ebf0d-111">Outra maneira de girar um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do objeto e defina sua <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="ebf0d-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="ebf0d-112">Para obter mais informações e um exemplo, consulte [girar um objeto usando um caminho Geométrico (animação de matriz)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="ebf0d-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="ebf0d-113">Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="ebf0d-113">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf0d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebf0d-114">See also</span></span>

- [<span data-ttu-id="ebf0d-115">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="ebf0d-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ebf0d-116">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="ebf0d-116">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="ebf0d-117">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="ebf0d-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
