---
title: Como criar um giro do elemento in-loco
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 56385d7c31465e25f19486ea5cdaa8876cdb30ff
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534406"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="f979d-102">Como criar um giro do elemento in-loco</span><span class="sxs-lookup"><span data-stu-id="f979d-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="f979d-103">Este exemplo mostra como criar um elemento de rotação usando um <xref:System.Windows.Media.RotateTransform> e um <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="f979d-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="f979d-104">O exemplo a seguir aplica-se a <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="f979d-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="f979d-105">O exemplo usa uma <xref:System.Windows.Media.Animation.DoubleAnimation> animar o <xref:System.Windows.Media.RotateTransform.Angle%2A> da <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="f979d-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="f979d-106">Para fazer com que o elemento girar em vigor, o exemplo define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade do elemento para o ponto (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="f979d-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f979d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f979d-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="f979d-108">Para o exemplo completo, que inclui mais exemplos de transformação, consulte [exemplo de transformações 2D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="f979d-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f979d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f979d-109">See Also</span></span>  
 [<span data-ttu-id="f979d-110">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="f979d-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="f979d-111">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="f979d-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
