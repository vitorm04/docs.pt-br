---
title: 'Como: Animar a posição de um objeto usando PointAnimation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: db0551ba7c22e6c13ef2875e5f4ba681fc6df14d
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304785"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="91d3a-102">Como: Animar a posição de um objeto usando PointAnimation</span><span class="sxs-lookup"><span data-stu-id="91d3a-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="91d3a-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.PointAnimation> classe para animar um objeto ao longo de um <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="91d3a-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d3a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91d3a-104">Example</span></span>  
 <span data-ttu-id="91d3a-105">O exemplo a seguir move uma elipse ao longo de um <xref:System.Windows.Shapes.Path> de um ponto na tela para outra.</span><span class="sxs-lookup"><span data-stu-id="91d3a-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="91d3a-106">O exemplo anima a posição de um <xref:System.Windows.Media.EllipseGeometry> por meio <xref:System.Windows.Media.Animation.PointAnimation> animar o <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="91d3a-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="91d3a-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91d3a-107">See also</span></span>
- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [<span data-ttu-id="91d3a-108">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="91d3a-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="91d3a-109">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="91d3a-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="91d3a-110">Tópicos explicativos de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="91d3a-110">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="91d3a-111">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="91d3a-111">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
