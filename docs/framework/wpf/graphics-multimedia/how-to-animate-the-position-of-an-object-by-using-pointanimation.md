---
title: Como animar a posição de um objeto usando PointAnimation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 326b71c10ad608e2481673e1c4a8cbc9ecbdc0dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="59545-102">Como animar a posição de um objeto usando PointAnimation</span><span class="sxs-lookup"><span data-stu-id="59545-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="59545-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.PointAnimation> classe para animar um objeto ao longo de um <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="59545-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59545-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59545-104">Example</span></span>  
 <span data-ttu-id="59545-105">O exemplo a seguir move uma elipse ao longo de um <xref:System.Windows.Shapes.Path> de um ponto na tela para outra.</span><span class="sxs-lookup"><span data-stu-id="59545-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="59545-106">O exemplo anima a posição de um <xref:System.Windows.Media.EllipseGeometry> usando <xref:System.Windows.Media.Animation.PointAnimation> para animar a <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="59545-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="59545-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59545-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="59545-108">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="59545-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="59545-109">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="59545-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="59545-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="59545-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="59545-111">Animação e temporização</span><span class="sxs-lookup"><span data-stu-id="59545-111">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="59545-112">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="59545-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
