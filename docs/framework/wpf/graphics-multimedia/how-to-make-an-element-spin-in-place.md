---
title: Como criar um giro do elemento in-loco
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452786"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="10ba6-102">Como criar um giro do elemento in-loco</span><span class="sxs-lookup"><span data-stu-id="10ba6-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="10ba6-103">Este exemplo mostra como fazer um elemento girar usando um <xref:System.Windows.Media.RotateTransform> e um <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="10ba6-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="10ba6-104">O exemplo a seguir aplica o <xref:System.Windows.Media.RotateTransform> à propriedade <xref:System.Windows.UIElement.RenderTransform%2A> do elemento.</span><span class="sxs-lookup"><span data-stu-id="10ba6-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="10ba6-105">O exemplo usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> do <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="10ba6-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="10ba6-106">Para fazer com que o elemento gire no lugar, o exemplo define a propriedade <xref:System.Windows.UIElement.RenderTransformOrigin%2A> do elemento como o ponto (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="10ba6-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ba6-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10ba6-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="10ba6-108">Para obter o exemplo completo, que inclui mais exemplos de transformação, consulte [amostra de transformações 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="10ba6-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ba6-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="10ba6-109">See also</span></span>

- [<span data-ttu-id="10ba6-110">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="10ba6-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="10ba6-111">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="10ba6-111">Transforms Overview</span></span>](transforms-overview.md)
