---
title: "Como girar um objeto usando um caminho geométrico"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="dc55a-102">Como girar um objeto usando um caminho geométrico</span><span class="sxs-lookup"><span data-stu-id="dc55a-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="dc55a-103">Este exemplo mostra como girar um objeto ao longo de um caminho geométrico que é definido por um <xref:System.Windows.Media.PathGeometry> objeto.</span><span class="sxs-lookup"><span data-stu-id="dc55a-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc55a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc55a-104">Example</span></span>  
 <span data-ttu-id="dc55a-105">O exemplo a seguir usa três <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico.</span><span class="sxs-lookup"><span data-stu-id="dc55a-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="dc55a-106">A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima um <xref:System.Windows.Media.RotateTransform> que é aplicada ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="dc55a-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="dc55a-107">A animação gera valores de ângulos.</span><span class="sxs-lookup"><span data-stu-id="dc55a-107">The animation generates angle values.</span></span> <span data-ttu-id="dc55a-108">Isso faz o retângulo girar ao longo dos contornos do caminho.</span><span class="sxs-lookup"><span data-stu-id="dc55a-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="dc55a-109">Os dois objetos animam a <xref:System.Windows.Media.TranslateTransform.X%2A> e <xref:System.Windows.Media.TranslateTransform.Y%2A> valores de um <xref:System.Windows.Media.TranslateTransform> que é aplicada ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="dc55a-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="dc55a-110">Eles fazem o retângulo ser mover horizontal e verticalmente ao longo do caminho.</span><span class="sxs-lookup"><span data-stu-id="dc55a-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="dc55a-111">Outra maneira de girar um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do objeto e defina seu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="dc55a-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="dc55a-112">Para obter mais informações e um exemplo, consulte [girar um objeto usando um caminho Geométrico (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="dc55a-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="dc55a-113">Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="dc55a-113">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc55a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc55a-114">See Also</span></span>  
 [<span data-ttu-id="dc55a-115">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="dc55a-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="dc55a-116">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="dc55a-116">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="dc55a-117">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="dc55a-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
