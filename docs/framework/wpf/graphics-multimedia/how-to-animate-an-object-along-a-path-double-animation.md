---
title: "Como animar um objeto ao longo de um caminho (animação dupla)"
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
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60f662562422169bc7b234ed0136797294f0b39a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="0c5d7-102">Como animar um objeto ao longo de um caminho (animação dupla)</span><span class="sxs-lookup"><span data-stu-id="0c5d7-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="0c5d7-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> classe para mover um objeto ao longo de um caminho definido por uma <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c5d7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c5d7-104">Example</span></span>  
 <span data-ttu-id="0c5d7-105">O exemplo a seguir usa duas <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico:</span><span class="sxs-lookup"><span data-stu-id="0c5d7-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="0c5d7-106">A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima a <xref:System.Windows.Media.TranslateTransform.X%2A> do <xref:System.Windows.Media.TranslateTransform> aplicada ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="0c5d7-107">Isto faz o retângulo mover horizontalmente ao longo do caminho.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="0c5d7-108">A segunda <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima a <xref:System.Windows.Media.TranslateTransform.Y%2A> do <xref:System.Windows.Media.TranslateTransform> aplicada ao retângulo.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="0c5d7-109">Isto faz o retângulo mover verticalmente ao longo do caminho.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="0c5d7-110">Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="0c5d7-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="0c5d7-111">Outra maneira de mover um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="0c5d7-112">Para obter um exemplo, consulte [animar um objeto ao longo de um caminho (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="0c5d7-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5d7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c5d7-113">See Also</span></span>  
 [<span data-ttu-id="0c5d7-114">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="0c5d7-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="0c5d7-115">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="0c5d7-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
