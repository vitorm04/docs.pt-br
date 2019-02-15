---
title: 'Como: Animar um retângulo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], rectangles
- rectangles [WPF], animating
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
ms.openlocfilehash: dbff015bdc5f9ce56d2c366e0d348429efb7f4b5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305149"
---
# <a name="how-to-animate-a-rectangle"></a><span data-ttu-id="90dae-102">Como: Animar um retângulo</span><span class="sxs-lookup"><span data-stu-id="90dae-102">How to: Animate a Rectangle</span></span>
<span data-ttu-id="90dae-103">Este exemplo mostra como animar alterações de tamanho e posição de um retângulo.</span><span class="sxs-lookup"><span data-stu-id="90dae-103">This example shows how to animate changes to the size and position of a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90dae-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90dae-104">Example</span></span>  
 <span data-ttu-id="90dae-105">O exemplo a seguir usa uma instância das <xref:System.Windows.Media.Animation.RectAnimation> classe animar o <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriedade de um <xref:System.Windows.Media.RectangleGeometry>, que anima as alterações para o tamanho e posição do retângulo.</span><span class="sxs-lookup"><span data-stu-id="90dae-105">The following example uses an instance of the <xref:System.Windows.Media.Animation.RectAnimation> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>, which animates changes to the size and position of the rectangle.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="90dae-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90dae-106">See also</span></span>
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [<span data-ttu-id="90dae-107">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="90dae-107">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="90dae-108">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="90dae-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="90dae-109">Tópicos explicativos de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="90dae-109">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="90dae-110">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="90dae-110">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
